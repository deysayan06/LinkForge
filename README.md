# LinkForge

LinkForge is a full-stack URL shortener built with React, Vite, Express, and Node.js. Submit an HTTP or HTTPS URL in the browser to create a compact link, copy it, inspect its details through the API, or follow it to the original destination.

## Project structure

The application layout below describes the intended project structure. The current checkout contains this README and `AGENTS.md`; application source and package manifests are not present yet.

```text
.
├── client/             # React and Vite frontend
├── server/
│   ├── src/            # Express app, entry point, and in-memory store
│   └── test/           # Black-box API tests
├── AGENTS.md           # Contributor guidance
└── package.json        # Root development scripts
```

## Requirements and setup

- Node.js 20.19 or newer (or Node.js 22.12+)
- npm

Once the root and app package manifests are added, install dependencies from the repository root:

```bash
npm install
npm run install:all
```

Then start the frontend and API together:

```bash
npm run dev
```

The frontend runs at `http://localhost:5173` and the API defaults to `http://localhost:3000`.

## Commands

These are the intended root commands. They become available when the root `package.json` and app manifests are added:

| Command | Purpose |
| --- | --- |
| `npm run dev` | Run the Express API and Vite development server |
| `npm start` | Start only the Express API |
| `npm test` | Run the backend test suite |
| `npm run build` | Create a production frontend build |
| `npm run install:all` | Install backend and frontend dependencies |

## Configuration

The server reads these optional environment variables:

| Variable | Default | Description |
| --- | --- | --- |
| `PORT` | `3000` | Express listening port |
| `BASE_URL` | `http://localhost:3000` | Public origin used in generated short URLs |

The Vite app uses `VITE_API_URL` when it needs a non-default API origin. For example:

```env
VITE_API_URL=http://localhost:3000/api
```

Keep local values in `.env` files and ensure those files are ignored by Git before adding secrets.

## API

All API results use either `{ "data": ... }` or `{ "error": "..." }`.

| Method | Endpoint | Result |
| --- | --- | --- |
| `GET` | `/api/health` | API health status |
| `GET` | `/api/urls` | List the 10 most recently created links |
| `POST` | `/api/urls` | Create a short URL from `{ "url": "https://example.com" }` |
| `GET` | `/api/urls/:shortCode` | Retrieve a stored URL record |
| `DELETE` | `/api/urls/:shortCode` | Delete a stored short URL |
| `GET` | `/:shortCode` | Redirect to the original URL |

Example:

```bash
curl -X POST http://localhost:3000/api/urls \
  -H 'Content-Type: application/json' \
  -d '{"url":"https://example.com/a-long-path"}'
```

Successful creation returns `201` with the original URL, generated `shortCode`, public `shortUrl`, creation time, and visit count. Invalid URLs return `400`; unknown codes return `404`.

## Testing and persistence

The intended backend tests use Node's built-in `node:test` runner and make requests to an ephemeral HTTP listener. Once the server package is present, run them with `npm test` or directly with `npm test --prefix server`.

The planned URL store is an in-memory `Map`; links will reset whenever the API restarts. Use a persistent datastore before deploying for production.

## Contributing

Read [AGENTS.md](./AGENTS.md) before making changes. Do not commit secrets or generated output, and include test results plus screenshots for user-interface changes in pull requests.
