# Push and pull without giving credentials
* Add the remote, call it "upstream":
```bash
git remote add upstream https://github.com/whoever/whatever.git
```
* SSH Keys
1. Generate keys
```bash
  ssh-keygen -t rsa -b 4096 -C your@email.com
```
2. Add your private key to ssh-agent 
```bash
ssh-add ~/.ssh/id_rsa
```

3. Add your public SSH key (~/.ssh/id_rsa.pub) to GitHub

# Reset commits
* Hard reset

`git reset --hard HEAD` resets your changes back to the last commit that your local repo has tracked.

`git reset --hard <your commit hash key>`

`git reset --hard origin/master`

`git clean -df` will discard any new files or directories that you may have added, in case you want to throw those away.

# Work flow between Github fork, local git repo and Github main repository
* Add the remote, call it "upstream":
```bash
git remote add upstream https://github.com/whoever/whatever.git
```
* Add the remote, call it "upstream":
```bash
git remote add upstream https://github.com/whoever/whatever.git
```
* Fetch all the branches of that remote into remote-tracking branches, such as upstream/master:
```bash
git fetch upstream
```
* Make sure that you're on your master branch:
```bash
git checkout master
```
* Rewrite your master branch so that any commits of yours that aren't already in upstream/master are replayed on top of that other branch:
```bash
git rebase upstream/master
```
If you don't want to rewrite the history of your master branch, (for example because other people may have cloned it) then you should replace the last command with git merge upstream/master. However, for making further pull requests that are as clean as possible, it's probably better to rebase.
If you've rebased your branch onto upstream/master you may need to force the push in order to push it to your own forked repository on GitHub. You'd do that with:
```bash
git push -f origin master
```
You only need to use the -f the first time after you've rebased.
