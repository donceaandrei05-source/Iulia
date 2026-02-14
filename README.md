# Iulia[index.html](https://github.com/user-attachments/files/25309262/index.html)
<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<title>My Valentine 💖</title>

<style>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    font-family: Arial, sans-serif;
    overflow: hidden;
}

body.shake {
    animation: shake 0.4s;
}

@keyframes shake {
    0% { transform: translate(0); }
    25% { transform: translate(-5px, 5px); }
    50% { transform: translate(5px, -5px); }
    75% { transform: translate(-5px, -5px); }
    100% { transform: translate(0); }
}

.card {
    background: white;
    padding: 40px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    max-width: 420px;
    position: relative;
}

h1 { color: #ff4d6d; }

p {
    font-size: 18px;
    min-height: 60px;
}

button {
    font-size: 18px;
    padding: 12px 25px;
    margin: 10px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    transition: all 0.3s ease;
}

#yes {
    background: #ff4d6d;
    color: white;
}

#yes.pulse {
    animation: pulse 0.8s infinite;
    box-shadow: 0 0 20px rgba(255,77,109,0.8);
}

@keyframes pulse {
    0% { transform: scale(1); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
}

#no {
    background: #ccc;
}

/* inimioare */
.heart {
    position: absolute;
    color: #ff4d6d;
    font-size: 20px;
    animation: floatUp 2s ease-out forwards;
}

@keyframes floatUp {
    from { opacity: 1; transform: translateY(0) scale(1); }
    to { opacity: 0; transform: translateY(-150px) scale(1.5); }
}
</style>
</head>

<body>

<div class="card" id="card">
    <h1>💖 Iulia 💖</h1>

    <p id="message">
        Vrei să fii <strong>Valentina mea</strong>? 🌹
    </p>

    <button id="yes" onclick="yesClicked()">DA 💕</button>
    <button id="no" onclick="noClicked()">NU 🙈</button>
</div>

<audio id="loveSound">
    <source src="https://www.soundjay.com/human/kiss-1.mp3" type="audio/mpeg">
</audio>

<script>
let noCount = 0;

const noMessages = [
    "Sachyo, stiu ca vrei",
    "Iti pute bluza",
    "Cea mai imputita bluza",
    "SAAACHYYYOOOOOOO",
    "BAAAAAAA SPALA BLUZA",
    "GETYOooooooo",
    "Doar apasa DA",
    "Auzi?",
    "Stiai ca",
    "iti pute bluza?",
    "Bei bluza stiu ca vrei sa fii valentina mea",
    "Ia gata",
    "Cacacioasooo",
    "Pe bune acum apasa DA"
];

function noClicked() {
    const msg = document.getElementById("message");
    const yesBtn = document.getElementById("yes");
    const body = document.body;

    if (noCount < noMessages.length) {
        msg.innerText = noMessages[noCount];
        noCount++;
    }

    // efect pe DA
    yesBtn.classList.add("pulse");
    yesBtn.style.transform = `scale(${1 + noCount * 0.08})`;

    // shake ecran la ultimele mesaje
    if (noCount >= 10) {
        body.classList.add("shake");
        setTimeout(() => body.classList.remove("shake"), 400);
    }
}

function yesClicked() {
    document.getElementById("loveSound").play();
    explodeHearts();

    setTimeout(() => {
        document.body.innerHTML = `
        <div style="
            display:flex;
            justify-content:center;
            align-items:center;
            height:100vh;
            background:linear-gradient(135deg,#ff9a9e,#fad0c4);
            text-align:center;
            padding:30px;
            font-family:Arial;
        ">
            <h1 style="color:#ff4d6d; max-width:650px;">
                💖 Good Boy 💖
            </h1>
        </div>`;
    }, 800);
}

function explodeHearts() {
    for (let i = 0; i < 30; i++) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.innerText = "💖";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.top = window.innerHeight - 100 + "px";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 2000);
    }
}
</script>

</body>
</html>
