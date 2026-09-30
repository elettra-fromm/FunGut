# Git Workflow – Quick Reference

### 1. PULL – Before starting work in JupyterHub

Get the latest changes from your teammates before editing anything.

```bash
cd ~/FunGut
git status
git pull origin main
```

### 2. WORK – Edit your notebook in JupyterHub

Work on your analysis, create figures, etc. Save your notebooks (`Cmd + S`).

### 3. STAGE – Select your changes

```bash
git add scripts/your_notebook.ipynb
```

This stages only the notebook you want to share, rather than automatically staging every changed file.

### 4. COMMIT – Save a snapshot locally

```bash
git commit -m "Add quality control analysis"
```

### 5. PULL AGAIN – Check for teammates' changes

```bash
git pull --no-rebase origin main
```

If someone pushed while you were working, Git integrates their changes with your local commits. If there are conflicts, resolve them before continuing.

### 6. PUSH – Share your work

```bash
git push origin main
```

Your teammates can now pull your changes into their own JupyterHub repositories!

---

**If something goes wrong:** Check `git status` first. Don't use `git push --force` on our shared `main` branch.
