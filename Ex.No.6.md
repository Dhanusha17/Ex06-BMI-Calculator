# Ex06 BMI Calculator
## Date:

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
### App.jsx
```
import { useState } from 'react';
import './App.css';

function App() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');

  const calculateBMI = (e) => {
    e.preventDefault();

    if (!weight || !height) {
      alert('Please enter both weight and height');
      return;
    }

    const heightInMeters = height / 100;
    const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
    setBmi(bmiValue);

    let msg = '';
    if (bmiValue < 18.5) msg = 'Underweight';
    else if (bmiValue >= 18.5 && bmiValue < 24.9) msg = 'Normal weight';
    else if (bmiValue >= 25 && bmiValue < 29.9) msg = 'Overweight';
    else msg = 'Obese';

    setMessage(msg);
  };

  return (
    <div className="container">
      <h1>BMI Calculator</h1>
      <form onSubmit={calculateBMI}>
        <div>
          <label>Weight (kg):</label>
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
          />
        </div>
        <div>
          <label>Height (cm):</label>
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
          />
        </div>
        <button type="submit">Calculate</button>
      </form>

      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <p>Status: {message}</p>
        </div>
      )}
    </div>
  );
}

export default App;

```
### App.css
```
.container {
  max-width: 400px;
  margin: 2rem auto;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-family: sans-serif;
  text-align: center;
}

form > div {
  margin-bottom: 1rem;
}

input {
  padding: 0.5rem;
  width: 100%;
  margin-top: 0.3rem;
}

button {
  padding: 0.5rem 1rem;
  background-color: #007bff;
  border: none;
  color: white;
  border-radius: 4px;
  cursor: pointer;
}

.result {
  margin-top: 1rem;
}

```
## OUTPUT
![alt text](<my/src/img/Screenshot 2025-05-17 at 8.57.42 AM.png>)
![alt text](<my/src/img/Screenshot 2025-05-17 at 8.58.01 AM.png>)
## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
