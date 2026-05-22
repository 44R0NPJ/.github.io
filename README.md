<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Relocation Countdown</title>
<style>
  body {
    background-color: #000000;
    color: #00FF00;
    font-family: monospace;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
  }
  h1 {
    font-size: 1.2rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 20px;
    text-shadow: 0 0 5px #00FF00;
  }
  #timer {
    font-size: 2.2rem;
    font-weight: bold;
    text-shadow: 0 0 10px #00FF00;
  }
</style>
</head>
<body>

<h1>Relocation Imminent</h1>
<div id="timer">CALCULATING...</div>

<script>
  const targetDate = new Date("June 30, 2026 00:00:00").getTime();

  const countdown = setInterval(() => {
    const now = new Date().getTime();
    const distance = targetDate - now;

    const days = Math.floor(distance / (1000 * 60 * 60 * 24));
    const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((distance % (1000 * 60)) / 1000);

    document.getElementById("timer").innerHTML =
      `${days}D ${hours.toString().padStart(2, '0')}H ${minutes.toString().padStart(2, '0')}M ${seconds.toString().padStart(2, '0')}S`;

    if (distance < 0) {
      clearInterval(countdown);
      document.getElementById("timer").innerHTML = "INITIATE TRANSIT";
    }
  }, 1000);
</script>

</body>
</html>
