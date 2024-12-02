<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catch the Ball Game</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: #333;
      color: white;
    }
    canvas {
      display: block;
      margin: 0 auto;
      background: #444;
    }
  </style>
</head>
<body>
<canvas id="gameCanvas"></canvas>

<script>
  const canvas = document.getElementById("gameCanvas");
  const ctx = canvas.getContext("2d");

  // Set canvas dimensions
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const paddleWidth = 100;
  const paddleHeight = 10;
  const ballRadius = 10;

  let paddleX = (canvas.width - paddleWidth) / 2;
  let ballX = Math.random() * (canvas.width - ballRadius * 2) + ballRadius;
  let ballY = ballRadius;
  let ballSpeed = 3;
  let score = 0;

  const paddleSpeed = 10;

  // Controls
  let rightPressed = false;
  let leftPressed = false;

  document.addEventListener("keydown", (e) => {
    if (e.key === "ArrowRight") rightPressed = true;
    else if (e.key === "ArrowLeft") leftPressed = true;
  });

  document.addEventListener("keyup", (e) => {
    if (e.key === "ArrowRight") rightPressed = false;
    else if (e.key === "ArrowLeft") leftPressed = false;
  });

  function drawPaddle() {
    ctx.fillStyle = "#0f0";
    ctx.fillRect(paddleX, canvas.height - paddleHeight, paddleWidth, paddleHeight);
  }

  function drawBall() {
    ctx.beginPath();
    ctx.arc(ballX, ballY, ballRadius, 0, Math.PI * 2);
    ctx.fillStyle = "#f00";
    ctx.fill();
    ctx.closePath();
  }

  function drawScore() {
    ctx.font = "20px Arial";
    ctx.fillStyle = "#fff";
    ctx.fillText(`Score: ${score}`, 10, 30);
  }

  function update() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Move paddle
    if (rightPressed && paddleX < canvas.width - paddleWidth) {
      paddleX += paddleSpeed;
    }
    if (leftPressed && paddleX > 0) {
      paddleX -= paddleSpeed;
    }

    // Move ball
    ballY += ballSpeed;

    // Ball collision with paddle
    if (
      ballY + ballRadius >= canvas.height - paddleHeight &&
      ballX >= paddleX &&
      ballX <= paddleX + paddleWidth
    ) {
      ballSpeed += 0.5; // Increase difficulty
      ballY = ballRadius; // Reset ball
      ballX = Math.random() * (canvas.width - ballRadius * 2) + ballRadius;
      score++;
    }

    // Ball missed
    if (ballY > canvas.height) {
      alert(`Game Over! Your score: ${score}`);
      document.location.reload();
    }

    drawPaddle();
    drawBall();
    drawScore();

    requestAnimationFrame(update);
  }

  update();
</script>
</body>
</html>
