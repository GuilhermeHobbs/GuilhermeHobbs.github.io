<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GPT Web App</title>
</head>
<body>
    <h1>Ask GPT</h1>
    <textarea id="prompt" placeholder="Type your question here..."></textarea>
    <button onclick="generateText()">Generate</button>
    <p id="response"></p>

    <script>
        async function generateText() {
            const prompt = document.getElementById("prompt").value;
            const response = await fetch("http://127.0.0.1:8000/generate", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ prompt })
            });
            const data = await response.json();
            document.getElementById("response").innerText = data.response;
        }
    </script>
</body>
</html>
