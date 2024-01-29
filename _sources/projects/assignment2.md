# Assignment 2

Online Store - Building a Vue 3.x Web App

## Objectives

- Gain hands-on experience with Vue 3.x's fundamental features.
- Employ CSS Grid layout and CSS Flexbox for design and structuring.
- Understand the core principles of Vue.js 3 component design and structuring.
- Understand how to use GitHub and Vercel for source code management and app deployment.

## Preparation

- **IDE Setup:** Use [VS Code](https://code.visualstudio.com/) with the [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) extension. Ensure Vetur is disabled. Additionally, install the [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

- **GitHub Setup:** Create a [GitHub account](https://github.com) if you haven't already. Then, accept your instructor's GitHub classroom invitation to initialize a repo under your account. Ensure you can access your GitHub account using an SSH Key. If you haven't set this up, follow the steps below or check this [tutorial](https://youtu.be/a-zX_qc2S-M).

  1. Open a Git terminal. If you haven't yet configured an SSH key for GitHub on your machine, generate a new one with the following command:

     ```
     ssh-keygen
     ```

  2. Navigate to your GitHub account settings. Click on "SSH and GPG keys" and then "New SSH key". Paste the public key that was generated in the first step and click "Add SSH key".

  3. Set up your GitHub username and email on your local machine in a Git terminal. You can do this with the following commands:

     ```
     git config --global user.name "Your Name"
     git config --global user.email "your-email@example.com"

     ```

  4. Now you're ready to clone the repository. In your Git terminal, enter the following command to download the repository to your local machine:

  ```bash
  git clone [YOUR_REPO_LINK]
  ```

  You can get YOUR_REPO_LINK in the assignment repo under your GitHub account:

  ![Layout](github-link.jpg)

- **Development Environment:** Ensure you're working inside the cloned repo.

  1. **[NodeJS](https://nodejs.org):** Ensure it's installed on your computer. (I would recommend building a node development environment using docker, check our class slides for detail.) Verify the installation with:

  ```bash
  node -v    # v14 or newer
  npm -v     # v8 or newer
  ```

  2. **Deployment with Vercel:** You need a [Vercel account](https://vercel.com/) to deploy your web page (or use your GitHub account to login to Vercel). To do that, you must first install Vercel CLI (Command-Line Interface) by running the following command

  ```bash
  npm install --global vercel
  ```

  To verify that you can run vercel locally. Login to Vercel using your GitHub account:

  ```bash
  vercel login
  ```

  If you cannot use your GitHub account to login to Vercel, you can create an account in Vercel and then link your GitHub account within your Versel account.

  3. Install required packages for your assignment:

  ```bash
  npm install
  ```

  4. Run a local development server (default port 5173):

  ```bash
  npm run dev
  ```

  Then you can access your project at `localhost:5173` in browser.

## Instructions

Your project includes the following starter files/directories:

![Starter Files](starter_files.jpg)

The `style.css` is imported by `main.ts` and will globally style the app. Apply component-specific styles in `App.vue` and `components/StoreItem.vue`.

Initially, it's recommended to only change the `#app` style in `style.css` and then focus on the `<style>` blocks in the `.vue` files.

### Task Breakdown

**App.vue (Main Layout)**

- Use CSS Grid to design the store layout: Header, Nav, Main Content, and Footer.

**Header:** Showcase the store's name or logo.

**Nav:** Contains navigation links to different sections or categories.

**Main Content:** Display a grid of store items.

- Implement `src/components/StoreItem.vue` using props, reactive references, and data-binding.
- In `App.vue`, use `v-for` to list items with the `StoreItem` component.

**Footer:** Contains attributions, copyrights, or other relevant links.

**StoreItem.vue Component Details:**

Properties:

- `name: string;`
- `description: string;`
- `price: number;`
- `rating: number;`
- `stock: number;`
- `image: string;`
- `category: string;`

**Layout:** The layout should span the browser's width.

![Layout](assignment2_layout.jpg)

## Extra Credit Options

- (4 pts) Highlight an item when the mouse hovers over it.
- (4 pts) Represent the rating using star icons.
- (4 pts) Use relevant images for the products instead of placeholder images.
- (4 pts) Incorporate a logo in the header.

For other extra credit ideas, consult with your instructor.

## Grading Rubrics

| Grading Item                                   | Points |
| ---------------------------------------------- | -----: |
| GitHub setup with SSH Key & cloned repo        |     10 |
| NodeJS and Vercel setup;                       |     10 |
| `StoreItem.vue` implementation                 |     30 |
| `App.vue` implementation                       |     30 |
| Commit all changes & push to GitHub            |     10 |
| Deploy the production version to Vercel server |     10 |

## Deliverables

Deploy your web app (in the assignment repo) to Vercel, use:

```bash
 vercel deploy
```

To deploy your assignment to production, use:

```bash
 vercel --prod
```

Visit the Production URL(ending in vercel.app) to confirm that you are able to see your page.

Submit your Vercel Production URL in Blackboard.

**Note:** While functionality is crucial, a well-designed and visually appealing user interface also plays a significant role.

## Best Solutions

- [Caleb Roe](https://cis371-assignment2-5yng76oaf-caleb-roes-projects.vercel.app)
- [Sebastian Torrejon Alonzo](https://chevasmarket-76mwqmt3f-sebastian-torrejon-alonzos-projects.vercel.app)
