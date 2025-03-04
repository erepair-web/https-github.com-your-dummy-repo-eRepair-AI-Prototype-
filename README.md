# https-github.com-your-dummy-repo-eRepair-AI-Prototype-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>eRepair AI Prototype</title>
    <style>
        body { font-family: Arial, sans-serif; }
        .chatbot { background: #f5f5f5; padding: 20px; border-radius: 10px; }
        #chat-log { height: 300px; overflow-y: auto; border: 1px solid #ddd; padding: 10px; }
        .user { color: blue; }
        .ai { color: green; }
        .ar-guide { display: none; } /* Placeholder for AR */
    </style>
</head>
<body>
    <header>
        <h1>eRepair AI</h1>
        <button onclick="startDiagnosis()">Start Free Diagnosis</button>
    </header>

    <!-- AI Chatbot Interface -->
    <div class="chatbot" id="chatbot">
        <div id="chat-log"></div>
        <input type="text" id="user-input" placeholder="Describe your issue...">
        <button onclick="sendMessage()">Send</button>
    </div>

    <!-- Device Photo Upload for AI Analysis -->
    <div class="upload-section">
        <input type="file" id="device-photo" accept="image/*">
        <button onclick="analyzePhoto()">Analyze with AI</button>
        <p id="ai-result"></p>
    </div>

    <!-- AR Guide Placeholder -->
    <div class="ar-guide">
        <video autoplay muted id="ar-feed"></video>
    </div>

    <script>
        // Mock AI Chatbot Logic
        let step = 0;
        const questions = [
            "What device are you using?",
            "Describe the issue (e.g., screen crack, battery drain):",
            "Upload a photo for AI analysis."
        ];

        function startDiagnosis() {
            document.getElementById('chatbot').style.display = 'block';
            addMessage('ai', questions[step]);
        }

        function sendMessage() {
            const userInput = document.getElementById('user-input').value;
            addMessage('user', userInput);
            step++;
            if (step < questions.length) {
                setTimeout(() => addMessage('ai', questions[step]), 1000);
            } else {
                addMessage('ai', 'Analyzing your issue...');
                // Call backend AI model here
            }
        }

        function addMessage(sender, text) {
            const chatLog = document.getElementById('chat-log');
            chatLog.innerHTML += `<p class="${sender}">${text}</p>`;
        }

        // Mock Computer Vision Analysis
        async function analyzePhoto() {
            const file = document.getElementById('device-photo').files[0];
            const resultElement = document.getElementById('ai-result');
            resultElement.textContent = 'AI is analyzing your photo...';

            // Simulate API call to backend AI model
            setTimeout(() => {
                resultElement.textContent = 'Issue detected: Cracked screen (98% confidence). Recommended solution: Replace screen ($120)';
            }, 2000);
        }
    </script>
</body>
</html>
