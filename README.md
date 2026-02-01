# Ruleta-aleatoria
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Ruleta aleatoria</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    h1 {
      margin-bottom: 20px;
    }

    .ruleta {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      border: 6px solid #333;
      position: relative;
      overflow: hidden;
      transform: rotate(0deg);
      transition: transform 3s cubic-bezier(0.33, 1, 0.68, 1);
      background: conic-gradient(
        #4CAF50 0deg 180deg,
        #2196F3 180deg 360deg
      );
    }

    .opcion {
      position: absolute;
      width: 100%;
      text-align: center;
      top: 50%;
      transform: translateY(-50%);
      font-size: 18px;
      font-weight: bold;
      color: #fff;
      pointer-events: none;
    }

    .opcion.grande {
      transform: rotate(0deg) translateY(-110px);
    }

    .opcion.pequeña {
      transform: rotate(180deg) translateY(-110px);
    }

    .flecha {
      width: 0;
      height: 0;
      border-left: 15px solid transparent;
      border-right: 15px solid transparent;
      border-bottom: 25px solid #333;
      margin-bottom: 10px;
    }

    button {
      margin-top: 25px;
      padding: 12px 25px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      background: #333;
      color: #fff;
      border-radius: 6px;
    }

    button:hover {
      background: #555;
    }

    .resultado {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h1>Ruleta aleatoria</h1>

  <div class="flecha"></div>

  <div class="ruleta" id="ruleta">
    <div class="opcion grande">Cama grande</div>
    <div class="opcion pequeña">Cama pequeña</div>
  </div>

  <button onclick="girar()">Girar ruleta</button>

  <div class="resultado" id="resultado"></div>

  <script>
    let rotacion = 0;

    function girar() {
      const ruleta = document.getElementById("ruleta");
      const resultado = document.getElementById("resultado");

      // Giro aleatorio visual
      const vueltas = Math.floor(Math.random() * 3) + 4;
      const gradosExtra = Math.floor(Math.random() * 360);

      // Ajuste para que SIEMPRE caiga en cama grande
      const ajusteFinal = 90;

      rotacion += (vueltas * 360) + gradosExtra + ajusteFinal;

      ruleta.style.transform = `rotate(${rotacion}deg)`;

      resultado.textContent = "Girando...";

      setTimeout(() => {
        resultado.textContent = "Resultado: Cama grande sin emojis ni nada";
      }, 3000);
    }
  </script>

</body>
</html>
