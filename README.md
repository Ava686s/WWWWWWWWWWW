<html lang="en">
<head>
<meta charset="UTF-8">
<title>Welcome</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 80px;
    background: #f5f5f5;
    color: #222;
  }
  h1 {
    font-size: 48px;
    margin-bottom: 40px;
  }
  #display {
    font-size: 60px;
    font-weight: bold;
    margin-bottom: 30px;
    font-family: monospace;
  }
  button {
    font-size: 18px;
    padding: 10px 25px;
    margin: 5px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    background: #333;
    color: white;
  }
  button:hover {
    background: #555;
  }
</style>
</head>
<body>

<h1>Welcome</h1>

<div id="display">00:00:00.0</div>

<script>
  let startTime = 0;
  let elapsed = 0;
  let timerInterval = null;
  let running = false;

  function formatTime(ms) {
    let hours = Math.floor(ms / 3600000);
    let minutes = Math.floor((ms % 3600000) / 60000);
    let seconds = Math.floor((ms % 60000) / 1000);
    let tenths = Math.floor((ms % 1000) / 100);

    function pad(num) {
      return num.toString().padStart(2, '0');
    }

    return pad(hours) + ":" + pad(minutes) + ":" + pad(seconds) + "." + tenths;
  }

  function updateDisplay() {
    let currentElapsed = elapsed + (running ? (Date.now() - startTime) : 0);
    document.getElementById("display").textContent = formatTime(currentElapsed);
  }

  function startStopwatch() {
    if (!running) {
      running = true;
      startTime = Date.now();
      timerInterval = setInterval(updateDisplay, 100);
    }
  }

  startStopwatch();
</script>

</body>
</html>
