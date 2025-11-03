# Ex06 BMI Calculator
## Date:19.05.25

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
## app.jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import BMICalculator from './BMIcalculator';

function App() {
  return (
    <Router>
      <div className="App">
        <nav>
          <Link to="/">Home</Link> | <Link to="/calculator">BMI Calculator</Link>
        </nav>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/calculator" element={<BMICalculator />} />
        </Routes>
      </div>
    </Router>
  );
}

## BMIcalculator
import React, { useState } from 'react';

function BMICalculator() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (weight > 0 && height > 0) {
      const heightInMeters = height / 100;
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(bmiValue);

      let resultCategory = '';
      if (bmiValue < 18.5) resultCategory = 'Underweight';
      else if (bmiValue < 24.9) resultCategory = 'Normal weight';
      else if (bmiValue < 29.9) resultCategory = 'Overweight';
      else resultCategory = 'Obesity';

      setCategory(resultCategory);
    } else {
      alert('Please enter valid weight and height.');
    }
  };

  return (
     <div>
      <h2>BMI Calculator</h2>
      <input
        type="number"
        placeholder="Weight in kg"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
      />
      <br />
      <input
        type="number"
        placeholder="Height in cm"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
      />
      <br />
      <button onClick={calculateBMI}>Calculate BMI</button>
      {bmi && (
        <div>
          <p>Your BMI: {bmi}</p>
          <p>Category: {category}</p>
        </div>
      )}
    </div>
  );
}

export default BMICalculator;


export default App;

## home.jsx
import React from 'react';

function Home() {
  return (
    <div>
      <h1>Welcome to BMI Calculator</h1>
      <p>Click on the navigation to calculate your BMI.</p>
    </div>
  );
}

export default Home;

## OUTPUT
![alt text](<Screenshot 2025-05-19 113001.png>)

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
