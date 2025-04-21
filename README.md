# feb-2025-avasjcript-events-and-basic-interactivity
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Harrison's Footwear Upstore</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #333;
      color: white;
      padding: 10px 0;
      text-align: center;
    }
    .container {
      width: 80%;
      margin: 20px auto;
    }
    .form-container {
      background-color: white;
      padding: 20px;
      box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
    }
    .form-container input,
    .form-container button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      font-size: 16px;
    }
    .form-container button {
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
    }
    .form-container button:hover {
      background-color: #45a049;
    }
    .error {
      color: red;
      font-size: 14px;
    }
    .success {
      color: green;
    }
  </style>
</head>
<body>

  <header>
    <h1>Welcome to Harrison's Footwear Upstore</h1>
  </header>

  <div class="container">
    <!-- Form for customer order -->
    <div class="form-container">
      <h2>Place Your Order</h2>
      <form id="orderForm">
        <label for="name">Name</label>
        <input type="text" id="name" placeholder="Enter your name" required>
        <span id="nameError" class="error"></span>

        <label for="email">Email</label>
        <input type="email" id="email" placeholder="Enter your email" required>
        <span id="emailError" class="error"></span>

        <label for="shoe">Select Shoe Size</label>
        <select id="shoe" required>
          <option value="">--Choose Size--</option>
          <option value="7">7</option>
          <option value="8">8</option>
          <option value="9">9</option>
          <option value="10">10</option>
        </select>
        <span id="shoeError" class="error"></span>

        <button type="submit">Submit Order</button>
        <p id="formMessage"></p>
      </form>
    </div>

    <!-- Interactive Button -->
    <div class="form-container">
      <h2>Discount Offer</h2>
      <button id="discountButton">Get 10% Discount</button>
      <p id="discountMessage"></p>
    </div>
  </div>

  <script>
    // Event listener to handle form submission and validation
    document.getElementById("orderForm").addEventListener("submit", function(event) {
      event.preventDefault(); // Prevent the form from submitting immediately

      // Get input values
      const name = document.getElementById("name").value.trim();
      const email = document.getElementById("email").value.trim();
      const shoeSize = document.getElementById("shoe").value;
      
      // Clear previous errors
      document.getElementById("nameError").textContent = '';
      document.getElementById("emailError").textContent = '';
      document.getElementById("shoeError").textContent = '';

      let isValid = true;

      // Name validation
      if (name === "") {
        document.getElementById("nameError").textContent = "Name cannot be empty.";
        isValid = false;
      }

      // Email validation
      if (email === "") {
        document.getElementById("emailError").textContent = "Email cannot be empty.";
        isValid = false;
      } else if (!/\S+@\S+\.\S+/.test(email)) {
        document.getElementById("emailError").textContent = "Please enter a valid email.";
        isValid = false;
      }

      // Shoe size validation
      if (shoeSize === "") {
        document.getElementById("shoeError").textContent = "Please select a shoe size.";
        isValid = false;
      }

      // Show success message if form is valid
      if (isValid) {
        document.getElementById("formMessage").textContent = "Order successfully placed!";
        document.getElementById("formMessage").classList.add("success");
      }
    });

    // Interactive button event listener
    document.getElementById("discountButton").addEventListener("click", function() {
      document.getElementById("discountMessage").textContent = "Congratulations! You've received a 10% discount on your next order!";
      document.getElementById("discountMessage").classList.add("success");
    });
  </script>

</body>
</html>
