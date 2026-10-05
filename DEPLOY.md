# Deploy notes (VPS)

This is a Next.js 15 frontend. It talks to the remote MediSmile API.

## 1) Clone

```bash
git clone <REPO_URL>
cd <PROJECT_FOLDER>
```

## 2) Environment

```bash
cp .env.example .env.local
```

Confirm:

```env
NEXT_PUBLIC_API_BASE_URL=https://api.medismile.xn--mgbaab0cxheq.tech/api
```

## 3) Install + build + run

```bash
npm install
npm run build
npm run start
```

Production app listens on port `3000` by default.

Recommended with PM2:

```bash
npm install -g pm2
pm2 start npm --name medismile-admin -- start
pm2 save
pm2 startup
```

## 4) Nginx + HTTPS

Put Nginx in front of `http://127.0.0.1:3000` and enable HTTPS (Certbot).

## 5) Update later

```bash
git pull
npm install
npm run build
pm2 restart medismile-admin
```

## Important

- Do **not** use `npm run dev` on the VPS.
- Do **not** commit `.env.local`.
- Ensure the API CORS allows the frontend domain.
