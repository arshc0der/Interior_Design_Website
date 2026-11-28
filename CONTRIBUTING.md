# Contributing to Infra Interiors

Thank you for wanting to help! 🎉 This guide is written for **complete beginners**. If you have never used Git or GitHub before, you are in the right place. Take it one step at a time.

## Table of contents

1. [What you need](#1-what-you-need)
2. [Step-by-step: your first contribution](#2-step-by-step-your-first-contribution)
3. [Keeping your fork up to date](#3-keeping-your-fork-up-to-date)
4. [What makes a good pull request](#4-what-makes-a-good-pull-request)
5. [Ways to contribute](#5-ways-to-contribute)
6. [Rules and expectations](#6-rules-and-expectations)
7. [Common problems and fixes](#7-common-problems-and-fixes)
8. [Getting help](#8-getting-help)

---

## 1. What you need

- A free [GitHub account](https://github.com/signup)
- [Git](https://git-scm.com/downloads) installed (check with `git --version`)
- A code editor, for example [VS Code](https://code.visualstudio.com/)
- A web browser (Chrome, Firefox or Edge)

First-time Git setup (run once):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the same email as your GitHub account.

## 2. Step-by-step: your first contribution

### Step 1 – Choose an issue

1. Open the [Issues tab](https://github.com/arshc0der/Interior_Design_Website/issues).
2. Filter by the label **good first issue**.
3. Open an issue you like and write a comment such as *"I would like to work on this."*
4. Wait until a maintainer assigns it to you. This stops two people doing the same work.

No suitable issue? Open a new one first and describe your idea before writing code.

### Step 2 – Fork the repository

A **fork** is your own copy of the project on GitHub.

1. Go to <https://github.com/arshc0der/Interior_Design_Website>.
2. Click the **Fork** button (top right).
3. Click **Create fork**. You now have `https://github.com/YOUR-USERNAME/Interior_Design_Website`.

### Step 3 – Clone your fork

This downloads **your fork** to your computer.

```bash
git clone https://github.com/YOUR-USERNAME/Interior_Design_Website.git
cd Interior_Design_Website
```

Add the original project as `upstream` so you can get updates later:

```bash
git remote add upstream https://github.com/arshc0der/Interior_Design_Website.git
git remote -v
```

You should see `origin` (your fork) and `upstream` (the original).

### Step 4 – Create a branch

Never work on `main` directly. Make a new branch with a short, clear name:

```bash
git checkout -b fix/typo-in-footer
```

Branch name examples: `fix/duplicate-ids`, `docs/improve-readme`, `feature/mobile-menu`.

### Step 5 – Make your change

1. Open the folder in VS Code.
2. Open `index.html` in your browser to see the result.
3. Edit the files for **only the issue you picked**. Keep the change small.
4. Refresh the browser and check that the page still looks right.

### Step 6 – Check your work

Before committing, check:

- [ ] The page opens without errors
- [ ] Your change looks correct at a wide and a narrow browser window
- [ ] You did not change unrelated lines
- [ ] Images still load (paths use `/`, not `\`)

See the [Style Guide](docs/STYLE_GUIDE.md) for code rules.

### Step 7 – Commit

```bash
git status                # see what changed
git add index.html        # add the files you changed
git commit -m "fix: correct spelling mistakes in footer (#12)"
```

Write the message as `type: short description (#issue-number)`. Types: `fix`, `feat`, `docs`, `style`, `refactor`, `chore`.

### Step 8 – Push to your fork

```bash
git push origin fix/typo-in-footer
```

### Step 9 – Open a pull request (PR)

1. Go to your fork on GitHub. A yellow banner will say **Compare & pull request**. Click it.
2. Make sure the base repository is `arshc0der/Interior_Design_Website` and the base branch is `main`.
3. Fill in the template. Write `Closes #12` (use your issue number) so the issue closes automatically.
4. Add screenshots for any visual change.
5. Click **Create pull request**.

### Step 10 – Respond to review

A maintainer may ask for changes. This is normal and not a criticism.

1. Make the changes on the **same branch** on your computer.
2. `git add`, `git commit` and `git push origin your-branch-name` again.
3. The pull request updates by itself.

When the PR is merged, congratulations, you are an open-source contributor! 🚀

## 3. Keeping your fork up to date

If a few days pass, `main` may have new changes. Before starting new work:

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

If your branch is behind:

```bash
git checkout your-branch-name
git merge main
```

## 4. What makes a good pull request

- **One issue per PR.** Small PRs are reviewed faster.
- **A clear title**, for example `fix: replace backslashes in image paths`.
- **A description** of what changed and why.
- **Screenshots** (before and after) when the look changes.
- **No unrelated changes**, such as reformatting the whole file.
- **No large or copyrighted files.** Use images you own or that are free for commercial use (e.g. Unsplash, Pexels) and mention the source.

## 5. Ways to contribute

You do not have to write code.

| Type | Examples |
| --- | --- |
| 🐞 Bug fixes | Broken paths, invalid HTML, CSS typos |
| ✨ Features | Mobile menu, gallery, form validation |
| 📱 Responsive design | `@media` queries for phones and tablets |
| ♿ Accessibility | Alt text, focus styles, semantic tags |
| 🔎 SEO | Meta tags, favicon, Open Graph |
| ⚡ Performance | Compress images, lazy loading |
| 📝 Documentation | Fix typos, improve guides, translate |
| 🧪 Testing | Test on other browsers and phones, report results |
| 🎨 Design | Suggest layouts, colors, fonts |

The complete list of ideas is in [docs/ISSUES_BACKLOG.md](docs/ISSUES_BACKLOG.md).

## 6. Rules and expectations

- Be kind. Read the [Code of Conduct](CODE_OF_CONDUCT.md).
- Ask before starting large work.
- Follow the [Style Guide](docs/STYLE_GUIDE.md).
- By contributing, you agree your work is released under the project's [MIT License](LICENSE).
- Do not commit secrets, passwords or personal data.
- If you use AI tools to help, you are still responsible for understanding and testing the code you submit.

## 7. Common problems and fixes

| Problem | Fix |
| --- | --- |
| `fatal: not a git repository` | You are in the wrong folder. Run `cd Interior_Design_Website`. |
| `Permission denied` when pushing | You cloned the original repo, not your fork. Run `git remote set-url origin https://github.com/YOUR-USERNAME/Interior_Design_Website.git`. |
| I edited `main` by mistake | Run `git checkout -b my-new-branch`, then commit there. |
| Merge conflict | Open the marked file, keep the correct lines, delete the `<<<<<<<`, `=======`, `>>>>>>>` markers, then `git add` and `git commit`. Ask for help if unsure. |
| Images do not show | Check file names and use `/` in paths. File names are case-sensitive on GitHub Pages. |
| I want to undo my last commit (not pushed) | `git reset --soft HEAD~1` |

More commands are explained in [docs/GIT_CHEAT_SHEET.md](docs/GIT_CHEAT_SHEET.md).

## 8. Getting help

- Ask a question in the issue you are working on.
- Open a new issue using the **Question** option.
- Be patient: maintainers are volunteers.

Happy coding! 💙
