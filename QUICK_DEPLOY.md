# 🚀 Quick Deploy Guide - Get Mad Trip Live in 10 Minutes!

## Step 1: Deploy Backend to Render (Free)

1. **Go to:** https://render.com
2. **Sign up** (free with GitHub)
3. **Click "New +" → "Web Service"**
4. **Connect your GitHub repository** (or push your code to GitHub first)
5. **Configure:**
   - **Name:** `mad-trip-backend`
   - **Root Directory:** `server`
   - **Environment:** `Node`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Plan:** Free

6. **Add Environment Variables:**
   ```
   PORT=10000
   NODE_ENV=production
   MONGODB_URI=your_mongodb_atlas_connection_string
   OPENAI_API_KEY=your_openai_key
   GOOGLE_MAPS_API_KEY=your_google_maps_key
   OPENWEATHER_API_KEY=your_openweather_key
   CLIENT_URL=https://your-frontend-url.vercel.app
   ```

7. **Click "Create Web Service"**
8. **Copy your backend URL** (e.g., `https://mad-trip-backend.onrender.com`)

---

## Step 2: Deploy Frontend to Vercel (Free)

### Option A: Using Vercel Dashboard (Easiest)

1. **Go to:** https://vercel.com
2. **Sign up** (free with GitHub)
3. **Click "Add New Project"**
4. **Import your GitHub repository**
5. **Configure:**
   - **Framework Preset:** Vite
   - **Root Directory:** `client`
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
   - **Install Command:** `npm install`

6. **Add Environment Variables:**
   ```
   VITE_API_URL=https://your-backend-url.onrender.com/api
   VITE_GOOGLE_MAPS_API_KEY=your_google_maps_key
   ```

7. **Click "Deploy"**
8. **Copy your frontend URL** (e.g., `https://mad-trip.vercel.app`)

### Option B: Using Vercel CLI

```bash
# Install Vercel CLI
npm install -g vercel

# Navigate to client folder
cd client

# Deploy
vercel

# Follow prompts and add environment variables when asked
```

---

## Step 3: Update Backend CORS

1. **Go back to Render dashboard**
2. **Update `CLIENT_URL` environment variable** with your Vercel URL
3. **Redeploy** (or it will auto-redeploy)

---

## Step 4: Set Up MongoDB Atlas (Free)

1. **Go to:** https://www.mongodb.com/cloud/atlas
2. **Sign up** (free tier available)
3. **Create a cluster** (choose free M0 tier)
4. **Create database user:**
   - Username: `mad-trip-user`
   - Password: (create a strong password)
5. **Network Access:**
   - Click "Add IP Address"
   - Click "Allow Access from Anywhere" (0.0.0.0/0)
6. **Get Connection String:**
   - Click "Connect" → "Connect your application"
   - Copy the connection string
   - Replace `<password>` with your password
   - Example: `mongodb+srv://mad-trip-user:yourpassword@cluster0.xxxxx.mongodb.net/ai-trip-planner?retryWrites=true&w=majority`
7. **Add to Render environment variables as `MONGODB_URI`**

---

## Step 5: Get API Keys

### OpenAI API Key:
1. Go to https://platform.openai.com/api-keys
2. Create new secret key
3. Copy and add to Render as `OPENAI_API_KEY`

### Google Maps API Key:
1. Go to https://console.cloud.google.com
2. Create new project or select existing
3. Enable "Maps JavaScript API" and "Places API"
4. Create credentials → API Key
5. Add to both Render (`GOOGLE_MAPS_API_KEY`) and Vercel (`VITE_GOOGLE_MAPS_API_KEY`)

### OpenWeatherMap API Key:
1. Go to https://openweathermap.org/api
2. Sign up (free tier available)
3. Get API key from dashboard
4. Add to Render as `OPENWEATHER_API_KEY`

---

## Step 6: Test Your Deployment

1. **Visit your Vercel URL:** `https://your-app.vercel.app`
2. **Test trip generation**
3. **Check browser console** for any errors
4. **Check Render logs** if backend issues occur

---

## 🎉 You're Live!

Your Mad Trip app should now be accessible at:
- **Frontend:** `https://your-app.vercel.app`
- **Backend:** `https://your-backend.onrender.com`

---

## Troubleshooting

### CORS Errors:
- Make sure `CLIENT_URL` in Render matches your Vercel URL exactly
- Check that backend URL in Vercel env vars is correct

### API Not Working:
- Check Render logs for errors
- Verify all API keys are correct
- Ensure MongoDB connection string is valid

### Build Errors:
- Check Node.js version (should be 18+)
- Verify all dependencies are in package.json
- Check build logs in Vercel dashboard

---

## Need Help?

- **Render Docs:** https://render.com/docs
- **Vercel Docs:** https://vercel.com/docs
- **MongoDB Atlas Docs:** https://docs.atlas.mongodb.com

