# Ex06 BMI Calculator
## Date: 13-03-2025

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
App.jsx
```
const { BrowserRouter, Routes, Route, Link } = ReactRouterDOM;

const App = () => (
  <BrowserRouter>
    <Routes>
      <Route path="/" element={
        <div className="container">
          <h1 className="title">Welcome to BMI Calculator</h1>
          <p className="text-lg text-gray-700 mb-6">Calculate your Body Mass Index quickly and easily.</p>
          <Link to="/calculator" className="calculate-button">
            Go to Calculator
          </Link>
        </div>
      } />
      <Route path="/calculator" element={<Calculator />} />
    </Routes>
  </BrowserRouter>
);

// Render the app
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

BMI_Calcuator.jsx
```
const Calculator = () => {
  const [weight, setWeight] = React.useState('');
  const [height, setHeight] = React.useState('');
  const [bmi, setBmi] = React.useState(null);
  const [category, setCategory] = React.useState('');

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100; // Convert cm to meters
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(1);
      setBmi(bmiValue);

      // Categorize BMI
      if (bmiValue < 18.5) {
        setCategory('Underweight');
      } else if (bmiValue >= 18.5 && bmiValue < 25) {
        setCategory('Normal weight');
      } else if (bmiValue >= 25 && bmiValue < 30) {
        setCategory('Overweight');
      } else {
        setCategory('Obesity');
      }
    }
  };

  return (
    <div className="container">
      <h1 className="title">BMI Calculator</h1>
      <div className="calculator-card">
        <div className="mb-4">
          <label className="input-label" htmlFor="weight">Weight (kg):</label>
          <input
            type="number"
            id="weight"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
            className="input-field"
            placeholder="Enter your weight"
          />
        </div>
        <div className="mb-4">
          <label className="input-label" htmlFor="height">Height (cm):</label>
          <input
            type="number"
            id="height"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
            className="input-field"
            placeholder="Enter your height"
          />
        </div>
        <button
          onClick={calculateBMI}
          className="calculate-button"
        >
          Calculate BMI
        </button>
        {bmi && (
          <div className="result-text">
            <p>Your BMI: <span>{bmi}</span></p>
            <p>Category: <span>{category}</span></p>
          </div>
        )}
        <Link to="/" className="link block text-center mt-4">
          Back to Home
        </Link>
      </div>
    </div>
  );
};
```

index.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
.container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #f3f4f6;
}
.title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #2563eb;
  margin-bottom: 1.5rem;
}
.link {
  color: #2563eb;
  text-decoration: none;
  font-size: 1.1rem;
}
.link:hover {
  text-decoration: underline;
}
.calculator-card {
  background: white;
  padding: 2rem;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 24rem;
}
.input-label {
  display: block;
  color: #374151;
  margin-bottom: 0.5rem;
  font-weight: 500;
}
.input-field {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  font-size: 1rem;
}
.input-field:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 2px rgba(37, 99, 235, 0.2);
}
.calculate-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #2563eb;
  color: white;
  border: none;
  border-radius: 0.375rem;
  font-size: 1rem;
  cursor: pointer;
}
.calculate-button:hover {
  background-color: #1d4ed8;
}
.result-text {
  font-size: 1.1rem;
  margin-top: 1rem;
  text-align: center;
}
.result-text span {
  font-weight: bold;
}
```


## OUTPUT

![image](https://github.com/user-attachments/assets/fe4ae516-36ee-49be-abe8-54db3c6d3704)


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
