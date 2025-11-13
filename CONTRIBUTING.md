# Contributing

## 1. Prerequisites

Install the following tools:

- Git  
- VS Code (recommended)  

## 2. Fork and Clone

1. Fork the repository on GitHub.  
2. Clone your fork and open it in VS Code.

```
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
cd REPO_NAME
```

## 3. One-Time Setup

Required: Node.js (v24).

## 4. Pull Fresh Code

```
git pull origin main
```

## 5. Validate

After changes to schemas or examples, validate as needed, using a Git Bash / bash / zsh terminal: 

```
npx ajv-cli validate --spec=draft2020 -s schema/ptag.core.schema.json  -d examples/core-lib_ptag.json

npx ajv-cli validate --spec=draft2020 -r schema/ptag.core.schema.json -s schema/ptag.civic-data.schema.json -d examples/civic-data_dataset_ptag.json

npx ajv-cli validate --spec=draft2020 --strict=false -s schema/ptag.privacy.schema.json -d examples/privacy_ptag.json
```

## 6. Commit and Push

```
git add .
git commit -m "Your message"
git push
```

## 7. Open a Pull Request

Open a PR from your fork to the `main` branch of the target repository.

Guidelines for good PRs are here:  
`REF_PULL_REQUESTS.md`

---

If you have questions, open an issue in the target repository.  
Thank you for contributing to Civic Interconnect.
