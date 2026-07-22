<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Clock</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 50px;
  }
  #clock {
    font-size: 48px;
    margin-bottom: 20px;
  }
  #codeInput {
    font-size: 18px;
    padding: 5px;
    text-align: center;
  }
  #hexText {
    margin-top: 20px;
    font-size: 14px;
    color: #555;
  }
</style>
</head>
<body>

<div id="clock">00:00:00</div>

<input type="text" id="codeInput" placeholder="Enter code">
<br>
<button id="submitBtn">Submit</button>

<div id="hexText">53 70 6c 65 6e 64 69 64 0d 0a</div>
<div id="message" style="margin-top:15px; color:red;"></div>

<script>
  function updateClock() {
    const now = new Date();
    const h = String(now.getHours()).padStart(2, '0');
    const m = String(now.getMinutes()).padStart(2, '0');
    const s = String(now.getSeconds()).padStart(2, '0');
    document.getElementById('clock').textContent = h + ':' + m + ':' + s;
  }
  updateClock();
  setInterval(updateClock, 1000);

  document.getElementById('submitBtn').addEventListener('click', function() {
    const value = document.getElementById('codeInput').value;
    const messageEl = document.getElementById('message');
    if (value === 'Splendid') {
      window.location.href = 'https://imgur.com/PwYQiwx';
    } else {
      messageEl.textContent = 'Incorrect code. Try again.';
    }
  });

  document.getElementById('codeInput').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') {
      document.getElementById('submitBtn').click();
    }
  });
</script>

</body>
</html>
