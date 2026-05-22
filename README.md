# Ex06 BMI Calculator
## Date: 

## AIM
To develop a responsive and interactive Body Mass Index (BMI) Calculator using React that allows users to input their height and weight, and calculates their BMI to categorize their health status (e.g., Underweight, Normal, Overweight, Obese).

## DESIGN STEPS

### STEP 1: Initialize React Project

<li>Create a new React app using create-react-app.</li>
<li>Install React Router using:</li>
npm install react-router-dom

### STEP 2: Set Up Routing

Create routing structure with react-router-dom:

<li>Home route (/) – Intro or Navigation</li>

<li>BMI Calculator route (/bmi)</li>

<li>Result route (/result)</li>

### STEP 3: Design the BMI Form Page

<li>Create a form to accept Height (in cm or m) and Weight (in kg).</li>

<li>On form submit, navigate to the result page with entered values via URL query params or context/state.</li>

## STEP 4: Handle Input Validation

<li>Check if height and weight are valid numbers.</li>

<li>Optionally, show error messages for invalid inputs.</li>

### STEP 5: Perform BMI Calculation

<li>In the result component:

<li>Extract height and weight from the route (URL or passed state).</li>

<li>Apply the BMI formula:</li>

![image](https://github.com/user-attachments/assets/ec785506-c96b-489e-8783-fb1a5d36101a)
​
 
<li>Convert height from cm to m if needed.</li></li>

### STEP 6: Display Result

<li>Show calculated BMI.</li>

<li>Show category based on BMI range:

<li>Underweight, Normal, Overweight, Obese, etc.</li></li>

### STEP 7: Navigation Options

<li>Provide a button to go back to the BMI form to calculate again.</li>

### STEP 8: Enhancements

<li>Add styling using CSS or Tailwind.</li>

## PROGRAM
## App.jsx:
```
import BMI from "./BMI";

function App() {
  return (
    <div>
      <BMI />
    </div>
  );
}

export default App;
```
BMI.jsx
```
import { useState } from "react";
import "./BMI.css";

function BMI() {

  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState("");
  const [status, setStatus] = useState("");

  const calculateBMI = () => {

    const heightInMeter = height / 100;

    const bmiValue =
      (weight / (heightInMeter * heightInMeter)).toFixed(2);

    setBmi(bmiValue);

    if (bmiValue < 18.5) {
      setStatus("Underweight");
    }

    else if (bmiValue >= 18.5 && bmiValue < 24.9) {
      setStatus("Normal");
    }

    else if (bmiValue >= 25 && bmiValue < 29.9) {
      setStatus("Overweight");
    }

    else {
      setStatus("Obese");
    }
  };

  return (
    <div className="container">

      <div className="bmi-box">

        <h2>BMI Calculator</h2>

        <input
          type="number"
          placeholder="Enter Height in cm"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />

        <input
          type="number"
          placeholder="Enter Weight in kg"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />

        <button onClick={calculateBMI}>
          Calculate BMI
        </button>

        <h3>Your BMI: {bmi}</h3>

        <h3>Status: {status}</h3>

      </div>

      <footer>
        SELVARANI.S | 24901160S2
      </footer>

    </div>
  );
}

export default BMI;
```
## BMI.css
```
body {
  margin: 0;
  padding: 0;
  background: #f2f2f2;
  font-family: Arial, sans-serif;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 60px;
}

.bmi-box {
  width: 350px;
  background: white;
  padding: 30px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0px 0px 10px gray;
}

input {
  width: 90%;
  padding: 12px;
  margin: 10px 0;
  font-size: 16px;
}

button {
  width: 100%;
  padding: 12px;
  background: green;
  color: white;
  border: none;
  font-size: 18px;
  border-radius: 5px;
}

footer {
  margin-top: 20px;
  font-weight: bold;
}
```


## OUTPUT

<img width="1911" height="950" alt="Screenshot 2026-05-22 192524" src="https://github.com/user-attachments/assets/8874cefa-d12b-4ccd-a278-b7becaf42938" />




## RESULT
The BMI Calculator successfully takes user input for height and weight, performs the BMI calculation in real-time using React state and event handling, and displays the BMI value along with the corresponding health category.
