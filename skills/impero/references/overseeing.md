# Overseeing

For how controls are going: rates and trends, what happened to an activity, and who changed the setup.

- **The overview:** `impero_get_dashboard` returns Impero's Dashboard for activities due in a range, for one program, tag or entity, or all the person can see.
- **The activities behind it:** `impero_list_activities` with scope `visible`, the same range as due dates, and a `health` filter such as `any_friction`, sorted by `health`. Each item has its health as Impero's Health column shows it. In large organizations, start from the overview, then list one program at a time.
- **One activity's history:** `impero_get_activity_timeline` lists every event, oldest first, with who did it, whom it then waited on, and whether that step was overdue. Its source `Agent` means it was made through an AI connector.
- **Changes to the setup:** `impero_list_changes`, for what changed on programs, controls and entities, and who changed it. It reads up to 31 days a call: for a longer period, such as how a control was set up earlier in the year, read it a month at a time. What happened to an activity is in its timeline instead.
- **User groups:** `impero_list_groups` lists them, with who created each and, at detail `full`, their members: who is in a group, or which groups someone is in with `member_user_id`. What waits on a group is `impero_list_activities` with scope `visible` and its `waiting_on_group_id`: only the activities waiting on the group now, not those where it holds a later step.
- **Words:** Friction means an activity was overdue, or was rejected or reopened. Say what happened, as Impero does; Impero doesn't rate controls or people.
- **Reviewing a framework:** when the person asks you to review their controls, list the program's controls with `impero_list_controls`, and read each with `impero_get_control` at detail `full`. Point out instructions that are unclear, controls that overlap, a responsibility split across controls or people, and controls that don't follow the program's usual shape. Say what you'd change and why: the changes are made in Impero, and a new control is drafted with `impero_open_control_draft`.
