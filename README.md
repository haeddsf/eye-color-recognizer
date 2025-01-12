<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eye Color Recognizer</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }

        .container {
            text-align: center;
        }

        .hidden {
            display: none;
        }

        .eye-button {
            font-size: 24px;
            padding: 10px 20px;
            cursor: pointer;
            margin-top: 20px;
        }

        #loading {
            font-size: 24px;
        }

        #result {
            font-size: 16px;
            margin-top: 20px;
        }

        #complete-btn {
            font-size: 14px;
            margin-top: 20px;
        }

        #title {
            animation: colorChange 1s infinite;
        }

        @keyframes colorChange {
            0% { color: red; }
            25% { color: blue; }
            50% { color: green; }
            75% { color: yellow; }
            100% { color: red; }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="title">What kind of your eye color</h1>
        <button id="start-btn" class="eye-button">👁️ Start</button>
        <input type="file" id="file-input" class="hidden" accept="image/*" capture="camera">
        <div id="loading" class="hidden">Loading...</div>
        <div id="result" class="hidden"></div>
        <button id="complete-btn" class="hidden">Complete</button>
    </div>
    <script>
        document.getElementById('start-btn').addEventListener('click', function() {
            document.getElementById('file-input').click();
        });

        document.getElementById('file-input').addEventListener('change', function(event) {
            if (event.target.files.length > 0) {
                document.getElementById('title').classList.add('hidden');
                document.getElementById('start-btn').classList.add('hidden');
                document.getElementById('loading').classList.remove('hidden');

                setTimeout(function() {
                    const colors = [
                        "Cloud Poop Color",
                        "Cat Color",
                        "Ghost Color",
                        "Stuck without Battery Color",
                        "German Administrative Speed Color",
                        "Bottle Cap Color",
                        "Insurance Fee Color",
                        "Colored Pencil Color"
                    ];
                    
                    const randomColor = colors[Math.floor(Math.random() * colors.length)];
                    
                    document.getElementById('loading').classList.add('hidden');
                    document.getElementById('result').innerText = `Recognition Complete: ${randomColor}`;
                    document.getElementById('result').classList.remove('hidden');
                    document.getElementById('complete-btn').classList.remove('hidden');
                }, 3000);
            }
        });

        document.getElementById('complete-btn').addEventListener('click', function() {
            document.getElementById('title').classList.remove('hidden');
            document.getElementById('start-btn').classList.remove('hidden');
            document.getElementById('result').classList.add('hidden');
            document.getElementById('loading').classList.add('hidden');
            document.getElementById('file-input').value = "";
            document.getElementById('complete-btn').classList.add('hidden');
        });
    </script>
</body>
</html>
