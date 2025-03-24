# Custom Drink Maker 2

In this homework, you will build based on homework, Custom Drink Maker. The main goal is to complete the app by creating a feature that allows users to concoct their own beverage recipes and then store them using Pinia.

## Objectives

- **Pinia Integration:** Implement Pinia to manage and store the state of user-created beverage recipes.
- **User Interaction:** Enhance the application interface to allow for more interactive and user-friendly recipe creation and selection.

## Instructions

Accept your instructor’s GitHub classroom invitation to set up your project repository. Copy necessay code for to the src folder from you homework "Custom Drink Maker", enhance the application with additional choices and functionalities as described below:

1. **Pinia Store Integration:** Create a Pinia store to manage the state of the application, specifically to store the user's beverage selections (temperature, creamer, syrup, base beverage) as named recipes temporarily.
2. **Interface Enhancement:** In App.vue, add a text input field labeled "Name" and a button labeled "Make Beverage". Bind the button with a click event that uses the $patch method to add the user's selections as a named recipe in the Pinia store.
3. **Display Recipes:** Show all the recipes currently stored in the Pinia Store In App.vue. Implement a click function, showBeverage, to allow users to click on a recipe name, which will then visually display the corresponding beverage in the mug.

## Expected Outcomes

Focus on implementing the functionalities; the aesthetic design of the radio button list, text box, and button is secondary.

- [Expected Outcome Demo](https://gvsu-cis371.github.io/w24-project4/)

## Grading Rubrics

| Grading Item                                        | Points |
| --------------------------------------------------- | -----: |
| Task 1: Implementation of Pinia Store               |     30 |
| Task 2: User Interface and Interaction Enhancement  |     30 |
| Task 3: Display and Interaction with Stored Recipes |     30 |
| Commit all changes & push to GitHub                 |      5 |
| GitHub Page Deployment                              |      5 |

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
