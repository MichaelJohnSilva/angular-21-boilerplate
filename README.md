# Angular 21 Auth Boilerplate

## Live URLs
- **Frontend:** https://angular-21-boilerplate-0o8b.onrender.com
- **Backend API:** https://node-mysql-api-t9ui.onrender.com
- **Swagger Docs:** https://node-mysql-api-t9ui.onrender.com/api-docs

## Features
- User registration with email verification
- Login / Logout with JWT + refresh token auto-refresh
- Forgot password & reset password flow
- Role-based access control (Admin & User)
- Profile management
- Admin panel for managing accounts
- Fake backend for Stage A testing (disabled in production)

## Local Development

### 1. Install dependencies
```bash
npm install
```

### 2. Run dev server (port 4000, fake backend active)
```bash
npm start
```
The fake backend is automatically enabled in development and disabled in production builds.

### 3. Test with live backend
Update `src/environments/environment.ts`:
```ts
export const environment = {
    production: false,
    apiUrl: 'http://localhost:3000'
};
```

## Render Deployment (Static Site)

| Setting | Value |
|---|---|
| Build command | `npm ci && npm run build` |
| Publish directory | `dist/ipt-2026-frontend` |

**Critical — SPA Rewrite Rule:**

| Field | Value |
|---|---|
| Source | `/*` |
| Destination | `/index.html` |
| Action | **Rewrite** (NOT Redirect) |

## Testing

### Stage A — Fake Backend (local)
1. Run `npm start`
2. Register → click verification link shown in alert
3. Login with verified credentials
4. Test `/admin` routes with first account (Admin)
5. Register second account → confirm no admin access

### Stage B — Live Backend
1. Register at https://angular-21-boilerplate-0o8b.onrender.com/account/register
2. Check Mailtrap inbox for verification email
3. Click verify link → login
4. Open DevTools → Application → Cookies → confirm `refreshToken` cookie
5. Open Network tab → confirm `Authorization: Bearer ...` on API requests
6. Test admin panel with first account
7. Test user restrictions with second account
