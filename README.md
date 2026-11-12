# Streamy API Database

A tiny REST backend for Streamy, an all-in-one streaming website. It stores the list of streams (a title, a description and an optional owner) and serves them over HTTP so the Streamy front end can read, create, edit and delete streams.

It is built with [json-server](https://github.com/typicode/json-server), which turns a single JSON file (`db.json`) into a full REST API with no code.

## What it does

- Serves a `streams` collection from `db.json` at `http://localhost:3001/streams`.
- Supports the usual REST calls: `GET`, `POST`, `PUT`, `PATCH` and `DELETE`.
- Supports json-server features such as filtering (`/streams?userId=...`), sorting, paging and full text search (`?q=`).
- Watches `db.json` and saves any change made through the API back to that file.

A stream looks like this:

```json
{
  "id": 2,
  "title": "Did something",
  "description": "Fail??",
  "userId": "some-user-id"
}
```

`userId` is optional. It is the id of the user who owns the stream in the Streamy front end.

## Tech stack

- Node.js
- json-server 0.15 (Express under the hood)

## Run it

You need Node.js and npm installed.

```bash
npm install
npm start
```

The API is then available at http://localhost:3001. Try it:

```bash
curl http://localhost:3001/streams
curl -X POST -H "Content-Type: application/json" \
  -d '{"title":"My stream","description":"Hello"}' \
  http://localhost:3001/streams
```

Edit `db.json` to change the starting data.

## Status

Working prototype. It has no login or access control, so anyone who can reach the server can change the data. Use it for local development and demos only, and do not expose it to the public internet as it is.

There is no static live demo, because it is a server. To try it, run it locally as described above.

## Credits

Built on [json-server](https://github.com/typicode/json-server) by typicode. The Streamy front end is a separate project.
