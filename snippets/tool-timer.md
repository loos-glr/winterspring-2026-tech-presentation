---
marp: true
theme: glr
paginate: false
---

# Oefening Timer
### Jullie hebben 5 minuten...

---

<div class="timer-container">
  <div id="timer-display">00:00</div>
  
  <div class="controls">
    <button onclick="toggleTimer()" id="btn-toggle">▶ START</button>
    <button onclick="resetTimer()" id="btn-reset">↺ RESET</button>
  </div>
  
  <div class="progress-bar-bg">
    <div id="progress-bar-fill"></div>
  </div>
</div>

<script>
  // ========================================================
  //  CONFIGURATIE: HOE LANG DUURT DE TIMER?
  // ========================================================
  const config = {
    minutes: 5,        // Pas hier de minuten aan
    seconds: 0,        // Pas hier de seconden aan
    alertAt: 30,       // Kleur verandert naar rood bij X seconden (optioneel)
    autoStart: false   // Zet op true als hij direct moet lopen
  };

  // ========================================================
  //  LOGICA
  // ========================================================
  let totalSeconds = (config.minutes * 60) + config.seconds;
  let timeRemaining = totalSeconds;
  let interval = null;
  let isRunning = false;

  const display = document.getElementById('timer-display');
  const progFill = document.getElementById('progress-bar-fill');
  const btnToggle = document.getElementById('btn-toggle');

  // Initialisatie
  updateDisplay();
  if(config.autoStart) toggleTimer();

  function toggleTimer() {
    if (isRunning) {
      pauseTimer();
    } else {
      startTimer();
    }
  }

  function startTimer() {
    if (timeRemaining <= 0) return;
    isRunning = true;
    btnToggle.innerText = "❚❚ PAUZE";
    btnToggle.style.background = "var(--glr-dark-grey)";
    
    interval = setInterval(() => {
      timeRemaining--;
      updateDisplay();

      if (timeRemaining <= 0) {
        timerFinished();
      }
    }, 1000);
  }

  function pauseTimer() {
    isRunning = false;
    btnToggle.innerText = "▶ HERVAT";
    btnToggle.style.background = "var(--glr-black)";
    clearInterval(interval);
  }

  function resetTimer() {
    pauseTimer();
    timeRemaining = totalSeconds;
    btnToggle.innerText = "▶ START";
    
    // Reset stijlen
    display.style.color = "var(--glr-dark-grey)";
    progFill.style.backgroundColor = "var(--glr-green)";
    updateDisplay();
  }

  function timerFinished() {
    pauseTimer();
    display.innerText = "TIJD OM!";
    btnToggle.innerText = "KLAAR";
    // Visuele feedback als het klaar is
    display.style.color = "#e74c3c"; // Rood
    progFill.style.width = "100%";
    progFill.style.backgroundColor = "#e74c3c";
  }

  function updateDisplay() {
    const m = Math.floor(timeRemaining / 60);
    const s = timeRemaining % 60;
    
    // Tijd formatteren (bijv. 05:09)
    display.innerText = `${pad(m)}:${pad(s)}`;
    
    // Progress bar updaten
    const percentage = ((totalSeconds - timeRemaining) / totalSeconds) * 100;
    progFill.style.width = percentage + "%";

    // Kleur verandering bij bijna klaar
    if (timeRemaining <= config.alertAt && timeRemaining > 0) {
        display.style.color = "#e67e22"; // Oranje waarschuwing
        progFill.style.backgroundColor = "#e67e22";
    }
  }

  function pad(num) {
    return num.toString().padStart(2, '0');
  }
</script>