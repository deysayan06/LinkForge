# Repository Guidelines

## Project Structure & Module Organization

LinkForge is a URL shortener built with React, Vite, Express, and Node.js. The documented application layout is `client/` for the frontend and `server/src/` for the API and in-memory URL store, with backend tests in `server/test/`. The current checkout contains only `README.md` and `AGENTS.md`; treat the app paths as the intended layout until the source is present. Keep tests and assets with the app they support.

## Build, Test, and Development Commands

The README documents root npm scripts for installing dependencies, running the API and frontend together, starting the API, testing, and building. No `package.json` is present in this checkout, so these commands are not currently runnable here. When manifests are added, use and maintain the scripts defined there; do not assume separate `web/` or integration-test commands.

## Coding Style & Naming Conventions

Use modern JavaScript and follow the conventions of the touched module. Use 2-space indentation, `camelCase` for variables and functions, and `PascalCase` for React components (for example, `LinkCard.jsx`). Keep filenames descriptive. Shape API responses as `{ "data": ... }` for success and `{ "error": ... }` for errors, consistent with the README.

## Testing Guidelines

The documented backend tests use Node.js's built-in `node:test` runner and exercise the API through an ephemeral HTTP listener. Place backend tests in `server/test/` and add regression coverage for behavior changes. Run the test script defined in the root package manifest once it is available. No coverage threshold is specified.

## Commit & Pull Request Guidelines

Use concise, imperative commit subjects, such as `Add short URL lookup`. Pull requests should summarize the change, report tests run, describe setup or configuration changes, and include screenshots for visible UI changes.

## Security & Configuration

Do not commit secrets or local `.env` files. Documented server settings are `PORT` and `BASE_URL`; `VITE_API_URL` can override the frontend API origin. The URL store is in memory and resets when the API restarts. Avoid committing generated output.
