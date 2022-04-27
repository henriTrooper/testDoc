https://medium.com/rupesh-tiwari/how-to-deploy-angular-apps-to-github-pages-gh-pages-setup-ci-cd-for-angular-app-with-github-714c1e555de5
https://betterprogramming.pub/building-angular-apps-using-github-actions-bf916b56ed0c

1. Creating a GitHub Config
  - Go to the personal access tokens section in your GitHub settings.
  - Generate a new token ( TOKEN_GITHUB_ACTION_TROOPER )  which has scope for repository access and copy its value.

2. Create Angular Project
   - ng new SampleApp
   - npm i 
  Update : 
   - In the root folder of your angular project, create a new folder, .github, and create a subfolder workflows. 
   - Create one final file, named main.yml, in the workflow folder.
   - Copy conf and update TOKEN_GITHUB_ACTION_TROOPER if needed
   - Add in Angular.json in "test" part juste behind builder :
 "configurations": {
  "production": {
    "sourceMap": false,
    "codeCoverage": true,
    "browsers": "ChromeHeadless",
    "watch": false
  }
},
  
3. Link with git
create a new repository on the command line
echo "#" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<NameAccountGit>/<nameRepo>.git
git push -u origin main

…or push an existing repository from the command line
git remote add origin https://github.com/<NameAccountGit>/<nameRepo>.git
git branch -M main
git push -u origin main**
  
Go to the repository settings for your project at <repo url>/settings/secrets/actions. In the “Secrets” tab, add a new secret with the same token name from your workflow file (TOKEN_GITHUB_ACTION_TROOPER  in this project) and paste the token value.

4. Deployed
  Add in package.json
  "deploy": "ng deploy --base-href=/<repoName>"



