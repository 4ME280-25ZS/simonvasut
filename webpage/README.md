# Wishlist (GitHub Pages + Firebase)

This repository contains a static wishlist page that stores claims in Firebase Firestore. Each product can be claimed by one person.

## Setup (Firebase)
1. Go to https://console.firebase.google.com and create a new project.
2. In your project, add a Web app (click the gear → Project settings → General → Add app).
3. Register the app and copy the Firebase config object (apiKey, authDomain, projectId, etc.).
4. In `index.html`, replace the `firebaseConfig` placeholder object with your values.
5. In Firestore Database, create a database in **test mode** or set rules allowing read/write for now (see note below).

## Security note
For a public GitHub Pages site you should restrict access. Options:
- Use Firebase Rules to restrict writes (e.g., require users to provide a short password stored in config). Or
- Use Firebase Authentication (anonymous or email) and enforce rules that only authenticated users can write.

## Deploy to GitHub Pages
1. Create a GitHub repository and push the `webpage/` folder contents to the `gh-pages` branch or to the `main` branch and enable Pages from `/ (root)` or `/docs` as you prefer.
2. In your repo settings → Pages, select the branch and folder to publish.
3. Wait a few moments and your site will be live.

## Usage
- Open the site, enter your name in the input, then click `Claim` on an available product.
- The product becomes claimed and shows the claimer's name. Claims are stored in Firestore in the `products` collection.

## Local testing
You can open `index.html` locally in a browser, but some browsers block module imports when opened with `file://`. To test locally run a simple HTTP server:

Windows PowerShell:

```powershell
# from the webpage folder
python -m http.server 8000
# then open http://localhost:8000
```

## Next steps (optional)
- Add Firebase Authentication and secure Firestore rules.
- Add unclaim / transfer claim functionality with confirmations.

If you want, I can set up Firestore rules and an example auth flow next.