# challenge-submission
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  background-color: white;
  border-radius: 8px;
  padding: 20px;
  width: 80%;
  max-width: 800px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

h2 {
  margin-bottom: 10px;
}

.form-container {
  margin-bottom: 30px;
}

label {
  font-weight: bold;
}

input, textarea {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.dashboard-container {
  margin-top: 40px;
}

.report {
  background-color: #e7f7e7;
  padding: 10px;
  margin: 10px 0;
  border-radius: 4px;
}
document.getElementById("emergencyForm").addEventListener("submit", function(event) {
  event.preventDefault();

  // Get values from the form
  const name = document.getElementById("name").value;
  const symptoms = document.getElementById("symptoms").value;
  const location = document.getElementById("location").value;

  // Create a new emergency report object
  const report = {
    name: name,
    symptoms: symptoms,
    location: location,
    severity: calculateSeverity(symptoms) // Use a simple function to determine severity
  };

  // Add report to the dashboard
  displayReport(report);

  // Clear the form after submission
  document.getElementById("emergencyForm").reset();
});

// Function to display the report on the dashboard
function displayReport(report) {
  const reportsContainer = document.getElementById("reports");

  const reportDiv = document.createElement("div");
  reportDiv.classList.add("report");

  reportDiv.innerHTML = `
    <strong>Name:</strong> ${report.name}<br>
    <strong>Symptoms:</strong> ${report.symptoms}<br>
    <strong>Location:</strong> ${report.location}<br>
    <strong>Severity:</strong> ${report.severity}
  `;

  reportsContainer.appendChild(reportDiv);
}

// Simple function to calculate severity based on symptoms (this can be improved)
function calculateSeverity(symptoms) {
  if (symptoms.includes("severe") || symptoms.includes("unconscious") || symptoms.includes("chest pain")) {
    return "High";
  } else if (symptoms.includes("fever") || symptoms.includes("headache")) {
    return "Medium";
  } else {
    return "Low";
  }
}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Emergency Medical Response</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Emergency Medical Response System</h1>

    <!-- Report Emergency Form -->
    <div class="form-container">
      <h2>Report an Emergency</h2>
      <form id="emergencyForm">
        <label for="name">Your Name:</label>
        <input type="text" id="name" required>
        
        <label for="symptoms">Symptoms:</label>
        <textarea id="symptoms" required></textarea>
        
        <label for="location">Location:</label>
        <input type="text" id="location" required>
        
        <button type="submit">Submit Report</button>
      </form>
    </div>

    <!-- Emergency Reports Dashboard -->
    <div class="dashboard-container">
      <h2>Emergency Reports</h2>
      <div id="reports"></div>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
