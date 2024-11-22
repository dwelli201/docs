<link rel="stylesheet" href="dark-theme.css">

<center>
    <img src="https://www.hamqsl.com/solarsystem.php" alt="Solar-Terrestrial Data">
</center>

<br>

<center>
    <img src="https://www.hamqsl.com/solarmuf.php" alt="Solar-Terrestrial Data">
</center>

<br>

<center>
    <img src="https://www.hamqsl.com/solarn0nbh.php" alt="Solar-Terrestrial Data">
</center>

<br>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3-Day Forecast</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            text-align: center;
        }
        #forecastBox {
            width: 80ch;
            height: 100em;
            overflow: auto;
            font-family: monospace;
            white-space: pre;
            border: 1px solid #ccc;
            padding: 10px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <h1>3-Day Space Weather Forecast</h1>
    <div>
        <pre id="forecastBox">Loading forecast data...</pre>
    </div>

    <script>
        // Fetch and display the text file content
        fetch('https://services.swpc.noaa.gov/text/3-day-forecast.txt')
            .then(response => response.text())
            .then(data => {
                document.getElementById('forecastBox').textContent = data;
            })
            .catch(error => {
                console.error('Error fetching forecast data:', error);
                document.getElementById('forecastBox').textContent = 'Error loading forecast data.';
            });
    </script>
</body>
</html>
