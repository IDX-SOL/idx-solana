# IDX AutoBot Next (Frontend)

IDX AutoBot Next is the frontend application for the IDX Solana tools ecosystem.  
It is a Next.js App Router web app that gives users a single UI to access token, liquidity, bot, and metadata tools.

This README is focused only on the frontend codebase (`IdxAutoBotNext`).

## What This Frontend Provides

The frontend delivers:

- a unified dashboard-style interface for all IDX tools
- wallet-connected Solana workflows
- tool-specific pages for token creation, burn, liquidity, metadata, and automation
- authenticated/gated user experience where required
- realtime and analytics-enabled product experience

## Tool Modules in the Frontend

Primary tools visible in navigation:

- Dashboard
- Volume Bot
- Holders Maker
- Reaction Booster
- Token Burn
- Bulk Sender (Solana)
- Update Token Metadata
- Create Token Pro
  - Create SPL Token
  - Create Token-2022 (Tax)
- Create Liquidity Pool
- Manage Liquidity
  - Add Liquidity
  - Remove Liquidity
- Revoke Authorities
  - Revoke Mint Authority
  - Revoke Freeze Authority
- Liquidity Simulator

These modules are represented by frontend routes and wired into backend APIs/services.

## Tools and USP

- **Dashboard** - Central control view for platform activity.  
  **USP:** One-screen visibility across token, bot, and liquidity workflows.
- **Volume Bot** - Automates trading activity patterns around a token.  
  **USP:** Maintains momentum with less manual intervention.
- **Holders Maker** - Supports holder distribution and holder activity patterns.  
  **USP:** Improves holder-side ecosystem depth for newer tokens.
- **Reaction Booster** - Drives engagement-style reaction workflows.  
  **USP:** Adds social momentum signals that support token attention.
- **Token Burn** - Executes and tracks token burn operations.  
  **USP:** Deflation actions in a simple, traceable flow.
- **Bulk Sender (Solana)** - Sends assets to many wallets in one operation.  
  **USP:** Replaces repetitive one-by-one transfer processes.
- **Update Token Metadata** - Updates token metadata and related media fields.  
  **USP:** Fast post-launch updates without rebuilding token setup.
- **Create Token Pro** - End-to-end token launch workflow.  
  **USP:** Unified professional flow for quick and repeatable launches.
  - **Create SPL Token**  
    **USP:** Fast standard SPL token creation.
  - **Create Token-2022 (Tax)**  
    **USP:** Advanced Token-2022 creation path for tax-enabled designs.
- **Create Liquidity Pool** - Sets up liquidity pool infrastructure.  
  **USP:** Reduces launch friction by keeping setup in one workflow.
- **Manage Liquidity** - Operates liquidity positions after launch.  
  **USP:** Active liquidity control without leaving the platform.
  - **Add Liquidity**  
    **USP:** Improves tradability and market depth.
  - **Remove Liquidity**  
    **USP:** Flexible capital and risk management.
- **Revoke Authorities** - Removes sensitive token authorities.  
  **USP:** Improves trust by reducing centralized control.
  - **Revoke Mint Authority**  
    **USP:** Prevents any future token minting.
  - **Revoke Freeze Authority**  
    **USP:** Prevents future account freezing power.
- **Liquidity Simulator** - Simulates liquidity behavior before execution.  
  **USP:** Test-before-action to reduce expensive on-chain mistakes.

## Core Layout Architecture

Global app shell is defined in `src/app/layout.js` and includes:

- global styles and font setup
- SEO metadata and social metadata
- JSON-LD structured data for IDX branding
- Google Tag Manager injection
- `ErrorBoundary` wrapper
- `ReduxProvider` for global state
- persistent `Sidebar`
- `MainContent` wrapper for all page content
- global `SupportButton`

This structure gives a consistent UI across all tool pages.

## Navigation System (Sidebar)

`src/components/layout/Sidebar.jsx` manages product navigation behavior:

- desktop collapse/expand behavior
- mobile open/close overlay behavior
- route-aware active highlighting
- nested menus for grouped tools
- auto-expand on child route load
- authentication-aware dashboard access flow

State is managed through Redux slice actions such as:

- `setIsCollapsed`
- `setIsHydrated`
- `setIsMobileSidebarOpen`

## State Management and Client Architecture

The frontend uses Redux Toolkit and client-side hooks for app behavior:

- global UI state (sidebar, shared controls)
- authentication/session flow integration
- wallet and transaction interaction state
- modular hooks for auth modal, onboarding, notifications, sockets

This keeps cross-page behavior predictable and avoids route-by-route state duplication.

## Backend Integration Model

The frontend is not standalone logic; it is an interface over backend services.

It integrates with backend domains such as:

- auth
- bots / holder-maker / reaction-maker
- token creator
- token burns / token creations
- liquidity pools / liquidity actions
- metadata / IPFS
- campaigns
- wallet balance
- referrals

It also works with proxied Solana RPC flows through backend endpoints for secure key handling.

## Security Posture (Frontend Side)

Frontend-side protections and safe patterns include:

- route guarding for protected experiences
- auth token/session handling via centralized utilities
- security headers applied via middleware
- wallet adapter-based signing flow (no private key handling in app code)
- environment-variable based configuration (no hardcoded secrets)

## Project Structure

- `src/app` - Next.js App Router pages and layouts
- `src/components` - UI components and layout system
- `src/redux` - store, providers, and slices
- `src/hooks` - reusable behavior hooks
- `src/utils` - helpers, api wrappers, auth/session utilities
- `src/config` - Solana/network/runtime configuration
- `src/services` - service-layer modules
- `public` - static assets and icons

## Tech Stack

- Next.js 15
- React 18
- Redux Toolkit + React Redux
- Solana Web3 + Wallet Adapter stack
- Axios
- Tailwind CSS
- Socket.io client
- Firebase (notification/integration use cases)

## Runtime Requirements

- Node `>=18.17.0`
- npm `>=9.0.0`

## Local Development

1. Install dependencies:
   - `npm install`
2. Add required environment variables in local env file.
3. Start dev server:
   - `npm run dev`
4. Open app:
   - `http://localhost:3000`

## Scripts

- `npm run dev` - start development server
- `npm run build` - create production build
- `npm run start` - run production server
- `npm run lint` - run lint checks
- `npm run rebuild` - rebuild dependencies

## Product Intent

IDX AutoBot Next frontend is designed to be the user-facing execution layer for token lifecycle and growth tooling.  
It unifies creation, liquidity, automation, metadata, and authority actions into one consistent product experience.

