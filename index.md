<link rel="stylesheet" href="dark-theme.css">

## _Index_

| [Commands](./commands.md) | [Education](./education.md) | [Links](./links.md) |

<br>

<a class="weatherwidget-io" href="https://forecast7.com/en/30d27n97d74/austin/?unit=us" data-label_1="AUSTIN" data-label_2="WEATHER" data-theme="original">AUSTIN WEATHER</a>
<script>
!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src='https://weatherwidget.io/js/widget.min.js';fjs.parentNode.insertBefore(js,fjs);}}(document,'script','weatherwidget-io-js');
</script>

<br>

<a class="weatherwidget-io" href="https://forecast7.com/en/36d85n76d29/norfolk/?unit=us" data-label_1="NORFOLK" data-label_2="WEATHER" data-theme="original" >NORFOLK WEATHER</a>
<script>
!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src='https://weatherwidget.io/js/widget.min.js';fjs.parentNode.insertBefore(js,fjs);}}(document,'script','weatherwidget-io-js');
</script>

<br>

<center>
    <img src="https://www.hamqsl.com/solar101vhf.php" alt="Solar-Terrestrial Data">
</center>

<br> 

<button onclick="openPopup()">Open Forecast</button>

<div id="popup" style="display:none; position:fixed; top:10%; left:10%; width:80%; height:80%; background:white; border:1px solid black; box-shadow:0px 0px 10px rgba(0,0,0,0.5); z-index:1000; overflow:auto;">
  <button onclick="closePopup()" style="float:right; margin:10px;">Close</button>
  <iframe src="https://dwelli201.github.io/docs/forecast.html" style="width:100%; height:90%; border:none;"></iframe>
</div>

<script>
  function openPopup() {
    document.getElementById('popup').style.display = 'block';
  }

  function closePopup() {
    document.getElementById('popup').style.display = 'none';
  }
</script>
