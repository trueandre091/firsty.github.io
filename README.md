<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <title>Telegram Web App</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 20px;
        padding: 20px;
        background-color: #f9f9f9;
      }
      h1 {
        color: #333;
      }
      button {
        padding: 10px 20px;
        font-size: 16px;
        background-color: #0088cc;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
      }
      button:hover {
        background-color: #006b8c;
      }
      #user-info {
        margin-top: 20px;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 5px;
      }
    </style>
  </head>
  <body>
    <h1>Добро пожаловать в Telegram Web App</h1>
    <button id="whoAmIButton">Кто я?</button>
    <div id="user-info"></div>

    <script>
      let tg = window.Telegram.WebApp;
      
      // Функция для вывода данных о пользователе
      function displayUserData() {
        const userData = {
          user_id: Telegram.WebApp.initDataUnsafe?.user?.id || "Unknown",
          first_name: Telegram.WebApp.initDataUnsafe?.user?.first_name || "Unknown",
        };

        // Отображаем данные
        const userInfoDiv = document.getElementById('user-info');
        userInfoDiv.innerHTML = `
          <p><strong>Ваш ID:</strong> ${userData.user_id}</p>
          <p><strong>Ваше имя:</strong> ${userData.first_name}</p>
        `;
      }

      // Инициализация Web App
      tg.ready();
      tg.expand();
      tg.MainButton.text = "Отправить данные";
      tg.MainButton.show();

      // Обработчик нажатия на кнопку "Кто я?"
      document.getElementById('whoAmIButton').addEventListener('click', function() {
        displayUserData();
      });
    </script>
  </body>
</html>


