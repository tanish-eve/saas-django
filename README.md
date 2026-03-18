---

# Scalable SaaS Subscription Platform
*An enterprise-grade reference architecture for Python-based SaaS systems.*

This project implements a robust Software as a Service (SaaS) foundation using **Python 3.12**, **Django 5.2**, **Tailwind CSS**, and **htmx**. It is designed to demonstrate core backend engineering competencies including secure recurring billing, serverless database orchestration with Neon Postgres, and automated background tasks via GitHub Actions.

## System Highlights
* **Automated Subscription Lifecycle:** Integrated **Stripe API** for secure, multi-tier recurring billing and webhook handling.
* **Serverless Persistence:** Leverages **Neon PostgreSQL** for high-performance relational data with automated branching for testing.
* **Reactive Frontend:** Engineered a responsive UI using **Tailwind CSS** and **htmx** to provide a modern, single-page application feel without the overhead of heavy SPA frameworks.
* **Enterprise Identity Management:** Utilizes **Django Allauth** for robust social (GitHub) and email-based authentication flows.
* **DevOps & Automation:** Fully containerized with **Docker** and managed via **Rav** to ensure consistent development and production parity.

---

## Technical Stack
| Category | Technologies |
| :--- | :--- |
| **Backend** | Python 3.12, Django 5.2 |
| **Persistence** | PostgreSQL (Neon serverless), Redis |
| **Payments** | Stripe API (Subscriptions & Webhooks) |
| **Frontend** | Tailwind CSS, htmx, Slippers |
| **Infrastructure** | Docker, Railway, GitHub Actions |

---

## Getting Started

### 1. Environment Setup
Clone the repository and initialize the virtual environment:

```bash
git clone https://github.com/tanish-eve/SaaS-Foundations.git
cd SaaS-Foundations

# Windows (Git Bash)
python -m venv venv
source venv/Scripts/activate
```

### 2. Dependency Management
Utilize **Rav** to automate requirements installation and static asset management:

```bash
pip install pip rav --upgrade
rav run install
```

### 3. Configuration
Copy the sample environment file and update your credentials:

```bash
cp .env.sample .env
```

**Key Required Variables:**
* `DJANGO_SECRET_KEY`: Generate using `openssl rand -base64 64`
* `DATABASE_URL`: Your Neon Postgres connection string.
* `STRIPE_SECRET_KEY`: Obtained from your Stripe Developer Dashboard.

### 4. Database & Static Assets
Initialize the database schema and pull vendor-specific assets:

```bash
cd src
python manage.py migrate
python manage.py createsuperuser
python manage.py vendor_pull
```

---

## Workflow Automation (Rav)
The project includes a `rav.yaml` file to streamline core development tasks:
* `rav run dev` - Launch the local development server.
* `rav run test` - Execute the automated test suite.
* `rav run collectstatic` - Prepare assets for production.
* `rav run vendors_pull` - Synchronize third-party static dependencies.

---