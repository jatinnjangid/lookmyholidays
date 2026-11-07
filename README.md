# LookMyHolidays ✈️🌴

LookMyHolidays is a modern travel agency web application offering customized holiday packages, destination guides, visa assistance, and 24/7 travel support.

## 🛠️ Tech Stack

- **Framework:** [TanStack Start](https://tanstack.com/start) / React 19
- **Routing:** [TanStack Router](https://tanstack.com/router)
- **Styling:** [Tailwind CSS v4](https://tailwindcss.com/) with OKLCH theme tokens
- **Animations:** [Framer Motion](https://www.framer.com/motion/)
- **Icons:** [Lucide React](https://lucide.dev/)
- **Backend & Auth:** [Supabase](https://supabase.com/) (PostgreSQL with Row Level Security)
- **Deployment:** [Vercel](https://vercel.com/)

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ or 20+
- npm (standard package manager)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/jatinnjangid/lookmyholidays.git
   cd lookmyholidays
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Configure Environment Variables:
   Create a `.env` file in the root directory:
   ```env
   VITE_SUPABASE_URL=https://your-supabase-project.supabase.co
   VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
   ```

### Development

Run the development server:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) (or the port specified by Vite/TanStack Start).

### Production Build

```bash
npm run build
npm run preview
```

---

## 🗄️ Database & Security

Database tables and Row Level Security (RLS) policies are configured in [`supabase_schema.sql`](./supabase_schema.sql):

- **`contact_enquiries`**: Stores booking requests and inquiries. Public insert enabled; read access strictly restricted to the enquiry owner (`auth.uid() = user_id`) or service role.
- **`general_inquiries`**: Stores general contact messages. Restrictive RLS enabled.
- **`searches`**: Stores user search queries.
- **`newsletter_subscriptions`**: Captures newsletter subscribers with uniqueness constraint.
- **`destinations`**: Public catalog of available holiday destinations.
- **`packages`**: Public catalog of travel packages.

To seed destination and package data safely:
```bash
node seed_database.js
```
*(Or execute non-destructive queries from [`seed_data.sql`](./seed_data.sql) in your Supabase SQL editor)*.

---

## ☁️ Deployment

LookMyHolidays is configured for deployment on **Vercel**:

1. Connect your repository to [Vercel](https://vercel.com).
2. Set the framework preset to **Vite** or **TanStack Start**.
3. Add the following environment variables in Vercel project settings:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`
4. Deploy the `main` branch.

---

## 🛡️ Security Best Practices

- **Row Level Security (RLS):** All public tables have RLS enabled with granular policies to prevent unauthorized data exposure.
- **Authentication:** Sessions are managed securely via Supabase Auth. Plaintext passwords are never persisted in client storage (`localStorage` / `sessionStorage`).
- **Form Integrity:** Submission flows require confirmation from the backend before displaying success confirmations, preventing false booking confirmations.

---

## 📄 License

LookMyHolidays © 2026. All rights reserved.
