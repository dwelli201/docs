<div style="text-align: center;">
    <textarea id="forecastBox" style="width: 80ch; height: 100em; overflow: auto;" readonly>
        Loading...
    </textarea>
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

<br>

<center>
    <img src="http://services.swpc.noaa.gov/images/animations/enlil/latest.jpg" alt="NOAA Solar Animation">
</center>

<br>

<center>
    <img src="https://www.hamqsl.com/solarsystem.php" alt="Solar-Terrestrial Data">
</center>

<br>

<center>
    <img src="https://www.hamqsl.com/solarn0nbh.php" alt="Solar-Terrestrial Data">
</center>
