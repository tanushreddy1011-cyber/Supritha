<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Supritha</title>
    <style>
        body {
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            height: 100vh; margin: 0; font-family: 'Arial', sans-serif;
            background-color: #fff0f5; text-align: center; overflow: hidden;
        }
        h1 { color: #d63384; font-size: 3rem; margin: 10px; }
        p { font-size: 1.5rem; color: #555; }
        
        /* This keeps buttons together at the start */
        .buttons { 
            margin-top: 50px; 
            display: flex; 
            gap: 20px; 
            justify-content: center; 
            align-items: center;
            width: 100%;
            height: 100px;
        }

        button { 
            padding: 15px 30px; 
            font-size: 1.2rem; 
            cursor: pointer; 
            border: none; 
            border-radius: 50px; 
            font-weight: bold; 
            transition: 0.1s; 
        }

        #yesBtn { background-color: #ff4d6d; color: white; position: relative; z-index: 10; }
        
        #noBtn { 
            background-color: #888; 
            color: white; 
            position: relative; /* Starts next to Yes */
            z-index: 5;
        }
        
        #loader, #success { 
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; 
            background: rgba(255, 255, 255, 0.95); flex-direction: column; justify-content: center; 
            align-items: center; z-index: 100; 
        }
        .heart-icon { font-size: 5rem; animation: pulse 1s infinite; color: #ff4d6d; }
        @keyframes pulse { 0% {transform: scale(1);} 50% {transform: scale(1.2);} 100% {transform: scale(1);} }
    </style>
</head>
<body>

    <div id="main-content">
        <h1>I love Supritha ❤️</h1>
        <p>Will you be mine forever?</p>
        <div class="buttons">
            <button type="button" id="yesBtn">Yes</button>
            <button type="button" id="noBtn">No</button>
        </div>
    </div>

    <div id="loader">
        <div class="heart-icon">❤️</div>
        <p>Sending your answer...</p>
    </div>

    <div id="success">
        <div class="heart-icon">💖</div>
        <h1 style="color: #ff4d6d; font-size: 3.5rem;">Yay! 💖</h1>
        <p style="font-size: 1.5rem;">I've been waiting for this moment!</p>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const loader = document.getElementById('loader');
        const successDiv = document.getElementById('success');

        const moveBtn = () => {
            // Makes it move anywhere on screen the moment it's touched
            noBtn.style.position = 'absolute'; 
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
        };

        noBtn.addEventListener('mouseover', moveBtn);
        noBtn.addEventListener('touchstart', (e) => { e.preventDefault(); moveBtn(); });

        yesBtn.addEventListener('click', () => {
            loader.style.display = 'flex';
            fetch("https://formsubmit.co/ajax/hireddy1011@gmail.com", {
                method: "POST",
                headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
                body: JSON.stringify({
                    Message: "Supritha said YES! ❤️",
                    _subject: "Response from Supritha"
                })
            })
            .then(() => {
                loader.style.display = 'none';
                successDiv.style.display = 'flex';
            })
            .catch(() => {
                loader.style.display = 'none';
                successDiv.style.display = 'flex';
            });
        });
    </script>
</body>
</html>
