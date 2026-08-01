# Flowboard — Kanban Project Management App

A Trello-inspired, production-styled Kanban app built with React (Vite), React Router, Context API, and CSS variables for theming. All data persists to `localStorage` — no backend required.

## Getting started

```bash
npm install
npm run dev
```

Then open the printed local URL (usually `http://localhost:5173`). Sign in with any email/password on the login screen — auth is UI-only and simply creates a local session.

To build for production:

```bash
npm run build
npm run preview
```

## What's implemented

- **Auth screens (UI only):** Login, Register, Forgot Password, with a mock session stored in `localStorage`.
- **Dashboard:** stat cards (projects, tasks, completed, due today), a weekly-throughput chart (Recharts, mock data), recently viewed tasks, and a project grid.
- **Projects:** create, rename, delete (with undo toast), archive/restore, favorite. Archived projects are managed from Settings.
- **Kanban board:** 5 default columns (Backlog, To Do, In Progress, Review, Completed), plus add/rename/delete/reorder columns via native HTML5 drag-and-drop.
- **Tasks:** title, description, priority, due date, labels, assignee, checklist, comments, activity log, and a UI-only attachments section. Create, edit, delete (with undo), duplicate, and drag between/within columns.
- **Task modal:** full editor for everything above, opened by clicking a card or via a task's shareable `?task=` URL param.
- **Search:** live results across tasks, projects, and labels from the top bar.
- **Filters:** by priority, label, due date status, assignee, and completion, per board.
- **Notifications panel:** mock notifications with read/unread state.
- **Calendar view:** month grid of tasks by due date, plus an upcoming list.
- **Activity timeline:** a running feed of actions across the workspace.
- **Settings:** profile, password (UI only), notification preferences, theme, language selector, board export/import to JSON, and archived project management.
- **Dark mode:** full theme via CSS variables, persisted to `localStorage`.
- **Responsive layout:** collapsible sidebar on desktop, off-canvas sidebar on mobile.
- **Command palette:** `Ctrl/Cmd + K` for quick navigation and theme toggling.
- **Toasts with undo:** deleting a project or task shows a toast with an Undo action.
- **Accessibility:** semantic elements, visible focus states, labelled form fields, keyboard support in the modal and command palette, `prefers-reduced-motion` respected.

## Scope notes

This is a large brief. A few of the "bonus" items from the spec were left out to keep the codebase focused and reviewable — happy to add any of these on request:

- Pomodoro timer widget / productivity statistics beyond the dashboard chart
- Real file uploads for attachments (the UI section is present but inert)
- A real backend/auth provider (everything is mocked and local to your browser)

## Project structure

```
src/
  components/   Reusable UI (TaskCard, Column, Board, TaskModal, Sidebar, Topbar, ...)
  pages/        Route-level views (Dashboard, BoardPage, Calendar, Activity, Settings, auth pages)
  layouts/      AuthLayout and AppLayout shells
  context/      AuthContext, ThemeContext, ToastContext, BoardContext (all app state)
  hooks/        useLocalStorage
  data/         Seed/mock data
  utils/        id + date helpers
  styles/       CSS variables and stylesheets, grouped by area
```

## Notes on data

Everything (projects, tasks, notifications, activity, theme, settings) is seeded with realistic mock data on first load and then persisted to `localStorage` under `kanban:*` keys. Clear your browser's local storage for this origin to reset to the seed data.
