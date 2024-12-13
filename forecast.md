
<style>
body {
    background-color: #121212;
    color: #ffffff;
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 20px;
}
a {
    color: #1e90ff;
    text-decoration: none;
}
a:hover {
    text-decoration: underline;
}
table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
}
th, td {
    border: 1px solid #333;
    padding: 10px;
    text-align: left;
}
th {
    background-color: #1e1e1e;
}
</style>


<link rel="stylesheet" href="dark-theme.css">

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3-Day Space Weather Forecast</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            text-align: center;
            margin: 20px;
        }
        #forecastBox {
            width: 80ch;
            height: 90em;
            overflow: auto;
            font-family: monospace;
            white-space: pre;
            border: 1px solid #ccc;
            padding: 10px;
            margin: 20px auto;
        }
    </style>
</head>
<body>
    <h1>3-Day Space Weather Forecast</h1>
    <div>
        <textarea id="forecastBox" readonly>Loading...</textarea>
    </div>

    <script>
        // Fetch the content of the text file and insert it into the textarea
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
</body>
</html>

<br>

[Index](./index.md)
