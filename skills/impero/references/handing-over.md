# Handing over

For moving someone's open work to another person, as when they go on leave or leave.

- **To see their work first,** call `impero_list_activities` with scope `visible` and their `waiting_on_user_id`, from `impero_search`. That lists what waits on them now; the panel also lists activities where a later step is theirs.
- **To move it,** call `impero_open_reassign`. The person ticks which activities to move, and confirms in the panel.
- **Some rows can't move,** and the panel says why. Those are changed in Impero.
- **Only open activities move.** The next periods' activities follow the control's setup, which `impero_get_control` shows under its assignments, and which is changed in Impero. `impero_list_changes` shows when an assignment was changed, and by whom.
- **Afterwards,** the activity's timeline shows the reassignment, with whom the step went to.
