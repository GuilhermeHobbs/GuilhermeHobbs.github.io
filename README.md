<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Pages + Flask API</title>
</head>
<body>
    <h1>Click the button to ask: "Name?"</h1>
    <button onclick="askAPI()">Ask API</button>
    <p id="response"></p>

    <script>
        async function askAPI() {
            const apiUrl = "https://checkersgpt-production.up.railway.app/ask"; // Replace with your actual Railway API URL
            try {
                let response = await fetch(apiUrl);
                let data = await response.json();
                document.getElementById("response").innerText = data.answer;
            } catch (error) {
                console.error("Error fetching from API:", error);
                document.getElementById("response").innerText = "Failed to connect to API";
            }
        }
    </script>
</body>
</html>
