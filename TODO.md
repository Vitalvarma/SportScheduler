# Deployment Plan for Render

## Information Gathered
- Project is a Node.js Express app with Sequelize ORM and PostgreSQL database.
- Uses EJS for templating.
- Has migrations for database schema.
- Code is already pushed to GitHub.
- Config updated for production to use DATABASE_URL env var.
- App.js updated to use PORT env var.
- Package.json updated with postinstall script for migrations.

## Plan
1. Push latest changes to GitHub (config.json, app.js, package.json updates).
2. Create Render account if not already.
3. Create a PostgreSQL database on Render.
4. Create a new Web Service on Render, connect to GitHub repo.
5. Set build settings:
   - Build Command: npm install
   - Start Command: npm run start:prod
6. Add environment variables:
   - DATABASE_URL: (from Render's PostgreSQL instance)
   - NODE_ENV: production
7. Deploy the service.
8. Monitor logs for any issues, especially database connection and migrations.

## Dependent Files Edited
- config/config.json: Set "use_env_variable": "DATABASE_URL" for production.
- app.js: Changed port to use process.env.PORT || 3001.
- package.json: Added "postinstall": "npx sequelize-cli db:migrate".

## Followup Steps
- Test locally with production settings if possible.
- After deploy, check the live app URL.
- If issues, check Render logs.
- Update README.md with live link once deployed.
