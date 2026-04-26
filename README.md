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

<img width="1563" height="938" alt="Screenshot 2026-04-26 at 8 07 07 PM" src="https://github.com/user-attachments/assets/bae08248-c91c-49fb-b34c-42646da389ef" />


### 2. Staging Branch Workflow Run

Triggered by pushing to `staging`. Both `test` and `deploy-staging` jobs succeeded.

<img width="1562" height="518" alt="Screenshot 2026-04-26 at 8 08 26 PM" src="https://github.com/user-attachments/assets/3b3fc8b4-5d35-4f4f-bea0-0a9ec920f86a" />


### 3. Repository Secrets

The required secrets configured in the repository.

<img width="1566" height="922" alt="Screenshot 2026-04-26 at 8 11 59 PM" src="https://github.com/user-attachments/assets/cd7c75ff-10da-4c68-bd51-f1a82f7edac3" />


<img width="1565" height="920" alt="Screenshot 2026-04-26 at 8 12 23 PM" src="https://github.com/user-attachments/assets/e9220e9b-4910-4bbf-b52a-9b386ebf6021" />


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

**Repository URL:** `https://github.com/Akashgope/flask_Practice`



