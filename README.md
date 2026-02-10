# Please follow the steps below:

 
1. clone the repo to your laptop git clone <url> 
2. After the clone, you will be inside the main branch
3. Create a new branch with your name using git checkout -b <yourname>
4. Create a file with your name. Mine will be AhmedAredah.txt and write
anything on it
5. pull changes from main branch in case if anyone made a change (git pull
origin main)
6. fix the conflict if any (git diff --name-only --diff-filter=U) and push the
changes (with conflict resolution)
6. Push changes to the branch
7. Create Pull Request (PR) to merge your changes to the main branch


## how a conflict look like:

<<<<<<< HEAD
your current branch code
=======
incoming code from origin/main
>>>>>>> origin/main
