<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Envelope + Letter (Open/Close on Click) with Snowfall Effect</title>
    <link rel="stylesheet" href="./style.css">
    <style>
        .snowflake {
            width: 30px;
            height: 30px;
            background-image: url('./snow.png');
            background-size: contain;
            background-repeat: no-repeat;
            position: absolute;
            animation: snowfall 10s linear infinite;
        }

        @keyframes snowfall {
            0% {
                transform: translateY(-100vh);
            }
            100% {
                transform: translateY(100vh);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="envelope-wrapper">
            <div class="envelope">
                <div class="letter">
                    <div class="text">
                        <strong>gửi chị pé</strong>
                        <br>     ----------------------------------------------------
                                Trước khi rời khỏi nhà chị pé nhớ
                                kt đồ đạc nhóa!!!
                                vd:thước,viết,căn cước công dân....
                                -------------------thi tốt nha-----------------------
                        </p>
                    </div>
                </div>
            </div>
            <div class="heart"></div>
        </div>
    </div>
    <audio id="myAudio" loop>
        <source src="./music.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>
    <script>
        const envelope = document.querySelector('.envelope-wrapper');
        envelope.addEventListener('click', () => {
            envelope.classList.toggle('flap');
            var audio = document.getElementById("myAudio");
            if (envelope.classList.contains('flap')) {
                audio.play();
            } else {
                audio.pause();
            }
        });

        function createSnowflake() {
            const snowflake = document.createElement('div');
            snowflake.classList.add('snowflake');
            snowflake.style.left = Math.random() * window.innerWidth + 'px';
            snowflake.style.animationDelay = Math.random() * 10 + 's';
            document.body.appendChild(snowflake);

            setTimeout(() => {
                snowflake.remove();
            }, 10000);
        }

        setInterval(createSnowflake, 100);
    </script>
</body>
</html>
