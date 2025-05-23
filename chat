<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <title>Cognigy Search Chat</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      background-color: #f9f9f9;
    }

    .search-bar {
      width: 300px;
      display: flex;
      align-items: center;
      border: 1px solid #ccc;
      border-radius: 25px;
      padding: 6px 10px;
      background-color: white;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    }

    .search-bar input {
      flex: 1;
      border: none;
      outline: none;
      font-size: 14px;
    }

    .search-bar button {
      background: none;
      border: none;
      cursor: pointer;
      font-size: 16px;
    }

    #webchat-container {
      width: 100%;
      height: 500px;
      display: none;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <!-- Suchleiste -->
  <div class="search-bar">
    <input type="text" id="userQuery" placeholder="Frage mich etwas...">
    <button onclick="openChat()">🔍</button>
  </div>

  <!-- Cognigy Chat Container -->
  <div id="webchat-container"></div>

  <script src="https://github.com/Cognigy/Webchat/releases/latest/download/webchat.js"></script>
  <script>
    let webchat;

    function openChat() {
      const query = document.getElementById("userQuery").value;

      if (!query) return; // Keine leeren Fragen senden

      // Chat nur einmal initialisieren
      if (!webchat) {
        initWebchat(
          "https://endpoint-trial.cognigy.ai/068564a11449495587f4bab61b4131bf8f9bb5570b9fe6677196adde275348c0",
          {
            targetElement: document.getElementById("webchat-container"),
            open: true,
            settings: {
              startBehavior: "injection",  // ⬅ direkt mit Frage starten
              startMessage: query,
              enableSendButton: true,
              enableAttachmentButton: true,
              designTemplate: "modern",
              showHeader: true
            }
          }
        ).then((w) => {
          webchat = w;
          document.getElementById("webchat-container").style.display = "block";
        });
      } else {
        webchat.sendMessage(query);
        document.getElementById("webchat-container").style.display = "block";
      }
    }

    // Enter-Taste in der Suchleiste auslösen
    document.getElementById("userQuery").addEventListener("keydown", function (e) {
      if (e.key === "Enter") {
        openChat();
      }
    });
  </script>

</body>
</html>
