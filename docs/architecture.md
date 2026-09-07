# Architecture

Browser → React/Vite → Axios → Express REST API → route handlers/controllers → Prisma ORM → SQLite.

JWT tokens are issued on login and attached as Bearer tokens by Axios. Candidates, jobs and applications are related through Prisma. Dashboard and analytics endpoints aggregate live application data.
