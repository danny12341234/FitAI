# FitAI - App Store Upload Guide

## What's in this folder
- www/index.html → Your complete FitAI app
- package.json → Dependencies
- capacitor.config.json → App settings
- codemagic.yaml → Codemagic build instructions

---

## STEP 1 — Apple Developer Account ($99)
1. Go to developer.apple.com
2. Click "Account" → Sign up
3. Pay $99/year
4. Wait for approval (can take 24-48 hours)

---

## STEP 2 — App Store Connect API Key
1. Go to appstoreconnect.apple.com
2. Click "Users and Access" → "Keys"
3. Click "+" to create a new key
4. Name it "Codemagic"
5. Role: "App Manager"
6. Download the .p8 file — SAVE THIS, you can only download once
7. Copy the Key ID and Issuer ID shown on screen

---

## STEP 3 — Upload to GitHub
1. Go to github.com → Sign up free
2. Click "+" → "New repository"
3. Name: fitai
4. Set to Public
5. Click "Create repository"
6. Click "uploading an existing file"
7. Drag ALL files from this folder into GitHub
8. Click "Commit changes"

---

## STEP 4 — Connect GitHub to Codemagic
1. Go to codemagic.io
2. Click "Add application"
3. Select GitHub
4. Authorize → select your "fitai" repository
5. Select "Other" as project type
6. Codemagic will detect the codemagic.yaml file automatically

---

## STEP 5 — Add your keys to Codemagic
In Codemagic → your app → Environment variables, add:

- APP_STORE_CONNECT_PRIVATE_KEY → paste contents of your .p8 file
- APP_STORE_CONNECT_KEY_IDENTIFIER → your Key ID
- APP_STORE_CONNECT_ISSUER_ID → your Issuer ID
- APP_STORE_APPLE_ID → your Apple ID email

---

## STEP 6 — Add iOS Certificate
1. In Codemagic → go to "Code signing identities"
2. Click "Generate certificate"
3. Select "App Store" distribution
4. Codemagic generates everything automatically

---

## STEP 7 — Start the Build
1. Click "Start new build"
2. Select branch: main
3. Select workflow: ios-app-store
4. Click "Start build"
5. Wait 20-30 minutes
6. Codemagic submits to App Store automatically

---

## STEP 8 — App Store Listing
While it builds, go to appstoreconnect.apple.com:
1. Click "My Apps" → "+"
2. Fill in:
   - Name: FitAI - AI Health Coach
   - Bundle ID: com.fitai.app
   - Category: Health & Fitness
3. Description:
   FitAI is your AI-powered health coach. Scan food with your
   camera to instantly get calories, protein, carbs and fat.
   Get personalised workout plans, 3-day meal plans, track your
   weight and hit your fitness goals. Powered by Claude AI.
4. Add screenshots (take from your phone browser)
5. Price: Free

---

## Need Help?
Every step is documented at docs.codemagic.io
