<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Celebrando Nuestra Amistad</title>

<style>
    body {
        margin: 0;
        padding: 0;
        font-family: 'Segoe UI', sans-serif;
        background: linear-gradient(135deg, #ff758c, #ff7eb3);
        overflow: hidden;
        text-align: center;
        color: white;
    }

    h1 {
        margin-top: 80px;
        font-size: 3em;
        animation: fadeIn 2s ease-in-out;
    }

    p {
        font-size: 1.4em;
        margin: 20px;
        animation: fadeIn 3s ease-in-out;
    }

    button {
        padding: 15px 35px;
        font-size: 1.2em;
        border: none;
        border-radius: 30px;
        background: white;
        color: #ff4f81;
        cursor: pointer;
        margin-top: 20px;
        transition: 0.3s;
    }

    button:hover {
        transform: scale(1.1);
        background: #ff4f81;
        color: white;
    }

    @keyframes fadeIn {
        from {opacity: 0; transform: translateY(-20px);}
        to {opacity: 1; transform: translateY(0);}
    }

    .corazon {
        position: absolute;
        font-size: 25px;
        animation: flotar 6s linear infinite;
    }

    @keyframes flotar {
        from {transform: translateY(100vh); opacity: 1;}
        to {transform: translateY(-10vh); opacity: 0;}
    }

    canvas {
        position: fixed;
        top: 0;
        left: 0;
        pointer-events: none;
    }
</style>
</head>

<body>

<h1>💛 ¡Feliz Día de la Amistad! 💛</h1>
<p>Gracias por cada risa, cada consejo y cada momento inolvidable.  
Nuestra amistad es de las mejores cosas que tengo. ✨</p>

<button onclick="celebrar()">Celebrar 🎉</button>

<canvas id="confetti"></canvas>

<script>
function celebrar() {
    // Corazones
    for (let i = 0; i < 40; i++) {
        let corazon = document.createElement("div");
        corazon.classList.add("corazon");
        corazon.innerHTML = "💖";
        corazon.style.left = Math.random() * 100 + "vw";
        corazon.style.animationDuration = (Math.random() * 3 + 3) + "s";
        document.body.appendChild(corazon);

        setTimeout(() => {
            corazon.remove();
        }, 6000);
    }

    lanzarConfetti();
}

// Confetti simple
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particulas = [];

function lanzarConfetti() {
    for (let i = 0; i < 100; i++) {
        particulas.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height - canvas.height,
            size: Math.random() * 8 + 4,
            speed: Math.random() * 3 + 2
        });
    }
}

function animar() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    particulas.forEach((p, i) => {
        ctx.fillStyle = `hsl(${Math.random()*360}, 100%, 60%)`;
        ctx.fillRect(p.x, p.y, p.size, p.size);
        p.y += p.speed;

        if (p.y > canvas.height) {
            particulas.splice(i, 1);
        }
    });

    requestAnimationFrame(animar);
}

animar();
</script>

</body>
</html>
