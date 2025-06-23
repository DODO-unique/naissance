# A repo creation utility  
Why? Because raccoons who memorize git commands are... well, idk, not lazy?

---

### What the code does (basically):

1. It creates a `.git`, which makes a folder Git-powered.
2. It adds `README.md` and `.gitignore` if they’re not already present; overwrites if the user gives consent.
3. It stages what you need and allows you to add files to `.gitignore`.
4. It commits with a default message.
5. It pushes to the working branch.

*All of the above comes with colors and sarcasm.*

---

### What an expected run should feel like:

1. You run the script (duh), it asks for the repo path.
   - If the path is incorrect or not found, the script ends.
   - If you entered `"these"` bad boys, it’s fine—but nothing else in the input, please.
   - Just Ctrl+Shift+C the path from File Explorer and Ctrl+Shift+V it here. That’s recommended.
2. After entering the repo (fingers crossed you pasted it), you’ll be prompted for the Git URL.
   - I have sanitization here, so no funky raccoon entries.
   - Injections? If you get some working, **share them with me**. I want to see what you broke. We’ll talk like friendly raccoons over virtual espresso.
3. Expect something dramatic here. Like a countdown before kaboom.
4. It asks if you want to push *all* the files. Technically it’s about staging, but you won’t get asked again—so decide now.
   - If you say `y`, it stages and pushes all files in the repo. This includes temp/junk files too.
   - If you say `n`, it asks if you want to edit `.gitignore`:
     - If yes: Notepad opens. Once you close it, git stages everything with `.gitignore` in effect.
       - ⚠️ *Note:* Save the file before closing.
     - If no: Only `.gitignore` and `README.md` are committed and pushed.
5. First commit will be `"initial commit"` and includes whatever was staged.
6. Git sets the remote origin to the URL you entered.
7. Git checks the current branch. Since we already committed in step 5, it'll be `main` or `master` (no custom branches assumed).
8. Repo gets pushed to origin.

---

### What's pending?

- Known edge cases I plan to handle:
  - Check if `origin` already exists.
  - Check if Git is installed (bruh… seriously).
  - Handle branch chaos (gut feeling: the logic is *too* simple, something’s off).
- Add custom commit message support (still thinking about input sanitization here).
- The script breaks easily if you poke it wrong—I don’t like that.
- I want to add ASCII art + fix colors (looked cool in VSCode but ugly on PowerShell, ngl).

---

### Insights:

- I was staring at my git notes and, despite uploading 4 repos already, I *still* couldn’t remember the sequence. So I sighed, set my webdev project aside for 4 hours, and automated this thing.
- I’ve uploaded 2 repos using this already and I’m lowkey proud.
- I used ChatGPT (because I didn’t know PowerShell and nobody Googles anymore) and learned while building. Now quiz me—I dare you.
- PowerShell is *shockingly intuitive*. Like:
  - `-ErrorAction Stop` halts on error instead of continuing silently.
  - String interpolation that’s easier than Python? Yup.
  - PHP should take notes.

---

### 💡 Niche Stuff You Might Like:

- `-ForegroundColor` = instant vibes
- `Write-Host` = output | `Read-Host` = input
- `Start-Sleep` = `time.sleep()` vibes
- Regex 101:
  - `^` outside brackets = start-of-line anchor
  - `^` inside brackets = *negation* (e.g., `[^a-z]`)
  - `$` = end-of-line anchor
- No `==` in PowerShell: use `-eq`, and `-ne` for `!=`
- Scripts ignore errors by default unless told to `exit`
- `$var` is a variable (yes, it surprised me too)
- `$true`, `$false` = booleans
- Arrays: use `@()` → `$example = @($example)`
- Dictionaries: use `@{}` → like Python dicts
- Interpolation rules:
  - `"Hello, $user"` → interpolates
  - `'Hello, $user'` → prints literally
- Escape characters use backticks: `` ` ``
- `Out-Null` suppresses noisy output
- `Push-Location` (like `pushd`) and `Pop-Location` are stack-based directory jumpers
- `Write-Host` for console, `Write-Output` for pipelines
- Git origin lives in `.git/config`, and adding it twice = error

---

### Final Thoughts:

This was fun. Worth the evening.
And honestly?  
The next time I need to create a repo, I’ll probably run this instead of thinking.

