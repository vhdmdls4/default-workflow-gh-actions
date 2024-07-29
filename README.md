# default-workflow-gh-actions

A boilerplate of a workflow at GitHub Actions to deploy a Vite website using Yarn as the dependency manager.

If you are struggling with deployment on GitHub Pages with Vite and Yarn, this guide might help you!

*Remember:* this workflow is activated by every change pushs to main branch, so, be careful!
When using pnpm or similar you need to install it first before the setup, [see more here about caching issues and stuff](https://github.com/actions/setup-node/issues/530)

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
*Note:* if you're using the default GitHub Pages URL, it will be `https://accountHere.github.io/repoHere/`.

Also add `"homepage": "https://accountHere.github.io/repoHere"` to your `package.json`. Additionally, inside the `scripts` property of the same file, add:
```json
"predeploy": "npm run build", // or yarn similar
"deploy": "gh-pages -d build"
```

And in the settings of the repo, config Pages section changing the source of Build and Deployment to GitHub Actions.
![image](https://github.com/user-attachments/assets/10cf2619-1478-459c-9b8d-f7f762d13552)

---
