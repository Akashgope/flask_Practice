# Flask App CI/CD with GitHub Actions

This project demonstrates a complete CI/CD pipeline using GitHub Actions for a Python Flask application.

## 📦 Repository Structure

## 🚀 GitHub Actions Workflow

The workflow (`.github/workflows/ci-cd.yml`) automates testing and deployment.

### Triggers
- Push to `main` → runs only **tests**
- Push to `staging` → runs **tests** + deploys to **staging**
- **Release created** → runs **tests** + deploys to **production**

### Jobs Explained

1. **test**  
   - Sets up Python 3.10  
   - Installs dependencies from `requirements.txt`  
   - Runs `pytest` on `test_app.py`

2. **deploy-staging**  
   - Runs only if the push is to `staging` branch AND tests pass  
   - Uses secret `STAGING_DEPLOY_KEY` (simulated in demo)

3. **deploy-production**  
   - Runs only when a GitHub Release is created AND tests pass  
   - Uses secret `PROD_API_TOKEN` (simulated)

### 🔐 Secrets Configuration

The following secrets must be added in **Settings → Secrets and variables → Actions**:

| Secret Name          | Purpose                          |
|----------------------|----------------------------------|
| `STAGING_DEPLOY_KEY` | Authentication for staging server|
| `PROD_API_TOKEN`     | Authentication for production    |

> *For this assignment, dummy values were used because the deployment is simulated.*

---

## 📸 Screenshots of Workflow Execution

### 1. All Workflow Runs (Actions Tab)

All runs (push to main, push to staging, release) show green checkmarks.

![All workflow runs](screenshots/actions_runs.png)

### 2. Staging Branch Workflow Run

Triggered by pushing to `staging`. Both `test` and `deploy-staging` jobs succeeded.

![Staging run success](screenshots/staging_run.png)

### 3. Release Workflow Run

Triggered by creating a release (v1.0.0). Both `test` and `deploy-production` jobs succeeded.

![Release run success](screenshots/release_run.png)

### 4. Repository Secrets

The required secrets configured in the repository.

![Secrets configuration](screenshots/secrets.png)

### 5. Workflow YAML File

The actual workflow file located at `.github/workflows/ci-cd.yml`.

![Workflow file](screenshots/workflow_file.png)

---

## 🛠️ Steps Performed to Complete This Task

1. **Forked** the original repository to my GitHub account.
2. **Created** the `staging` branch locally and pushed it.
3. **Created** the `.github/workflows/` directory and added `ci-cd.yml` with the pipeline definition.
4. **Added** two secrets (`STAGING_DEPLOY_KEY`, `PROD_API_TOKEN`) in GitHub Settings.
5. **Triggered** the workflow by:
   - Pushing a commit to `main`
   - Pushing a commit to `staging`
   - Creating a release (v1.0.0)
6. **Verified** all runs succeeded via the Actions tab.
7. **Captured** screenshots of each successful run.
8. **Documented** everything in this README.md file.

---

## 📤 How to Test This Workflow Yourself

1. Clone this repository.
2. Create a `staging` branch if not present.
3. Add the required secrets in your fork.
4. Push changes to `main` / `staging` or create a release.
5. Watch the Actions tab for the automated pipeline.

---

## ✅ Deliverables for Assignment

- GitHub repository with workflow file ✓
- Documentation in README.md ✓
- Screenshots of GitHub Actions workflow runs ✓

**Repository URL:** `https://github.com/Akashgope/flask_Practice`# Student Registration System

A simple **Flask** web application to manage student records with **MongoDB** as the backend database. Users can **add, view, update, and delete** student details.

---

## Features

* List all students on the home page
* Add a new student
* Update existing student details
* Delete a student with confirmation
* Simple and responsive UI using Bootstrap

---

## Tech Stack

* **Backend:** Python, Flask
* **Database:** MongoDB (via Flask-PyMongo)
* **Frontend:** HTML, Jinja2 templates, Bootstrap 5
* **Environment Variables:** Managed via `.env` file

---

## Setup Instructions

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-folder>
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv
# Activate venv
# Windows:
venv\Scripts\activate
# Linux / Mac:
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

**`requirements.txt` example:**

```
Flask
Flask-PyMongo
python-dotenv
bson
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```
MONGO_URI=<your-mongodb-connection-string>
SECRET_KEY=<your-secret-key>
```

### 5. Run the application

```bash
python app.py
```

Open your browser at: [http://localhost:8000](http://localhost:8000)

---

## Project Structure

```
project/
│
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── add_student.html
│   ├── update_student.html
│
├── app.py
├── requirements.txt
└── .env
```

---

## Screenshots

**Home Page**
Lists all students with Edit/Delete buttons.
- <img width="1902" height="607" alt="image" src="https://github.com/user-attachments/assets/a58a6a6d-4978-4769-8074-232e4d31e69d" />


**Add Student**
Form to add a new student.
- <img width="1897" height="801" alt="image" src="https://github.com/user-attachments/assets/d65d25c3-ebb5-410a-adb1-e130ad7c5878" />


**Update Student**
Form pre-filled with student details.
- <img width="1905" height="897" alt="image" src="https://github.com/user-attachments/assets/04febf01-879f-431f-ab07-abcfb993acf1" />



---

## Notes

* Make sure MongoDB is running and accessible via the URI in `.env`
* Delete action includes a confirmation page to prevent accidental deletion
* Uses `ObjectId` from `bson` to work with MongoDB document IDs
* If you use MongoDB Atlas on macOS, install dependencies again (`pip install -r requirements.txt`). This project now uses `certifi` CA bundle explicitly to avoid common TLS certificate verification failures with `pymongo`.

---

## License

MIT License

---



