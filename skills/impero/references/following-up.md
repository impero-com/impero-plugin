# Following up

For late and overdue work: reminding people, extending due dates and reopening completed activities.

## Find the work

- The person's own late work: `impero_list_activities` with scope `mine` and due `overdue`.
- Someone else's, or a program's: scope `visible` with `waiting_on_user_id`, `program_id` or another filter, and due `overdue` or a due window. `health` shows which ran late before.

## Choose what fits

- **A reminder** nudges whoever the activity waits on now, with Impero's own email and an optional message. `impero_open_remind`.
- **An extension** moves the final due date, and every step not yet done by the same amount, so a step can stay overdue. It needs the organisation to allow moving due dates. `impero_open_extend`.
- **A reopen** sends a completed activity back to be performed again, every step, with an optional comment and new due date. `impero_open_reopen`.

A panel holds up to 25 activities. For more, open one panel, and the next once the person is done with it.

## What stops it

The panel lists each activity it won't act on, and why. Two of the reasons are about people, not the activity:

- **A deactivated person** can't be reminded, and work waiting on them stays where it is until it's moved to someone else: see [Handing over](handing-over.md).
- **A group with nobody in it** has no one to email. Who holds the step is changed in Impero.

## Afterwards

The activity's timeline, from `impero_get_activity_timeline`, shows the reminder, the extension or the reopen, with its source `agent` when it was made through a connector like this one.
