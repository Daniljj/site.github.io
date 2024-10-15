<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram Web App</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
</head>
<body>
    <h1>Добро пожаловать в ваше веб-приложение!</h1>
    <script>
        // Настройка цвета фона
        document.body.style.backgroundColor = '#f0f0f0';
        // Получаем данные о пользователе
        const userId = window.Telegram.WebApp.user.id;
        console.log(`ID пользователя: ${userId}`);
        // Обработка событий закрытия приложения
        window.Telegram.WebApp.onEvent('close', function() {
            console.log('Приложение закрыто');
        });
    </script>
</body>
</html>
