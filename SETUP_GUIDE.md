# Setup Guide - Hi Secure Solutions E-commerce + ERP

## 📋 Prerequisites

Before starting, make sure you have installed:

1. **Node.js** (version 18 or higher)
   - Download from: https://nodejs.org/
   - Verify installation: Open terminal and run `node --version`

2. **MongoDB** (Local or MongoDB Atlas)
   - **Option A - Local MongoDB**: Download from https://www.mongodb.com/try/download/community
   - **Option B - MongoDB Atlas** (Cloud - Free): Sign up at https://www.mongodb.com/cloud/atlas

3. **Code Editor** (Optional but recommended)
   - Visual Studio Code: https://code.visualstudio.com/

---

## 🚀 Step-by-Step Setup Instructions

### Step 1: Open the Project Folder

1. Navigate to your project folder:
   ```
   E:\Billing Website
   ```

2. Open this folder in your terminal/command prompt:
   - **Windows**: Right-click in the folder → "Open in Terminal" or "Open PowerShell window here"
   - Or open Command Prompt/PowerShell and type:
     ```bash
     cd "E:\Billing Website"
     ```

### Step 2: Install Dependencies

1. Install all required packages (this may take a few minutes):
   ```bash
   npm install
   ```

   This will install dependencies for both frontend and backend.

2. Wait for installation to complete. You should see "added X packages" message.

### Step 3: Set Up MongoDB

#### Option A: Using Local MongoDB

1. Make sure MongoDB is running on your computer
2. MongoDB usually runs on: `mongodb://localhost:27017`

#### Option B: Using MongoDB Atlas (Cloud - Recommended for beginners)

1. Go to https://www.mongodb.com/cloud/atlas
2. Sign up for a free account
3. Create a free cluster
4. Click "Connect" → "Connect your application"
5. Copy the connection string (it looks like: `mongodb+srv://username:password@cluster.mongodb.net/`)
6. Replace `<password>` with your actual password
7. Add database name at the end: `mongodb+srv://.../hi-secure`

### Step 4: Configure Environment Variables

#### Backend Configuration

1. Create a file named `.env` in the `apps/server/` folder

2. Copy and paste this template into the `.env` file:

```env
# Database - Use your MongoDB connection string
MONGODB_URI=mongodb://localhost:27017/hi-secure
# OR for MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/hi-secure

# JWT Secrets (you can use any random strings)
JWT_SECRET=your-super-secret-jwt-key-change-in-production-12345
JWT_REFRESH_SECRET=your-refresh-secret-key-67890
JWT_EXPIRES=15m
JWT_REFRESH_EXPIRES=7d

# Web URL (frontend address)
WEB_URL=http://localhost:5173

# Razorpay (Optional - for payments, get from https://razorpay.com)
RAZORPAY_KEY_ID=your-razorpay-key-id
RAZORPAY_KEY_SECRET=your-razorpay-key-secret

# Email Configuration (Optional - for sending emails)
# For Gmail: Enable 2FA and create App Password
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password
BUSINESS_EMAIL=smssiddiq2011@gmail.com

# Firebase (Optional - for cloud storage)
FIREBASE_PROJECT_ID=your-firebase-project-id
FIREBASE_CLIENT_EMAIL=your-firebase-client-email
FIREBASE_PRIVATE_KEY=your-firebase-private-key

# Image APIs (Optional - for auto-fetching product images)
UNSPLASH_ACCESS_KEY=your-unsplash-access-key
PEXELS_API_KEY=your-pexels-api-key

# WhatsApp (Optional - for WhatsApp notifications)
WA_ACCESS_TOKEN=your-whatsapp-access-token
WA_PHONE_NUMBER_ID=your-whatsapp-phone-number-id
WA_VERIFY_TOKEN=your-verify-token
```

3. **Minimum Required Settings** (to get started quickly):
   - `MONGODB_URI` - Your MongoDB connection string
   - `JWT_SECRET` - Any random string (e.g., "my-secret-key-123")
   - `JWT_REFRESH_SECRET` - Any random string (e.g., "my-refresh-key-456")
   - `WEB_URL` - Keep as `http://localhost:5173`

   All other settings are optional and can be added later.

#### Frontend Configuration

1. Create a file named `.env` in the `apps/web/` folder

2. Add this content:
```env
VITE_API_URL=http://localhost:4000/api
```

### Step 5: Start the Application

#### Option A: Start Both Servers Together (Recommended)

From the root folder (`E:\Billing Website`), run:

```bash
npm run dev
```

This will start both:
- Backend server on: http://localhost:4000
- Frontend server on: http://localhost:5173

#### Option B: Start Servers Separately

**Terminal 1 - Backend:**
```bash
cd apps/server
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd apps/web
npm run dev
```

### Step 6: Access the Application

1. Open your web browser
2. Go to: **http://localhost:5173**
3. You should see the Hi Secure Solutions homepage!

---

## 🎯 First Time Usage

### 1. Create an Admin Account

1. Click "Register" or go to: http://localhost:5173/register
2. Fill in your details:
   - Name: Your name
   - Email: Your email
   - Password: Choose a password (min 6 characters)
3. Click "Register"

**Note:** By default, new users are registered as "customer". To create an admin account:

**Option 1 - Using MongoDB:**
- Open MongoDB Compass or any MongoDB client
- Connect to your database
- Go to the `users` collection
- Find your user document
- Change `role` from `"customer"` to `"admin"`

**Option 2 - Using API:**
- Register normally
- Then manually update the role in the database

### 2. Add Products

1. Login with your admin account
2. Go to Admin Dashboard (or create products via API)
3. Add your first product:
   - Name, Brand, Model
   - Category (CCTV, LED TV, Gadgets, Accessories)
   - Price, Stock
   - Description, Warranty

### 3. Test the Application

1. Browse products on the homepage
2. Search and filter products
3. Add products to cart
4. Proceed to checkout
5. Place an order

---

## 🔧 Troubleshooting

### Problem: "Cannot find module" error
**Solution:** Run `npm install` again in the root folder

### Problem: MongoDB connection error
**Solution:** 
- Check if MongoDB is running (for local)
- Verify your MongoDB connection string in `.env`
- Make sure there are no spaces in the connection string

### Problem: Port already in use
**Solution:**
- Backend (4000): Change port in `apps/server/src/index.ts` or set `PORT=4001` in `.env`
- Frontend (5173): Change port in `apps/web/vite.config.ts`

### Problem: "JWT_SECRET is required"
**Solution:** Make sure you created `.env` file in `apps/server/` with JWT_SECRET

### Problem: Frontend can't connect to backend
**Solution:** 
- Check if backend is running on port 4000
- Verify `VITE_API_URL` in `apps/web/.env` is correct
- Check browser console for errors

---

## 📝 Quick Start (Minimal Setup)

If you want to get started quickly with minimal configuration:

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Create `apps/server/.env`:**
   ```env
   MONGODB_URI=mongodb://localhost:27017/hi-secure
   JWT_SECRET=dev-secret-123
   JWT_REFRESH_SECRET=dev-refresh-123
   WEB_URL=http://localhost:5173
   ```

3. **Create `apps/web/.env`:**
   ```env
   VITE_API_URL=http://localhost:4000/api
   ```

4. **Start MongoDB** (if using local)

5. **Run the app:**
   ```bash
   npm run dev
   ```

6. **Open browser:** http://localhost:5173

---

## 🎉 You're All Set!

Your application should now be running. Start by:
1. Registering a user account
2. Adding some products
3. Testing the shopping cart and checkout

For detailed feature documentation, see `README.md`

---

## 📞 Need Help?

- Check the `README.md` for detailed feature documentation
- Review error messages in the terminal
- Check browser console (F12) for frontend errors
- Verify all environment variables are set correctly

