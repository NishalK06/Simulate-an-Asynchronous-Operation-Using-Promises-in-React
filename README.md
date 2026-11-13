# React Lab Exercise 13: Simulate an Asynchronous Operation Using Promises in React

## Name: Nishal K

## Roll no: 2305001021

## Department: CSE

## AIM

To develop a React application that simulates an asynchronous student-data operation using a JavaScript Promise, displays a loading message while the operation is in progress, and displays the result when the Promise is fulfilled.

## PROGRAM

### i) App.jsx

```javascript
import { useState } from "react";
import "./App.css";

function fetchStudentData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const student = {
        name: "Arun",
        department: "CSE",
        year: "III",
      };

      resolve(student);
    }, 3000);
  });
}

function App() {
  const [loading, setLoading] = useState(false);
  const [student, setStudent] = useState(null);
  const [error, setError] = useState("");

  const handleFetch = () => {
    setLoading(true);
    setStudent(null);
    setError("");

    fetchStudentData()
      .then((data) => {
        setStudent(data);
      })
      .catch((err) => {
        setError(err.message);
      })
      .finally(() => {
        setLoading(false);
      });
  };

  return (
    <div className="app">
      <h1>Student Data Fetch</h1>

      <button onClick={handleFetch} disabled={loading}>
        {loading ? "Fetching..." : "Fetch Student"}
      </button>

      {loading && <p>Fetching student information...</p>}

      {student && (
        <div>
          <h2>Student Details</h2>
          <p>Student Name: {student.name}</p>
          <p>Department: {student.department}</p>
          <p>Year: {student.year}</p>
          <p>Status: Data Loaded Successfully</p>
        </div>
      )}

      {error && <p>Error: {error}</p>}
    </div>
  );
}

export default App;
```

### ii) App.css

```css
#root {
  width: 100%;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f2f5f9;
}

.app {
  max-width: 600px;
  margin: 70px auto;
  padding: 30px;
  text-align: center;
  background-color: white;
  border-radius: 12px;
  box-shadow: 0 4px 12px #0000001a;
}

h1 {
  color: darkblue;
}

h2 {
  color: darkgreen;
}

button {
  padding: 12px 24px;
  background-color: #2563eb;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}

button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

p {
  font-size: 16px;
  color: #333;
}
```

## OUTPUT
<img width="1014" height="381" alt="image" src="https://github.com/user-attachments/assets/23228683-1d4c-4788-8e09-0c1cce7fce06" />
<img width="1986" height="792" alt="image" src="https://github.com/user-attachments/assets/5a9c80d9-2e42-4f8b-8c04-ced8fba4ee5c" />


## RESULT

Thus, a React application was developed successfully to simulate an asynchronous student-data operation using JavaScript Promises. The application displays a loading message during the operation and handles successful results and errors using .then(), .catch(), and .finally().
