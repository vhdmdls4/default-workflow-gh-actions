# default-workflow-gh-actions

A boilerplate of a workflow at GitHub Actions to deploy a Vite website using Yarn as the dependency manager.

If you are struggling with deployment on GitHub Pages with Vite and Yarn, this guide might help you!

Let's assume that you have already finished your project and want to "host" it on GitHub Pages. First, you should install `gh-pages` as a dev dependency:
  ```bash
  yarn add gh-pages
  ```

Then, add your base URL to your `vite.config.js` file:
```javascript
export default defineConfig({
  base: "/nameOfYourRepo/",
  ...restOfYourConfigHere,
});
```
*Note:* If you're using the default GitHub Pages URL, it will be `https://accountHere.github.io/repoHere/`.

As a fallback for any errors, also add `"homepage": "https://accountHere.github.io/repoHere"` to your `package.json`. Additionally, inside the `scripts` property of the same file, add:
```json
"predeploy": "npm run build", // or yarn similar
"deploy": "gh-pages -d build"
```

---
