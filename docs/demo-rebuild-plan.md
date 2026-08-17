# Pixel-Perfect Live Demo Rebuild Plan

## Summary
Replace every screenshot-based live demo with pixel-perfect, real DOM/CSS/JS mini apps inside the phone popup.

The goal is to remove hidden screenshot hotspots completely. Each demo must render actual UI controls, lists, forms, cards, tabs, sliders, counters, maps, progress bars, and state changes that match the screenshots closely enough that a visitor feels they are using the real app.

## Scope
Rebuild all project demos:

- `GCS_DEMO`
- `Zonaro`
- `Instagram clone`
- `Food delivery app`
- `Edu_questor`
- `task-tracker`
- `Finance_Terminal`
- `overlay_app`

Do not use screenshots as the interactive surface. Screenshots may remain in `images/` as visual references only.

## Core Architecture
- Replace the current `projectDemos` screenshot/hotspot renderer with a component-style mini app system in `index.html`.
- Add a shared renderer:
  - `openDemo(projectKey)`
  - `closeDemo()`
  - `setPhoneApp(projectKey)`
  - `renderCurrentDemo()`
  - `setDemoState(projectKey, patch)`
  - `phoneToast(message)`
  - `phoneTransition(callback)`
- Each demo gets:
  - a dedicated state object
  - a render function returning HTML
  - delegated event handlers using `data-action`
  - a theme class matching its screenshots
- Use one phone shell for all demos.
- Keep the modal phone-only.

## Pixel-Perfect Method
- Audit every screenshot and document:
  - screen dimensions
  - dominant colors
  - typography scale
  - spacing rhythm
  - corner radii
  - shadows
  - button shapes
  - card density
  - navigation position
- Recreate each screen as HTML/CSS with matching layout.
- Use original screenshot images only for internal comparison, not for user interaction.
- Use project-specific CSS variables:
  - background
  - surface
  - accent
  - text colors
  - border color
  - radius
  - shadow
  - font weight
- Add screenshot comparison checkpoints during verification.

## Shared UI System
Add scoped classes for mini apps:

- `.mini-app`
- `.mini-screen`
- `.mini-topbar`
- `.mini-tabbar`
- `.mini-card`
- `.mini-button`
- `.mini-input`
- `.mini-list`
- `.mini-pill`
- `.mini-progress`
- `.mini-sheet`
- `.mini-toast`
- `.mini-map`
- `.mini-chart`
- `.mini-toggle`
- `.mini-counter`

All classes must be scoped under `.demo-phone` or `.mini-app` to avoid affecting the portfolio page.

## Demo Requirements

### GCS_DEMO
- Rebuild splash screen with animated boot progress.
- Rebuild login screen with callsign/password fields and authorize button.
- Dashboard must show live telemetry:
  - battery
  - altitude
  - GPS
  - signal
  - mode
  - armed state
- Controls:
  - Arm / Disarm
  - RTL
  - Mission
  - Payload
- Mission screen:
  - waypoint list
  - add waypoint button
  - mission status
  - simulated geofence/failsafe state
- UI must feel like a tactical control station.

### Zonaro
- Rebuild splash, onboarding, login, run, summary, guild, leaderboard, achievements.
- Run screen must simulate:
  - start
  - pause
  - resume
  - finish
  - distance increasing
  - captured zones increasing
  - pace/time changing
- Summary must reflect the simulated run.
- Guild/leaderboard/achievements must have working tabs/cards.
- UI must feel like a polished fitness-game app.

### Instagram Clone
- Rebuild feed, explore, reels, profile.
- Feed:
  - stories row
  - posts
  - like/save/comment state changes
- Explore:
  - grid tiles
  - search input
  - selected tile opens detail sheet
- Reels:
  - vertical reel screen
  - like/comment/share controls
- Profile:
  - follow/message buttons
  - tab switching between grid/reels/tagged
- UI must match social app conventions closely.

### Food Delivery
- Rebuild home, detail, cart, order tracking.
- Home:
  - location
  - search
  - categories
  - featured card
  - restaurant list
- Detail:
  - quantity counter
  - size/options
  - add to cart
- Cart:
  - item list
  - quantity updates
  - subtotal/delivery/total
- Order:
  - checkout state
  - preparing/on-way/delivered progress
- UI must feel like a real commerce flow.

### Edu_questor
- Rebuild feed, tutor profile, chat.
- Feed:
  - tutor cards
  - subject filters
  - search
- Tutor profile:
  - rating
  - expertise
  - availability
  - book/message actions
- Chat:
  - message list
  - input field
  - send button
  - sent message appears immediately
- UI must feel like an education marketplace.

### task-tracker
- Rebuild desktop-like task manager inside the phone shell while preserving the screenshot's compact dashboard feel.
- Task list:
  - complete/uncomplete
  - filter by status
  - priority pills
- New task panel:
  - title input
  - priority selector
  - save/cancel
- Saved task must appear in the list.

### Finance_Terminal
- Rebuild login, assets, markets, profile.
- Login:
  - unlock button
  - optional PIN input visual
- Assets:
  - portfolio total
  - holdings
  - allocation chart
  - holding detail panel
- Markets:
  - indices
  - watchlist
  - simulated price movement
- Profile:
  - account settings
  - risk profile
  - security controls
- UI must feel premium fintech, dark, dense, and responsive.

### overlay_app
- Rebuild launcher, bubble, quick tools.
- Launcher:
  - enable overlay
  - permission status
- Bubble:
  - draggable-style floating button visual
  - tap expands
- Tools:
  - quick actions
  - collapse button
  - action feedback
- UI must feel like a real utility overlay flow.

## Interaction Rules
- No visible demo labels.
- No hidden buttons over screenshots.
- Every clickable thing must be an actual UI element.
- Tapping a control must visibly update UI state.
- Navigation must happen through real tabs/buttons inside the app.
- Toasts should be short: `Saved`, `Added`, `Sent`, `Armed`, `Following`.
- Use transitions sparingly:
  - screen fade
  - bottom sheet slide
  - button press scale
  - loading spinner only where an app would naturally show one.

## Implementation File Plan
- Update `index.html`:
  - remove screenshot hotspot renderer
  - add mini app renderer
  - add project state/render functions
  - add scoped mini-app CSS
- Keep existing assets:
  - `images/**` remain as visual references
  - no image deletion in this pass

## Testing
- Static:
  - parse inline scripts with `new Function`
  - check asset references
  - `git diff --check`
- Browser:
  - launch each demo with `?demo=gcs`, `?demo=zonaro`, `?demo=ig`, `?demo=food`, `?demo=edu`, `?demo=task`, `?demo=finance`, `?demo=overlay`
  - verify no `.demo-screen-img` or screenshot hotspot system is used for rebuilt apps
  - click through main flow for every demo
  - assert DOM state changes after each action
- Visual:
  - capture mobile screenshots for every demo
  - compare against source screenshots manually
  - verify no text overflow
  - verify no overlapping controls
  - verify phone viewport scrolls only when content requires it
- Deployment:
  - commit changes
  - push to `main`
  - confirm GitHub Pages workflow success
  - verify live HTML contains mini-app renderer
  - capture at least one live screenshot

## Acceptance Criteria
- All eight demos render as real UI, not screenshots with overlays.
- User can interact with visible controls and see meaningful state changes.
- Core screens visually match the original screenshots closely.
- The popup feels like using an actual app prototype.
- The portfolio page outside the popup remains unchanged except for demo launch behavior.
- GitHub Pages deploys successfully.

## Assumptions
- The plan file path is `docs/demo-rebuild-plan.md`.
- Pixel-perfect means close visual reconstruction in DOM/CSS, not embedding screenshots.
- This stays a static site with vanilla HTML/CSS/JS.
- No framework migration is included in this plan.
