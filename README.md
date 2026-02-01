<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Valentine Question</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #ffe6ec;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
            overflow: hidden; /* keep button inside screen */
        }
        .container {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            position: relative;
        }
        button {
            padding: 10px 20px;
            margin: 10px;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: transform 0.3s ease, left 0.3s ease, top 0.3s ease;
            position: relative;
        }
        .yes {
            background-color: #ff7fa8;
            color: white;
        }
        .no {
            background-color: #bfbfbf;
        }
    </style>
</head>
<body>

<div class="container">
    <img id="gifImage" src="https://i.imgur.com/919T2gN.gif" 
         alt="Cute Valentine GIF" 
         width="200">

    <h2 id="questionText">Will you be my Valentine? 💖</h2>

    <button id="yesBtn" class="yes" onclick="sayYes()">Yes</button>
    <button id="noBtn" class="no" onclick="shrinkAndGrow()">No</button>
</div>

<script>
    let yesScale = 1;
    let noScale = 1;

    const phrases = [
      "No",
      "Are you sure?",
      "Really sure?",
      "Think again!",
      "Last chance!",
      "Surely not?",
      "You might regret this!",
      "Give it another thought!",
      "Are you absolutely certain?",
      "This could be a mistake!",
      "Have a heart!",
      "Don't be so cold!",
      "Change of heart?",
      "Wouldn't you reconsider?",
      "Is that your final answer?",
      "You're breaking my heart ;(",
    ];

    let phraseIndex = 0;

    function shrinkAndGrow() {
        // scale behavior
        yesScale += 0.2;
        noScale -= 0.1;
        if (noScale < 0.3) noScale = 0.3;

        document.getElementById("yesBtn").style.transform = `scale(${yesScale})`;
        document.getElementById("noBtn").style.transform = `scale(${noScale})`;

        // text change behavior
        document.getElementById("questionText").innerText = phrases[phraseIndex];
        phraseIndex = (phraseIndex + 1) % phrases.length;

        // random movement of No button
        moveNoButton();
    }

    function moveNoButton() {
        const noBtn = document.getElementById("noBtn");
        const container = document.querySelector(".container");

        const maxX = container.clientWidth - 120; 
        const maxY = container.clientHeight - 60;

        const randomX = Math.random() * maxX;
        const randomY = Math.random() * maxY;

        noBtn.style.position = "absolute";
        noBtn.style.left = randomX + "px";
        noBtn.style.top = randomY + "px";
    }

    function sayYes() {
        document.getElementById("questionText").innerText =
            "Yeheey I Loooveee youu Cutieee my Looooveeessss :)";

        document.getElementById("gifImage").src =
            "https://i.imgur.com/vJMwja7.gif";
    }
</script>

</body>
</html>
