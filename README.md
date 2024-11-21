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
      let tg = window.Telegram.WebApp;
      // Функция для вывода сообщений на экран
      function logMessage(message) {
          const debugDiv = document.getElementById('debug');
          const paragraph = document.createElement('p');
          paragraph.textContent = message;
          debugDiv.appendChild(paragraph);
      }
      tg.ready();
      tg.expand();
      tg.MainButton.text = "Send Data";
      tg.MainButton.setText("Send Data");
      tg.MainButton.show();
      logMessage("Web App initialized.");
      logMessage(`Init Data: ${JSON.stringify(Telegram.WebApp.initDataUnsafe)}`);
      Telegram.WebApp.MainButton.onClick(() => {
        const userData = {
            user_id: Telegram.WebApp.initDataUnsafe?.user?.id || "Unknown",
            first_name: Telegram.WebApp.initDataUnsafe?.user?.first_name || "Unknown",
        };
        // Логируем данные перед отправкой
        document.body.innerHTML += `<p>Sending data: ${JSON.stringify(userData)}</p>`;
        // Отправляем данные
        Telegram.WebApp.sendData(JSON.stringify(userData));
      });
    </script>
  </body>
</html>
