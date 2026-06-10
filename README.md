# Flywheel — Mon suivi (field app, PWA)

Companion to the Control Tower. Each task-owner installs it, gets daily reminders,
reports progress (written + optional voice), and sends a point that your limited
group pastes into the Tower's **Agent de saisie**.

## 1. Host it (one-time, required for install + offline + notifications)
A web app needs **https** to install with an icon. Pick one:
- **Netlify Drop** (fastest): go to https://app.netlify.com/drop and drag this whole
  folder onto the page. You get an https link instantly.
- **GitHub Pages**: push these files to a repo → Settings → Pages → deploy from branch.
Your base URL becomes e.g. `https://<you>.netlify.app/` (index.html is the entry).

## 2. Pre-configure each collaborator (no setup on their side)
Open the app → **Réglages → Outils coordinateur**. Enter their name, tick their tasks,
hit **Générer le lien**, then **Inviter par WhatsApp**. They open the link, then
**Partager → Sur l'écran d'accueil** (iPhone) and the app shows only their tasks.
The link looks like: `…/index.html?u=Name&t=A1,A2,A3&c=<your WhatsApp number>`

## 3. Daily reminder (works even when the app is closed)
In the app: **Réglages → Ajouter le rappel à mon agenda** → imports a recurring
08:00 reminder into the phone's Calendar → a real OS notification every morning.
This is the reliable backbone on iPhone (no server needed).

## 4. The loop back to the Tower
Owner taps **Envoyer** → WhatsApp/e-mail to you. The message ends with a
`Pour la tour (Agent de saisie)` block (e.g. `B3 fait`). Your team pastes that block
into the Tower's Agent console → preview → apply. One source of truth.

## Known limits (by design)
- Progress is stored locally on each phone; the Tower is the system of record.
- Voice notes are shared immediately (not stored across app restarts).
- Fully dynamic server-push (closed-app, task-aware) needs a backend — Phase 2.
- iPhone dictation = use the keyboard mic inside the note field (Web speech-to-text
  is unreliable on iOS).
