# Impero for Claude

The official [Impero](https://www.impero.com) plugin for Claude. It connects Claude to Impero, so you can work with your controls and activities in plain language in Claude, Cowork and Claude Code.

## What's included

- **The Impero connector.** Claude connects to Impero's MCP server at `https://login.impero.com/mcp` and works with Impero as you, with the same access you have.
- **The Impero skill.** How Impero is organised, from programs and controls to activities and their review steps, and how to use the connector for common tasks.

With them, you can ask Claude to:

- Show what's due, overdue or waiting for your review
- Review a submission against its control and its files
- Remind, extend, reopen or reassign an activity
- Fill in and submit your own activities
- Draft a new control
- Check the Dashboard or recent changes to your setup
- See your risks and the controls that mitigate them
- Find a user group and see what waits on it

Claude can't change anything in Impero by itself. Changes are made in an Impero panel in the conversation, and only when you confirm them. Claude Code doesn't show panels, so there Claude gives you a link to make the change in Impero instead.

## Installation

### Claude Code

```
/plugin marketplace add impero-com/impero-plugin
/plugin install impero@impero
```

Then run `/mcp`, select **impero** and sign in with your Impero account.

### Claude and Cowork

Add the marketplace `impero-com/impero-plugin` under **Customize > Plugins** and add the Impero plugin. Then connect it from the plugin's **Connectors** tab and sign in with your Impero account.

## Requirements

- An Impero account with the **MCP user** role. Administrators have access already.
- Impero needs to have turned on the connector for your organisation. Ask your Impero contact or [Impero support](https://support.impero.com).

## Privacy and support

The plugin sends your requests only to Impero's server. See Impero's [privacy policy](https://www.impero.com/privacy-policy). For help, contact [Impero support](https://support.impero.com).

## License

MIT. See [LICENSE](LICENSE).
