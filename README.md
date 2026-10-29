# Two Plates

A workout planner with a custom split builder, how-to video links, supersets, a set logger with rest timer, and workout history. Sign in with Google to sync across devices and share workouts with anyone.

## Files

| File | What it is |
|---|---|
| `index.html` | The app |
| `firebase-config.js` | Your Firebase project settings (you fill this in once) |
| `firestore.rules` | Security rules that keep each person's data private |

When the app gets updated later, you only replace `index.html`. Your settings in `firebase-config.js` stay put.

## One-time setup (about 15 minutes)

### 1. Create the Firebase project
1. Go to [console.firebase.google.com](https://console.firebase.google.com) and click **Create a project** (or open an existing one).
2. Name it something like `two-plates`. Google Analytics is optional; you can turn it off.

### 2. Turn on Google sign-in
1. In the left menu, open **Build → Authentication** and click **Get started**.
2. On the **Sign-in method** tab, click **Google**, switch it to **Enable**, pick your support email, and **Save**.

### 3. Allow your GitHub Pages site to sign people in
1. Still in Authentication, open the **Settings** tab → **Authorized domains**.
2. Click **Add domain** and enter `YOUR-GITHUB-USERNAME.github.io` (just the domain, no `https://` and no repo name).

### 4. Create the database
1. Open **Build → Firestore Database** and click **Create database**.
2. Pick a location close to you (for example `nam5 (United States)`). This can't be changed later.
3. Choose **Start in production mode** and finish.

### 5. Add the security rules
1. In Firestore, open the **Rules** tab.
2. Delete what's there, paste the contents of `firestore.rules`, and click **Publish**.

### 6. Get your app settings
1. Click the gear icon next to **Project Overview** → **Project settings**.
2. Under **Your apps**, click the web icon (`</>`). Name it `Two Plates`. Leave "Firebase Hosting" unchecked. Click **Register app**.
3. Firebase shows a code snippet. Copy only the `const firebaseConfig = { ... };` block.
4. Open `firebase-config.js`, replace the example block between the two "paste" lines with yours, and save.

### 7. Put it on GitHub Pages
1. On GitHub, create a new repository, for example `two-plates`.
2. Upload `index.html`, `firebase-config.js`, `firestore.rules` and this `README.md` (**Add file → Upload files**, then **Commit changes**).
3. Open the repo's **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and **Save**.
4. After a minute or two, the app is live at `https://YOUR-GITHUB-USERNAME.github.io/two-plates/`.

### 8. Bring your data over from the Claude version
1. In the Claude version of the planner, go to **Setup → Copy backup** and copy it.
2. Open your new site, tap **Sign in**, and sign in with Google.
3. Go to **Setup → Restore from backup**, paste, and tap **Restore** twice to confirm.

## Sharing workouts

On the **Week** tab, tap the share button on any day, or **Share week** at the top.

- **Copy as text** gives you the workout with how-to video links to paste into a text or email. Works for anyone.
- **Create share code** gives you a link. Anyone who opens it can sign in with Google and add the workout to their own planner with one tap. Everyone's plan and history stay private to them.

## Troubleshooting

- **"This site isn't on Firebase's authorized domains list"**: redo step 3 and make sure the domain matches your site exactly.
- **Header says "Sign-in not set up yet"**: `firebase-config.js` still has the example `PASTE_` values, or the file didn't get uploaded.
- **Sign-in window doesn't open on your phone**: the app falls back to a full-page sign-in. If that also fails, check that your browser isn't blocking pop-ups for the site.
- **"Couldn't reach your account"**: usually the security rules weren't published (step 5). Everything still saves on the device in the meantime.
