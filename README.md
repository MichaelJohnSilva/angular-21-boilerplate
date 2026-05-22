# Angular 21 Auth Boilerplate

## Live URLs
- **Frontend:** https://your-frontend.onrender.com
- **Backend API:** https://your-backend.onrender.com
- **Swagger Docs:** https://your-backend.onrender.com/api-docs

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
    apiUrl: 'http://localhost:3000'   // or your deployed backend URL
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

Before deploying, update `src/environments/environment.prod.ts` with your real backend URL.

## Testing

### Stage A — Fake Backend (local)
1. Run `npm start`
2. Register → click verification link shown in alert
3. Login with verified credentials
4. Test `/admin` routes with first account (Admin)
5. Register second account → confirm no admin access

### Stage B — Live Backend
1. Deploy backend to Render
2. Update `environment.prod.ts` with backend URL
3. `npm run build` → deploy `dist/ipt-2026-frontend`
4. Register → check Mailtrap inbox for verification email
5. Verify JWT cookie in DevTools → Application → Cookies
