## Team Git Rules & Best Practices 

## 1.	Git Usage Rules
1	Git ignore files (.gitignore) should never be pushed to remote if they contain system-specific or sensitive files.
2	Avoid using `git add .` or adding all files by default. Always add specific files that are required.
3	Always pull the latest changes from the master (or main) branch before starting work on your feature branch using `git pull origin master`.
4	Keep your branch updated regularly to avoid merge conflicts.
5	Never commit build, log, or temporary files.
6	Always check for migration duplication before committing. Ensure no repeated or conflicting migration timestamps.

 ## 2. Migration Rules
1	Before creating a new migration, check the existing migrations to ensure no duplicate columns or table creations.
2	Use clear and descriptive names for migrations (e.g., `add_status_to_orders` instead of generic names).
3	Run migrations locally before pushing to verify schema correctness using `rails db:migrate`.
4	Never manually edit existing migrations once pushed to a shared branch.

 ## 3.	Server Setup Steps
•	Install required Ruby gems using: `bundle install` 
•	Install JavaScript dependencies using: `yarn install` 
•	Create the database: `rails db:create`
•	Run all migrations: `rails db:migrate`
•	Start the Vite development server: `vite dev` 
• Start the Rails server: `rails s`	

## 4.	Validation Best Practices
1	Avoid adding validations to every column field by default—it can cause unexpected model-wide issues.
2	Add validations only when necessary, i.e., when the field is required across the model’s workflow.
3	Ensure validation logic matches business requirements and does not break existing data entries.
4	Always test validations with both valid and invalid data before committing.

## 5.	General Best Practices
1.	Commit frequently with meaningful commit messages.
2.Use feature branches for new features and bug fixes.
3.Always review your code before creating a pull request.
4.Run the test suite before pushing code to ensure stability.
5.Follow consistent naming conventions for branches (e.g., `feature/add-user-auth`,`bugfix/fix-login-error`).
6.Do not commit secrets, environment variables, or sensitive credentials.

# Anvaya CMS

## 🧱 Overview

Anvaya CMS is a **SaaS platform** built using **Ruby on Rails**, designed for modular, secure, and scalable application management. The project is developed and maintained by **Trikaan Dev Team**.

---

## ⚙️ Core Features

* **Single-Tenant Architecture**: Built for a single organization with modular feature expansion.
* **Admin Panel**: Central control for managing users, roles, and feature access.
* **Feature-based Access**: Enable or disable features per user role or plan.
* **Audit Logging**: All system and user actions (including custom events) are logged for transparency.
* **Secure Sessions & Secrets**: Rails credentials and cookies use the latest security standards.
* **Future Chat Integration**: ActionCable + Redis-based chat module.

---

## 🧩 Tech Stack

* **Backend:** Ruby on Rails 8 (PostgreSQL)
* **Frontend:** TailwindCSS (via `tailwindcss-rails`)
* **Auth:** Devise (customized for role-based authentication)
* **Audit Logging:** `audited` gem with support for domain events
* **Database:** PostgreSQL

---

## 🚀 Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/trikaan-solutions/anvaya-cms.git
cd anvaya-cms
```

### 2️⃣ Install Dependencies

```bash
bundle install
yarn install --check-files
```

### 3️⃣ Setup the Database

```bash
bin/rails db:create db:migrate db:seed
```

This seeds the database with:

* Default Plans (Basic, Pro, Enterprise)
* A default Admin user and base configurations

### 4️⃣ Start the Server

```bash
bin/dev
```

Visit the app at: `http://localhost:3000`

---

## 🧠 Application Architecture

```
app/
 ├── controllers/
 │   ├── admin/
 │   ├── users/
 │   └── public/
 ├── models/
 │   ├── user.rb
 │   ├── plan.rb
 │   ├── feature.rb
 │   └── audit_log.rb
 ├── views/
 └── middleware/
     └── custom_session_store.rb
```

---

## 🛡️ Security & Best Practices

* CSRF, XSS, and cookie tampering protection enabled.
* Strong session management with encrypted keys.
* All secrets stored using `Rails.application.credentials`.

---

## 🔍 Audit Logging

* Logs all CRUD actions via `audited` gem.
* Supports **custom domain events** like Purchase Orders, Vehicle Inspections, etc.

---

## 📦 Future Enhancements

* ✅ Role-based Permission Engine
* ✅ Feature Toggles per Plan
* ✅ Admin Analytics Dashboard
* ✅ Real-time Chat System
* ✅ React Integration (optional frontend)

---

## 👨‍💻 Authors

**Trikaan Dev Team** — Core Development, Architecture & Product Management

---

## 🧭 Next Steps

* [ ] Finalize role-based permissions
* [ ] Add admin feature control dashboard
* [ ] Implement event-based audit logging
* [ ] Prepare React SPA integration


---

**📘 License:** MIT
