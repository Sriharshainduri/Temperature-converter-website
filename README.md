# Temperature-converter-website.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

<div class="converter-container">
    <h2>Temperature Converter</h2>
    <div class="input-group">
        <label for="temperature">Enter Temperature:</label>
        <input type="text" id="temperature" placeholder="e.g., 32">
    </div>

    <div class="input-group">
        <label for="unit">Select Unit:</label>
        <select id="unit">
            <option value="celsius">Celsius</option>
            <option value="fahrenheit">Fahrenheit</option>
            <option value="kelvin">Kelvin</option>
        </select>
    </div>

    <button onclick="convertTemperature()">Convert</button>

    <div id="result" class="result"></div>
</div>

<script>
    function convertTemperature() {
        const tempInput = document.getElementById("temperature").value;
        const unit = document.getElementById("unit").value;
        const resultDisplay = document.getElementById("result");

        if (isNaN(tempInput) || tempInput === "") {
            resultDisplay.textContent = "Please enter a valid number.";
            return;
        }

        const temperature = parseFloat(tempInput);
        let convertedTemp;

        if (unit === "celsius") {
            convertedTemp = `${(temperature * 9/5) + 32} °F (Fahrenheit) | ${(temperature + 273.15)} K (Kelvin)`;
        } else if (unit === "fahrenheit") {
            convertedTemp = `${((temperature - 32) * 5/9)} °C (Celsius) | ${((temperature - 32) * 5/9 + 273.15)} K (Kelvin)`;
        } else if (unit === "kelvin") {
            convertedTemp = `${(temperature - 273.15)} °C (Celsius) | ${(temperature * 9/5 - 459.67)} °F (Fahrenheit)`;
        }

        resultDisplay.textContent = `Converted Temperature: ${convertedTemp}`;
    }
</script>

</body>
</html>


#Temperature converter website.css

body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background: linear-gradient(135deg, #cf50ad, #e75dc7);
    color: #333;
}

/* Main container styling */
.converter-container {
    background-color: #fff;
    padding: 25px;
    border-radius: 10px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    max-width: 350px;
    width: 100%;
    text-align: center;
    transition: transform 0.3s;
}

/* Hover effect for main container */
.converter-container:hover {
    transform: scale(1.05);
}

/* Heading styling */
.converter-container h2 {
    margin: 0 0 20px;
    font-size: 1.6em;
    color: #444;
}

/* Input group styling */
.input-group {
    margin-bottom: 15px;
}

.input-group label {
    display: block;
    font-size: 1em;
    color: #333;
    margin-bottom: 5px;
}

.input-group input, .input-group select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
    font-size: 1em;
    outline: none;
}

.input-group input:focus, .input-group select:focus {
    border-color: #5479ff;
}

/* Convert button styling */
button {
    background-color: #3a34ea;
    color: white;
    border: none;
    padding: 12px;
    width: 100%;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1em;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #3659b5;
}

/* Result display styling */
.result {
    font-size: 1.2em;
    margin-top: 20px;
    color: #5479ff;
}
