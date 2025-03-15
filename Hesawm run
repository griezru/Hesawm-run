<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>ماجراجویی حسام</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            overflow: hidden;
            touch-action: none;
            background: linear-gradient(45deg, #1a1a2e, #16213e);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        #gameContainer {
            position: relative;
            width: 100vw;
            height: 100vh;
            overflow: hidden;
        }

        .character {
            position: absolute;
            transition: all 0.15s ease-out;
            display: flex;
            flex-direction: column;
            align-items: center;
            filter: drop-shadow(0 3px 8px rgba(0,0,0,0.3));
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #fff;
            position: relative;
            animation: float 3s ease-in-out infinite;
        }

        .avatar::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 1.5px solid rgba(255,255,255,0.8);
            animation: pulse 2s infinite;
        }

        #hesam .avatar {
            background: #3498db url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="%23ffffff"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/><path d="M12 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/></svg>') center/60% no-repeat;
        }

        #omid .avatar { background-color: #e74c3c; }
        #yazdan .avatar { background-color: #9b59b6; }
        #shayan .avatar { background-color: #f39c12; }

        .name-tag {
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 10px;
            margin-top: 3px;
            white-space: nowrap;
        }

        .letter {
            position: absolute;
            width: 35px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            opacity: 0;
            transform: scale(0);
            transition: all 0.3s ease;
            filter: drop-shadow(0 3px 6px rgba(255,50,50,0.4));
        }

        .letter::before {
            content: '❤️';
            position: absolute;
            font-size: 35px;
            filter: drop-shadow(0 0 6px rgba(255,0,0,0.4));
        }

        .letter span {
            position: relative;
            top: -2px;
            color: white;
            text-shadow: 0 0 6px rgba(0,0,0,0.5);
        }

        .letter.active {
            opacity: 1;
            transform: scale(1);
            animation: heartbeat 1.5s infinite;
        }

        #ui {
            position: fixed;
            top: 12px;
            left: 12px;
            color: white;
            padding: 8px 12px;
            background: rgba(0,0,0,0.7);
            border-radius: 8px;
            backdrop-filter: blur(4px);
            font-size: 12px;
        }

        #gameOver {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0,0,0,0.9);
            color: white;
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            display: none;
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255,255,255,0.1);
            max-width: 90%;
        }

        button {
            background: #3498db;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            margin-top: 12px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 12px;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        @keyframes pulse {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(1.3); opacity: 0; }
        }
    </style>
</head>
<body>
    <div id="gameContainer">
        <div id="ui">
            <span>❤️ × <span id="lives">3</span></span> | 
            <span>مرحله: <span id="level">1</span></span>
        </div>
        
        <div id="hesam" class="character">
            <div class="avatar"></div>
            <div class="name-tag">حسام</div>
        </div>
        
        <div id="omid" class="character">
            <div class="avatar"></div>
            <div class="name-tag">امید</div>
        </div>
        
        <div id="yazdan" class="character">
            <div class="avatar"></div>
            <div class="name-tag">یزدان</div>
        </div>
        
        <div id="shayan" class="character">
            <div class="avatar"></div>
            <div class="name-tag">شایان</div>
        </div>

        <div class="letter" data-order="1" style="left: 20%; top: 20%;"><span>ح</span></div>
        <div class="letter" data-order="2" style="left: 70%; top: 30%;"><span>س</span></div>
        <div class="letter" data-order="3" style="left: 40%; top: 60%;"><span>ا</span></div>
        <div class="letter" data-order="4" style="left: 60%; top: 80%;"><span>م</span></div>

        <div id="gameOver">
            <h2>☠️ بازی تمام شد!</h2>
            <p>مرحله نهایی: <span id="finalLevel">1</span></p>
            <button onclick="resetGame()">دوباره شروع کن</button>
        </div>
    </div>

    <script>
        const hesam = document.getElementById('hesam');
        const letters = document.querySelectorAll('.letter');
        const livesElement = document.getElementById('lives');
        const levelElement = document.getElementById('level');
        const gameOverScreen = document.getElementById('gameOver');
        const finalLevelElement = document.getElementById('finalLevel');

        const enemies = [
            {
                element: document.getElementById('omid'),
                speed: 2.3,
                startPos: { x: '5%', y: '5%' }
            },
            {
                element: document.getElementById('yazdan'),
                speed: 1.6,
                startPos: { x: '95%', y: '5%' }
            },
            {
                element: document.getElementById('shayan'),
                speed: 3.0,
                startPos: { x: '5%', y: '95%' }
            }
        ];

        let currentLetter = 0;
        let lives = 3;
        let level = 1;
        let isGameActive = true;
        let touchX = window.innerWidth / 2;
        let touchY = window.innerHeight / 2;
        let isPushed = false;
        let pushVelocity = { x: 0, y: 0 };
        const pushForce = 12;
        let pushDuration = 0;

        function initPositions() {
            hesam.style.left = '50%';
            hesam.style.top = '50%';
            enemies.forEach(enemy => {
                enemy.element.style.left = enemy.startPos.x;
                enemy.element.style.top = enemy.startPos.y;
            });
            letters.forEach(letter => letter.classList.remove('active'));
            letters[0].classList.add('active');
        }

        document.addEventListener('touchstart', handleTouch);
        document.addEventListener('touchmove', handleTouch);

        function handleTouch(e) {
            if (!isGameActive || isPushed) return;
            e.preventDefault();
            const touch = e.touches[0];
            touchX = touch.clientX - hesam.offsetWidth / 2;
            touchY = touch.clientY - hesam.offsetHeight / 2;
        }

        function update() {
            if (!isGameActive) return;

            if (!isPushed) {
                hesam.style.left = `${touchX}px`;
                hesam.style.top = `${touchY}px`;
            } else {
                touchX += pushVelocity.x;
                touchY += pushVelocity.y;
                hesam.style.left = `${touchX}px`;
                hesam.style.top = `${touchY}px`;
                pushDuration-- > 0 || (isPushed = false);
            }

            const hesamRect = hesam.getBoundingClientRect();

            enemies.forEach(enemy => {
                const enemyRect = enemy.element.getBoundingClientRect();
                const dx = hesamRect.left - enemyRect.left;
                const dy = hesamRect.top - enemyRect.top;
                const distance = Math.sqrt(dx*dx + dy*dy);
                
                if (distance > 8) {
                    enemy.element.style.left = `${enemyRect.left + (dx/distance)*enemy.speed}px`;
                    enemy.element.style.top = `${enemyRect.top + (dy/distance)*enemy.speed}px`;
                }

                if (checkCollision(hesamRect, enemyRect) && !isPushed) {
                    handleCollision(enemyRect);
                }
            });

            letters.forEach((letter, index) => {
                if (letter.classList.contains('active')) {
                    const letterRect = letter.getBoundingClientRect();
                    if (checkCollision(hesamRect, letterRect)) {
                        letter.classList.remove('active');
                        currentLetter++;
                        currentLetter < letters.length 
                            ? letters[currentLetter].classList.add('active')
                            : levelUp();
                    }
                }
            });

            requestAnimationFrame(update);
        }

        function checkCollision(rect1, rect2) {
            const collisionMargin = 10;
            return !(
                rect1.right < rect2.left + collisionMargin ||
                rect1.left + collisionMargin > rect2.right ||
                rect1.bottom < rect2.top + collisionMargin ||
                rect1.top + collisionMargin > rect2.bottom
            );
        }

        function handleCollision(enemyRect) {
            livesElement.textContent = --lives;
            
            const hesamRect = hesam.getBoundingClientRect();
            const pushDirection = {
                x: hesamRect.left - enemyRect.left,
                y: hesamRect.top - enemyRect.top
            };
            const length = Math.sqrt(pushDirection.x**2 + pushDirection.y**2);
            
            pushVelocity = {
                x: (pushDirection.x / length) * pushForce,
                y: (pushDirection.y / length) * pushForce
            };
            
            isPushed = true;
            pushDuration = 15;

            lives <= 0 && gameOver();
        }

        function levelUp() {
            levelElement.textContent = ++level;
            currentLetter = 0;
            letters.forEach(letter => {
                letter.style.left = `${Math.random() * 85 + 7.5}%`;
                letter.style.top = `${Math.random() * 85 + 7.5}%`;
                letter.classList.remove('active');
            });
            letters[0].classList.add('active');
            enemies.forEach(enemy => enemy.speed *= 1.08);
        }

        function gameOver() {
            isGameActive = false;
            finalLevelElement.textContent = level;
            gameOverScreen.style.display = 'block';
        }

        function resetGame() {
            lives = 3;
            level = 1;
            currentLetter = 0;
            isGameActive = true;
            isPushed = false;
            livesElement.textContent = lives;
            levelElement.textContent = level;
            gameOverScreen.style.display = 'none';
            enemies.forEach(enemy => enemy.speed = enemy.originalSpeed);
            initPositions();
            update();
        }

        enemies.forEach(enemy => enemy.originalSpeed = enemy.speed);
        initPositions();
        update();
    </script>
</body>
</html>
