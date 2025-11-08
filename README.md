# Mad Trip - AI-Powered Smart Trip Planner

A modern, full-stack web application that helps users plan their entire journey using AI-powered recommendations, route optimization, and comprehensive travel information.

## Features

- 🤖 **Smart Trip Planner**: AI-generated personalized itineraries based on destination, dates, budget, and interests
- 🗺️ **Route Finder**: Optimized travel routes with Google Maps integration
- 🍽️ **Restaurant & Stay Recommendations**: Top-rated restaurants and hotels near your destination
- 🎯 **Attraction & Event Finder**: Popular sightseeing spots and local events
- 💬 **Travel Guide AI Chat**: Virtual travel assistant for questions and tips
- 🌤️ **Weather Forecast**: Current and upcoming weather for travel days
- 💰 **Budget Estimator**: Total travel cost breakdown
- 💾 **Save & Share Trips**: Save trips and share with friends
- 👥 **Collaborative Editing**: Plan trips together with friends
- 📄 **PDF Download**: Download your itinerary as PDF

## Tech Stack

- **Frontend**: React 18, TailwindCSS, Vite
- **Backend**: Node.js, Express
- **Database**: MongoDB with Mongoose
- **APIs**: OpenAI, Google Maps/Places, OpenWeatherMap

## Setup Instructions

### Prerequisites

- Node.js (v18 or higher)
- MongoDB (local or MongoDB Atlas)
- API Keys:
  - OpenAI API key
  - Google Maps API key
  - OpenWeatherMap API key

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd mad-trip
```

2. Install dependencies:
```bash
npm run install-all
```

3. Set up environment variables:
```bash
cp .env.example .env
```

Edit `.env` and add your API keys:
- `OPENAI_API_KEY`
- `GOOGLE_MAPS_API_KEY`
- `OPENWEATHER_API_KEY`
- `MONGODB_URI`

4. Start the development servers:
```bash
npm run dev
```

This will start:
- Backend server on `http://localhost:5000`
- Frontend dev server on `http://localhost:3000`

### Production Build

```bash
cd client
npm run build
```

## Project Structure

```
mad-trip/
├── client/          # React frontend
├── server/          # Node.js/Express backend
├── .env.example     # Environment variables template
└── README.md
```

## API Endpoints

- `POST /api/trips/generate` - Generate new trip itinerary
- `GET /api/trips` - Get user's saved trips
- `GET /api/trips/:id` - Get trip details
- `PUT /api/trips/:id` - Update trip
- `DELETE /api/trips/:id` - Delete trip
- `POST /api/trips/:id/share` - Share trip
- `GET /api/trips/:id/pdf` - Download trip PDF
- `GET /api/places/restaurants` - Get restaurant recommendations
- `GET /api/places/hotels` - Get hotel recommendations
- `GET /api/places/attractions` - Get attraction recommendations
- `POST /api/routes/optimize` - Get optimized route
- `GET /api/weather` - Get weather forecast
- `POST /api/chat` - Chat with AI assistant

## License

MIT

