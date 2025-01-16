# Assignment
<h1>Git Exercise :</h1>

<h3>1) Create a new repository with a template :</h3>
<ul>
  <li>login to GitHub account.</li>
  <li>Click on New to create repository. Select whatever is needed from repo details they asked.</li>
  <li>After creating repo marked it as "Template Repository" from Settings to enable template functionalities.</li>
  <li>Using template repository will enables user to use the same structure of repo in their new repo.</li>
</ul>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/develop/01-Git/Images/Screenshot%20from%202025-01-16%2011-10-21.png" alt="Screenshot" width="500"/>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/develop/01-Git/Images/Screenshot%20from%202025-01-16%2011-11-04.png" alt="Screenshot" width="500"/>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/develop/01-Git/Images/Screenshot%20from%202025-01-16%2011-11-21.png" alt="Screenshot" width="500"/>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/develop/01-Git/Images/Screenshot%20from%202025-01-16%2011-11-35.png" alt="Screenshot" width="500"/>


<h3>2) Initialize git-flow :</h3>
<pre>
  <code>
    git flow init
  </code>
</pre>
<ul>
  <li>Run the above command to initialize the git flow model.</li>
  <li>After initializing git flow model 2 base branches is created as : develop and main</li>
</ul>


<h3>3) Create a feature branch for project setup with the proper Zoho task ID (example: TP2-T1299_Project_Setup) :</h3>
<pre>
  <code>
    git checkout -b abc_Project_Setup
  </code>
</pre>
<ui>
  <li>Above command will create the new branch for adding feature in the project.</li>
  <li>Now all created new branch are pushed to github using below code for each branch</li>
</ui>
<pre>
  <code>
    git checkout develop
    git push origin develop
  </code>
</pre>
<li>For newly created feature branch we have to push it to Github</li>
<pre>
  <code>
    git checkout abc_Project_Setup
    git push origin abc_Project_Setup
  </code>
</pre>

 
<h3>4) Create a sub-branch from the project setup branch and perform squash, reset, rebase and cherrypick ​​​​​.</h3>
<li>Let's first create the sub branch of feature branch using below code.</li>
<pre>
  <code>
    git checkout abc_Project_Setup
    git checkout -b abc_sub_Project
  </code>
</pre>
<ol>
  <li>Squash
  <p>Apply multiple commit to the sub-feature branch to perform squashing.</p>
  <pre>
  <code>
    git rebase -i HEAD~n
  </code>
</pre>
    <p>Repalce n with the number of commit you want to commit.</p>
  </li>
  <li>Reset
  <p>Set a commit to the sub-feature branch to perform reset.</p>
  <pre>
  <code>
    git reset HEAD~n
  </code>
</pre>
    <p>Repalce n with the number of commit you want to commit.</p>
    <p>This reset commit will not discard the commit. instead it step backward to staged commit</p>
    <pre>
  <code>
    git reset --hard HEAD~n
  </code>
</pre>
    <p>This reset command will completely discard the commit we have done as per value of n.</p>
  </li>
  <li>Rebase
  <p>Let's rebase the commit of sub-feature branch to main feature branch.</p>
  <pre>
  <code>
   git checkout abc_sub_Project
   git rebase abc_Project_Setup
  </code>
</pre>
    <p>This command will apply all the commits to main abc_Project_Setup branch</p>
  </li>
  </li>
  <li>Cherry-pick
  <p>If we have apply any specific commit to another branch then this is used.</p>
  <pre>
  <code>
   git log abc_Project_Setup --oneline
  </code>
</pre>
     <pre>
  <code>
   git cherry-pick <commit-hash>
     </code>
  </pre>
     </code>
    <p>Any specific commit's hash provided is now apply to main feature branch.</p>
  </li>
</ol>

<h1>Git Practice Senario :</h1>

<h3>1) Create a branch from the develop :</h3>
<li>To create new branch from develop branch execute below code</li>
<pre>
  <code>
    git checkout develop
    git checkout -b new-feature-branch
  </code>
</pre>

<h3>2) Add a commit message hook to the repo :</h3>
<li>Navigate to the git hooks directory</li>
<pre>
  <code>
    cd .git/hooks/
  </code>
</pre>
<li>create a new commit-hook using below code</li>
<pre>
  <code>
    touch commit-msg
  </code>
</pre>
<li>Now, click on created hook and apply the logic you want apply for commit the message as below</li>
<pre>
  <code>
    commit_msg=$(cat $1)
    regex="^JIRA-[0-9]+: .+"

    if [[ ! $commit_msg =~ $regex ]]; then
      echo "Error: Commit message must follow the format 'JIRA-1234: Description'"
      exit 1
    fi
  </code>
</pre>
<li>Now apply the hook so that if some one commit the changes they need to follow uper hook format</li>
<li>This hooks says that : follow the format 'JIRA-1234: Description'</li>
<pre>
  <code>
    chmod +x commit-msg
  </code>
</pre>

<h3>3) Perform multiple commits in the new branch :</h3>
<li>Add a file with some feature so that we can commit it using hook format</li>
<pre>
  <code>
    git commit -m "JIRA-1234: Implemented feature A"
  </code>
</pre>
<li>Do further commit on it</li>
<pre>
  <code>
    git commit -m "JIRA-1235: Fixed bug in feature A"
  </code>
</pre>

<h3>4) Create PR to develop :</h3>
<h3>5) PR should be small in size, It's recommended to do one commit per PR. However, based on the situation we can have multiple commits in PR. e.g. if someone is doing 10 bug fixes which are one-liner fixes in such cases instead of 10 different PRs you can do 10 commits in a single PR :</h3>
<li>So, goto the github and that branch to whom we need to pull request and click on compare and pull and write the appropriate description relate the pull request(PR)</li>
<li>So, while creating PR we can combine multiple small fixes or commits into single commit PR and all fixes in details in the PR description.</li>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/new-feature/01-Git/Images/Screenshot%20from%202025-01-16%2015-08-38.png" alt="Screenshot" width="500"/>

<h3>6) Create another branch from develop given your previous PR is still in review state :</h3>
<li>So we can create another branch from develop branch as new-feature</li>
<pre>
  <code>
    git checkout develop
    git checkout -b new-feature
  </code>
</pre>
<li>Here we note that still our previous PR is in review state and it is not merged yet. </li>

<h3>7) Now commit something in your current branch and push it :</h3>
<li>Now add file to the current branch with new feature.</li>
<pre>
  <code>
    git add .
  </code>
</pre>
  <li>Now, commit the staged changes loaded with new feature</li>
<pre>
  <code>
    git commit -m "Add_PR"
  </code>
</pre>
<li>After commiting it push it to the Github and launched the branch on it.</li>
<pre>
  <code>
    git push origin new-feature
  </code>
</pre>

<h3>8) In the meantime, your previous PR has been merged to develop :</h3>
<li>So, now your previous PR is reviwed and merged by someone after giving final touch.</li>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/new-feature/01-Git/Images/Screenshot%20from%202025-01-16%2015-14-56.png" alt="Screenshot" width="500"/>

<h3>9) Create a PR for the current branch given your branch should be up to date with develop branch :</h3>
<li>So to make the current branch up-to-date with develop branch follow below code</li>
<pre>
  <code>
    git fetch origin
    git rebase origin/develop
  </code>
</pre>
<li>Now create th PR as we have created before as develop as base branch and new-feature as compare branch</li>
<img src="https://github.com/JashDhaduk-Simform/Assignment/blob/new-feature/01-Git/Images/Screenshot%20from%202025-01-16%2018-38-14.png" alt="Screenshot" width="500"/>

<h3>10)For any new build release add a version tag to that specific commit to keep track of each version :</h3>
<li>So to add version tag follow the commands</li>
<pre>
  <code>
    git tag -a v1.0.0 -m "Release version 1.0.0"
  </code>
</pre>
<li>Now push it to the Github</li>
<pre>
  <code>
   git push origin v1.0.0
  </code>
</pre>

<h3>11)Create 2 another branch (3rd and 4th) from develop, push read me changes to 3rd brach :</h3>
<li>Craeting the 3rd branch from develop</li>
<pre>
  <code>
    git checkout develop
    git checkout -b feature/readme-changes
  </code>
</pre>
<li>Add the read me changes and push it</li>
<pre>
  <code>
   git add README.md
   git commit -m "Update README"
   git push origin feature/readme-changes
  </code>
</pre>
