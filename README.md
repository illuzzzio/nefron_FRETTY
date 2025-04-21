

This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.js`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.


    Project introduction

    Features

    Setup instructions

    Clerk configuration

    iForm integration

    Developer notes

# 🗣️ NEFRON - Voice Web Assistant (Next.js + Clerk)

NEFRON is a Voice Web Assistant built using **Next.js** and **Clerk** for authentication. It supports **voice search, web commands, jokes**, and more — powered by **Speech Synthesis** and **Recognition APIs**. Additionally, this project demonstrates how to integrate **plain HTML, CSS, and JS** files into a Next.js app using the `app/page.js` route without converting them to JSX.

## ✨ Features

- 🔐 Authentication using [Clerk.dev](https://clerk.dev)
- 🗣️ Voice-controlled assistant (search, jokes, shortcuts)
- 🧠 Speech synthesis and recognition
- 💡 Easy integration of static `index.html`, `style.css`, and `app.js` using `iform`
- ⚡ Powered by Next.js App Router

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/nefron-voice-assistant.git
cd nefron-voice-assistant

2. Install Dependencies

npm install
# or
yarn install

3. Configure Clerk Authentication
a. Create a Clerk project

    Go to https://clerk.dev

    Create a new project

    Grab the Frontend API and Publishable Key

b. Create a .env.local file

touch .env.local

Paste the following:

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your-publishable-key
CLERK_SECRET_KEY=your-secret-key
NEXT_PUBLIC_CLERK_FRONTEND_API=your-frontend-api

    🔐 Note: Never commit .env.local to GitHub.

4. Run the App

npm run dev

Your app will be running on http://localhost:3000
📁 iForm Integration - Static HTML, CSS & JS in Next.js

To help developers easily migrate or embed static content, we’ve created an iForm system. This loads index.html, style.css, and app.js into the app/page.js.
File Structure:

app/
  page.js       # Main app page where we load static files
public/
  index.html    # Your static HTML file
  style.css     # Custom styles
  app.js        # Voice logic (JavaScript)

page.js Example

"use client";

import { useEffect } from "react";

export default function Home() {
  useEffect(() => {
    const iframe = document.getElementById("iform");
    if (iframe) {
      iframe.srcdoc = `
        <!DOCTYPE html>
        <html>
          <head>
            <link rel="stylesheet" href="/style.css" />
          </head>
          <body>
            ${require("fs").readFileSync("public/index.html", "utf8")}
            <script src="/app.js"></script>
          </body>
        </html>
      `;
    }
  }, []);

  return <iframe id="iform" className="w-full h-screen border-none" />;
}

    🧩 You can also just include the files statically via public/ and set the src="/index.html" in an iframe, or inject HTML/CSS via innerHTML and <style> blocks if needed.

🧑‍💻 Developer Notes

    Built using Next.js 14+ App Router (app/)

    Uses useEffect for client-side rendering and loading static content

    Clerk handles both sign in and sign up flows

    Voice functionality handled via window.SpeechRecognition and speechSynthesis

📸 Screenshots

🧾 License

MIT License
🤝 Contributing

Pull requests are welcome! If you’d like to improve the voice assistant, add new commands, or enhance authentication flows, feel free to fork and contribute.
👤 Author

Pranjal Malhotra
Student @ VIT Chennai | CSE AIML
Building cool AI things in public 🚀

