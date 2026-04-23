# charlotteT123.github.io

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Values Card Sort – Young Enterprise</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=DM+Serif+Display&display=swap');
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'DM Sans', sans-serif;
    background: #f7f7f3;
    color: #111;
    padding: 24px 16px;
    min-height: 100vh;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
  }

  .header {
    margin-bottom: 24px;
  }

  .header h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 28px;
    margin-bottom: 6px;
  }

  .header p {
    font-size: 14px;
    color: #555;
    line-height: 1.5;
    max-width: 560px;
  }

  .counter-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-top: 12px;
  }

  .counter {
    background: #fff;
    border: 1.5px solid #ddd;
    border-radius: 8px;
    padding: 6px 14px;
    font-size: 14px;
    color: #555;
  }

  .counter span {
    font-weight: 600;
    color: #111;
  }

  .counter.full span {
    color: #3B6D11;
  }

  .filter-row {
    display: flex;
    gap: 8px;
    margin-bottom: 20px;
    flex-wrap: wrap;
  }

  .filter-btn {
    padding: 6px 14px;
    border-radius: 99px;
    border: 1.5px solid #ddd;
    background: #fff;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 500;
    color: #555;
    cursor: pointer;
    transition: all 0.15s;
  }

  .filter-btn:hover { background: #f0f0ea; }
  .filter-btn.active { background: #fff; color: #111; border-color: #888; }
  .filter-btn.active.econ { background: #EAF3DE; color: #27500A; border-color: #639922; }
  .filter-btn.active.env  { background: #E6F1FB; color: #0C447C; border-color: #378ADD; }
  .filter-btn.active.soc  { background: #EEEDFE; color: #3C3489; border-color: #534AB7; }

  .board {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 32px;
  }

  @media (max-width: 560px) {
    .board { grid-template-columns: 1fr; }
  }

  .col-header {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: #888;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .badge {
    background: #eee;
    border-radius: 99px;
    padding: 2px 9px;
    font-size: 11px;
    color: #666;
  }

  .badge.full {
    background: #EAF3DE;
    color: #27500A;
  }

  .cards-grid {
    display: flex;
    flex-direction: column;
    gap: 8px;
    min-height: 100px;
  }

  .empty-state {
    border: 1.5px dashed #ddd;
    border-radius: 10px;
    padding: 24px;
    text-align: center;
    font-size: 13px;
    color: #aaa;
  }

  .card {
    background: #fff;
    border: 1.5px solid #e0e0e0;
    border-radius: 10px;
    padding: 14px 14px 14px 16px;
    cursor: pointer;
    transition: all 0.15s;
    user-select: none;
  }

  .card:hover { border-color: #bbb; background: #fafafa; transform: translateY(-1px); }

  .card.econ { border-left: 4px solid #639922; }
  .card.env  { border-left: 4px solid #378ADD; }
  .card.soc  { border-left: 4px solid #534AB7; }

  .card.selected {
    background: #EAF3DE;
    border-color: #639922;
  }

  .card.selected .card-name { color: #27500A; }
  .card.selected .card-cat  { color: #3B6D11; }
  .card.selected .card-desc { color: #4a7a20; }

  .card-cat {
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    color: #999;
    margin-bottom: 3px;
  }

  .card.econ .card-cat { color: #3B6D11; }
  .card.env  .card-cat { color: #185FA5; }
  .card.soc  .card-cat { color: #3C3489; }

  .card-name {
    font-size: 16px;
    font-weight: 600;
    color: #111;
    margin-bottom: 3px;
  }

  .card-desc {
    font-size: 12px;
    color: #666;
    line-height: 1.4;
  }

  .divider {
    border: none;
    border-top: 1.5px solid #e0e0e0;
    margin: 28px 0;
  }

  .reflect-section h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    margin-bottom: 6px;
  }

  .reflect-section > p {
    font-size: 13px;
    color: #555;
    margin-bottom: 20px;
  }

  .reflect-q {
    margin-bottom: 16px;
  }

  .reflect-q label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: #333;
    margin-bottom: 6px;
  }

  .reflect-q textarea {
    width: 100%;
    border: 1.5px solid #ddd;
    border-radius: 8px;
    padding: 10px 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    color: #111;
    background: #fff;
    resize: vertical;
    min-height: 72px;
    line-height: 1.5;
    transition: border-color 0.15s;
  }

  .reflect-q textarea:focus {
    outline: none;
    border-color: #639922;
  }

  .selected-summary {
    background: #fff;
    border: 1.5px solid #ddd;
    border-radius: 10px;
    padding: 14px 16px;
    margin-bottom: 20px;
    font-size: 13px;
    color: #555;
  }

  .selected-summary strong { color: #111; display: block; margin-bottom: 6px; font-size: 13px; }

  .pill {
    display: inline-block;
    background: #EAF3DE;
    border: 1px solid #639922;
    border-radius: 99px;
    padding: 2px 10px;
    margin: 2px;
    font-size: 12px;
    font-weight: 500;
    color: #27500A;
  }

  .warning {
    background: #FFF8E6;
    border: 1.5px solid #EF9F27;
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 13px;
    color: #633806;
    margin-bottom: 16px;
    display: none;
  }
</style>
</head>
<body>
<div class="container">

  <div class="header">
    <h1>Values Card Sort</h1>
    <p>As a group, discuss each value and click to add it to your Top 5. You must choose exactly 5 — so talk it through before you commit!</p>
    <div class="counter-row">
      <div class="counter" id="counter">Selected: <span id="count">0</span> / 5</div>
    </div>
  </div>

  <div class="filter-row">
    <button class="filter-btn active" onclick="setFilter('all', this)">All values</button>
    <button class="filter-btn econ" onclick="setFilter('econ', this)">Economic</button>
    <button class="filter-btn env"  onclick="setFilter('env', this)">Environmental</button>
    <button class="filter-btn soc"  onclick="setFilter('soc', this)">Social</button>
  </div>

  <div class="board">
    <div>
      <div class="col-header">All values <span class="badge" id="pool-badge">20</span></div>
      <div class="cards-grid" id="pool"></div>
    </div>
    <div>
      <div class="col-header">Our top 5 <span class="badge" id="top5-badge">0</span></div>
      <div class="cards-grid" id="top5"><div class="empty-state">Click a card to add it here</div></div>
    </div>
  </div>

  <hr class="divider">

  <div class="reflect-section">
    <h2>Reflect as a group</h2>
    <p>Once you've agreed on your top 5, answer these questions together.</p>

    <div class="selected-summary" id="summary" style="display:none">
      <strong>Your top 5 values:</strong>
      <div id="pills"></div>
    </div>

    <div class="reflect-q">
      <label>Why do these 5 values fit your business?</label>
      <textarea id="q1" placeholder="Write your group's reasoning here…"></textarea>
    </div>
    <div class="reflect-q">
      <label>Name a value you left out — and why it didn't make the cut</label>
      <textarea id="q2" placeholder="e.g. We chose not to include 'Profit' because our primary goal is community impact…"></textarea>
    </div>
    <div class="reflect-q">
      <label>Which of these will you mention in your mission statement?</label>
      <textarea id="q3" placeholder="Think about which values best describe who you are and what you do…"></textarea>
    </div>

    <div class="warning" id="warning">Please select at least one value before sending.</div>
  </div>

</div>

<script>
const values = [
  { id:1,  name:'Profit',          cat:'econ', label:'Economic',      desc:'Generating a financial return that keeps the business going' },
  { id:2,  name:'Growth',          cat:'econ', label:'Economic',      desc:'Expanding reach, revenue, or impact over time' },
  { id:3,  name:'Innovation',      cat:'econ', label:'Economic',      desc:'Finding new ways to solve problems or create value' },
  { id:4,  name:'Efficiency',      cat:'econ', label:'Economic',      desc:'Getting the best results with minimal waste of time or money' },
  { id:5,  name:'Quality',         cat:'econ', label:'Economic',      desc:'Delivering products or services that meet a high standard' },
  { id:6,  name:'Value for money', cat:'econ', label:'Economic',      desc:'Giving customers a fair return on what they spend' },
  { id:7,  name:'Kaitiakitanga',   cat:'env',  label:'Environmental', desc:'Guardianship and care for the natural world' },
  { id:8,  name:'Sustainability',  cat:'env',  label:'Environmental', desc:'Operating in a way that can continue without harming the planet' },
  { id:9,  name:'Zero waste',      cat:'env',  label:'Environmental', desc:'Minimising materials sent to landfill' },
  { id:10, name:'Locally sourced', cat:'env',  label:'Environmental', desc:'Using materials and suppliers from close to home' },
  { id:11, name:'Renewable',       cat:'env',  label:'Environmental', desc:'Choosing energy and materials that can be replenished' },
  { id:12, name:'Circular design', cat:'env',  label:'Environmental', desc:'Making products that can be reused, repaired, or recycled' },
  { id:13, name:'Community',       cat:'soc',  label:'Social',        desc:'Contributing positively to the people around us' },
  { id:14, name:'Whānau',          cat:'soc',  label:'Social',        desc:'Caring for each other and those we serve' },
  { id:15, name:'Fairness',        cat:'soc',  label:'Social',        desc:'Treating everyone equally and without bias' },
  { id:16, name:'Transparency',    cat:'soc',  label:'Social',        desc:'Being open and honest about how the business operates' },
  { id:17, name:'Inclusivity',     cat:'soc',  label:'Social',        desc:'Welcoming people of all backgrounds and identities' },
  { id:18, name:'Integrity',       cat:'soc',  label:'Social',        desc:'Doing the right thing even when no one is watching' },
  { id:19, name:'Manaakitanga',    cat:'soc',  label:'Social',        desc:'Showing respect, generosity, and care for others' },
  { id:20, name:'Empowerment',     cat:'soc',  label:'Social',        desc:'Helping others grow, lead, and reach their potential' },
];

let selected = new Set();
let currentFilter = 'all';

function setFilter(f, btn) {
  currentFilter = f;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  render();
}

function toggle(id) {
  if (selected.has(id)) {
    selected.delete(id);
  } else {
    if (selected.size >= 5) return;
    selected.add(id);
  }
  render();
}

function render() {
  const poolEl = document.getElementById('pool');
  const top5El = document.getElementById('top5');
  const countEl = document.getElementById('count');
  const counterEl = document.getElementById('counter');
  const poolBadge = document.getElementById('pool-badge');
  const top5Badge = document.getElementById('top5-badge');
  const summary = document.getElementById('summary');
  const pills = document.getElementById('pills');

  countEl.textContent = selected.size;
  if (selected.size >= 5) counterEl.classList.add('full'); else counterEl.classList.remove('full');

  const filtered = values.filter(v => currentFilter === 'all' || v.cat === currentFilter);
  const unselected = filtered.filter(v => !selected.has(v.id));
  const sel = values.filter(v => selected.has(v.id));

  poolBadge.textContent = unselected.length;
  top5Badge.textContent = sel.length;
  if (sel.length >= 5) top5Badge.classList.add('full'); else top5Badge.classList.remove('full');

  poolEl.innerHTML = unselected.length === 0
    ? '<div class="empty-state">All visible cards selected</div>'
    : unselected.map(v => cardHTML(v, false)).join('');

  top5El.innerHTML = sel.length === 0
    ? '<div class="empty-state">Click a card to add it here</div>'
    : sel.map(v => cardHTML(v, true)).join('');

  if (sel.length > 0) {
    summary.style.display = 'block';
    pills.innerHTML = sel.map(v => `<span class="pill">${v.name}</span>`).join('');
  } else {
    summary.style.display = 'none';
  }
}

function cardHTML(v, sel) {
  return `<div class="card ${v.cat}${sel ? ' selected' : ''}" onclick="toggle(${v.id})">
    <div class="card-cat">${v.label}</div>
    <div class="card-name">${v.name}</div>
    <div class="card-desc">${v.desc}</div>
  </div>`;
}

render();
</script>
</body>
</html>
