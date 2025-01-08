<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <!-- Bootstrap CSS for styling -->
  <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
  <style>
    /* Basic layout styling */
    body {
      background-color: #f8f9fa;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      max-width: 400px;
      width: 100%;
    }

    .calculator {
      border: 2px solid #ccc;
      padding: 20px;
      border-radius: 10px;
      background-color: white;
    }

    .display {
      margin-bottom: 20px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      font-size: 1.5rem;
      height: 60px;
    }

    button:focus {
      outline: none;
    }

    button.btn-success {
      background-color: #28a745;
      color: white;
    }

    button.btn-secondary {
      background-color: #6c757d;
      color: white;
    }

    button:hover {
      opacity: 0.8;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="calculator">
      <div class="display">
        <input type="text" id="display" class="form-control" disabled>
      </div>
      <div class="buttons">
        <button class="btn btn-secondary" onclick="clearDisplay()">AC</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('%')">%</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('/')">/</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('*')">*</button>

        <button class="btn btn-secondary" onclick="appendToDisplay('7')">7</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('8')">8</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('9')">9</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('-')">-</button>

        <button class="btn btn-secondary" onclick="appendToDisplay('4')">4</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('5')">5</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('6')">6</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('+')">+</button>

        <button class="btn btn-secondary" onclick="appendToDisplay('1')">1</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('2')">2</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('3')">3</button>
        <button class="btn btn-secondary" onclick="calculateSquare()">x²</button>

        <button class="btn btn-secondary" onclick="appendToDisplay('0')">0</button>
        <button class="btn btn-secondary" onclick="appendToDisplay('.')">.</button>
        <button class="btn btn-success" onclick="calculateResult()">=</button>
      </div>
    </div>
  </div>

  <script>
    // Function to append values to the display
    function appendToDisplay(value) {
      document.getElementById("display").value += value;
    }

    // Function to clear the display
    function clearDisplay() {
      document.getElementById("display").value = '';
    }

    // Function to calculate the result of the expression
    function calculateResult() {
      let expression = document.getElementById("display").value;
      
      // Handle the case of an empty or invalid input
      if (expression === '') {
        alert('Please enter a valid expression');
        return;
      }

      try {
        // Using JavaScript's eval to compute the result of the expression
        let result = eval(expression);
        
        // Display the result
        document.getElementById("display").value = result;
      } catch (error) {
        alert('Invalid expression');
        clearDisplay();
      }
    }

    // Function to calculate the square of a number
    function calculateSquare() {
      let value = document.getElementById("display").value;
      
      // Handle empty input
      if (value === '') {
        alert('Please enter a number');
        return;
      }

      // Calculate the square and display the result
      let square = Math.pow(parseFloat(value), 2);
      document.getElementById("display").value = square;
    }
  </script>
</body>
</html>
