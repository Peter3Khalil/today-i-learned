# Push to different repos.

1. Add the two remotes to your project. For example:

   - `origin` for your primary repository.
   - `backup` for the second repository.

   ```bash
   git remote add origin <URL-of-first-repo>
   git remote add backup <URL-of-second-repo>
   ```

2. Use the `git remote` command to verify both remotes are added:

   ```bash
   git remote -v
   ```

3. Create a custom remote that combines both repositories into one. You can do this by setting up a push URL:

   ```bash
   git remote set-url --add origin <URL-of-first-repo>
   git remote set-url --add origin <URL-of-second-repo>
   ```

4. Push changes to both repositories:

   ```bash
   git push origin main
   ```

This will push your changes to both repositories simultaneously. Let me know if you'd like me to clarify or assist further!

If you want the flexibility to push to specific remotes (instead of all at once), you can push to individual remotes manually when needed. Here's how:

### 1. **Push to a Specific Remote**

You can push to a specific remote by specifying the remote name and the branch. For example:

- To push to the `origin` remote:

  ```bash
  git push origin main
  ```

- To push to the `backup` remote:
  ```bash
  git push backup main
  ```

This gives you control over which repository to push to.

---

### 2. **Default Behavior for `git push`**

If you want `git push` without arguments to push only to a specific remote by default, you can set the default remote:

```bash
git branch --set-upstream-to=origin/main main
```

This ensures that `git push` defaults to the `origin` remote. To push to the `backup` remote, you can still explicitly specify it as shown above.

---

### 3. **Push to Both Repos Occasionally**

If you still want to occasionally push to both remotes at the same time, you can set up a custom alias in Git:

```bash
git config --global alias.pushall '!git push origin master && git push backup master'
```

Now, you can simply type:

```bash
git pushall
```

This will push to both remotes when needed, while still letting you push to a single remote using standard commands.

If you've added multiple URLs to the `origin` remote and now want to remove one or reset them, you can follow these steps:

### 1. **List All URLs for the Remote**

Check the current URLs associated with `origin`:

```bash
git remote get-url --all origin
```

This will show you all the URLs currently configured for the `origin` remote.

---

### 2. **Remove a Specific URL**

To remove a specific URL (e.g., `<URL-of-second-repo>`), use the following command:

```bash
git remote set-url --delete origin <URL-of-second-repo>
```

This will remove the specified URL from the `origin` remote.

---

### 3. **Reset the Remote URL**

If you want to reset the `origin` remote to a single URL, you can do so with this command:

```bash
git remote set-url origin <new-URL>
```

This will replace all existing URLs for `origin` with the new one.

---

### 4. **Verify the Changes**

After making changes, verify the URLs for `origin` again:

```bash
git remote get-url --all origin
```

This ensures that only the desired URLs are now associated with `origin`.
