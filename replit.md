# Workspace

## Overview

pnpm workspace monorepo — **AntiGravity Housing**, a student-run off-campus housing directory for VIT college students.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (artifacts/antigravity-housing)
- **API framework**: Express 5 (artifacts/api-server)
- **Database**: PostgreSQL + Drizzle ORM (lib/db)
- **Validation**: Zod (`zod/v4`), `drizzle-zod`, Orval codegen
- **Auth**: Custom token-based (in-memory store, Bearer tokens)
- **UI**: Tailwind CSS, shadcn/ui, Framer Motion, Lucide icons, Sonner

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server
- `pnpm --filter @workspace/antigravity-housing run dev` — run frontend

## App Features

- Property listings with trust scores (0–100), Reliable/Average/Risky labels
- Anonymous student reviews (pending → moderator approval → published)
- Search + filters (name, location, rent range, amenities)
- Login/Register with anonymous ID assignment (User#XXXX)
- Moderator dashboard (approve/reject reviews, delete listings, view reports)
- Report system for suspicious reviews/listings
- VIT college building as hero background image

## Demo Accounts

- Moderator: `moderator@vit.edu` / `mod123`
- Student: `student@vit.edu` / `pass123`

## DB Tables

- users, properties, reviews, reports

## Architecture Notes

- Auth tokens stored in-memory (Map) — resets on server restart. For production, use a proper session store.
- The `@assets` alias in vite.config.ts points to `attached_assets/`
- College BG image: `public/college-bg.png`
