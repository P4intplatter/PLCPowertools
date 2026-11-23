# Teacher Toolbox: setup and upkeep

## First-time setup (about 10 minutes)
1. Create a free account at github.com, then click **New repository**. Name it (for example `teacher-toolbox`), set it to **Public**, and create it.
2. Click **Add file > Upload files**. Drag in `index.html`, `tools.json`, and the `images` and `tools` folders (`tools` holds your four HTML tools). Click **Commit changes**.
3. Go to **Settings > Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, choose **main** and **/ (root)**, then Save.
4. After a minute or two, your site is live at `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`.
5. Connect the feedback form (see "Feedback form setup" below).

## Feedback form setup
The feedback page sends responses to a Google Form you own, and they land in a Google Sheet in your Drive.
1. In Google Forms, make four questions, all **Short answer** except the last, which is **Paragraph**: `Email`, `Tool used`, `Issue`, `Additional details`. Using text questions (not dropdowns) means new tools never get rejected.
2. Leave **Collect email addresses** and **Limit to 1 response** off. If your Google account is a school one, open **Send** and make sure the form isn't restricted to people in your district.
3. On the **Responses** tab, click the green Sheets icon to link a spreadsheet.
4. Click the three dots, then **Get pre-filled link**, type any text in each question, click **Get link**, and paste that link to Claude (or use it to fill in the `feedback` block in `tools.json`).
5. Send a test response from the live site and check that it appears in the sheet.

## File names
Your tool files must match the `file` entries in `tools.json`, or rename the entries to match what you have:
- `tools/plc-test-analysis.html`
- `tools/accommodation-tracker.html`
- `tools/score-merger.html`
- `tools/missed-it.html`

## Updating a tool
1. In GitHub, open the `tools` folder, then **Add file > Upload files** and upload the new version with the same file name. It replaces the old one.
2. Open `tools.json`, bump that tool's `version` and `updated` date, and add a line to `changelog`. Commit.
3. Changes show up within a couple of minutes. The version number is added to each link, so teachers get the new file rather than a cached copy.

## Optional card fields
In `tools.json`, add `"status": "Beta"` to show a yellow badge, or `"note": "..."` to show a short highlighted message on the card (good for storage or privacy heads-ups).

## Card icons
Each tool has an `"icon"` in `tools.json`. Available names: `drill`, `saw`, `hammer`, `balance`, `wrench`, `screwdriver`, `level`, `tape-measure`, `pliers`, `clamp`, `magnifier`, `paintbrush`, `glue`. Change it to swap a card's icon. A name that isn't on the list simply shows no icon.

## Adding a tool
Upload the HTML file to `tools/`, then copy one block in `tools.json` and edit it. Mind the commas between blocks. If the site goes blank, paste the file into jsonlint.com to find the typo.

## Privacy checklist for every tool
- No `<script src="https://...">`, no web fonts, no analytics, no `fetch()` to outside sites. Everything the tool needs should be inside the one HTML file.
- If a tool saves anything with `localStorage`, use a unique key prefix (like `plc_` or `missedit_`), because all tools on your site share one storage area.
- Never put real student data in a GitHub repo or an issue. Feedback links remind teachers of this.
