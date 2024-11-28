<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Musify App - README</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
            background-color: #f9f9f9;
            color: #333;
        }
        h1, h2 {
            color: #2c3e50;
        }
        code {
            background-color: #e8e8e8;
            padding: 2px 4px;
            border-radius: 4px;
        }
        .example {
            background-color: #f4f4f4;
            padding: 10px;
            margin: 10px 0;
            border-left: 5px solid #2c3e50;
        }
    </style>
</head>
<body>
    <h1>Musify App</h1>
    <p>The <strong>Musify App</strong> is a simple web-based application for playing and managing music files. The app dynamically renders a playlist of songs using files stored locally, including:</p>
    <ul>
        <li><code>MP3</code> files for the songs</li>
        <li><code>JSON</code> file to store metadata (e.g., song title, artist)</li>
        <li><code>Image</code> files for album art</li>
    </ul>

    <h2>Features</h2>
    <ul>
        <li>Dynamic rendering of a playlist based on the file system.</li>
        <li>Display of song title, artist, and album art using a JSON file.</li>
        <li>Playback controls for each song.</li>
        <li>Responsive design for compatibility with various devices.</li>
    </ul>

    <h2>Folder Structure</h2>
    <div class="example">
        <pre>
        /musify
        ├── index.html         # Main HTML file
        ├── style.css          # Optional CSS for styling
        ├── app.js             # JavaScript logic
        ├── songs/             # Folder for MP3 files
        │   ├── song1.mp3
        │   ├── song2.mp3
        │   └── ...
        ├── images/            # Folder for album art
        │   ├── album1.jpg
        │   ├── album2.png
        │   └── ...
        ├── data.json          # JSON file with metadata
        </pre>
    </div>

    <h2>JSON File Format</h2>
    <p>The <code>data.json</code> file contains metadata for each song. Example:</p>
    <div class="example">
        <pre>
        [
            {
                "title": "Song 1",
                "artist": "Artist 1",
                "albumArt": "images/album1.jpg",
                "file": "songs/song1.mp3"
            },
            {
                "title": "Song 2",
                "artist": "Artist 2",
                "albumArt": "images/album2.png",
                "file": "songs/song2.mp3"
            }
        ]
        </pre>
    </div>

    <h2>How to Use</h2>
    <ol>
        <li>Place your MP3 files in the <code>songs/</code> folder.</li>
        <li>Add corresponding album art to the <code>images/</code> folder.</li>
        <li>Update the <code>data.json</code> file with song details (title, artist, paths).</li>
        <li>Open <code>index.html</code> in a web browser.</li>
    </ol>

    <h2>Dynamic Rendering Example</h2>
    <p>Here’s a simple JavaScript snippet used for dynamically rendering the playlist:</p>
    <div class="example">
        <pre>
        fetch('data.json')
            .then(response => response.json())
            .then(data => {
                const playlist = document.getElementById('playlist');
                data.forEach(song => {
                    const songDiv = document.createElement('div');
                    songDiv.innerHTML = `
                        <img src="${song.albumArt}" alt="${song.title}" style="width: 100px; height: 100px;">
                        <h3>${song.title}</h3>
                        <p>${song.artist}</p>
                        <audio controls>
                            <source src="${song.file}" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    `;
                    playlist.appendChild(songDiv);
                });
            });
        </pre>
    </div>

    <h2>Demo</h2>
    <div id="playlist"></div>

    <h2>Dependencies</h2>
    <ul>
        <li>Modern web browser (Chrome, Firefox, Safari, etc.)</li>
        <li>JavaScript enabled</li>
    </ul>

    <h2>License</h2>
    <p>Open source - feel free to use, modify, and share!</p>
</body>
</html>
