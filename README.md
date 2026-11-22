# StudySquad Sync — Production Release Package

StudySquad Sync is a responsive campus study-room availability and peer study group matching web application. It visualizes real-time library room occupancy, enables temporary study space holds, and matches students into collaborative study squads based on shared subjects and schedules.

## Project Structure & Modules

### Modules 1–2: Static Phase & UI Foundation
- **How-it-Works Page**: Interactive step-by-step breakdown of space reservation and squad matching.
- **Group Cards & Room Visualizer**: Animated room status grids and squad feed cards.
- **Custom CSS & Dark Mode**: CSS custom properties for dynamic theme switching, custom glassmorphic styling, and smooth animations.

### Modules 3–4: Dynamic Phase & React Application State
- **State Management (Context API & React Hooks)**: Integrated global state handling active study squads, room occupancy, member rosters, and user hold timers.
- **Study Group Creation & Matcher**: Form to create squads by subject/topic with schedule compatibility matching.
- **Room Occupancy & 20-min Hold Countdown**: Interactive library space visualizer with automatic hold timers and simulated live status updates.
- **Squad Workspace & Member Roster**: Dedicated view with goal checklists, session timers, member list, and synchronized Pomodoro timer.

## Setup & Running Locally

1. Install dependencies:
   ```bash
   npm install
   ```
2. Start development server:
   ```bash
   npm run dev
   ```
3. Build for production:
   ```bash
   npm run build
   ```

## Key Technologies
- **React 18** (useState, useEffect, useContext, React Router)
- **Tailwind CSS + Custom CSS Variables** (Theme switching, custom animations)
- **Lucide React Icons**
