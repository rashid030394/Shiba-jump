const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

canvas.width = 400;
canvas.height = 600;

const shibImg = new Image();
shibImg.src = "shib.png"; // Shiba Inu character image

let shib = {
    x: canvas.width / 2 - 25,
    y: canvas.height - 100,
    width: 50,
    height: 50,
    velocityY: 0,
    gravity: 0.4,
    jumpPower: -8
};

let platforms = [{ x: canvas.width / 2 - 50, y: canvas.height - 20, width: 100, height: 10 }];
let score = 0;
let gameRunning = true;

function drawShib() {
    ctx.drawImage(shibImg, shib.x, shib.y, shib.width, shib.height);
}

function drawPlatforms() {
    ctx.fillStyle = "green";
    platforms.forEach(p => {
        ctx.fillRect(p.x, p.y, p.width, p.height);
    });
}

function update() {
    if (!gameRunning) return;

    shib.velocityY += shib.gravity;
    shib.y += shib.velocityY;

    if (shib.y > canvas.height) {
        gameRunning = false;
        alert("Game Over! Score: " + score);
        document.location.reload();
    }

    platforms.forEach(p => {
        if (shib.y + shib.height > p.y && shib.y + shib.height < p.y + p.height && shib.velocityY > 0 &&
            shib.x + shib.width > p.x && shib.x < p.x + p.width) {
            shib.velocityY = shib.jumpPower;
            score++;
        }
    });

    draw();
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawPlatforms();
    drawShib();
}

function jump() {
    if (gameRunning) shib.velocityY = shib.jumpPower;
}

canvas.addEventListener("click", jump);

function gameLoop() {
    update();
    requestAnimationFrame(gameLoop);
}

gameLoop();
