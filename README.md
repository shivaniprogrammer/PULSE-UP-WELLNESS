# PULSE-UP-WELLNESS

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Health & Wellness Dashboard</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(135deg, #fceabb, #f8b500);
      display: flex;
      flex-direction: column;
      align-items: center;
      animation: pulseBackground 8s infinite alternate;
    }
    @keyframes pulseBackground {
      0% { filter: brightness(1); }
      100% { filter: brightness(1.1); }
    }
    h1 {
      text-align: center;
      font-size: 2rem;
      margin: 20px 0;
      animation: pulseHeading 1.5s infinite alternate;
    }
    @keyframes pulseHeading {
      0% { transform: scale(1); color:#ff6b6b; }
      100% { transform: scale(1.1); color:#ff4757; }
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 1rem;
      width: 95%;
      max-width: 1000px;
    }
    .section {
      background: rgba(255,255,255,0.85);
      backdrop-filter: blur(10px);
      padding: 1.5rem;
      border-radius: 1.5rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      animation: fadeIn 0.8s ease-in-out;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    button {
      background: #86c5ba;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 8px 14px;
      margin: 5px;
      cursor: pointer;
      transition: transform 0.2s ease, background 0.3s ease;
    }
    button:hover { transform: scale(1.05); background:#5cbdb9; }
    .progress {
      height: 20px;
      background: rgba(217,243,238,0.7);
      border-radius: 10px;
      overflow: hidden;
      margin: 10px 0;
    }
    .progress-bar {
      height: 100%;
      background: linear-gradient(90deg, #4caf50, #8bc34a);
      width: 0;
      transition: width 0.4s ease-in-out;
    }
    @keyframes waterFill {
      from { width: 0; }
      to { width: 100%; }
    }
    .breathing-circle {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      background: #a2d2ff;
      margin: auto;
    }
    .breathing-active {
      animation: breathe 8s infinite;
    }
    @keyframes breathe {
      0%,100% { transform: scale(0.8); background: #a2d2ff; }
      50% { transform: scale(1.2); background: #bde0fe; }
    }
    select, input, textarea {
      width: 100%;
      padding: 8px;
      margin: 8px 0;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    ul { list-style-type: none; padding: 0; }
  </style>
</head>
<body>
  <h1>💪 Pulse Up – Health Dashboard</h1>
  <div class="grid">
    <div class="section" id="steps">
      <h2>🚶 Steps Counter</h2>
      <p>Steps: <span id="stepCount">0</span>/5000</p>
      <div class="progress"><div class="progress-bar" id="stepProgress"></div></div>
      <button onclick="addSteps(100)">+100 Steps</button>
      <button onclick="resetSteps()">Reset</button>
    </div>

    <div class="section" id="tips">
      <h2>🥗 Nutrition Tips</h2>
      <p id="tipText">Click below to get a tip</p>
      <button onclick="showTip()">Get Tip</button>
    </div>

    <div class="section" id="mood">
      <h2>😊 Mood Journal</h2>
      <textarea id="moodInput" placeholder="How are you feeling?"></textarea>
      <button onclick="saveMood()">Save Mood</button>
      <ul id="moodList"></ul>
    </div>

    <div class="section" id="water">
      <h2>💧 Water Tracker</h2>
      <p>Glasses: <span id="waterCount">0</span>/8</p>
      <div class="progress"><div class="progress-bar" id="waterProgress"></div></div>
      <button onclick="drinkWater()">Drink Water</button>
    </div>

    <div class="section" id="bmi">
      <h2>⚖️ BMI Calculator</h2>
      <input type="number" id="weight" placeholder="Weight (kg)">
      <input type="number" id="height" placeholder="Height (cm)">
      <button onclick="calcBMI()">Calculate BMI</button>
      <p id="bmiResult"></p>
    </div>

    <div class="section" id="snacks">
      <h2>🍎 Healthy Snacks</h2>
      <p id="snackText">Click to see a snack idea</p>
      <button onclick="showSnack()">Get Snack</button>
    </div>

    <div class="section" id="breathing">
      <h2>🌬️ Breathing Exercise</h2>
      <div class="breathing-circle" id="breathingCircle"></div>
      <button onclick="startBreathing()">Start</button>
      <button onclick="stopBreathing()">Stop</button>
    </div>

    <div class="section" id="medicine">
      <h2>💊 Medicine Reminder</h2>
      <input type="text" id="medicineName" placeholder="Medicine Name">
      <input type="time" id="medicineTime">
      <button onclick="setMedicineReminder()">Set Reminder</button>
      <p id="medicineMsg"></p>
    </div>

    <div class="section" id="veggie">
      <h2>🥦 Veggie Recipes</h2>
      <select id="veggieSelect" onchange="showVeggieRecipe()">
        <option value="">Select a vegetable</option>
        <option>Broccoli</option><option>Spinach</option><option>Carrot</option><option>Tomato</option>
        <option>Potato</option><option>Cabbage</option><option>Cauliflower</option><option>Beans</option>
        <option>Peas</option><option>Corn</option><option>Bell Pepper</option><option>Onion</option>
        <option>Garlic</option><option>Sweet Potato</option><option>Zucchini</option><option>Pumpkin</option>
        <option>Beetroot</option><option>Radish</option><option>Cucumber</option><option>Lettuce</option>
        <option>Kale</option><option>Okra</option><option>Eggplant</option><option>Turnip</option>
        <option>Celery</option><option>Mushroom</option><option>Spring Onion</option><option>Leek</option>
        <option>Asparagus</option><option>Green Chilli</option>
      </select>
      <p id="recipe"></p>
    </div>

    <div class="section" id="appointment">
      <h2>👩‍⚕️ Book Appointment</h2>
      <select id="doctorSelect">
        <option>Dr. Aditi Sharma – Nutritionist</option>
        <option>Dr. Rohan Mehta – Physiotherapist</option>
        <option>Dr. Sneha Rao – General Physician</option>
        <option>Dr. Vivek Iyer – Psychologist</option>
        <option>Dr. Kavya Menon – Fitness Coach</option>
      </select>
      <input type="date" id="apptDate">
      <input type="time" id="apptTime">
      <button onclick="bookAppt()">Book</button>
      <p id="apptConfirm"></p>
    </div>
  </div>

  <script>
    let steps = localStorage.getItem('steps') ? parseInt(localStorage.getItem('steps')) : 0;
    let water = localStorage.getItem('water') ? parseInt(localStorage.getItem('water')) : 0;
    const tips = ["Eat more leafy greens", "Drink 8 glasses of water", "Limit sugar intake", "Have fruits daily", "Avoid junk food", "Chew food slowly", "Don't skip breakfast", "Stay hydrated", "Add protein to diet", "Practice mindful eating"];
    const snacks = ["Apple slices with peanut butter","Greek yogurt with berries","Carrot sticks with hummus","Roasted chickpeas","Mixed nuts","Banana with almond butter","Cucumber sandwiches","Trail mix","Smoothie bowl","Dark chocolate (small piece)"];
    const recipes = {
      'Broccoli': 'Broccoli Soup: Boil broccoli, blend with spices, serve warm.',
      'Spinach': 'Spinach Curry: Cook spinach with garlic and spices.',
      'Carrot': 'Carrot Salad: Grate carrots, add lemon & salt.',
      'Tomato': 'Tomato Soup: Boil tomatoes, blend and season.'
    };

    function updateSteps() {
      document.getElementById('stepCount').textContent = steps;
      const percent = Math.min((steps/5000)*100, 100);
      document.getElementById('stepProgress').style.width = percent + '%';
      localStorage.setItem('steps', steps);
    }
    function addSteps(count) { steps += count; updateSteps(); }
    function resetSteps() { steps = 0; updateSteps(); }
    updateSteps();

    function showTip() {
      document.getElementById('tipText').textContent = tips[Math.floor(Math.random()*tips.length)];
    }

    function saveMood() {
      const mood = document.getElementById('moodInput').value;
      if (!mood) return;
      let moods = JSON.parse(localStorage.getItem('moods')||'[]');
      moods.push(mood);
      localStorage.setItem('moods', JSON.stringify(moods));
      document.getElementById('moodInput').value = '';
      renderMoods();
    }
    function renderMoods() {
      let moods = JSON.parse(localStorage.getItem('moods')||'[]');
      document.getElementById('moodList').innerHTML = moods.map(m=>`<li>${m}</li>`).join('');
    }
    renderMoods();

    function drinkWater() {
      if (water<8) water++;
      document.getElementById('waterCount').textContent = water;
      document.getElementById('waterProgress').style.width = (water/8)*100 + '%';
      localStorage.setItem('water', water);
    }
    document.getElementById('waterCount').textContent = water;
    document.getElementById('waterProgress').style.width = (water/8)*100 + '%';

    function showVeggieRecipe() {
      const v = document.getElementById('veggieSelect').value;
      document.getElementById('recipe').textContent = recipes[v] || 'Try steaming, sautéing, or adding it to salads!';
    }

    function bookAppt() {
      const doctor = document.getElementById('doctorSelect').value;
      const date = document.getElementById('apptDate').value;
      const time = document.getElementById('apptTime').value;
      if (date && time) {
        document.getElementById('apptConfirm').textContent = `Appointment booked with ${doctor} on ${date} at ${time}.`;
      } else {
        document.getElementById('apptConfirm').textContent = 'Please select date and time';
      }
    }

    function calcBMI() {
      const w = parseFloat(document.getElementById('weight').value);
      const h = parseFloat(document.getElementById('height').value)/100;
      if (!w || !h) return;
      const bmi = (w/(h*h)).toFixed(1);
      let msg = `Your BMI is ${bmi}. `;
      if (bmi<18.5) msg += "Underweight";
      else if (bmi<24.9) msg += "Normal";
      else if (bmi<29.9) msg += "Overweight";
      else msg += "Obese";
      document.getElementById('bmiResult').textContent = msg;
    }

    function showSnack() {
      document.getElementById('snackText').textContent = snacks[Math.floor(Math.random()*snacks.length)];
    }

    function startBreathing() {
      document.getElementById('breathingCircle').classList.add('breathing-active');
    }
    function stopBreathing() {
      document.getElementById('breathingCircle').classList.remove('breathing-active');
    }

    function setMedicineReminder() {
      const name = document.getElementById('medicineName').value;
      const time = document.getElementById('medicineTime').value;
      if (!name || !time) {
        document.getElementById('medicineMsg').textContent = 'Please enter medicine name and time.';
        return;
      }
      document.getElementById('medicineMsg').textContent = `Reminder set for ${name} at ${time}`;
      alert(`⏰ Reminder set for ${name} at ${time}`);
    }
  </script>
</body>
</html>
