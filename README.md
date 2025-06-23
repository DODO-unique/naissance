# A repo creation utility
why? because raccoons who memorize git commands are ... well, idk, not lazy?


### What the code does (basically):

1. It creates a .git, which makes a folder git-powered.
2. It adds README.md and .gitignore if they are already not present; overwrite if user gives consent
3. It stages what you need and allows user to add files to `.gitignore`
4. It commits with a default message
5. It pushes to the working branch

*All of the above with colors and sarcasm.*

### What an expected run should feel like:

1. You run the script (duh), it asks you a repo
    - if the repo is incorrect or not found, the script ends.
    - if you entered `"` these bad boys, its fine, but nothing else with the input.
    - just go ctrl+shift+C on the desired file, honestly and ctrl+shift+V the address, that's all. That's reccommended.
2. After entering the repo (fingers crossed you pasted it), you will be prompted to enter the URL
    - I have senitization measures here, so no funky raccoon entries.
    - Injections? If you could get some working please share them with me, I want to know what you did and what you broke. We will talk like friendly raccoons over espresso--virtual one.
3. Expect something dramatic here. Like a countdown before kaboom.
4. It asks you if you want to push all the files. Technically, it is asking you for staging those files but you won't be asked again before it gets pushed, so might as well decide now.
    - if you go `y`, it will push all the files currently in the repo. Please note that this would include the temp files.
    - if you go `n`, it will ask you if you want to add files to .gitignore
        - if you agree, you would be able to edit .gitignore (in Notepad); operations will resume when Notepad is closed. `git add .` would be ran, but this time, with `.gitignore` updated, specified changes would be ignored.
            - Note: closing the file will not save changes, please save before closing.
        - if you disagree, only .gitignore and README.md will be commited and pushed
5. first commit will be "initial commit" and whatever was staged in step 4.
6. git would stage for the remote URL as origin
7. git checks the current branch, since a commit has been made already in step 5, it would highlight main/master accordingly (no custom branch assuming this entire script is about creating a fresh repo in the first place)
8. Pushed to origin.

### What *I* know is pending:
- I have to work on these three known edge cases:
    - checking if origin already exists
    - checking if there is git at all (I mean, bruh, my guy)
    - checking the branch chaos (because my gut is telling me that logic is broken somehow-- as if, too simple, idk)
- I have to add custom commit message option but I need to figure out how I would handle sanitization there.
- This script can break very easily if you try it, and I don't like that, honestly.
- I want to add ASCII art and fix the colors because when I tested it on VScode, it felt good, but it is ugly on ps, ngl

### Insights:
- I was looking at my git notes and though I have uploaded 4 repos on github already I still can't remember what the sequence was, so I sighed, set my webdev project aside for 4 hrs, and decided to automate this thing. Now, I have uploaded two repos already, and I am lowkey proud.
- I used ChatGPT (because I did not know ps and no one googles stuff these days, come on, suck up) and learned things as I created the script. I can proudly be quizzed now and even nerd about it, and listen to it for hours.
- ps1 is *very* intuitive: you know what -ErrorAction Stop would do (it would make the script pause at errors and not ignore them, opposite of what `SilentlyContinue`) or string interpolation that is more convenient than even python? yup, just realized this gem existed-- PHP should learn.
- Some things to notice which are quite niche:

    - `-ForegroundColor`: lowkey sick for making your life colorful

    - `Write-Host` is output, `Read-Host` is input

    - `Start-Sleep` is intuitive, like `time.sleep(seconds)`, similarly `Start-Sleep -Seconds sec` or `Start-Sleep -Miliseconds ms`

    - regex: `^` has context, outside the box brackets it means 'begining', an achor as in 'match only me in the start', inside the box, it is for negation 'match anything but me'. Completely contradictory, yes. `$` checks match for ending stuff.

    - no `==`, go `-eq`; `-ne` for `!=`

    - note that ps scripts ignore errors and move on to finish the script by default. remember to `exit`, like you `return` in other languages, when you want

    - `$something` is a variable, and yes i was suprised when I realised this thing has variables, now I am won't flinch here for using recursion

    - `$true` and `$false` are the booleans here. Not case-sensitive but keep them short, that is convention.

    - this thing has collections, you call them arrays here. Take a `$example = string`, go `$example = @($example)` and that is an array now. So you could call it as $example[0] and would get `s` but now it would return `string`. You can have this as a key-value pair by using curly brakcets instead like `@{}` and call it like dictionaries in python.

    - There is juicy lore in string interpolation here and I can't sleep without sharing it: So double quotes automatically format things, so `"Hello, $user"` would print the value of the `$user` container. but single quotes print the string as it is, so `'Hello, $user'` would print as `Hello, $user`. So no f-strings or escape-seq

    - talking of escape sequences, you do it here by backsticks and not backward hashes, `\`` this thing defines escape characters.

    - Out-Null, this thing avoids the ps outputs being displayed after a command, quite handy for clean code.

    - Push-Location (pushd) and Pop-Location: Very interesting stuff, worth mentionining- when you pushd, you mvoe to that location, and add the previous one in a default, unamed stack. When you popd, you go back to the previous locaiton (i.e. the location at the top of the stack). You can have named stack as well, btw.


That said, this was fun. Worth the evening.