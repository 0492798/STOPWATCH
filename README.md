<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Stopwatch Clock App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f0f0;
      text-align: center;
      padding: 50px;
    }
    h1 {
      margin-bottom: 30px;
    }
    .clock, .stopwatch {
      background: white;
      padding: 20px;
      margin: 20px auto;
      width: 300px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    .time {
      font-size: 2em;
      margin-bottom: 10px;
    }
    .buttons button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>Stopwatch & Clock App</h1>

  <div class="clock">
    <h2>Current Time</h2>
    <div id="clockTime" class="time">00:00:00</div>
  </div>

  <div class="stopwatch">
    <h2>Stopwatch</h2>
    <div id="stopwatchTime" class="time">00:00:00</div>
    <div class="buttons">
      <button onclick="startStopwatch()">Start</button>
      <button onclick="stopStopwatch()">Stop</button>
      <button onclick="resetStopwatch()">Reset</button>
    </div>
  </div>

  <script>
    // Clock
    function updateClock() {
      const now = new Date();
      const h = String(now.getHours()).padStart(2, '0');
      const m = String(now.getMinutes()).padStart(2, '0');
      const s = String(now.getSeconds()).padStart(2, '0');
      document.getElementById('clockTime').textContent = `${h}:${m}:${s}`;
    }
    setInterval(updateClock, 1000);
    updateClock();

    // Stopwatch
    let stopwatchInterval;
    let elapsedSeconds = 0;

    function updateStopwatch() {
      const h = String(Math.floor(elapsedSeconds / 3600)).padStart(2, '0');
      const m = String(Math.floor((elapsedSeconds % 3600) / 60)).padStart(2, '0');
      const s = String(elapsedSeconds % 60).padStart(2, '0');
      document.getElementById('stopwatchTime').textContent = `${h}:${m}:${s}`;
    }

    function startStopwatch() {
      if (!stopwatchInterval) {
        stopwatchInterval = setInterval(() => {
          elapsedSeconds++;
          updateStopwatch();
        }, 1000);
      }
    }

    function stopStopwatch() {
      clearInterval(stopwatchInterval);
      stopwatchInterval = null;
    }

    function resetStopwatch() {
      stopStopwatch();
      elapsedSeconds = 0;
      updateStopwatch();
    }

    updateStopwatch(); // Initialize display
  </script>
</body>
</html>
# STOPWATCH
