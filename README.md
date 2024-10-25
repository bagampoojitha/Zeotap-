<!-- HTML form (Simple UI) -->
<!DOCTYPE html>
<html lang="en">
<head>
    <title>User Eligibility Check</title>
</head>
<body>
    <h1>Check User Eligibility</h1>
    <form id="eligibilityForm">
        <label>Age:</label>
        <input type="number" id="age" name="age" required><br>
        <label>Department:</label>
        <input type="text" id="department" name="department" required><br>
        <label>Income:</label>
        <input type="number" id="income" name="income" required><br>
        <label>Spend:</label>
        <input type="number" id="spend" name="spend" required><br><br>
        <input type="submit" value="Check Eligibility">
    </form>

    <p id="result"></p>

    <script>
        document.getElementById('eligibilityForm').onsubmit = async function(event) {
            event.preventDefault();
            const formData = {
                age: document.getElementById('age').value,
                department: document.getElementById('department').value,
                income: document.getElementById('income').value,
                spend: document.getElementById('spend').value
            };
            
            const response = await fetch('/api/check-eligibility', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(formData)
            });
            
            const result = await response.json();
            document.getElementById('result').innerText = result.message;
        };
    </script>
</body>
</html># Zeotap-
