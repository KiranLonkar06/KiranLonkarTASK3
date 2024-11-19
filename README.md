<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Temperature Converter</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f1f1f1;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background-color: #ffffff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      width: 90%;
      max-width: 400px;
      text-align: center;
    }
    h1 {
      color: #4b6cb7;
      margin-bottom: 20px;
      font-size: 1.5rem;
    }
    input, select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 1rem;
      background-color: #f9f9f9;
    }
    input:focus, select:focus {
      border-color: #4b6cb7;
      outline: none;
    }
    button {
      width: 100%;
      padding: 12px;
      background-color: #4b6cb7;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #3a5a8d;
    }
    #result {
      margin-top: 20px;
      padding: 10px;
      font-size: 1.2rem;
      color: #333;
      background-color: #f9f9f9;
      border-radius: 8px;
      border: 1px solid #ddd;
    }
    #result.error {
      color: red;
      background-color: #f8d7da;
      border-color: #f5c6cb;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Temperature Converter</h1>
    <label for="tempInput">Enter Temperature:</label>
    <input type="text" id="tempInput" placeholder="Enter temperature" />
    <label for="unit">Select Unit:</label>
    <select id="unit">
      <option value="Celsius">Celsius</option>
      <option value="Fahrenheit">Fahrenheit</option>
      <option value="Kelvin">Kelvin</option>
    </select>
    <button id="convertBtn">Convert</button>
    <div id="result"></div>
  </div>
  <script>
    document.getElementById("convertBtn").addEventListener("click", function () {
      const tempValue = parseFloat(document.getElementById("tempInput").value);
      const unit = document.getElementById("unit").value;
      const resultElement = document.getElementById("result");
      let result;

      // Validate input
      if (isNaN(tempValue)) {
        resultElement.textContent = "Please enter a valid number for the temperature!";
        resultElement.classList.add("error");
        return;
      }

      if (unit === "Celsius") {
        result = {
          Fahrenheit: (tempValue * 9) / 5 + 32,
          Kelvin: tempValue + 273.15,
        };
        resultElement.textContent = `${tempValue} °C is equal to ${result.Fahrenheit.toFixed(2)} °F and ${result.Kelvin.toFixed(2)} K.`;
      } else if (unit === "Fahrenheit") {
        result = {
          Celsius: ((tempValue - 32) * 5) / 9,
          Kelvin: ((tempValue - 32) * 5) / 9 + 273.15,
        };
        resultElement.textContent = `${tempValue} °F is equal to ${result.Celsius.toFixed(2)} °C and ${result.Kelvin.toFixed(2)} K.`;
      } else if (unit === "Kelvin") {
        result = {
          Celsius: tempValue - 273.15,
          Fahrenheit: (tempValue - 273.15) * 9 / 5 + 32,
        };
        resultElement.textContent = `${tempValue} K is equal to ${result.Celsius.toFixed(2)} °C and ${result.Fahrenheit.toFixed(2)} °F.`;
      }

      resultElement.classList.remove("error");
    });
  </script>
</body>
</html>
