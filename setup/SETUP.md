# Connecting the Apply form (free, no Blaze plan)

| What | Where it goes | Cost |
|---|---|---|
| Drafts and applications | Firebase **Firestore** | Free (Spark plan) |
| Each application + its pitch deck | **Email** to bubble.youthimpact@gmail.com via FormSubmit, with the deck attached | Free |

Your Firebase config is already in `index.html`. The only Firebase step left is creating Firestore.

## 1. Firestore: drafts and applications
1. Go to <https://console.firebase.google.com> and open **changemakers-korea**.
2. Click **Build → Firestore Database → Create database**.
3. Location: **asia-northeast3 (Seoul)**. Start in **production mode**.
4. Open the **Rules** tab, delete everything, paste the contents of `firestore.rules`, and click **Publish**.

You don't need Firebase Storage. Skip it and stay on the free Spark plan.

## 2. Activate FormSubmit (one time)
After the site is live, submit one test application. FormSubmit sends an **Activate Form** email to bubble.youthimpact@gmail.com. Click the link once.
**The test application sent before activation won't arrive**, so submit a second test afterwards and check that the email comes with the pitch deck attached.

## How pitch decks arrive
- Files up to **10 MB** (PDF, PPT or PPTX) are attached to the application email.
- For bigger files, applicants paste a **Google Drive, Canva or OneDrive link** instead, and the link appears in the email.
- FormSubmit doesn't keep a copy, so the email is the only copy of the file. Check your spam folder now and then, and don't delete application emails.

## Where to find everything
- **Every application:** your inbox. The subject is `New application: <project> (<type>) · CMK-XXXXXX`.
- **A backup of all application details (without the file):** Firestore → `applications`, with one document per reference number.
- **Unfinished applications:** Firestore → `drafts`. Once someone submits, their draft is marked `submitted` and locked.

## How drafts work
A draft is saved under a scrambled key made from the applicant's **email + date of birth**. Visitors can't browse or list drafts; they can only open the one that matches what they type in. Anyone who knows both values for someone could open that person's draft.
Drafts keep everything except the file itself. After loading a draft, the applicant attaches the pitch deck again before submitting.

## Free-plan limits
Firestore's free plan allows 50,000 reads and 20,000 writes per day and 1 GB of storage, which is far more than a competition needs.
