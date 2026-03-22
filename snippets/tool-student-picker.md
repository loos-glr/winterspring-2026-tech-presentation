---
marp: true
theme: glr
paginate: false
---

# Random Student Picker
### Wie is er aan de beurt?

---

<div class="picker-container">
  <div id="result-display">🎲</div>
  <button id="action-btn" onclick="pickStudent()">KIES IEMAND</button>
</div>

<script>
  // ========================================================
  //  CONFIGURATIE: PLAATS HIER JE STUDENTENLIJST
  // ========================================================
  const config = {
    students: [
      "Amira", 
      "Bas", 
      "Charlotte", 
      "Daan", 
      "Esmee", 
      "Freek",
      "Giovanni",
      "Hanna"
    ],
    duration: 2000 // Hoe lang het 'husselen' duurt in ms
  };

  // ========================================================
  //  LOGICA (Hier hoef je niets aan te passen)
  // ========================================================
  let isSpinning = false;
  const display = document.getElementById('result-display');
  const btn = document.getElementById('action-btn');

  function pickStudent() {
    if (isSpinning) return;
    isSpinning = true;
    btn.disabled = true;
    btn.style.opacity = "0.5";
    
    let counter = 0;
    const intervalTime = 100;
    const totalSteps = config.duration / intervalTime;

    const interval = setInterval(() => {
      // Toon willekeurige naam tijdens het 'spinnen'
      const randomName = config.students[Math.floor(Math.random() * config.students.length)];
      display.innerText = randomName;
      
      counter++;
      
      // Klaar met spinnen?
      if (counter >= totalSteps) {
        clearInterval(interval);
        
        // De definitieve winnaar
        const winner = config.students[Math.floor(Math.random() * config.students.length)];
        display.innerText = winner;
        display.style.transform = "scale(1.2)";
        display.style.color = "var(--glr-green)"; // Jouw huisstijl kleur
        
        // Reset knop
        isSpinning = false;
        btn.disabled = false;
        btn.style.opacity = "1";
        
        setTimeout(() => {
           display.style.transform = "scale(1)";
           display.style.color = "var(--glr-dark-grey)";
        }, 3000);
      }
    }, intervalTime);
  }
</script>