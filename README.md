# REVODIX Inquiry Management — Vercel Deployment Package

A static website containing the same screens, styles, and demo behavior as the existing public demo. It uses HTML, CSS, and plain JavaScript. No application build, dependency installation, environment variables, or API keys are required.

Existing demo: [REVODIX Inquiry Management](https://revodix-inquiry-demo.nimblecrown17.chatgpt.site/)

## Deployment Request for the Developer

Upload this folder to a separate Git repository and deploy it as a new Vercel project. Use the folder containing `vercel.json` as the project root and serve `dist` as the static output directory. After deployment, share the Production URL for distribution to the client.

## Deploying to Vercel

### Option 1: Connect a Git Repository

1. Extract the ZIP and add all files inside `revodix-vercel` to a GitHub, GitLab, or Bitbucket repository. Keep `vercel.json` and `dist` in the same parent folder.
2. Create a new project in Vercel and import the repository.
3. Check the settings below, then deploy. These settings are already declared in the included `vercel.json`.

| Setting | Value |
| --- | --- |
| Framework Preset | Other |
| Root Directory | The folder containing `vercel.json`. Keep the default if these files are at the repository root. |
| Build Command | Leave empty to skip the build step. |
| Install Command | Leave empty to skip dependency installation. |
| Output Directory | `dist` |
| Environment Variables | None |

Do not select `dist` itself as the project root. The project root must contain `vercel.json`.

### Option 2: Vercel CLI

With the Vercel CLI installed and your account signed in, run the following from the extracted folder:

```sh
cd revodix-vercel
vercel --prod
```

During initial setup, select the owning team, create a new project, and use the current folder as the project root. No install or build command needs to be added. The application has no dependencies; Node.js is only needed to run the CLI.

After deployment, check the dashboard and `/#inbox` at the Production URL. For public sharing, also check the Vercel project's Deployment Protection settings. The application itself has no login screen.

Configuration references: [Skipping the build step for static websites](https://vercel.com/docs/builds#skipping-the-build-step), [vercel.json configuration](https://vercel.com/docs/project-configuration/vercel-json), and [CLI deployment](https://vercel.com/docs/cli/deploying-from-cli).

## Running Locally

If Python 3 is available, run this command from the project root and open `http://localhost:8788`:

```sh
python3 -m http.server 8788 --bind 127.0.0.1 --directory dist
```

## File Structure

```text
revodix-vercel/
├── README.md
├── vercel.json
├── .gitignore
└── dist/
    ├── index.html
    ├── styles.css
    ├── ui.js
    ├── data.js
    ├── app.js
    ├── management.js
    └── actions.js
```

The files in `dist` are editable application source files, rather than minified or obfuscated build artifacts. `data.js` contains fictional inquiries and documents, `app.js` and `management.js` render the screens, and `actions.js` implements demo interactions. Edit these files and redeploy to publish changes.

Navigation uses URL hashes such as `/#dashboard` and `/#inbox`, so no additional SPA rewrite rules are required. There are no API calls tied to the original hosting domain. The Pretendard font loads from a CDN, with system fonts used as a fallback.

## Included Demo Features

- Operations dashboard, unified inbox, and analytics reports
- Sample inquiries from Amaranth 10 email, KakaoTalk Channel, Channel Talk, and the website inquiry form
- Draft editing, approval, hold, rejection, simulated sending, assignee management, and internal notes
- Reference document review, knowledge creation and editing, version management, and review of corrected replies for inclusion in shared knowledge
- Response mode and review settings, with outage, duplicate receipt, and failed sending scenarios
- Channel status, activity history, demo user roles, and CSV export

## Integrations Required for Production

This package is a frontend demo for client review. Live channel collection and sending, LLM calls, RAG retrieval, document parsing, authentication, server-side authorization, and a database are not connected. Customers, users, equipment, and manuals shown in the application are fictional. Sample evaluation results do not measure actual model performance.

Changes are saved in each browser's `localStorage` under the key `revodix.demo.v1`. Data is not synchronized between users. A new Vercel domain starts with the initial sample state. The demo can be reset from the Users & Operations Settings screen (`/#settings`). Role selection is provided to demonstrate the interface.

The ZIP excludes real REVODIX customer data, the original quotation, contract terms, credentials, original hosting project settings, and Git history. Relay source files are also excluded.

## Package Verification

The public demo's baseline source commit is `1a9f00f440b13612c893e6ab1a5cc73d4ab6ef4f`. All seven files in `dist` are byte-for-byte identical to the baseline checkout. JavaScript syntax, static asset references, and ZIP integrity have been checked. Deployment to a Vercel account is to be performed by the developer.
