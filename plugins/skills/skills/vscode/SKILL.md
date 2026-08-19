---
name: vscode
description: Editor session, VS Code window, stale path, repo moved, directory renamed, `mv` the repo, reopen at new path, `code <path>`, stale file tree. Use right after this repo's directory is moved or renamed, so the open editor is not pointed at the old path.
---

# VS Code

Keeping the editor session honest with the repo's actual location.

1. **A move or rename invalidates the open editor window.** After `mv`-ing or
   renaming this repo's directory, reopen it at the new path: `code <new-path>`.
   An editor left pointed at the old path shows a stale tree and its
   integrated terminal `cd`s back into a directory that no longer exists.
