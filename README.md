# auth-system-frontend

A React + Vite + Tailwind CSS v4 front end for [simple-authentication-system](https://github.com/Onileola14/simple-authentication-system) — a JWT + bcrypt auth API with role-based access control.

## Features

- **Sign in / sign up** in one panel with tabbed switching
- Client-side validation mirroring the API (`name` ≥ 3, valid email, `password` ≥ 6) plus an advisory password-strength meter
- Real calls to the API with `credentials: "include"`, so the `httpOnly` JWT cookie flows automatically
- Inline surfacing of server validation errors
- **RBAC-aware account console** — shows the user's role (admin/user) and the routes available to them, with sign-out hitting `/auth/logout`
- Stark, technical brutalist aesthetic: near-black canvas, hairline grid, mono labels, slab display, single acid accent

## Tech stack

- React 19 + React DOM 19
- Vite 8, TypeScript 5.7
- Tailwind CSS v4 (`@tailwindcss/vite`)

## Getting started

```bash
npm install
npm run dev
```

The app expects the auth API at `http://localhost:3000/api/v2`. Override with an env var:

```bash
VITE_API_BASE=https://your-api.example.com/api/v2 npm run dev
```

## API endpoints used

| Method | Endpoint          | Purpose                     |
| ------ | ----------------- | --------------------------- |
| POST   | `/auth/register`  | Create an account           |
| POST   | `/auth/login`     | Log in, sets the JWT cookie |
| GET    | `/auth/logout`    | Clear the auth cookie       |

The backend's user routes (`/user`, `/user/:id`, `/user/:id/password`) are surfaced in the console UI for reference.

## Notes

- In development the API's `cors()` is open to all origins, so browser calls work out of the box. Restrict it to this app's origin before production.
- This is the front end only; run the [backend](https://github.com/Onileola14/simple-authentication-system) separately.
