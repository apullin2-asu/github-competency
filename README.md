# github-notes
Notes on how to work in Github.

From Git for Professionals Tutorial:
Link: https://www.youtube.com/watch?v=Uszj_k0DGsg
Side Note: Look up Tower for Git, a GUI for working with GitHub.

  Topic 1: Perfect Commit
    - Don't cram everything into one commit.
    - A good commit separates different topics.
    - The Git staging area lets you select individual files or parts of files for one commit.
    - You can use "git status" in terminal to see changes not staged for commit.
    - To include specific file, use "git add [filename]"
    - Use "git diff [filename]" to see the changes that are being made in that file.
    - Use -p with git add to go down to the patch level. Now git will step through each chunk of changes.
    - Crucial to have a commit history that is easy to read and understand.
    - The perfect commit message contains:
      * Subject = concise summary of what happened
        o If you have trouble writing something concise, you might have too many topics.
      * Body = more detail explanation
        o What is different from before?
        o What's the reason for the change?
        o Is there anything to watch out for?
        o Is there anything particularly remarkable?
    - Typing "git commit" will bring up the editor window to make the commit message.
    - Subject goes on top line. An empty line after this will let the editor know we are now writing body of message.
    - Typing "git log" shows a log of previous commits.
    
  Topic 2: Branching Strategies
    - Git leaves it completely up to you for how you work with branches.
    - Make sure to agree on a branching workflow with your team.
    - Make up a written list of best practices for how work should be done.
    - Highly dependent on team/team size/team strategies.
    - Having these helps onboard new team members.
    - Two examples of how to design branching: Mainline Development and State/Release/Feature Branches
    - Mainline Development:
      * "Always Be Integrating"
      * few branches
      * small commits
      * high quality testing and QA
      * code integrated quickly into mainline code, that's why need high quality testing/QA
    - State/Release/Feature Branches:
      * a bunch of different branches
      * each branch has its own job
      * feature branches, development branches, main branch, etc.
      * seems complicated, but just needs practice
    - Most teams are between these two extremes.
    - Two main types of branches are Long-Running and Short-Lived branches.
    - Long-Running Branch:
      * exists throughout the complete lifetime of the project
      * often mirror stages in dev cycle
      * usually includes main, but also might include development branch or production branch or integration branch
      * common convention: no direct commits!
      * commits should only make it to the main branch through integration, through merge for example
      * reasons for this rule: quality (don't add untested/unreviewed code) and release bundling/scheduling (release new code in batches, not just random updates to main)
    - Short-Lived Branch:
      * for new features, bug fixes, refactoring, experiments, etc.
      * will be deleted after integration (safely)
    - Two popular branching strategies are GitHub Flow and GitFlow (this is very confusing)
    - GitHub Flow:
      * very simple, very lean
      * only one long-running branch ("main") and then multiple short-lived branches (feature/bugfix/etc)
    - GitFlow:
      * more structure, but also more rules
      * long running branches: "main" and "develop"
      * main branch is reflection of current production state
      * develop branch is where many of the short-lived branches start from
      * short-lived branches include features, releases, and hotfixes.
      * short-lived branches get merged back into develop branch.
      * once you are confident develop branch is ready for production, you merge it back into main, add a tag for that release commit on main, then close that release branch.
    - No perfect branching model, adjust it to your project and your team

  Topic 3: Pull Requests
    - Pull requests are not a core feature, they are provided by your host, so they will look different on different platforms (GitHub vs Bitbucket)
    - Without pull requests, you would need to merge directly.
    - Pull request allows other people to review and provide feedback on the code before it merges.
    - Pull requests also allows you to contribute code to repositories you do not have access to. (Like in open-source)
    - A fork is your personal copy of a git repository.
    - You can fork original repository, make changes, then make pull request to include those changes. Then main contributors can review if they want to include them.
    - Use "git clone [link to repository fork]" to create a clone in your directory.
    - Use "git branch [name]" to create a branch of the code. Then use "git checkout [same name]" to switch to that branch.
    - You can tell GitHub which branch you want to merge into in the pull request.

  Topic 4: Merge Conflicts
    - Merge conflicts occur when integrating commits from different sources
      * These can include git merge, git rebase, git pull, git cherry-pick, and git stash apply.
      * All of these perform some kind of integration, which is when merge conflicts happen.
      * Not every time of course.
    - Most of the time, Git will figure this shit out on its own.
    - But when contradictory changes are made, it can't figure out what to do. (Maybe exact same line of code was changed in two branches, file modified in one branch but deleted in another, etc.)
    - Problem is always the same, the changes contradict.
    - You will know a conflict has occurred because Git will tell you. Message will come up that says "CONFLICT".
    - Don't necessarily have to resolve a conflict; you can start over fresh.
      * Use git merge --abort or git rebase --abort
    - Git marks the problematic area in the file with "<<<<<<<<<<<<<" and ">>>>>>>>>>>>"
      * Content after first marker is from current working branch.
      * There will be "==========="
      * Then content between that and end marker is from the other branch.
    - To solve a conflict, you need to clean up the file.
    - Talk to the person who did the other commit and figure out which one you want to go with.
    - There are dedicated merge tools.
    - After cleaning, commit like any other change.
    - Can configure it to have a safety copy just in case.

  Topic 5: Merge vs. Rebase
  - Having separate containers for your work is very helpful.
  - Goal of integration is to combine the current state of two branches.
  - When Git performs a merge, it looks for three commits:
    1.) Common Ancestor
    2.) Last commit on Branch A
    3.) Last commit on Branch B
  - A Fast-Forward merge is the simplest merge in Git. Both branches share the exact same history.  (Simple, unrealistic)
  - A Merge Commit is created automatically by Git and does not wrap a set of related changes. It connects two branches like a knot.
  - Rebase is not better or worse than merge, it's just different.
  - Rebase is a straight line of commits.
  - To start rebase, do "git rebase [branch to integrate]".
  - Steps of Rebase:
    1.) Git will remove all commits on Branch A that happened after the common ancestor commit, but they are not thrown away (saved somewhere else temporarily).
    2.) Git applies new commits from Branch B.  Temporarily, both branches look exactly the same.
    3.) The commits from Branch A that were saved temporarily are positioned on top of the commits from Branch B. They are "rebased".
  - Result is it looks like commmits happened in a straight line.
  - Rebase rewrites commit history. Before rebase, Branch A's commit's parent was the common ancestor commit. After rebase, its parent is the last commit from Branch B.
  - Creates a new commit with a new commit hash.
  - Not a problem for commits that haven't been published or pushed yet. But if you do this with already pushed commits, might have trouble.
  - Another developer might have based work on a commit that is now no longer there.
  - Do NOT use Rebase on commits that you've already pushed/shared on a remote repository!
  - Instead, use it for cleaning up your local commit history before merging it into a shared team branch.
    
  
