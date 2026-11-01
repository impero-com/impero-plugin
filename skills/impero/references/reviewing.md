# Reviewing

For first and second reviews, and for pre-assessing the submissions waiting for one. The records say what was asked and what was submitted; deciding is the reviewer's, in Impero.

## Find the work

- Call `impero_list_activities` with scope `mine` and step `first_reviewer` (`second_reviewer` or `any_reviewer` when asked). Follow `next_cursor` until there's none.
- For only what's new, add `submitted_from`: in a scheduled run, the time your last run started, which you or your flow stored, since the service keeps no record of runs; in chat, the time or date the person gives. A resubmission is new.
- Two cases don't show as new. An activity the second reviewer sends back to the first keeps its old time. And a second review carries the responsible's submission time, not when the first reviewer passed it on, so a second reviewer's run can't rely on `submitted_from`. Say so when it matters.

## Read the activities

- Call `impero_get_activities` with up to 25 `activity_ids`; split more into calls of 25. Take one part at a time: get its files and work through it, then pass `next_cursor` as `cursor` for the next part.
- An activity under `not_read` wasn't read: pass on its message, and say nothing about what it holds.

## Get the evidence

- Call `impero_get_file` with each file's `file_id` and the id of the activity it's on.
- If the file doesn't reach you, use its `download_url`: the one in `impero_get_activities` works until `downloads_expire_at`, 15 minutes after its part, and the one in `impero_get_file` for 15 minutes after that call. If you can't fetch links yourself, give the person each file's `download_url` (not the activity's `url`), say until when the links work, and ask them to download and attach the files. Don't wait: work with what you have now, and again once they're attached. In an automation, a step of the flow downloads them for you.
- A task's `missing_files` counts files the performer attached that Impero no longer has. There is nothing to fetch.

## What the records mean

- What the control asks for is its `description` and the tasks on the `responsible` step: each task's title, `instructions` and `options`. The description often doesn't repeat the tasks, and a task asks for its answer even where the description doesn't mention it. Headings ask nothing. Tasks a condition hides aren't returned; don't ask for them.
- `programs` lists each activity's program once. Its `description`, tags and entities are part of what the customer set up, as the control's description is. A program the person can't see in Impero is left out, and the summary says so: don't guess what it holds.
- Tasks on the reviewer steps are the reviewer's own checklist for the review. The reviewer answers them, not the performer.
- An answer is what the performer typed or chose. One that says figures agree, names a file's period or says there's nothing to explain is their statement, not a reading of the file.
- Impero enforces mandatory tasks on submit, but a submitted answer can still look empty: nothing chosen, no rows, only spaces, or files Impero no longer has. `answered` is false for those.
- An answer marked `truncated`, or with fewer `rows` than `rows_total`, is shown only in part.
- On the `responsible` step, `answers` says what there is: `returned` means a reviewer sent it back and it hasn't been submitted again, `saved` that it was saved but never submitted, and `none` that nothing was answered. In all three there is no submission to review.
- A comment with event `rejected` means a reviewer returned the submission. Its text says what they asked for.

## The previous period

`previous` is last period's activity of the same control, with its answers, comments and files. It's there for continuity: this period's opening balance against last period's closing one, recurring items, what the last reviewer said. Its approval covers that period only. It's left out when there's no single activity for the period before, and when it couldn't be read, which the activity's summary then says.

## The review panel

When the person goes through their own review with you, or asks you to approve or return it, open it with `impero_open_review`, so they see what you're talking about: one activity at a time. The decision is theirs: never say it's decided.

While it's open, put what you'd suggest into it with `impero_suggest`: the comment, or the answer to one of the person's own review tasks, by its title as `impero_get_activity` gives it, one task a call. It shows in the panel tagged as suggested, and waits there until the person takes it. Never say a suggestion is sent, taken or submitted: only the person takes it and submits. Don't open the review again to change one, which would replace the panel and what the person typed in it: suggest again.
