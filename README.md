# Phonebook

A phonebook backend built with Node.js, Express, and MongoDB for Full Stack Open. It stores names and phone numbers and serves a bundled React frontend from `dist/`.

The source frontend and the course version of this backend are available in [fullstackopen](https://github.com/DanielD221/fullstackopen), under `part2/the_phonebook` and `part3/phonebook_backend`.

## Features

- List, add, edit, and delete contacts.
- Require a name and number when adding a contact.
- Reject duplicate names when creating contacts.
- Display the number of stored contacts at `/info`.
- Persist contacts with Mongoose and expose a JSON API.
- Serve the included frontend and API from the same origin.

## Run locally

Requires Node.js 24, npm, and a MongoDB database.

```sh
npm ci
```

Create a `.env` file:

```dotenv
MONGODB_URI=mongodb://127.0.0.1:27017/phonebook
PORT=3001
```

```sh
npm run dev
```

Open `http://localhost:3001`. Use `npm start` to run without file watching. The port defaults to `3001` if `PORT` is unset.

## API

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/api/persons` | List contacts |
| GET | `/api/persons/:id` | Retrieve a contact |
| POST | `/api/persons` | Create a contact |
| PUT | `/api/persons/:id` | Update a contact |
| DELETE | `/api/persons/:id` | Delete a contact |
| GET | `/info` | Show contact count and server time |

Contact request body:

```json
{
  "name": "Example Person",
  "number": "040-1234567"
}
```

## Frontend and deployment

This checkout already includes the static frontend in `dist/`. Its original documented deployment URL is [fullstackopen-jhw7.onrender.com](https://fullstackopen-jhw7.onrender.com); availability depends on the hosting service.

The `build:ui` and `deploy:full` scripts were written for the directory layout in the course repository. They do not work unchanged in an isolated clone of this repository. To rebuild the UI, use the frontend source in `fullstackopen/part2/the_phonebook`, then copy its build output into this repository's `dist/`.

## Structure

- `index.js` — server, routes, and middleware.
- `models/person.js` — database connection and contact model.
- `utils/requestLogger.js` — request logging.
- `dist/` — bundled frontend.
- `mongo.js` — a separate command-line database exercise.

## Development status

This is a learning project without authentication. The `npm test` command is a placeholder and exits with an error; no automated test suite is configured in this repository.
