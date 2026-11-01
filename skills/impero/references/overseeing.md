# Overseeing

For how controls are going: rates and trends, what happened to an activity, and who changed the setup.

- **The overview:** `impero_get_control_health` returns Impero's Control Health dashboard for activities due in a range, for one program, tag or entity, or all the person can see.
- **The activities behind it:** `impero_list_activities` with scope `visible`, the same range as due dates, and `friction`, sorted by `health`. Each item has its health as Impero's Health column shows it.
- **One activity's history:** `impero_get_activity_timeline` lists every event, oldest first, with who did it, whom it then waited on, and whether that step ran late. Its source `agent` means it was made through an AI connector.
- **Changes to the setup:** `impero_list_changes`, for what changed on programs, controls and entities, and who changed it. What happened to an activity is in its timeline instead.
- **Words:** friction means an activity ran late, or was rejected or reopened. Say what happened, as Impero does; Impero doesn't rate controls or people.
- **Reviewing a framework:** when the person asks you to review their controls, list the program's controls with `impero_search`, and read each with `impero_get_control` at detail `full`. Point out instructions that are unclear, controls that overlap, a responsibility split across controls or people, and controls that don't follow the program's usual shape. Say what you'd change and why: the changes are made in Impero, and a new control is drafted with `impero_open_control_draft`.
