Unlimited Undo-Redo

Audacity handles undo-redo using a stack of complete copies of all the tracks in the project. When  the user modifies the project audio, a complete copy of the audio in every track in the project is copied onto the undo-redo stack at the current position, removing all potential redos and making the current position the new top of the stack. When the user requests an undo, the current position on the undo-redo stack is decremented, and all audio tracks in the project are replaced by the copy on the stack at the current position. When the user requests a redo, which is only available if the current position is not the top of the stack, the current position is incremented and all audio tracks in the project are replace by the copy on the stack at the current position.

This approach has several significant weaknesses:
	1) Storing a complete copy of every change consumes unnecessarily large amounts of memory. 	
	2) The user cannot chose to revert changes on a track-by-track basis.
	3) Upon changing a track after undoing, all the states that were reachable by redo are lost.

1) The large memory requirements of this method of undo-redo handling are well understood by the authors of Audacity. Audacity will tell the user how much memory is currently being used by each entry the undo-redo stack, and the user can delete entries from the bottom of the stack manually. Operations that perform multiple small modifications to the audio only generate a stack entry for every three changes.
A standard response to this problem is the command pattern [1]. The command pattern is a software design pattern where actions taken by the user on the data are encapsulated in a command object. Each command object contains a method (or reference to and object that performs the method) that performs the change the command applies to the data. When used in an undo-redo stack, command objects also contain a method  which performs the reverse operation on the data. In the case where an operation is irreversible, the command object retains a copy of only the part of the data that was altered. These objects are then stored on the undo-redo stack as opposed to entire copies of the data, and their operations are run and reversed for redos and undos respectively. These objects consume far less memory that copies of every track, and still allow the user the full range of undo-redo functionality.

2) Most audio effects in Audacity are applied to a single waveform at a time. This lends itself naturally to an undo mechanism connected to each track individually. The natural argument against this is that it defies the users expectations, a serious violation of most user interface design doctrine. 
Here the solution is simple: Add a keyboard shortcut which allows the user to undo-redo for the currently active track, and keep a track-by-track undo-redo stack. This maintains the users expectations for the project as a whole, and allows a more experienced user to achieve more specific results.

3) When a user undoes their changes to reference some earlier state (not because they dislike their changes) they often lose track of the fact that any change to the current state will delete all potential redos, and that work will be permanently lost. This is a common mistake and significantly discourages the user.
Tree-based undo systems solve this problem very elegantly. Instead of a stack, the previous states of the data are stored in a tree. As the user works forward this tree initially resembles a stack. When the user backtracks with undo and then makes a change, the tree branches off at the point at which the change is made. The standard undo command moves the user closer to the root, and the standard redo command move the user down the tree towards the leaf that is a descendant of the current node with the latest modification time. . If the user wishes to recover changes on another branch, they must select from a specific undo-redo tree user interface. Combined with the command pattern, this tree structure is relatively memory efficient. This approach provides the user complete freedom with their undo-redo use, as no data is ever lost.

The fully copy stack approach currently used by Audacity has its benefits as well:
	1) New data-altering functionality does not have to worry about being reversible.
	2) Development simplicity.

1) Many of the operations applied to waveforms are irreversible (phaser, click removal, wahwah). This means if the command pattern is employed, a copy of the previous state of the audio must be maintained. This leads to marginal benefits over full copies of the entire track in cases where these operations are applied often.

2) Undo-redo trees are more complicated to develop, and thus required more developer time. In an open source project such as Audacity, developer time is a precious commodity and may be better spend on other functionality. The full copy stack approach to undo-redo is simple to develop and maintain, and performs well enough for everyday use.

Audacity's full copy stack undo-redo functionality could be improved by implementing the command pattern, track-by-track undo-redo, and using an undo-redo tree. These improvements would improve the user experience in Audacity. However, the current undo-redo functionality performs well enough, and restrictions on irreversible waveform functions and developer time make the suggested improvements difficult to implement.

[1] E. Gamma, R. Helm, R. Johnson, and J. Vlissides, Design Patterns. Boston, MA: Addison-Wesley, 2009, ch. 5, pp. 233-242.
