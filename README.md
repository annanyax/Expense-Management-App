# 💰 Shared Expense Management App

A modern and simple Vue.js application to manage shared expenses among a group of people. This app allows users to add, view, filter, and summarize expenses seamlessly.

## ✨ Features

- **Add Expenses**: Record expenses with a description, amount, and the person who paid.
- **View All Expenses**: See a comprehensive list of expenses with filtering and sorting options.
- **Filter and Sort**:
  - Filter expenses by person.
  - Sort expenses by amount in ascending or descending order.
- **Expense Summary**: View a summary of total expenses for each person.
- **Data Persistence**: Automatically saves expenses in local storage to retain data even after a page refresh.

## 🖼️ Screenshots

![App Overview] (./src/image/emapp.png)
_A preview of the Shared Expense Management App_

## **Technologies Used**
- **Vue 3**: For building the frontend.
- **HTML/CSS**: For structuring and styling.
- **JavaScript**: For interactive behavior.
- **LocalStorage**: For saving and retrieving contact data.

## 🛠️ Installation and Setup

Follow these steps to set up and run the project locally.

### Prerequisites

- **Node.js**: Make sure you have Node.js installed. [Download here](https://nodejs.org/).

## **How to Run This Project**

### **Step 1: Clone or Download the Repository**
#### Option 1: Clone the Repository
1. Open a terminal and run: 
git clone https://github.com/annanyax/expense-management-app.git
2. Navigate to the project folder:
cd contact-management-app

#### Option 2: Download as a ZIP File
1. Go to the GitHub repository in your browser.
2. Click on the green "Code" button and select "Download ZIP".
3. Extract the ZIP file and open the extracted folder.

### **Step 2: Install Dependencies**
1. Ensure you have Node.js and npm installed on your computer.
2. Open the project folder in your terminal and run:
npm install

### **Step 3: Start the Development Server**
1. Start the app locally by running:
npm run dev
2. Open the URL provided in the terminal (e.g., http://localhost:5173) in your browser to view the app.

### **File Descriptions**

1. **App.vue**:
   - The main file that manages the app's state and acts as the root component.
   - Integrates the ExpenseForm, ExpenseList, and ExpenseSummary components.

2. **ExpenseForm.vue**:
   - Contains the form to add a new expense with fields for description, amount, and the person who paid.
   - Emits events to the parent component (`App.vue`) to add expenses dynamically.

3. **ExpenseList.vue**:
   - Displays the list of all expenses.
   - Provides filtering options to filter expenses by person and sorting by amount (ascending/descending).
   - Allows deleting and editing expenses dynamically via emitted events.

4. **ExpenseSummary.vue**:
   - Displays a summary of total expenses grouped by each person.
   - Dynamically calculates totals using the list of expenses passed as props.

5. **style.css**:
   - Contains global styling for the app, including layout, colors, fonts, and hover effects.
   - Ensures consistent design for the ExpenseForm, ExpenseList, and ExpenseSummary components.

6. **main.js**:
   - Entry point for the application.
   - Configures Vue and mounts the `App.vue` component to the DOM.

7. **vite.config.js**:
   - Configuration file for Vite.
   - Optimizes the development and build process for the app.

8. **package.json**:
   - Defines project dependencies, scripts, and metadata.
   - Includes information for running and building the app.



