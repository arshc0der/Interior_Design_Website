# Git Cheat Sheet for Beginners

Git is a tool that records changes to your files. GitHub is a website that stores Git projects online. Here are the words and commands you need.

## Words you will see

| Word | Meaning |
| --- | --- |
| **Repository (repo)** | A project folder tracked by Git |
| **Fork** | Your own copy of someone else's repo on GitHub |
| **Clone** | Download a repo to your computer |
| **Branch** | A separate line of work, so `main` stays clean |
| **Commit** | A saved snapshot of your changes with a message |
| **Push** | Upload your commits to GitHub |
| **Pull request (PR)** | A request to add your changes to the original project |
| **Origin** | Your fork on GitHub |
| **Upstream** | The original project |
| **Merge** | Combine two branches |
| **Conflict** | Two changes touched the same lines and Git needs you to choose |

## The contribution workflow in one picture

```text
Original repo (upstream)
        │  Fork
        ▼
Your fork (origin) ──Clone──► Your computer
        ▲                          │  branch → edit → commit
        └────────── Push ──────────┘
        │
        └── Open Pull Request ──► back to the original repo
```

## Everyday commands

```bash
git status                       # What changed?
git diff                         # Show the exact changes
git add <file>                   # Stage a file for commit
git add .                        # Stage all changes (check git status first!)
git commit -m "fix: message"     # Save a snapshot
git push origin <branch>         # Upload your branch to your fork
git pull upstream main           # Get the latest changes from the original repo
git log --oneline                # Show commit history
```

## Branches

```bash
git branch                       # List branches
git checkout -b my-branch        # Create and switch to a new branch
git checkout main                # Switch back to main
git branch -d my-branch          # Delete a branch (after it is merged)
```

## Oops, I need to undo something

| Situation | Command |
| --- | --- |
| Discard changes in one file (not committed) | `git checkout -- <file>` |
| Unstage a file | `git restore --staged <file>` |
| Undo last commit but keep the changes | `git reset --soft HEAD~1` |
| Fix the last commit message (not pushed) | `git commit --amend` |
| I committed on `main` by mistake | `git checkout -b new-branch` then continue there |

> ⚠️ Be careful with `git reset --hard` and `git push --force`. They can permanently delete work. Ask for help first.

## Fixing a merge conflict

1. Git marks the file like this:

   ```text
   <<<<<<< HEAD
   your version
   =======
   their version
   >>>>>>> main
   ```

2. Edit the file so only the final, correct text is left. Delete the three marker lines.
3. Run:

   ```bash
   git add <file>
   git commit
   ```

## Useful links

- [GitHub: Fork a repo](https://docs.github.com/en/get-started/quickstart/fork-a-repo)
- [GitHub: Creating a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)
- [First Contributions tutorial](https://github.com/firstcontributions/first-contributions)
