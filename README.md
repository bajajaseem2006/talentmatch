# TalentMatch

TalentMatch is a technical talent placement and application management system. It uses synthetic data for academic/training demonstration.

## Run locally

1. `npm install --prefix server && npm install --prefix client`
2. Copy `server/.env.example` to `server/.env` and set values.
3. `npm --prefix server run db:setup && npm --prefix server run db:seed`
4. In separate terminals: `npm run dev:server` and `npm run dev:client`

Open `http://localhost:5173`. Demo accounts: `admin@talentmatch.demo` / `admin123`, and `recruiter@talentmatch.demo` / `recruiter123`.

The REST API is under `/api`: health, auth, candidates, companies, jobs, applications, dashboard, and analytics. Use the Postman collection in `postman/`. Features include JWT-protected access, candidate and job management, application workflow, search/filtering, dashboard KPIs, and API-driven charts.

## Deployment

Deploy `client` to Vercel with `VITE_API_URL=https://YOUR-RENDER-URL/api`. Deploy `server` to Render using build command `npm install && npm run build` and start command `npm start`.

For Render PostgreSQL, create a Render PostgreSQL database and copy its **internal database URL** into the Render web service's `DATABASE_URL` environment variable. Do not commit this value. Also set a strong `JWT_SECRET`, `CLIENT_URL` to the deployed Vercel origin, and allow Render to provide `PORT`.

The datasource is PostgreSQL. From a terminal with `DATABASE_URL` set to the Render PostgreSQL connection string, run `npm --prefix server run db:setup` to apply the schema and `npm --prefix server run db:seed` only when synthetic initial data is desired. No Prisma migration directory currently exists; schema deployment uses the existing `prisma db push` workflow.
