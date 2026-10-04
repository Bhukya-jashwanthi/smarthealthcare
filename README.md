# 🩺 Smart Healthcare

A full-stack MERN web app for managing personal health: log vitals, store medical reports in the cloud, find nearby hospitals on a map, and get general health guidance from an AI chatbot.

## 🚀 Features

- **Secure accounts**: sign up and log in, with passwords hashed using bcrypt; health pages are protected routes
- **Health records**: log blood pressure, blood sugar, heart rate and notes, then view your history
- **Medical report storage**: upload reports (JPG, PNG, PDF) to Cloudinary, then view or delete them
- **Hospitals near me**: uses browser geolocation and OpenStreetMap (Overpass API), with links to Google Maps
- **Interactive map**: Leaflet map of nearby hospitals using the Geoapify Places API
- **AI health assistant**: OpenAI-powered chatbot for general, non-critical health guidance
- **Rule-based chatbot and live chat**: instant answers to common questions, plus a Tidio live-chat widget
- **Health tips**: a tip of the day and personalised wellness tips

## 🛠️ Tech Stack

| Layer | Technologies |
| --- | --- |
| Frontend | React 19, React Router 7, Axios, Leaflet / React-Leaflet, Framer Motion, Swiper, Lucide icons |
| Backend | Node.js, Express |
| Database | MongoDB with Mongoose |
| File storage | Cloudinary, Multer |
| AI | OpenAI API |
| Auth | bcryptjs |
| Maps & location | Geoapify Places API, OpenStreetMap Overpass API |

## 📂 Project Structure

```
smarthealthcare/
├── healthcare-backend/
│   ├── models/          # Mongoose schemas: User, Health, Report
│   ├── routes/          # auth, health records, reports
│   ├── server.js        # Express app, Cloudinary upload, AI chat endpoint
│   └── .env.example     # required environment variables
├── healthcare-frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/  # HealthTips, TipOfDay, PrivateRoute, ...
│   │   ├── pages/       # Login, Signup, Chatbot
│   │   └── App.js       # routes
│   └── .env.example
└── package.json         # map libraries (Leaflet)
```

## 🔌 API Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | `/api/auth/signup` | Register a new user |
| POST | `/api/auth/login` | Log in |
| POST | `/api/health` | Save a health record |
| GET | `/api/health` | Get all health records |
| POST | `/upload` | Upload a medical report (form field `healthReport`) |
| GET | `/reports` | List uploaded reports |
| DELETE | `/delete` | Delete a report |
| POST | `/chat` | Ask the AI health assistant |

## ⚙️ Getting Started

**Prerequisites:** Node.js 18+, a MongoDB database (e.g. MongoDB Atlas), and Cloudinary, OpenAI and Geoapify API keys.

```bash
git clone https://github.com/Bhukya-jashwanthi/smarthealthcare.git
cd smarthealthcare
npm install
```

**Backend**

```bash
cd healthcare-backend
npm install
cp .env.example .env    # then fill in your own values
node server.js          # runs on http://localhost:5000
```

**Frontend** (in a new terminal)

```bash
cd healthcare-frontend
npm install
cp .env.example .env    # add your Geoapify key
npm start               # opens http://localhost:3000
```

## 🔐 Environment Variables

| Variable | Where | Purpose |
| --- | --- | --- |
| `MONGO_URI` | backend | MongoDB connection string |
| `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET` | backend | Report file storage |
| `OPENAI_API_KEY` | backend | AI chatbot |
| `PORT` | backend | Server port (default 5000) |
| `REACT_APP_GEOAPIFY_KEY` | frontend | Nearby-hospital search on the map |

`.env` files are git-ignored; never commit real keys.

## 🧭 Future Improvements

- Link health records and reports to the logged-in user
- JWT-based sessions and server-side route protection
- Charts showing vitals trends over time
- Deployment (Render for the API, Vercel for the frontend)

## ⚠️ Disclaimer

This project is for learning purposes. The AI assistant gives general information only and is not a substitute for professional medical advice.
