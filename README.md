# LinkForge

LinkForge is a web application built with **React** on the frontend and **Express.js** on the backend.

## Project structure

This repository is currently empty. When the application files are added, document the actual layout here. A common structure for this stack is:

```text
LinkForge/
├── client/   # React frontend
└── server/   # Express.js API
```

## Prerequisites

- [Node.js](https://nodejs.org/) (includes npm)
- npm, or another Node.js package manager

## Getting started

After the frontend and backend source code and their `package.json` files are in place, install dependencies in each app directory:

```bash
cd server && npm install
cd ../client && npm install
```

Start the backend and frontend using the scripts defined in their respective `package.json` files. For example, if both define a `dev` script:

```bash
# Terminal 1
cd server && npm run dev

# Terminal 2
cd client && npm run dev
```

The exact scripts, local URLs, environment variables, and API routes depend on the project configuration and should be filled in once those files are added.

## Configuration

Add any required environment variables to a local `.env` file in the relevant app directory. Do not commit secrets. If the app needs environment variables, document their names and purpose here and provide safe example values in a `.env.example` file.

## Development notes

- React is responsible for the user interface.
- Express.js is responsible for backend routes and API behavior.
- Configure the frontend API base URL and backend CORS settings to match the local development setup.

## License

No license has been specified yet.
