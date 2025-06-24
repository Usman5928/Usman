# <!DOCTYPE html>
<html>
<head>
  <title>Spin the Wheel</title>
  <style>
    .wheel {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      position: relative;
      overflow: hidden;
      border: 5px solid #333;
      margin: 50px auto;
      transition: transform 4s cubic-bezier(0.17, 0.67, 0.12, 0.99);
      transform: rotate(0deg);
    }
    .section {
      position: absolute;
      width: 50%;
      height: 50%;
      transform-origin: bottom right;
      text-align: center;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    button {
      display: block;
      margin: 20px auto;
      padding: 10px 20px;
      font-size: 18px;
      background: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="wheel" id="wheel">
    <!-- Wheel sections will be added by JS -->
  </div>
  <button onclick="spinWheel()">SPIN!</button>

  <script>
    const prizes = ["Prize 1", "Prize 2", "Prize 3", "Prize 4", "Prize 5"];
    const wheel = document.getElementById("wheel");
    let deg = 0;

    // Create wheel sections
    prizes.forEach((prize, index) => {
      const section = document.createElement("div");
      section.className = "section";
      section.style.backgroundColor = `hsl(${index * (360 / prizes.length)}, 70%, 50%)`;
      section.style.transform = `rotate(${index * (360 / prizes.length)}deg)`;
      section.innerHTML = `<div style="transform: rotate(${360 / prizes.length / 2}deg)">${prize}</div>`;
      wheel.appendChild(section);
    });

    // Spin function
    function spinWheel() {
      deg = Math.floor(5000 + Math.random() * 5000);
      wheel.style.transform = `rotate(${deg}deg)`;
    }
  </script>
</body>
</html>
