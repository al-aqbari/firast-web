# firast-web
this is a firast web in my laife

## CityCot University — Staff Information System (SIS) · Upgrade v2

`apps-script/` holds an add-on for the existing Google Apps Script project
(`Code.gs` + `Index.html`). It adds, without rewriting the original files:

- **New Executive Overview**: welcome banner, an HR Health Score gauge, and instant smart insights (expiring contracts, unverified qualifications, data completeness …).
- **AI Executive Briefing**: a summary, the main risks and recommended actions, written by Claude.
- **HR AI Assistant**: a chat window (✨ button, or Ctrl+J) that answers questions about the workforce in English or Somali.
- **Draft letters with AI**: a "✨ Draft with AI" button in HR Correspondence → Create Letter.
- **Command palette** (Ctrl+K): jump to any page or employee.
- **Dark mode** (🌙 button in the top bar).
- **Administration → AI Settings**: add the API key and choose the model.

### Installation

1. In the Apps Script editor, add a script file named **`AI`** and paste in `apps-script/AI.gs`.
2. Add an HTML file named **`Upgrade`** and paste in `apps-script/Upgrade.html`.
3. In `Index.html`, add this line just before `</body>`:
   ```html
   <?!= include('Upgrade'); ?>
   ```
4. **Deploy → Manage deployments → Edit → New version**.
5. Sign in as an administrator, open **Administration → AI Settings** and paste your Anthropic API key (from console.anthropic.com).

You do not need to change `Code.gs`: `AI.gs` reuses its helpers.

### Privacy

When someone uses an AI feature, a summary of the staff records **that person is already allowed to see** is sent to the Anthropic API. Users limited to one campus send only that campus; salary is included only for roles with the `viewSalary` permission. The key is kept in Script Properties, and every AI action is recorded in the Audit Log.
