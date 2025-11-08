# Deployment Guide for Mad Trip

## Quick Deploy Options

### Option 1: Vercel (Frontend) + Render (Backend) - Recommended

#### Deploy Frontend to Vercel:

1. **Install Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Navigate to client folder:**
   ```bash
   cd client
   ```

3. **Deploy:**
   ```bash
   vercel
   ```

4. **Add Environment Variables in Vercel Dashboard:**
   - `VITE_API_URL` = Your backend URL (from Render)
   - `VITE_GOOGLE_MAPS_API_KEY` = Your Google Maps API key

#### Deploy Backend to Render:

1. **Go to:** https://render.com
2. **Create New Web Service**
3. **Connect your GitHub repository**
4. **Configure:**
   - **Root Directory:** `server`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Environment:** Node

5. **Add Environment Variables:**
   - `PORT` = 10000 (or any port Render assigns)
   - `NODE_ENV` = production
   - `MONGODB_URI` = Your MongoDB Atlas connection string
   - `OPENAI_API_KEY` = Your OpenAI API key
   - `GOOGLE_MAPS_API_KEY` = Your Google Maps API key
   - `OPENWEATHER_API_KEY` = Your OpenWeatherMap API key
   - `CLIENT_URL` = Your Vercel frontend URL

6. **Update CORS in server.js** to allow your Vercel domain

---

### Option 2: Railway (Full Stack - Easiest)

1. **Go to:** https://railway.app
2. **Sign up with GitHub**
3. **New Project** → **Deploy from GitHub repo**
4. **Add Services:**
   - **Frontend Service:**
     - Root Directory: `client`
     - Build Command: `npm install && npm run build`
     - Start Command: `npm run preview`
     - Environment Variables:
       - `VITE_API_URL` = Your backend URL
       - `VITE_GOOGLE_MAPS_API_KEY` = Your Google Maps API key
   
   - **Backend Service:**
     - Root Directory: `server`
     - Build Command: `npm install`
     - Start Command: `node server.js`
     - Environment Variables:
       - `PORT` = 5000
       - `MONGODB_URI` = Your MongoDB Atlas connection string
       - `OPENAI_API_KEY` = Your OpenAI API key
       - `GOOGLE_MAPS_API_KEY` = Your Google Maps API key
       - `OPENWEATHER_API_KEY` = Your OpenWeatherMap API key
       - `CLIENT_URL` = Your frontend URL

---

### Option 3: Netlify (Frontend) + Railway (Backend)

#### Netlify Frontend:

1. **Go to:** https://netlify.com
2. **New site from Git** → Connect repository
3. **Build settings:**
   - Base directory: `client`
   - Build command: `npm install && npm run build`
   - Publish directory: `client/dist`
4. **Environment variables:**
   - `VITE_API_URL` = Your backend URL
   - `VITE_GOOGLE_MAPS_API_KEY` = Your Google Maps API key

---

## MongoDB Atlas Setup (Free)

1. **Go to:** https://www.mongodb.com/cloud/atlas
2. **Create free cluster**
3. **Create database user**
4. **Whitelist IP:** 0.0.0.0/0 (for all IPs)
5. **Get connection string** and replace `<password>` with your password
6. **Use this as `MONGODB_URI`**

---

## Quick Deploy Script

After setting up MongoDB Atlas, you can use these commands:

```bash
# Install Vercel CLI globally
npm install -g vercel

# Deploy frontend
cd client
vercel

# For backend, use Render or Railway dashboard
```

---

## Post-Deployment Checklist

- [ ] MongoDB Atlas cluster created and connection string added
- [ ] All API keys added to environment variables
- [ ] CORS configured to allow frontend domain
- [ ] Frontend environment variables set
- [ ] Test the deployed application
- [ ] Verify Google Maps is working
- [ ] Test trip generation
- [ ] Test chatbot functionality

---

## Troubleshooting

### CORS Issues:
Update `server/server.js` to include your frontend URL:
```javascript
app.use(cors({
  origin: ['http://localhost:3000', 'https://your-frontend-url.vercel.app'],
  credentials: true,
}));
```

### Build Errors:
- Make sure all dependencies are in package.json
- Check Node.js version (should be 18+)
- Verify all environment variables are set

### API Not Working:
- Check backend logs
- Verify API keys are correct
- Ensure MongoDB connection is working
- Check CORS settings

