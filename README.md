
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>浪漫的照片画廊</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            color: #333;
            text-align: center;
            font-family: 'Georgia', serif;
            transition: background-color 0.5s;
        }
        button {
            padding: 15px 30px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background: rgba(255, 255, 255, 0.8);
            color: #333;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            transition: background-color 0.3s, transform 0.2s;
        }
        button:active { /* 使用 :active 状态代替 :hover 状态 */
            background-color: rgba(255, 255, 255, 1);
            transform: scale(1.05);
        }
        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        input[type="file"] {
            margin-top: 20px;
        }
      .image-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 20px;
        }
        img {
            max-width: 150px;
            max-height: 150px;
            margin: 10px;
            border: 2px solid #fff;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
    </style>
</head>
<body>

    <h1>让我们的时光更加多彩</h1>
    <button id="colorButton">点击我变换颜色!</button>
    <input type="file" id="imageUploader" accept="image/*" multiple>

    <div class="image-container" id="imageContainer"></div>

    <script>
        const colors = [
            '#FF5733',
            '#33FF57',
            '#3357FF',
            '#FF33A1',
            '#F1C40F',
            '#8E44AD',
            '#E67E22',
            '#FFC300',
            '#DAF7A6',
            '#C70039'
        ];

        const button = document.getElementById('colorButton');
        const imageUploader = document.getElementById('imageUploader');
        const imageContainer = document.getElementById('imageContainer');

        button.addEventListener('click', () => {
            const randomColor = colors[Math.floor(Math.random() * colors.length)];
            document.body.style.backgroundColor = randomColor;
        });

        imageUploader.addEventListener('change', (event) => {
            const files = event.target.files;
            imageContainer.innerHTML = ''; // 清空之前显示的图片

            Array.from(files).forEach(file => {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    imageContainer.appendChild(img);
                }
                reader.readAsDataURL(file);
            });
        });
    </script>

</body>
</html>
