<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Free Text-to-Video AI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
        }

        header {
            background-color: #007BFF;
            color: white;
            padding: 20px;
            text-align: center;
        }

        main {
            padding: 20px;
        }

        #input-section {
            margin-bottom: 20px;
        }

        textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            display: block;
            margin: 10px 0;
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        #output-section {
            text-align: center;
        }

        video {
            max-width: 100%;
            height: auto;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        footer {
            text-align: center;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <header>
        <h1>Free Text-to-Video AI</h1>
        <p>Turn your text into videos for free!</p>
    </header>

    <main>
        <section id="input-section">
            <textarea id="text-input" placeholder="Enter your text here..."></textarea>
            <button id="generate-btn">Generate Video</button>
        </section>

        <section id="output-section">
            <h2>Your Generated Video</h2>
            <video id="video-output" controls>
                <source src="" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </section>
    </main>

    <footer>
        <p>&copy; 2023 Free Text-to-Video AI. All rights reserved.</p>
    </footer>

    <script>
        document.getElementById('generate-btn').addEventListener('click', function () {
            const textInput = document.getElementById('text-input').value;
            if (textInput.trim() === "") {
                alert("Please enter some text!");
                return;
            }

            // Replace with your free API endpoint
            const apiUrl = "https://api.free-text-to-video.com/generate";
            const apiKey = "your-free-api-key";

            // Show loading message
            alert("Generating video... This may take a few seconds.");

            // Send text to the API
            fetch(apiUrl, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": `Bearer ${apiKey}`
                },
                body: JSON.stringify({
                    text: textInput
                })
            })
            .then(response => response.json())
            .then(data => {
                if (data.videoUrl) {
                    // Display the generated video
                    const videoOutput = document.getElementById('video-output');
                    videoOutput.src = data.videoUrl;
                    videoOutput.load();
                } else {
                    alert("Failed to generate video. Please try again.");
                }
            })
            .catch(error => {
                console.error("Error:", error);
                alert("An error occurred. Please check the console for details.");
            });
        });
    </script>
</body>
</html>
