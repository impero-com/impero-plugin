# Reassigning

For reassigning someone's open work to another person, as when they go on leave or leave.

- **To see their work first,** call `impero_list_activities` with scope `visible` and their `waiting_on_user_id`, from `impero_search`. That lists what waits on them now; the panel also lists activities where a later step is theirs. In large organizations, start from a program: give `program_id` here and to the panel, one panel per program.
- **To reassign it,** call `impero_open_reassign`. The person ticks which activities to reassign, and confirms in the panel.
- **Some rows can't be reassigned,** and the panel says why. Those are changed in Impero.
- **Only open activities are reassigned.** The next periods' activities follow the control's Assignees, which `impero_get_control` shows under its assignments, and which are changed in Impero's control editor. Reassigning a control can mean either: when it's unclear which the person means, ask. `impero_list_changes` shows when an assignment was changed, and by whom.
- **Afterwards,** the activity's timeline shows the reassignment, with whom the step went to.
