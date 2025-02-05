<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-image: url('https://source.unsplash.com/1600x900/?fitness,gym');
            background-size: cover;
            color: white;
        }
        .container {
            background: rgba(0, 0, 0, 0.7);
            padding: 20px;
            border-radius: 10px;
            width: 300px;
            margin: auto;
            margin-top: 50px;
        }
        input, select, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
        }
        #result {
            font-size: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <h1>BMI CAGE</h1>
    <div class="container">
        <h2>BMI Calculator</h2>

        <label>Height:</label>
        <input type="number" id="height" placeholder="Enter height">
        <select id="heightUnit">
            <option value="cm">cm</option>
            <option value="m">meters</option>
            <option value="feet">feet</option>
        </select>

        <label>Weight:</label>
        <input type="number" id="weight" placeholder="Enter weight">
        <select id="weightUnit">
            <option value="kg">kg</option>
            <option value="pounds">pounds</option>
        </select>

        <button onclick="calculateBMI()">Calculate BMI</button>

        <p id="result"></p>
        <p id="category"></p>
    </div>

    <script>
        function calculateBMI() {
            let height = parseFloat(document.getElementById('height').value);
            let weight = parseFloat(document.getElementById('weight').value);
            let heightUnit = document.getElementById('heightUnit').value;
            let weightUnit = document.getElementById('weightUnit').value;

            // Convert height to meters
            if (heightUnit === "cm") {
                height = height / 100;
            } else if (heightUnit === "feet") {
                height = height * 0.3048;
            }

            // Convert weight to kg
            if (weightUnit === "pounds") {
                weight = weight * 0.453592;
            }

            if (height > 0 && weight > 0) {
                let bmi = weight / (height * height);
                document.getElementById('result').innerText = `Your BMI: ${bmi.toFixed(2)}`;

                let category = "";
                if (bmi < 18.5) category = "Underweight";
                else if (bmi < 25) category = "Normal";
                else if (bmi < 30) category = "Overweight";
                else category = "Obese";

                document.getElementById('category').innerText = `Category: ${category}`;
            } else {
                alert("Please enter valid height and weight.");
            }
        }
    </script>

</body>
</html>
