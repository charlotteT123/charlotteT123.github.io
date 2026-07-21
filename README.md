<!DOCTYPE html>
<html lang="en-NZ">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kai Cart Ledger — Financial Decision Simulation</title>
<style>
  :root{
    --ink:#14213D;
    --paper:#F7F5EF;
    --ledger-green:#2E5339;
    --ledger-green-light:#e7efe9;
    --gold:#C99A3F;
    --rust:#A6403D;
    --rust-light:#f7e9e8;
    --charcoal:#232323;
    --line:#d8d3c4;
    --font-display: Georgia, 'Iowan Old Style', 'Palatino Linotype', serif;
    --font-body: -apple-system, 'Segoe UI', Helvetica, Arial, sans-serif;
    --font-mono: 'Courier New', Courier, monospace;
  }

  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--ink);
    color:var(--charcoal);
    font-family:var(--font-body);
    min-height:100vh;
    display:flex;
    justify-content:center;
    padding:28px 16px 60px;
  }
  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; transition-duration:0.01ms !important;}
  }

  .rig{
    width:100%;
    max-width:640px;
  }

  /* Ticker / header */
  .ticker{
    background:var(--ink);
    color:var(--paper);
    border-radius:10px 10px 0 0;
    padding:20px 22px 16px;
    border:1px solid #2a3a63;
    border-bottom:none;
  }
  .ticker-top{
    display:flex;
    justify-content:space-between;
    align-items:baseline;
    gap:12px;
  }
  .brand{
    font-family:var(--font-display);
    font-size:1.5rem;
    letter-spacing:0.02em;
  }
  .brand span{color:var(--gold);}
  .balance-label{
    font-family:var(--font-mono);
    font-size:0.68rem;
    letter-spacing:0.12em;
    text-transform:uppercase;
    color:#9fb0d6;
    margin-bottom:2px;
  }
  .balance{
    font-family:var(--font-mono);
    font-size:1.9rem;
    font-variant-numeric:tabular-nums;
    text-align:right;
    transition:color 0.3s ease;
  }
  .balance.up{color:#7fd9a0;}
  .balance.down{color:#e08b87;}
  .stage-track{
    display:flex;
    gap:6px;
    margin-top:16px;
  }
  .stage-chip{
    flex:1;
    font-family:var(--font-mono);
    font-size:0.62rem;
    letter-spacing:0.06em;
    text-transform:uppercase;
    padding:7px 6px;
    border-radius:5px;
    text-align:center;
    background:#22305a;
    color:#8494bd;
    border:1px solid #2a3a63;
  }
  .stage-chip.active{background:var(--gold);color:var(--ink);border-color:var(--gold);font-weight:700;}
  .stage-chip.done{background:#22305a;color:#7fd9a0;border-color:#3a5a4a;}

  /* Paper card */
  .card{
    background:var(--paper);
    border:1px solid var(--line);
    border-top:none;
    border-radius:0 0 10px 10px;
    padding:30px 28px 26px;
    box-shadow:0 20px 50px rgba(0,0,0,0.35);
  }

  .stage-title{
    font-family:var(--font-display);
    font-size:1.5rem;
    margin:0 0 4px;
    color:var(--ink);
  }
  .stage-sub{
    font-family:var(--font-mono);
    font-size:0.72rem;
    text-transform:uppercase;
    letter-spacing:0.1em;
    color:#8a8474;
    margin-bottom:20px;
    border-bottom:1px dashed var(--line);
    padding-bottom:14px;
  }

  .scenario{
    background:var(--ledger-green-light);
    border-left:3px solid var(--ledger-green);
    padding:14px 16px;
    border-radius:4px;
    font-size:0.95rem;
    line-height:1.5;
    margin-bottom:18px;
  }

  .prompt{
    font-size:1.08rem;
    line-height:1.5;
    margin-bottom:18px;
    color:var(--ink);
  }
  .prompt strong{color:var(--ink);}

  .figures{
    font-family:var(--font-mono);
    font-size:0.88rem;
    background:#fff;
    border:1px solid var(--line);
    border-radius:6px;
    padding:12px 16px;
    margin-bottom:18px;
    line-height:1.7;
  }
  .figures div{display:flex;justify-content:space-between;}

  .options{
    display:flex;
    flex-direction:column;
    gap:10px;
    margin-bottom:6px;
  }
  .opt{
    text-align:left;
    background:#fff;
    border:1.5px solid var(--line);
    border-radius:7px;
    padding:13px 16px;
    font-family:var(--font-body);
    font-size:0.95rem;
    color:var(--charcoal);
    cursor:pointer;
    transition:border-color 0.15s ease, background 0.15s ease;
  }
  .opt:hover:not(:disabled){border-color:var(--ink);}
  .opt:focus-visible{outline:3px solid var(--gold); outline-offset:1px;}
  .opt:disabled{cursor:default;}
  .opt.correct{background:var(--ledger-green-light);border-color:var(--ledger-green);}
  .opt.incorrect{background:var(--rust-light);border-color:var(--rust);}

  .feedback{
    margin-top:16px;
    padding:14px 16px;
    border-radius:6px;
    font-size:0.92rem;
    line-height:1.55;
    display:none;
  }
  .feedback.show{display:block;}
  .feedback.correct{background:var(--ledger-green-light);border:1px solid var(--ledger-green);}
  .feedback.incorrect{background:var(--rust-light);border:1px solid var(--rust);}
  .feedback-label{
    font-family:var(--font-mono);
    font-size:0.68rem;
    text-transform:uppercase;
    letter-spacing:0.1em;
    display:block;
    margin-bottom:5px;
  }
  .feedback.correct .feedback-label{color:var(--ledger-green);}
  .feedback.incorrect .feedback-label{color:var(--rust);}

  .nextbtn{
    margin-top:18px;
    background:var(--ink);
    color:var(--paper);
    border:none;
    border-radius:7px;
    padding:12px 20px;
    font-family:var(--font-body);
    font-size:0.92rem;
    font-weight:600;
    cursor:pointer;
    display:none;
  }
  .nextbtn.show{display:inline-block;}
  .nextbtn:hover{background:#1e2c52;}
  .nextbtn:focus-visible{outline:3px solid var(--gold); outline-offset:2px;}

  .progress-line{
    font-family:var(--font-mono);
    font-size:0.7rem;
    color:#9a9484;
    margin-top:20px;
    text-align:right;
  }

  /* End screen */
  .end{
    text-align:center;
    padding:20px 0 4px;
  }
  .end h2{
    font-family:var(--font-display);
    font-size:1.7rem;
    color:var(--ink);
    margin-bottom:6px;
  }
  .end p{line-height:1.6;color:var(--charcoal);}
  .restart{
    margin-top:16px;
    background:transparent;
    border:1.5px solid var(--ink);
    color:var(--ink);
    padding:10px 18px;
    border-radius:7px;
    font-family:var(--font-body);
    font-weight:600;
    cursor:pointer;
  }
  .restart:hover{background:var(--ink);color:var(--paper);}

  .hidden{display:none;}
</style>
</head>
<body>

<div class="rig">

  <div class="ticker">
    <div class="ticker-top">
      <div>
        <div class="brand">Kai Cart <span>Ledger</span></div>
      </div>
      <div>
        <div class="balance-label">Cash on hand</div>
        <div class="balance" id="balance">$1,200</div>
      </div>
    </div>
    <div class="stage-track">
      <div class="stage-chip" id="chip-0">Setting up the books</div>
      <div class="stage-chip" id="chip-1">Balancing the ledger</div>
      <div class="stage-chip" id="chip-2">Making the call</div>
    </div>
  </div>

  <div class="card" id="card">
    <!-- populated by JS -->
  </div>

</div>

<script>
const STAGES = [
  {
    name: "Setting up the books",
    sub: "Stage 1 — Know your terms",
    questions: [
      {
        prompt: "Kai Cart pays $600 a week to lease the van, whether it sells one pie or one hundred. What kind of cost is this?",
        options: ["Variable cost", "Fixed cost", "Gross profit", "Contribution margin"],
        correct: 1,
        correctMsg: "Right. A fixed cost stays the same regardless of how much Kai Cart sells — the van lease doesn't change whether they sell 10 pies or 100.",
        incorrectMsg: "Not quite. Think about whether this cost changes with the number of pies sold. The van lease is charged weekly no matter what — that makes it a fixed cost.",
        hint: "Fixed costs don't move with sales volume. Variable costs do."
      },
      {
        prompt: "The flour, meat, and packaging for each pie cost $3.50 in total. What kind of cost is this?",
        options: ["Fixed cost", "Variable cost", "Revenue", "Break-even point"],
        correct: 1,
        correctMsg: "Correct — this cost rises and falls directly with how many pies are made, so it's a variable cost.",
        incorrectMsg: "Have another look: this cost only exists per pie made. If Kai Cart makes zero pies, it pays nothing here — that's the signature of a variable cost.",
        hint: "Ask: does the total change if Kai Cart sells more or fewer pies?"
      },
      {
        prompt: "Which term describes the point where total revenue exactly equals total costs — no profit, no loss?",
        options: ["Gross profit margin", "Break-even point", "Net cash flow", "Return on investment"],
        correct: 1,
        correctMsg: "Exactly. The break-even point is the sales level where Kai Cart covers all its costs but hasn't started making profit yet.",
        incorrectMsg: "Not this one. You're looking for the specific term for 'costs = revenue, profit is zero.'",
        hint: "The word itself is a clue — the business is 'even', not up or down."
      }
    ]
  },
  {
    name: "Balancing the ledger",
    sub: "Stage 2 — Do the maths",
    questions: [
      {
        prompt: "Kai Cart sells pies for $9.00 each. Variable cost per pie is $3.50. Weekly fixed costs are $825. How many pies must Kai Cart sell per week to break even?",
        figures: [["Selling price per pie", "$9.00"], ["Variable cost per pie", "$3.50"], ["Contribution per pie", "$5.50"], ["Weekly fixed costs", "$825"]],
        options: ["110 pies", "150 pies", "236 pies", "92 pies"],
        correct: 1,
        correctMsg: "Correct. Break-even = fixed costs ÷ contribution per unit = $825 ÷ $5.50 = 150 pies a week.",
        incorrectMsg: "Try the formula: Break-even (units) = Fixed costs ÷ Contribution per unit. Contribution per unit is selling price minus variable cost ($9.00 − $3.50 = $5.50). Then $825 ÷ $5.50.",
        hint: "Contribution per pie = selling price − variable cost. Break-even units = fixed costs ÷ contribution per pie."
      },
      {
        prompt: "Last month Kai Cart had sales revenue of $9,000 and cost of goods sold of $3,150. What was the gross profit margin?",
        figures: [["Sales revenue", "$9,000"], ["Cost of goods sold", "$3,150"], ["Gross profit", "$5,850"]],
        options: ["35%", "65%", "45%", "58%"],
        correct: 1,
        correctMsg: "Correct. Gross profit margin = (Gross profit ÷ Sales revenue) × 100 = ($5,850 ÷ $9,000) × 100 = 65%.",
        incorrectMsg: "Use: Gross profit margin = (Gross profit ÷ Sales revenue) × 100. Gross profit is $9,000 − $3,150 = $5,850. Then divide by $9,000 and multiply by 100.",
        hint: "Gross profit = revenue − cost of goods sold. Then divide gross profit by revenue, ×100."
      }
    ]
  },
  {
    name: "Making the call",
    sub: "Stage 3 — Justify a recommendation",
    questions: [
      {
        scenario: "Kai Cart's gross profit margin has held steady at 65% for six months — strong for a food business, where 55–65% is typical. The owner is considering a $4,000 loan to buy a second van and expand to a new suburb.",
        prompt: "Based on the gross profit margin above, which recommendation is best justified?",
        options: [
          "Reject the loan — a 65% margin means the business isn't profitable enough to expand.",
          "Accept the loan — a strong, stable 65% margin suggests the core business model is profitable, which supports taking on the risk of expansion.",
          "It's impossible to make a recommendation without knowing the owner's age.",
          "Accept the loan only if pie prices are lowered first."
        ],
        correct: 1,
        correctMsg: "Well justified. A consistently strong gross profit margin is evidence the core business is financially healthy, which is a reasonable basis to support taking on manageable debt for growth — though a full recommendation would also check cash flow and the loan's repayment terms.",
        incorrectMsg: "Look again at what a 65% gross profit margin actually signals about the business's underlying profitability before deciding whether it supports expansion.",
        hint: "A high, steady margin is generally a sign of a healthy core business — how does that relate to the risk of expanding?"
      },
      {
        scenario: "A competing food truck has just parked two streets away, undercutting Kai Cart's pie price by $1.50. The owner is debating whether to match the lower price.",
        prompt: "Using what you know about contribution per unit, what's the strongest concern with matching the competitor's price?",
        options: [
          "There is no concern — lower prices always increase total profit.",
          "Matching the price would cut contribution per pie from $5.50 to $4.00, meaning far more pies would need to be sold each week just to cover the same fixed costs.",
          "It only matters if the competitor also sells pies.",
          "Fixed costs would automatically decrease to compensate."
        ],
        correct: 1,
        correctMsg: "Exactly right — this is the core trade-off. A lower price shrinks contribution per unit, which raises the break-even point, so Kai Cart would need a higher sales volume just to stand still.",
        incorrectMsg: "Think back to the break-even formula from Stage 2: fixed costs ÷ contribution per unit. What happens to that number if contribution per unit drops?",
        hint: "If contribution per pie falls, and fixed costs stay the same, what happens to the break-even quantity?"
      }
    ]
  }
];

let stageIdx = 0;
let qIdx = 0;
let balance = 1200;
let answered = false;

const card = document.getElementById('card');
const balanceEl = document.getElementById('balance');

function fmtMoney(n){
  return (n<0?'-$':'$') + Math.abs(n).toLocaleString();
}

function updateChips(){
  for(let i=0;i<3;i++){
    const chip = document.getElementById('chip-'+i);
    chip.classList.remove('active','done');
    if(i < stageIdx) chip.classList.add('done');
    else if(i === stageIdx) chip.classList.add('active');
  }
}

function flashBalance(delta){
  balance += delta;
  balanceEl.textContent = fmtMoney(balance);
  balanceEl.classList.remove('up','down');
  void balanceEl.offsetWidth;
  balanceEl.classList.add(delta >= 0 ? 'up' : 'down');
}

function render(){
  updateChips();
  if(stageIdx >= STAGES.length){
    renderEnd();
    return;
  }
  const stage = STAGES[stageIdx];
  const q = stage.questions[qIdx];
  answered = false;

  let html = `<h2 class="stage-title">${stage.name}</h2>
    <div class="stage-sub">${stage.sub} — Question ${qIdx+1} of ${stage.questions.length}</div>`;

  if(q.scenario){
    html += `<div class="scenario">${q.scenario}</div>`;
  }

  html += `<div class="prompt">${q.prompt}</div>`;

  if(q.figures){
    html += `<div class="figures">`;
    q.figures.forEach(f => { html += `<div><span>${f[0]}</span><span>${f[1]}</span></div>`; });
    html += `</div>`;
  }

  html += `<div class="options" id="options">`;
  q.options.forEach((opt, i) => {
    html += `<button class="opt" data-idx="${i}">${opt}</button>`;
  });
  html += `</div>`;

  html += `<div class="feedback" id="feedback"></div>`;
  html += `<button class="nextbtn" id="nextbtn">Continue →</button>`;

  const totalQ = STAGES.reduce((a,s)=>a+s.questions.length,0);
  const doneQ = STAGES.slice(0,stageIdx).reduce((a,s)=>a+s.questions.length,0) + qIdx;
  html += `<div class="progress-line">${doneQ+1} of ${totalQ} total questions</div>`;

  card.innerHTML = html;

  document.querySelectorAll('.opt').forEach(btn => {
    btn.addEventListener('click', () => handleAnswer(parseInt(btn.dataset.idx)));
  });
}

function handleAnswer(idx){
  if(answered) return;
  answered = true;
  const stage = STAGES[stageIdx];
  const q = stage.questions[qIdx];
  const buttons = document.querySelectorAll('.opt');
  const feedback = document.getElementById('feedback');
  const nextbtn = document.getElementById('nextbtn');
  const isCorrect = idx === q.correct;

  buttons.forEach((b,i) => {
    b.disabled = true;
    if(i === q.correct) b.classList.add('correct');
    else if(i === idx) b.classList.add('incorrect');
  });

  if(isCorrect){
    flashBalance(50);
    feedback.className = 'feedback show correct';
    feedback.innerHTML = `<span class="feedback-label">Correct</span>${q.correctMsg}`;
  } else {
    flashBalance(-15);
    feedback.className = 'feedback show incorrect';
    feedback.innerHTML = `<span class="feedback-label">Not quite — here's a hint</span>${q.incorrectMsg}<br><br><em>Hint: ${q.hint}</em>`;
  }

  nextbtn.classList.add('show');
  nextbtn.addEventListener('click', advance);
  nextbtn.focus();
}

function advance(){
  const stage = STAGES[stageIdx];
  if(qIdx < stage.questions.length - 1){
    qIdx++;
  } else {
    stageIdx++;
    qIdx = 0;
  }
  render();
}

function renderEnd(){
  card.innerHTML = `
    <div class="end">
      <h2>Ledger closed 📕</h2>
      <p>You worked through all three stages — terms, calculations, and a justified business recommendation.<br>
      Final cash on hand: <strong>${fmtMoney(balance)}</strong></p>
      <button class="restart" id="restart">Run it again</button>
    </div>`;
  document.getElementById('restart').addEventListener('click', () => {
    stageIdx = 0; qIdx = 0; balance = 1200;
    balanceEl.textContent = fmtMoney(balance);
    balanceEl.classList.remove('up','down');
    render();
  });
}

render();
</script>

</body>
</html>
