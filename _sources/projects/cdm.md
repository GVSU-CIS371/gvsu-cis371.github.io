# Custom Drink Maker

In this homework, you will leverage Vue.js to create a dynamic and interactive beverage component. The goal is to implement a versatile component that allows users to customize their beverage by selecting various options for creamers, syrups, and base beverages.

## Objectives

- **Conditional Rendering:** Utilize Vue's conditional rendering capabilities to dynamically display beverage components based on user selections.
- **Two-Way Data Binding:** Implement two-way data binding to ensure seamless updates between the user interface and the application state.
- **Vue 3 Components with Properties:** Create Vue 3 components that accept properties.
- **Slots:** Use Vue's slot system to create flexible and reusable component templates.

## Preparation

1. Accept your instructor's [GitHub classroom invitation](https://classroom.github.com/a/E9FFIy0L) to set up your project repository.

   1. **Select Your Name:** ![select-name](../assets/img/project1-selectname.jpg)
   2. **Team Setup:**
      1. If your team does not exist yet, create a new team.
      2. If it already exists, join your existing team. !
   3. **Initialize Your Project Repository:**
   4. **Clone the Repository:** You're now ready to clone the repository. In your `terminal`, use the following command with your SSH repository link to download the repository to your local machine:

      ```bash
      git clone [YOUR_SSH_REPO_LINK]
      ```

   5. **Install Required Packages:** Execute the following command to install the necessary packages for your project:

      ```bash
      cd [YOUR_REPO]
      npm install
      ```

2. Run a local development server (default port 5173):

   ```bash
   npm run dev
   ```

   Then you can access your project at `localhost:5173` in browser.

## Instructions

In this homework, you will develop a Beverage Vue Application. Your objective is to enhance the application with additional choices for creamer, syrup, and base beverages, while ensuring proper UI behavior based on the customer's selections.

1. Expand the selection options in the `App.vue` to include more varieties of creamer, syrup, and base beverages for customers to choose from:

   - Creamer: No Creamer, Milk, Cream, Half & Half
   - Syrup: No Syrup, Vanilla, Caramel, Hazelnut
   - Base Beverage: Coffee, Green Tea, Black Tea

     ```{image} ../assets/img/project3-beverage1.jpg
     :width: 300px
     :name: beverage1
     ```

2. Update the `Base.vue`, `Creamer.vue`, and `Syrup.vue` components to dynamically adjust their appearance based on the customer's selections.

   Dynamically changing styles refers to visually altering the appearance of the beverage in response to the selected ingredients (e.g., different colors or textures for each creamer, syrup, and base beverage).

3. In `Beverage.vue`, implement conditional rendering to ensure the beverage's visual presentation is logical based on customer selections:

   - If "No Creamer" and "No Syrup" are selected, only display the base beverage in the mug.
   - If "No Syrup" is selected and some creamer is chosen, display the creamer directly on top of the base beverage without any gap.

   ```{image} ../assets/img/project3-beverage2.jpg
   :width: 300px
   :name: beverage2
   ```

## Grading Rubrics

| Grading Item                                             | Points |
| -------------------------------------------------------- | -----: |
| **Task 1**                                               |     25 |
| **Task 2**                                               |     25 |
| **Task 3**                                               |     40 |
| **GitHub Clone, Commit, Push, & Deploy to GitHub Pages** |     10 |

## Deliverables

- Deploy your web application using the following commands in your `terminal`:

  ```bash
   npm run build
   npm run deploy
  ```

- Github Page Setup

  - Set up your GitHub repository for GitHub Pages deployment. Follow the steps shown in the image below: ![Layout](../assets/img/project1-githubpage.jpg).
  - Your web application will be accessible at the URL: gvsu-cis371.github.io/YOUR-REPO

- Submit the URL of your GitHub Page in Blackboard.
