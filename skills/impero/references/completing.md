# Completing a control

For the person's own work as a performer: what an activity asks them to fill in, what they've saved so far, and where they answer it.

## Read it first

- Call `impero_get_activity` for the activity. What it asks is the control's `description` and the tasks on the `responsible` step: each task's title, `instructions` and `options`. Headings ask nothing.
- On the `responsible` step, `answers` says what's there: `saved` means a draft was saved and not submitted, and `returned` that a reviewer sent it back. A comment with event `rejected` says what the reviewer asked for.
- Figures the person gave you in the chat, or in a file they attached there, are what they've given you, not what's in Impero.

## The activity form

When the person works through their own activity with you, or asks you to fill it in, save or submit it, open it with `impero_open_activity_form`, so they see what you're talking about: what each task asks, its instructions, the control's own files, and what's saved. One activity at a time: a new form replaces the last.

- **Suggest into it** with `impero_suggest`, from what the person gave you in the chat: a figure they typed, a statement or a workbook they attached. One task a call, by its title as `impero_get_activity` gives it. A table goes whole, as `rows`, one string per row with its cells separated by tabs in the task's column order, so adding a row or fixing one cell sends every other row as it stands. A suggestion waits in the form, tagged, until the person takes it. Never say it's filled in or taken: only the person takes it. Don't open the form again to change a suggestion, which would replace the panel and what the person typed in it: suggest again.
- The person fills it in, saves a draft and submits it themselves, in the panel. Saving keeps the form open and emails nobody; submitting goes through Impero's Complete control step, with a comment for the reviewer when there is one. Never say it's saved or submitted until the panel says so, or the activity, read again, shows it.
- **A Currency task or a datasheet** is filled in on Impero's page. While a Currency task shows, or a datasheet that changed in Impero since it was saved or has cells Impero would refuse, the form is submitted there: the panel's Open in Impero takes Submit's place. The result's `counts.datasheets_blocking` says how many such datasheets show.
- **A group's step,** or one segregation of duties keeps from the person, opens read-only. Say what the panel says, and give the activity's link.
- **Not theirs:** when it waits on someone else, on a review, or is done, no panel opens. Say where it stands, as the answer does, with its link. A review that waits on the person opens with `impero_open_review`.
