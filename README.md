<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>พลุวันวาเลนไทน์</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            overflow: hidden;
            text-align: center;
        }

        .letter {
            width: 70%;
            max-width: 300px;
            height: 200px;
            margin: 50px auto;
            background: linear-gradient(145deg, #ff5c8e, #ff8ca1);
            border-radius: 20px;
            cursor: pointer;
            position: relative;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            transition: all 0.3s ease-in-out;
        }

        .letter:hover {
            transform: scale(1.05);
        }

        .letter::before {
            content: '❤️';
            font-size: 48px;
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
        }

        /* พลุ (Fireworks) */
        .firework {
            position: absolute;
            border-radius: 50%;
            background-color: #ff3366;
            opacity: 0;
            animation: explode 3s ease-out forwards;
        }

        @keyframes explode {
            0% {
                transform: scale(0) translate(0, 0);
                opacity: 1;
            }
            50% {
                transform: scale(1) translate(var(--x), var(--y));
                opacity: 0.7;
            }
            100% {
                transform: scale(0) translate(var(--x), var(--y));
                opacity: 0;
            }
        }

        /* ข้อความ */
        .message {
            display: none;
            font-size: 24px;
            margin-top: 30px;
            color: #ff6699;
            animation: fadeIn 2s ease-out;
            text-shadow: 1px 1px 5px rgba(0, 0, 0, 0.3);
        }

        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        /* ปรับขนาดข้อความสำหรับมือถือ */
        @media (max-width: 600px) {
            .letter {
                width: 80%;
                max-width: 280px;
                height: 180px;
            }

            .letter::before {
                font-size: 36px;
            }

            .message {
                font-size: 22px;
            }
        }

    </style>
</head>
<body>

    <div class="letter" onclick="openLetter()">
        <div class="inner-text">คลิกที่ซองจดหมาย</div>
    </div>

    <!-- ข้อความ -->
    <div class="message">
        วาเลนไทน์นี้ อยากให้รู้ว่า ทุกวันที่ได้อยู่กับหนูคือความสุข หนูคือคนที่สำคัญที่สุดในชีวิต
         
        เค้าอยากอยู่เคียงข้างเสมอ ขอบคุณที่รักกัน ขอบคุณที่เอาใจใส่ และขอบคุณที่ทำให้เค้ารู้
        
        ว่ารักที่ดีมันเป็นยังไง 
        
        รักหนูที่สุดเลยนะ!
    </div>

    <script>
        function openLetter() {
            // พลุระเบิดเต็มหน้าจอจากกลาง
            const centerX = window.innerWidth / 2;
            const centerY = window.innerHeight / 2;

            // สร้างพลุระเบิด 100 ลูก
            for (let i = 0; i < 100; i++) {
                const firework = document.createElement('div');
                firework.classList.add('firework');
                
                // Randomly set size of firework
                const size = Math.random() * 10 + 10;
                firework.style.width = `${size}px`;
                firework.style.height = `${size}px`;

                // Randomly set the direction of explosion
                const angle = Math.random() * 360;
                const distance = Math.random() * 300 + 150;

                const x = distance * Math.cos(angle);
                const y = distance * Math.sin(angle);

                // Set custom CSS variables for explosion
                firework.style.setProperty('--x', `${x}px`);
                firework.style.setProperty('--y', `${y}px`);

                // กำหนดตำแหน่งของพลุให้เริ่มที่กลางหน้าจอ
                firework.style.left = `${centerX}px`;
                firework.style.top = `${centerY}px`;

                document.body.appendChild(firework);

                // ลบพลุหลังจากแอนิเมชันเสร็จ
                setTimeout(() => {
                    firework.remove();
                }, 3000);
            }

            // แสดงข้อความหลังจากพลุระเบิด
            setTimeout(function() {
                document.querySelector('.message').style.display = 'block';
            }, 3000);
        }
    </script>

</body>
</html>
