<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <title>Telegram Web App</title>
  </head>
  <body>
    <h1>Welcome to the Web App</h1>
    <script>
      Telegram.WebApp.ready();
      Telegram.WebApp.expand();
      Telegram.WebApp.MainButton.text = "Send Data";
      Telegram.WebApp.MainButton.show();
      Telegram.WebApp.MainButton.onClick(function() {
        console.log('Sending data...');
        Telegram.WebApp.sendData(JSON.stringify({user_id: Telegram.WebApp.initDataUnsafe.user.id}));
      });
    </script>
  </body>
</html>
