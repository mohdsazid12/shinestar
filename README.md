<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Avatar Video Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }

        #video-container {
            width: 100%;
            max-width: 600px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>AI Avatar Video Generator</h1>

    <label for="description">Enter Description:</label>
    <textarea id="description" rows="4" cols="50"></textarea>

    <button onclick="generateAvatarVideo()">Generate Avatar Video</button>

    <div id="video-container"></div>

    <script>
        async function generateAvatarVideo() {
            const description = document.getElementById('description').value;

            // Assuming you have a backend endpoint for generating avatar videos
            const apiUrl = 'https://your-backend-api.com/generate-avatar-video';

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ description }),
                });

                const data = await response.json();

                if (data.success) {
                    displayVideo(data.videoUrl);
                } else {
                    alert('Failed to generate avatar video. Please try again.');
                }
            } catch (error) {
                console.error('Error:', error);
                alert('An error occurred. Please try again later.');
            }
        }

        function displayVideo(videoUrl) {
            const videoContainer = document.getElementById('video-container');
            videoContainer.innerHTML = `<video controls width="100%" src="${videoUrl}" type="video/mp4"></video>`;
        }
    </script>
</body>
</html>
