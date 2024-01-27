# Deployment-and-Git-Guide     

## Git Command   
```
$ git init
$ git add .
$ git commit -m "initial-commit"
$ git branch -M main
$ git remote add origin http://github.com/{username}/{repo-name}.git
$ git push -u origin main
```

create new branch    
```
$ git checkout -b gh-pages
```

switch existing branch   
```
$ git checkout main
```

list of branch  
```
$ git branch
```   


## Deploying Vite Deploying Vite App to GitHub Pages ![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)      

### `Step 1:` **Initialize Git Repository**    
Run the following commands to initialize a git repository in your Vite app and push your existing code to a remote repository on GitHub.
```
$ git init
$ git add .
$ git commit -m "initial-commit"
$ git branch -M main
$ git remote add origin http://github.com/{username}/{repo-name}.git
$ git push -u origin main
```

### `Step 2:` **Update vite.config.js**    
Add the base URL in this file by setting the base as `“/{repo-name}/”`. For example, if your repository’s name is landing-page then set the base like this:    
```
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  base: "/landing-page/"
})
```

### `Step 3:` **Install gh-pages**    
Install **gh-pages** package as a dev dependency.     
```
npm install gh-pages --save-dev
```

### `Step 4:` **Update package.json**      
Update package.json with the following **predeploy** and **deploy** scripts.
```
"scripts": {
    "predeploy" : "npm run build",
    "deploy" : "gh-pages -d dist",
    ...
}
```
Add the complete website URL by setting **homepage** in package.json    
```
"homepage": "https://{username}.github.io/{repo-name}/"
```
Thus, your updated **package.json** will look like this:  
```
{
  "name": "product",
  "private": true,
  "version": "0.0.0",
  "homepage": "https://harrshhpattell.github.io/landing-page/",
  "type": "module",
  "scripts": {
    "predeploy" : "npm run build",
    "deploy" : "gh-pages -d dist",
    "dev": "vite",
    "build": "vite build",
    ...
}
```

### `Step 5:` **Run Deploy**    
If you’ve made it till here, you’re almost there. Run the final command:     
```
npm run deploy
```

One last `step` though!     
Navigate to your remote repository on GitHub -> Settings -> Pages (left sidebar). Select source as “Deploy from branch” and branch as “gh-pages”.

**And you’re done!**
