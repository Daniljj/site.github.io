<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram Web App Example</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            color: #333;
            text-align: center;
            padding: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Добро пожаловать в наше веб-приложение!</h1>
    <button id="sendData">Отправить данные на сервер</button>
    <script>
        // Инициализация приложения
        window.Telegram.WebApp.ready();
        // Получаем данные о пользователе
        const userId = window.Telegram.WebApp.user.id;
        console.log(`ID пользователя: ${userId}`);
        // Обработка нажатия кнопки
        document.getElementById('sendData').onclick = async function() {
            const response = await fetch('/api/data', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ user_id: userId }),
            });
            const data = await response.json();
            alert(data.message); // Выводим ответ от сервера
        };
        // Обработка события закрытия приложения
        window.Telegram.WebApp.onEvent('close', function() {
            console.log('Приложение закрыто');
        });
    </script>
</body>
</html>
