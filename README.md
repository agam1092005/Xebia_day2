# InternifyGroup

**A Gamified Learning Platform for Software Development**

Welcome to InternifyGroup! This platform is built to make learning software development interactive, competitive, and highly rewarding. Instead of just reading tutorials, users can master tech stacks, earn XP, unlock badges, and climb the global leaderboard.

**Live MVP:** [https://internifygroup.vercel.app/](https://internifygroup.vercel.app/)

---

## Tech Stack

Built with a modern and scalable tech stack:

- **Frontend**: [Next.js (App Router)](https://nextjs.org) & React
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) & [Framer Motion](https://www.framer.com/motion/) for micro-animations
- **Backend & Auth**: [Firebase](https://firebase.google.com/) (Firestore & Firebase Authentication)
- **Deployment**: [Vercel](https://vercel.com/)

---

## Key Features

- **Gamified Experience**: Learn by doing. Complete course milestones to earn XP and level up.
- **Global Leaderboard**: See how you rank against other developers. 
- **Badges & Achievements**: Unlock custom badges (like *First Login*, *3-Day Streak*, *React Beginner*) on your personalized profile.
- **Interactive Courses**: Browse and enroll in curated Software Development courses ranging from Frontend Mastery to Backend Architecture.
- **Secure Authentication**: Fast and reliable user registration and login powered by Firebase Auth.

---

## Database Architecture (Firebase Firestore)

The platform utilizes a NoSQL document database schema optimized for fast queries and real-time gamification tracking.

### `users` Collection
Stores user profiles and gamification statistics.
- `uid` (String) - Firebase Auth User ID
- `email` (String) - User's email address
- `xp` (Number) - Total experience points earned
- `rank` (Number) - Global leaderboard position
- `badges` (Array<String>) - List of unlocked badge IDs

### `courses` Collection
Stores metadata for available learning modules.
- `courseId` (String) - Unique slug for the course (e.g. `frontend-mastery`)
- `title` (String) - Display name of the course
- `jd` (String) - Detailed description and syllabus

### `transactions` Collection
Logs user course enrollments and activities.
- `userId` (String) - Reference to the user's `uid`
- `courseId` (String) - Reference to the enrolled course
- `amount` (Number) - Price or XP cost
- `timestamp` (Timestamp) - Time of enrollment

---

## The Team

Our platform is brought to life by the following contributions:

- **Aashika Jain** – Feature thinking & MVP Definition
- **Abhishek Joy** – Wireframes & Workflow Diagram
- **Agampreet Singh** – Code & Database Architecture
