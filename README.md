# Webshop Simulator

Webshop Simulator is a simple Vue.js application that simulates the experience of an online store. Users can enter their initial cash amount, add products to their cart, make purchases, and track their current shopping session.

## Getting Started

1. Install [Node.js](https://nodejs.org/) if it's not already installed on your computer.

2. Clone this repository to your computer using the following command:

   ```bash
   git clone https://github.com/YourUsername/webshop-simulator.git
   
3. Inside the project's root directory, install all the necessary packages by running:

   npm install

4. Start the local development server with the following command:

  npm run serve

5. Open your web browser and access the application at http://localhost:8080

## Using the Application

First, enter your initial cash amount in the "Enter cash amount" field and click "Confirm entry."

You can then enter products into the webshop using the fields to input the product name, price per piece, and quantity. Pressing "Add product" will add the product to the offerings.

Products available for purchase will be displayed below, along with the quantity available. Enter the desired quantity and click "Buy" to add them to your cart.

Your current shopping session will be displayed on the left, with the total price of your current purchase displayed at the bottom.

By clicking the "Buy" button, your available cash will be reduced by the total purchase price, and the current purchase amount will be updated.

Repeat steps 3-5 to add and purchase more products.

You can continue adding products and making purchases until you have spent all your money.

Additional Information
This application is created as a demonstration of using Vue.js in a real-world project and as an exercise in state manipulation and communication between components.

The application is not connected to a real store and does not perform real financial transactions.

Feel free to explore the source code to better understand how the application is built and customize it to your needs.   
