Student Management System
A comprehensive database-driven student management system built with React, Express, and Firebase following MVC architecture. This app is designed to run on Google AI Studio but can also be deployed independently

More Updates Coming Soon !!!...

Overview
This application allows administrators to manage student records, including creating, reading, updating, and deleting student information. It integrates with Firebase Firestore for data persistence and uses Gemini AI for intelligent features (optional). The frontend is built with React, Tailwind CSS, and shadcn/ui components, while the backend uses Express to serve the application and provide a simple API health check.

Features
Student CRUD Operations: Create, read, update, and delete student records.

Firestore Integration: Data stored securely in Firebase Firestore.

Responsive UI: Built with Tailwind CSS and shadcn/ui components.

MVC Architecture: Clean separation of concerns with models (Firestore schema), views (React components), and controllers (API routes and frontend logic).

Gemini AI Integration: Optional AI-powered features using Gemini API.

Theming Support: Dark/light mode with next-themes.

Toast Notifications: User feedback using sonner.

Vite + Express: Fast development server and production-ready serving.

Tech Stack
Frontend: React 19, TypeScript, Tailwind CSS 4, shadcn/ui, Lucide icons, Framer Motion

Backend: Express 4, Vite (for middleware)

Database: Firebase Firestore

Authentication: Firebase Auth (ready to be integrated)

AI: Google Gemini API (@google/genai)

Build Tool: Vite 6

Package Manager: npm

Prerequisites
Node.js 18+ (20+ recommended)

npm or yarn

A Firebase project with Firestore enabled

(Optional) Gemini API key for AI features

Getting Started
1. Clone the Repository
bash
git clone <your-repo-url>
cd student-management-system
2. Install Dependencies
bash
npm install
3. Configure Environment Variables
Create a .env.local file in the root directory (or copy from .env.example):

env
GEMINI_API_KEY="your_gemini_api_key_here"
APP_URL="http://localhost:3000"
GEMINI_API_KEY – Required for Gemini AI features. Obtain from Google AI Studio.

APP_URL – The base URL of your app (used for callbacks). Defaults to http://localhost:3000 in development.

4. Configure Firebase
Update the Firebase configuration in your frontend code (usually src/lib/firebase.ts). Use the values from firebase-applet-config.json:

json
{
  "apiKey": "AIzaSyB6uelBnRYjo_daB843k-fEei7PiMLdiy8",
  "authDomain": "gen-lang-client-0184886612.firebaseapp.com",
  "projectId": "gen-lang-client-0184886612",
  "storageBucket": "gen-lang-client-0184886612.firebasestorage.app",
  "messagingSenderId": "254491030700",
  "appId": "1:254491030700:web:9e4c7b78763bcb0e715b09",
  "firestoreDatabaseId": "ai-studio-b4f1a6a0-c56d-4dd5-9930-af589e574644"
}
Note: The configuration above is specific to the AI Studio environment. For local development, you may need to create your own Firebase project and update these values.

5. Run the Development Server
bash
npm run dev
This starts an Express server on port 3000 with Vite’s hot module replacement (HMR). Open http://localhost:3000 to view the app.

6. Build for Production
bash
npm run build
The output will be in the dist folder. To preview the production build:

bash
npm run preview
Or run the production server:

bash
npm run start
Project Structure
text
.
├── src/                      # Frontend React source
│   ├── components/           # Reusable UI components (shadcn/ui)
│   ├── lib/                  # Utilities (Firebase, helpers)
│   ├── hooks/                # Custom React hooks
│   ├── pages/                # Page components (StudentList, StudentForm, etc.)
│   ├── App.tsx               # Main app component
│   ├── main.tsx              # Entry point
│   └── index.css             # Global styles with Tailwind
├── server.ts                 # Express server + Vite middleware
├── vite.config.ts            # Vite configuration
├── tsconfig.json             # TypeScript configuration
├── components.json           # shadcn/ui configuration
├── firebase-blueprint.json   # Firestore schema definition (Student entity)
├── firebase-applet-config.json # Firebase project configuration
├── package.json              # Dependencies and scripts
├── .env.example              # Example environment variables
└── README.md                 # This file
MVC Pattern Implementation
Model: Defined in firebase-blueprint.json (Student entity) and implemented via Firebase Firestore collections (/students/{studentId}).

View: React components in src/pages and src/components.

Controller: API endpoints in server.ts (e.g., /api/health) and frontend logic that calls Firestore directly (or through a service layer).

API Endpoints
Method	Endpoint	Description
GET	/api/health	Health check (returns status)
Note: Most data operations (CRUD) are performed directly from the frontend using the Firebase Firestore SDK, following a client‑centric MVC approach. If you need server‑side endpoints, you can extend server.ts.

Firebase Blueprint
The file firebase-blueprint.json defines the Student entity:

json
{
  "student": {
    "properties": {
      "id": "string",
      "name": "string",
      "email": "string",
      "rollNumber": "string",
      "course": "string",
      "age": "number",
      "status": "Active | Inactive | Graduated",
      "createdAt": "date-time",
      "updatedAt": "date-time",
      "createdBy": "string"
    }
  }
}
This blueprint is used by AI Studio to generate type definitions and Firestore security rules.

Deployment on Google AI Studio
This app is pre‑configured to run on Google AI Studio. When deployed:

The GEMINI_API_KEY is injected from user secrets.

The APP_URL is automatically set to the Cloud Run service URL.

The Firebase configuration is already provided.

To deploy:

Push your code to a Git repository connected to AI Studio.

In AI Studio, create a new app from this repository.

Set the required secrets (e.g., GEMINI_API_KEY).

Deploy – the platform will build and host the application automatically.

Customization
Adding a New Entity
Update firebase-blueprint.json with the new entity definition.

Create corresponding Firestore collection and security rules.

Build React components for CRUD operations.

Styling
The project uses Tailwind CSS 4 with shadcn/ui. To customize the theme, modify src/index.css and update components.json (e.g., baseColor, menuAccent).

Troubleshooting
HMR not working: AI Studio disables file watching by setting DISABLE_HMR=true. For local development, ensure this variable is not set.

Firestore permissions: Make sure your Firebase security rules allow read/write access for authenticated users. The blueprint file helps AI Studio generate appropriate rules.

Missing Gemini API key: AI features will fail. Either provide a valid key or remove AI‑dependent code.

License
This project is provided as a template for educational purposes. You are free to modify and use it in your own applications.

# Run and deploy your AI Studio app

This contains everything you need to run your app locally.

View your app in AI Studio: https://ai.studio/apps/b4f1a6a0-c56d-4dd5-9930-af589e574644

## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
3. Run the app:
   `npm run dev`
