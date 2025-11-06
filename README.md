# Experiment 9.2: CI/CD Pipeline using GitHub Actions

##  🎯 Objective
Understand how to automate testing and deployment using GitHub Actions. Learn to trigger workflows on code pushes, run tests automatically, and deploy artifacts to GitHub Pages.

## 📦 Project Structure
```
experiment-9.2/
├── .github/
│   └── workflows/
│       └── main.yml          # CI/CD workflow configuration
├── public/
│   └── index.html
├── src/
│   ├── App.js
│   ├── App.css
│   ├── App.test.js        # Test file
│   ├── index.js
│   └── index.css
├── package.json
└── README.md
```

## ⚙️ CI/CD Pipeline Workflow

The workflow is configured to:

### Triggers
- ▶️ **Push to main branch** - Automatically runs on every push
- ▶️ **Pull requests** - Runs on PRs targeting main branch

### Pipeline Steps

1. **Checkout Code** 📋
   - Uses `actions/checkout@v3`
   - Clones the repository

2. **Setup Node.js** 🟢
   - Uses `actions/setup-node@v3`
   - Sets up Node.js version 18
   - Caches npm dependencies for faster builds

3. **Install Dependencies** 📦
   - Runs `npm ci` (clean install)
   - Installs exact versions from package-lock.json

4. **Run Tests** ✅
   - Runs `npm test`
   - Executes Jest tests
   - Fails the workflow if tests fail

5. **Build Project** 🛠️
   - Runs `npm run build`
   - Creates optimized production build
   - Outputs to `build/` directory

6. **Deploy to GitHub Pages** 🚀
   - Uses `peaceiris/actions-gh-pages@v3`
   - Only runs on push to main (not on PRs)
   - Deploys build artifacts to `gh-pages` branch
   - Makes app available at GitHub Pages URL

## 🚀 Getting Started

### Prerequisites
- Git installed
- Node.js 18+ installed
- GitHub account

### Local Setup

1. **Clone the repository**
```bash
git clone https://github.com/TanSehgal/experiment-9.2.git
cd experiment-9.2
```

2. **Install dependencies**
```bash
npm install
```

3. **Run the app locally**
```bash
npm start
```
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

4. **Run tests**
```bash
npm test
```

5. **Build for production**
```bash
npm run build
```

## 🔄 How the CI/CD Pipeline Works

### Automated Workflow Execution

1. **Developer pushes code to main branch**
2. **GitHub Actions automatically triggers the workflow**
3. **Runner spins up Ubuntu environment**
4. **Workflow executes all steps sequentially**
5. **Tests run - if they fail, deployment is stopped**
6. **Build creates production artifacts**
7. **Deployment publishes to GitHub Pages**
8. **App is live at: https://tansehgal.github.io/experiment-9.2**

## 📊 Viewing Workflow Status

### In GitHub Repository
1. Go to the **Actions** tab
2. See list of all workflow runs
3. Click on any run to see detailed logs
4. Each step shows execution time and output
5. Green checkmark = success ✅
6. Red X = failure ❌

### Workflow Badge
Add this to your README to show build status:
```markdown
![CI/CD Pipeline](https://github.com/TanSehgal/experiment-9.2/workflows/CI/CD%20Pipeline/badge.svg)
```

## 🛠️ Configuration Files

### `.github/workflows/main.yml`
The workflow configuration file that defines:
- When to trigger (push/PR events)
- What environment to use (ubuntu-latest)
- What steps to execute
- How to deploy

### `package.json`
Contains:
- Project dependencies
- Test scripts
- Build scripts
- GitHub Pages homepage URL
- Deploy scripts

## 🌐 Deployment

### GitHub Pages Setup
1. Repository Settings → Pages
2. Source: Deploy from branch
3. Branch: `gh-pages` (created automatically by workflow)
4. App URL: `https://tansehgal.github.io/experiment-9.2`

### Deployment Process
- Workflow builds the app
- Creates static files in `build/` directory
- Pushes build folder to `gh-pages` branch
- GitHub Pages serves the app

## ✨ Key Features

- ✅ **Automated Testing** - Tests run on every push
- ✅ **Automated Building** - Production build created automatically
- ✅ **Automated Deployment** - App deployed to GitHub Pages
- ✅ **Pull Request Checks** - PRs are tested before merge
- ✅ **Build Status Visibility** - See workflow status in Actions tab
- ✅ **Fast Feedback** - Know immediately if something breaks

## 📝 Learning Outcomes

1. **Understanding CI/CD concepts**
2. **Writing GitHub Actions workflows**
3. **Configuring workflow triggers**
4. **Setting up automated testing**
5. **Automating deployment processes**
6. **Reading workflow logs and debugging**
7. **Managing secrets and tokens**
8. **Deploying to GitHub Pages**

## 👨‍💻 Author
TanSehgal

## 📝 License
This project is for educational purposes.

---

**Happy Automating! 🤖✨**
