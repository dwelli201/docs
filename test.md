<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Space Weather Dashboard</title>
    <style>
        /* Center content and style the textarea */
        .center {
            text-align: center;
        }
        #forecastBox {
            width: 80ch;
            height: 100em;
            overflow: auto;
            font-family: monospace;
            white-space: pre;
        }
        img {
            max-width: 100%;
            height: auto;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <!-- Textarea for 3-day forecast -->
    <div class="center">
        <textarea id="forecastBox" readonly>Loading...</textarea>
    </div>

    <!-- Script to fetch and display forecast data -->
    <script>
        fetch('https://services.swpc.noaa.gov/text/3-day-forecast.txt')
            .then(response => response.text())
            .then(data => {
                document.getElementById('forecastBox').textContent = data;
            })
            .catch(error => {
                console.error('Error fetching the text file:', error);
                document.getElementById('forecastBox').textContent = 'Error loading content.';
            });
    </script>

    <!-- Images -->
    <div class="center">
        <img src="http://services.swpc.noaa.gov/images/animations/enlil/latest.jpg" alt="NOAA Solar Animation">
    </div>
    <div class="center">
        <img src="https://www.hamqsl.com/solarsystem.php" alt="Solar-Terrestrial Data">
    </div>
    <div class="center">
        <img src="https://www.hamqsl.com/solarn0nbh.php" alt="Solar-Terrestrial Data">
    </div>
</body>
</html>
