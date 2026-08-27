# Portfolio Site

A modern Vue 3 portfolio for frontend developers, built with Vite and Tailwind CSS.

## Stack

- **Vue 3** (Composition API, `<script setup>`)
- **Vite** for dev server and bundling
- **Tailwind CSS** for styling with a custom design system
- **Vue Router** for client-side routing
- **EmailJS** for contact form delivery (no backend required)
- **Lucide Icons** for iconography

## Project Structure

```
src/
├── components/       # Reusable UI components
│   ├── Header.vue
│   ├── Hero.vue
│   ├── About.vue
│   ├── Skills.vue
│   ├── Projects.vue
│   ├── ProjectCard.vue
│   ├── Contact.vue
│   └── Footer.vue
├── views/
│   ├── Home.vue
│   └── ProjectDetail.vue
├── router/           # Vue Router configuration
├── assets/css/       # Global styles & design tokens
├── App.vue
└── main.js
```

## Getting Started

```bash
npm install
npm run dev
```

Visit `http://localhost:5173`.

## Scripts

- `npm run dev` — start the dev server
- `npm run build` — build for production
- `npm run preview` — preview the production build

## Setting Up the Contact Form (EmailJS)

The contact form uses [EmailJS](https://www.emailjs.com/) to send messages directly to your inbox — no backend needed.

### 1. Create an EmailJS account
Sign up at [emailjs.com](https://www.emailjs.com) (free tier allows 200 emails/month).

### 2. Add an email service
In the dashboard, go to **Email Services** → **Add New Service** → connect your email provider (Gmail, Outlook, etc.). Copy the **Service ID**.

### 3. Create an email template
Go to **Email Templates** → **Create New Template**. Use these variable names so the form data maps correctly:

| Variable | Source |
|----------|--------|
| `{{from_name}}` | Sender's name |
| `{{from_email}}` | Sender's email |
| `{{subject}}` | Subject line |
| `{{message}}` | Message body |

Example template:
```
Subject: [Portfolio] {{subject}}

From: {{from_name}} <{{from_email}}>

{{message}}
```

Copy the **Template ID**.

### 4. Get your public key
Go to **Account** → **General** tab → copy your **Public Key**.

### 5. Add credentials to `.env`
```bash
cp .env.example .env
```

Edit `.env` and replace the placeholder values:
```
VITE_EMAILJS_SERVICE_ID=service_abc123
VITE_EMAILJS_TEMPLATE_ID=template_xyz789
VITE_EMAILJS_PUBLIC_KEY=aBcDeFgHiJkLmNoPq
```

### 6. Restart the dev server
```bash
npm run dev
```

The form is now live. Test it by submitting a message — it should arrive in your inbox within seconds.

## Customization

- **Profile info:** Edit components in `src/components/`
- **Projects:** Update the `projects` array in `src/components/Projects.vue`
- **Skills:** Update the arrays in `src/components/Skills.vue`
- **Colors / theme:** Edit CSS variables in `src/assets/css/globals.css`
- **Social links:** Search for `https://github.com` / `https://linkedin.com` and replace

## Deployment

Build the static site and deploy to any static host (Vercel, Netlify, Cloudflare Pages, GitHub Pages):

```bash
npm run build
```

The `dist/` folder contains the production build. When deploying, set the environment variables in your host's dashboard so the contact form keeps working.
