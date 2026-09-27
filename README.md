# JANTA.EXE v2 — Supabase + Android-ready

This is a production-oriented Expo React Native starter. It includes:
- Premium/simple Gen-Z dark UI
- Supabase email magic-link auth
- Postgres schema + Row Level Security
- Poll creation and one-vote-per-user
- Realtime-ready publication tables
- Reports/moderation tables
- Expo push-token table
- Supabase Edge Functions for moderation and push delivery
- EAS Android APK build profile

## 1. Create Supabase project
Create a project in Supabase and copy the Project URL + Publishable key.

## 2. Database
Open Supabase SQL Editor and run `supabase/migrations/001_init.sql`.

## 3. Local setup
```bash
npm install
cp .env.example .env
# fill EXPO_PUBLIC_SUPABASE_URL and EXPO_PUBLIC_SUPABASE_PUBLISHABLE_KEY
npx expo start
```

Scan with Expo Go. For a standalone Android APK:
```bash
npm install -g eas-cli
eas login
eas build:configure
npm run build:preview
```
The preview profile is configured for an installable APK.

## 4. Edge Functions
Install/login to Supabase CLI, link the project, then:
```bash
supabase functions deploy moderate-post
supabase functions deploy send-push
```

## 5. Production hardening
- Add server-side rate limits / abuse controls.
- Require email verification or another suitable anti-abuse gate.
- Add admin-only moderation policies; never expose service-role keys in the app.
- Add CAPTCHA/anti-bot controls where appropriate.
- Add source fields and review workflow for current-event factual claims.
- Configure Expo push credentials and notification permissions.
- Add privacy policy, terms, reporting/appeal process, account deletion.
- Add Realtime subscriptions in the poll screen for live vote counts.
