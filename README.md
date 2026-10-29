# Ayla

## A gentler way to get focused

Ayla is a desktop productivity companion designed to help you move from *what matters* to *what you are doing right now*.

She helps you shape the day, choose a meaningful next step, and settle into focused work without turning productivity into a punishment. Ayla lives quietly on the desktop, checks in at useful moments, and celebrates progress as it happens.

> This repository is a public showcase of a private project. It is shared to demonstrate the product thinking, interaction design, and technical direction behind Ayla.

## Why Ayla?

Most productivity tools are good at collecting plans. Ayla is built around the harder part: starting.

She creates a small bridge between intention and action:

1. Define a goal or capture a task.
2. Break larger goals into milestones and daily steps.
3. Choose the next focused block from your plan or calendar.
4. Work in a calm Pomodoro session with the right context ready.
5. Review what moved forward and carry useful momentum into tomorrow.

The result is a productivity loop that feels supportive rather than noisy: plan with clarity, focus with structure, and reflect with honesty.

## What Ayla can do

### Start the day with context

The morning briefing brings together your priorities, a grounding thought, personal reflection text, and the day's relevant calendar blocks. It gives the day a shape before notifications and open tabs take over.

### Turn goals into doable work

Create long-term goals with target dates, then organize them into milestones and daily tasks. AI-assisted goal breakdown can suggest weekly milestones and practical next steps that you can edit before saving.

### Make focus easier to enter

Start a session from the overlay, the Planning Room, or a linked calendar block. Ayla can open your chosen apps and URLs, play optional ambient noise, and keep the current task visible while you work.

### Protect attention without taking control away

During a session, Ayla can notice when you move to an app outside your approved focus list and offer a soft check-in. You decide whether to return to the task or allow the detour; overrides are logged for reflection rather than blocked outright.

### Keep progress connected to the work

Focused time is recorded against the active goal, milestone, or task. Progress combines completed sub-tasks with the Pomodoro time you actually invested, so planning and effort reinforce each other.

### Close the loop

End-of-day reflection helps you see what was completed, what remains, and what could make tomorrow easier. Small celebrations mark finished tasks and milestones without interrupting the work itself.

## The experience

| Surface | Purpose |
| --- | --- |
| **Ayla overlay** | A lightweight desktop presence for greetings, focus sessions, prompts, and transitions between work and rest. |
| **Planning Room** | A dedicated space for schedule, goals and tasks, calendar, and focus settings. |
| **Focus session** | A configurable Pomodoro timer with task context, optional white noise, app/URL launch, and attention check-ins. |
| **Calendar connection** | Read today's Google Calendar events, link them to goals or tasks, and receive a confirmation prompt when a planned block begins. |

## Privacy and control

- The app stores its working data locally in Electron's user data directory.
- Google Calendar is optional and uses an OAuth desktop flow. Ayla reads calendar data to support planning; it does not create calendar events.
- AI features are isolated behind one provider layer. Without an API key, the app uses local stub responses and makes no AI network request.
- Calendar tokens are stored in the operating system's Electron user data location, not in the project directory.
- Desktop monitoring is optional, time-bounded, and dormant outside the access window you configure.

## Technology

- React 18 and TypeScript
- Vite
- Electron
- Google Calendar API via `googleapis`
- Optional Gemini-powered briefing, goal breakdown, reflection, and calendar-to-goal matching
- Local JSON persistence through Electron IPC, with a browser `localStorage` fallback

## Getting started

### Requirements

- Node.js 20 or newer
- npm
- Electron's platform prerequisites for your operating system

### Install and run

```bash
npm install
npm run dev
```

`npm run dev` starts Vite and Electron together. The development app opens with the Ayla overlay; the Planning Room is available from the app's planning controls and tray integration.

### Build

```bash
npm run build       # Build the renderer and Electron process
npm run dist        # Build and package for the current platform
```

Platform-specific packaging commands are also available:

```bash
npm run dist:win
npm run dist:mac
npm run dist:linux
```

### Optional integrations

Create a `.env.local` file when you want to enable integrations locally. Keep credentials out of version control.

```dotenv
# Optional AI features
VITE_GEMINI_API_KEY=your_gemini_api_key

# Optional Google Calendar connection
GOOGLE_CALENDAR_CLIENT_ID=your_desktop_client_id
GOOGLE_CALENDAR_CLIENT_SECRET=your_desktop_client_secret
```

Without the Gemini key, AI surfaces use deterministic placeholder content. Without Google Calendar credentials, the rest of the planning and focus experience remains available.

## Project shape

```text
src/
  App.tsx                 Desktop overlay and morning/session flow
  PlanningRoom.tsx        Planning window
  ai/                     Provider abstraction and AI-powered helpers
  components/             Overlay, focus, briefing, and planning UI
  hooks/                  Session, Pomodoro, scheduler, and state logic
  lib/                    Local persistence and audio helpers
  states/                 Ayla's companion state machine
electron/
  main.ts                 Electron windows, tray, and lifecycle
  calendar.ts             Google Calendar OAuth and event access
  ipc.ts                  Renderer/main-process bridge
```

## Status

Ayla is an active prototype and portfolio project. The core planning, session, persistence, calendar, and companion flows are present, while the product continues to evolve through testing and refinement.

## License

This project is currently shared for showcase purposes. No open-source license has been declared.
