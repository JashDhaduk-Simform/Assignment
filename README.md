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
    git cheackout -b abc_sub_Project
  </code>
</pre>
