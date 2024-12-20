# HOW TO DEPLOY A REACT APP IN GITHUB PAGES

**Author**: `PedroTech`  
**Type**: `TUTORIAL`  
**Topics**: #REACT #GitHub #Vite #GitHubPages #Programacion  
**Link**: [Link del video](https://www.youtube.com/watch?v=hn1IkJk24ow)

---

## **First Create a Vite React App**

This is the full guide to install Vite: [Source here](https://vite.dev/guide/)

### 1. Create a React App using Vite:

To create a new React app using Vite, run the following command:

```SHELL
npm create vite@latest my-react-app --template react
```

Here:

- **my-react-app** is the name of your project. You can replace it with the name of your choice.
- **--template react** tells Vite to use the React template.

### 2. Create a remote repository on GitHub:

Go to [GitHub](https://github.com/) and create a new repository for your project.

### 3. Edit `vite.config.js` to specify the base path:

Open the `vite.config.js` file and add the `base` property with the repository name you created:

```JavaScript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'

// https://vite.dev/config/

export default defineConfig({
  plugins: [react()],
  base: "/name-of-your-repository", // Replace with your repository name
})
```
### 4. Add the homepage property in `package.json`:

Open the `package.json` file and add the `homepage` property. It should look like this:

```JavaScript
"homepage": "https://<your-username>.github.io/<repository-name>/"
```
### 5. Install the GitHub Pages dependency:

Run the following command to install the `gh-pages` package, which helps deploy your app to GitHub Pages:

```BASH
npm install gh-pages
```
### 6. Modify `package.json` to include deploy scripts:

In the `package.json` file, add the following two properties in the `scripts` section:

- `predeploy`: This script will run before deployment and builds your app.
- `deploy`: This script deploys the app to GitHub Pages.

```JavaScript
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist",
  "dev": "vite",
  "build": "vite build",
  "lint": "eslint .",
  "preview": "vite preview"
}
```

### 7. Initialize a local Git repository:

Navigate to your project directory and initialize a local Git repository:

```BASH
git init
```
### 8. Add and commit your changes:

Add all your files to the Git staging area and commit your changes:

``` BASH
git add ./ 
git commit -m "first commit"
```
### 9. Set the remote GitHub repository:

Link your local repository to the remote repository you created on GitHub:

``` BASH
git remote add origin <url-github-repository>
```

### 10. Push the changes to GitHub:

Push your changes to the `main` branch of your remote GitHub repository:

``` BASH
git push -u origin main
```
### 11. Deploy the app to GitHub Pages:

Now, you can deploy your app to GitHub Pages with the following command:

``` BASH
npm run deploy
```

This will build your app and deploy it to the `gh-pages` branch, which GitHub Pages will use to serve your app.

---

**Note**: Make sure to replace `<your-username>` and `<repository-name>` with your actual GitHub username and the name of your repository.