<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <title>Telegram Web App</title>
  </head>
  <body>
    <h1>Welcome to the Web App</h1>
    <div id="debug" style="margin-top: 20px; padding: 10px; border: 1px solid #ccc;"></div>
    <script>
      // Функция для вывода сообщений на экран
      function logMessage(message) {
          const debugDiv = document.getElementById('debug');
          const paragraph = document.createElement('p');
          paragraph.textContent = message;
          debugDiv.appendChild(paragraph);
      }
      Telegram.WebApp.ready();
      Telegram.WebApp.expand();
      Telegram.WebApp.MainButton.text = "Send Data";
      Telegram.WebApp.MainButton.setText("Send Data");
      Telegram.WebApp.MainButton.show();
      // Выводим информацию при загрузке страницы
      logMessage("Web App initialized.");
      logMessage(`Init Data: ${JSON.stringify(Telegram.WebApp.initDataUnsafe)}`);
      Telegram.WebApp.MainButton.onClick(() => {
          logMessage("MainButton clicked!");
          if (Telegram.WebApp.initDataUnsafe && Telegram.WebApp.initDataUnsafe.user) {
              const userData = {
                  user_id: Telegram.WebApp.initDataUnsafe.user.id,
                  first_name: Telegram.WebApp.initDataUnsafe.user.first_name,
              };
              logMessage(`Sending data to bot: ${JSON.stringify(userData)}`);
              Telegram.WebApp.sendData(JSON.stringify(userData));
          } else {
              logMessage("User data is not available!");
          }
      });
    </script>
  </body>
</html>

