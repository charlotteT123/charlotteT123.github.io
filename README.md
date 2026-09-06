<html lang="en-NZ">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>3.2 External Factors - Practice Quiz</title>
<style>
  :root{
    --bg: #FFFFFF;
    --panel: #F2FAFD;
    --text: #26303A;
    --muted: #51616D;
    --border: #AACBDE;
    --accent: #21708C;
    --accent-dark: #175369;
    --wrong: #8B3A3A;
    --focus: #1B2430;
  }
  *{ box-sizing: border-box; }
  html,body{ height:100%; }
  body{
    margin:0;
    background: var(--bg);
    color: var(--text);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    font-size: 18px;
    line-height: 1.65;
    letter-spacing: 0.01em;
    word-spacing: 0.05em;
  }
  .wrap{
    max-width: 700px;
    margin: 0 auto;
    padding: 32px 20px 80px;
  }
  header.top{
    display:flex;
    align-items:center;
    gap:12px;
    margin-bottom: 28px;
  }
  header.top svg{ flex-shrink:0; color: var(--accent); }
  header.top h1{
    font-size: 1.05rem;
    font-weight: 600;
    margin:0;
    color: var(--muted);
  }
  h2{ font-size: 1.5rem; margin: 0 0 8px; }
  h3{ font-size: 1.15rem; margin: 0 0 4px; }
  p{ margin: 0 0 16px; }
  .card{
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 28px 26px;
  }
  .muted{ color: var(--muted); }
  .small{ font-size: 0.9rem; }

  /* buttons */
  button{
    font: inherit;
    cursor: pointer;
  }
  .btn{
    display:inline-block;
    background: var(--accent);
    color: #fff;
    border: none;
    padding: 12px 22px;
    border-radius: 5px;
    font-weight: 600;
    font-size: 1rem;
  }
  .btn:hover{ background: var(--accent-dark); }
  .btn:disabled{ background: #A9BAC4; cursor: not-allowed; }
  .btn.secondary{
    background: transparent;
    color: var(--accent-dark);
    border: 1.5px solid var(--accent);
  }
  .btn.secondary:hover{ background: #E4F1F7; }
  button:focus-visible, a:focus-visible, input:focus-visible, label:focus-within{
    outline: 3px solid var(--focus);
    outline-offset: 2px;
  }

  /* progress */
  .progress-label{
    display:flex;
    justify-content: space-between;
    font-size: 0.85rem;
    color: var(--muted);
    margin-bottom: 6px;
  }
  .progress-track{
    height: 8px;
    background: var(--border);
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 26px;
  }
  .progress-fill{
    height:100%;
    background: var(--accent);
    transition: width 0.3s ease;
  }
  @media (prefers-reduced-motion: reduce){
    .progress-fill{ transition: none; }
  }

  .section-tag{
    display:inline-block;
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--accent-dark);
    background: #C7E1EE;
    border: 1px solid #A0C7DB;
    padding: 3px 10px;
    border-radius: 20px;
    margin-bottom: 14px;
  }

  fieldset{
    border: none;
    padding: 0;
    margin: 0 0 22px;
  }
  legend{
    font-size: 1.15rem;
    font-weight: 600;
    padding:0;
    margin-bottom: 16px;
  }
  .option{
    display:flex;
    align-items:flex-start;
    gap: 12px;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    padding: 13px 15px;
    margin-bottom: 10px;
    cursor: pointer;
  }
  .option:hover{ border-color: var(--accent); }
  .option input{
    margin-top: 3px;
    width: 18px;
    height: 18px;
    accent-color: var(--accent);
    flex-shrink:0;
  }
  .option.correct-answer{
    border-color: var(--accent);
    background: #DDF0E7;
  }
  .option.wrong-answer{
    border-color: var(--wrong);
    background: #F7E4E4;
  }

  .feedback{
    border-top: 1px solid var(--border);
    margin-top: 20px;
    padding-top: 20px;
  }
  .feedback-head{
    display:flex;
    align-items:center;
    gap:10px;
    font-weight: 700;
    margin-bottom: 8px;
  }
  .feedback-head.correct{ color: var(--accent-dark); }
  .feedback-head.incorrect{ color: var(--wrong); }
  .feedback-head svg{ flex-shrink:0; }
  .level-chip{
    display:inline-block;
    font-size: 0.78rem;
    font-weight: 700;
    padding: 2px 9px;
    border-radius: 20px;
    margin-left: 4px;
    border: 1px solid var(--border);
    color: var(--muted);
  }

  .btn-row{
    display:flex;
    justify-content: flex-end;
    gap: 10px;
    margin-top: 22px;
  }

  .hint-toggle{
    background:none;
    border:none;
    color: var(--accent-dark);
    text-decoration: underline;
    padding: 0;
    font-size: 0.92rem;
    margin: -6px 0 18px;
  }
  .hint-box{
    background:#E4F1F7;
    border-left: 3px solid var(--accent);
    padding: 10px 14px;
    font-size: 0.92rem;
    margin: -8px 0 18px;
    border-radius: 0 4px 4px 0;
  }

  /* summary bars */
  .bar-row{ margin-bottom: 18px; }
  .bar-row .label-line{
    display:flex;
    justify-content: space-between;
    font-size: 0.95rem;
    margin-bottom: 6px;
  }
  .bar-track{
    height: 14px;
    background: var(--border);
    border-radius: 7px;
    overflow:hidden;
  }
  .bar-fill{
    height:100%;
    background: var(--accent);
  }

  .quote-box{
    background: #E4F1F7;
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 16px 18px;
    margin: 18px 0;
    font-style: normal;
  }

  footer.note{
    margin-top: 40px;
    font-size: 0.85rem;
    color: var(--muted);
    text-align:center;
  }

  .visually-hidden{
    position:absolute; width:1px; height:1px;
    overflow:hidden; clip:rect(0,0,0,0); white-space:nowrap;
  }
</style>
</head>
<body>
<div class="wrap">

  <header class="top">
    <svg width="28" height="28" viewBox="0 0 24 24" fill="none" aria-hidden="true">
      <path d="M4 19.5V6a2 2 0 0 1 2-2h11a1 1 0 0 1 1 1v13" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M6 19.5h12" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"/>
      <path d="M4 19.5a1.5 1.5 0 0 1 1.5-1.5H17" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
    <h1>Level 3 Business Studies - 3.2 External Factors</h1>
  </header>

  <div id="app" class="card" role="main" aria-live="polite"></div>

  <footer class="note">This is an anonymous practice tool. Nothing you enter is saved or recorded. Take it as many times as you like - each attempt mixes a different set of questions.</footer>
</div>

<script>
/* ---------------------------------------------------------
   DATA BANKS
--------------------------------------------------------- */

const recallBank = [
  {
    prompt: "What three things must be considered when identifying a strategic business decision?",
    options: [
      "Size, scope, and timeframe",
      "Profit, revenue, and location",
      "Staffing, marketing, and pricing",
      "Suppliers, customers, and competitors"
    ],
    correct: 0,
    explanation: "A strategic decision is judged by its size (resources committed), scope (how much of the business it affects) and timeframe (how long it will take to see results)."
  },
  {
    prompt: "Which level of management is typically responsible for tactical decisions?",
    options: [
      "Senior / top management",
      "Middle management",
      "Operational / first-line management",
      "Shareholders"
    ],
    correct: 1,
    explanation: "Tactical decisions sit between strategy and daily operations, so they're usually made by middle management, translating strategic goals into departmental action."
  },
  {
    prompt: "Which of these is a potential positive impact of tariffs on a domestic business?",
    options: [
      "They always lower consumer prices",
      "They increase the variety of imported goods available",
      "They can protect domestic industries from foreign competition",
      "They reduce the cost of imported raw materials"
    ],
    correct: 2,
    explanation: "Tariffs raise the price of imported goods, which can shield local businesses from cheaper overseas competition - though this often comes at a cost to consumers and importers."
  },
  {
    prompt: "Which of the following is an example of an external factor affecting a business?",
    options: [
      "A change in government regulation",
      "Poor cash flow management",
      "A disagreement between staff members",
      "An outdated internal IT system"
    ],
    correct: 0,
    explanation: "External factors sit outside the business's control - government regulation is a classic example. The other options are internal issues the business itself could fix."
  },
  {
    prompt: "In the context of a strategic decision, what does \"scope\" refer to?",
    options: [
      "How long the decision takes to implement",
      "How many parts or areas of the business are affected",
      "How much money the decision commits",
      "Who approved the decision"
    ],
    correct: 1,
    explanation: "Scope is about reach - whether a decision touches one department or the whole organisation. Timeframe covers duration, and size covers resource commitment."
  },
  {
    prompt: "What best distinguishes a strategic decision from a tactical decision?",
    options: [
      "Strategic decisions are long-term and affect the whole business; tactical decisions are shorter-term and department-specific",
      "Strategic decisions are made by any employee; tactical decisions require board approval",
      "Strategic decisions cost nothing to implement; tactical decisions always cost more",
      "There is no real difference between them"
    ],
    correct: 0,
    explanation: "Strategic decisions shape the long-term direction of the whole business, while tactical decisions are shorter-term and usually confined to a department."
  }
];

const maoriBank = [
  {
    prompt: "What does Kaitiakitanga mean in a business context?",
    options: [
      "Guardianship and stewardship of resources, people, and the environment",
      "Hospitality and generosity shown towards others",
      "Self-determination and the right to exercise leadership",
      "The underlying purpose or reason behind an action"
    ],
    correct: 0,
    explanation: "Kaitiakitanga refers to guardianship - looking after resources, people, and the environment responsibly, often for future generations."
  },
  {
    prompt: "What does Manaakitanga mean?",
    options: [
      "Guardianship of resources and the environment",
      "Hospitality, care, and support shown towards others",
      "Customary protocols that guide behaviour",
      "Prestige and authority held by a person or group"
    ],
    correct: 1,
    explanation: "Manaakitanga is about hospitality and care - the way a business treats its customers, staff, and community."
  },
  {
    prompt: "What does Whanaungatanga mean?",
    options: [
      "Relationships, kinship, and a sense of connection between people",
      "Guardianship of resources and the environment",
      "The underlying purpose behind a decision",
      "Customary protocols that guide behaviour"
    ],
    correct: 0,
    explanation: "Whanaungatanga is about relationships and connection - relevant to how a business builds trust with staff, customers, and its wider community."
  },
  {
    prompt: "What does Pūtake mean?",
    options: [
      "Guardianship of resources",
      "Hospitality towards others",
      "Kinship and connection",
      "The underlying purpose or reason for a decision or action"
    ],
    correct: 3,
    explanation: "Pūtake refers to the underlying purpose or reason behind a decision - the 'why' driving a business's actions."
  },
  {
    prompt: "What does Tikanga mean?",
    options: [
      "Authority and prestige held by a person or organisation",
      "The underlying purpose behind a decision",
      "Customary practices, values, and protocols that guide behaviour",
      "Relationships and connection between people"
    ],
    correct: 2,
    explanation: "Tikanga refers to customary practices and protocols - the accepted 'right way' of doing things within a cultural context."
  },
  {
    prompt: "What does Mana mean?",
    options: [
      "Hospitality and generosity",
      "Authority, prestige, and standing held by a person or organisation",
      "Customary protocols that guide behaviour",
      "Guardianship of resources"
    ],
    correct: 1,
    explanation: "Mana refers to authority, prestige, and standing - something a business can build or damage through its actions and reputation."
  },
  {
    prompt: "What does Rangatiratanga mean?",
    options: [
      "The underlying purpose behind a decision",
      "Relationships and kinship between people",
      "Hospitality shown towards others",
      "Self-determination and the right to exercise leadership or authority"
    ],
    correct: 3,
    explanation: "Rangatiratanga refers to self-determination and leadership - the right of a person or group to govern their own affairs."
  }
];

const businessBank = [
  {
    prompt: "What is meant by a \"strategic response\"?",
    options: [
      "A short-term fix applied with no planning",
      "An action a business takes to address an external factor, considering its size, scope, and timeframe",
      "A response that only applies to internal problems",
      "A legal requirement imposed by government"
    ],
    correct: 1,
    explanation: "A strategic response is a considered action to address the impact of an external factor - evaluated by size, scope, and timeframe."
  },
  {
    prompt: "What is an \"external factor\"?",
    options: [
      "A factor arising from within the business, such as cash flow",
      "An influence from outside the business that it cannot directly control, such as government policy or competitor actions",
      "A type of financial statement",
      "A marketing strategy used to attract customers"
    ],
    correct: 1,
    explanation: "External factors originate outside the business and are largely beyond its control - the business can only respond to them, not prevent them."
  },
  {
    prompt: "What is a \"contingency plan\"?",
    options: [
      "A plan for routine daily operations",
      "A record of past financial performance",
      "A plan prepared in advance for responding to an unexpected event",
      "A type of employment contract"
    ],
    correct: 2,
    explanation: "A contingency plan is prepared ahead of time so a business can respond quickly if an unexpected event, like an external shock, occurs."
  },
  {
    prompt: "What does \"diversification\" mean as a strategic response?",
    options: [
      "Reducing the number of products a business offers",
      "Expanding into new products or markets to spread risk",
      "Increasing prices across all products",
      "Closing underperforming branches"
    ],
    correct: 1,
    explanation: "Diversification means expanding into new products or markets, which spreads risk so the business isn't overly dependent on one area."
  },
  {
    prompt: "What does Corporate Social Responsibility (CSR) mean?",
    options: [
      "A legal requirement to publish financial statements",
      "A strategy focused only on maximising short-term profit",
      "A business considering the ethical, social, and environmental impact of its decisions",
      "A tax paid by businesses operating internationally"
    ],
    correct: 2,
    explanation: "CSR means a business weighs up the ethical, social, and environmental effects of its decisions, not just the financial ones."
  }
];

const scenarios = [
  {
    company: "KMD Brands Limited",
    context: "KMD Brands Limited (which owns Kathmandu) is dually listed on the NZX and ASX.",
    factor: "A new competitor enters the market.",
    prompt: "What is a potential strategic response for KMD Brands Limited to this external factor?",
    options: [
      { text: "Do nothing", level: "Not Achieved", explanation: "Taking no action leaves the business exposed to losing market share, with no strategic reasoning behind it." },
      { text: "Diversify your product offering", level: "Excellence", explanation: "Broadening the product range reduces reliance on any single line and gives customers reasons to stay, directly addressing the new competition without triggering a price war." },
      { text: "Increase prices", level: "Achieved", explanation: "This shows some reasoning, but raising prices just as a competitor enters risks pushing customers straight toward the cheaper new option." },
      { text: "Seek different markets", level: "Merit", explanation: "Moving into new markets reduces exposure to the newly competitive segment, though it carries its own cost and risk of entry." }
    ],
    correctIndex: 1,
    bonus: {
      prompt: "Why is diversifying the product offering generally a stronger response than increasing prices when a new competitor enters?",
      options: [
        "Because it reduces reliance on the threatened product line, while a price rise could push customers toward the cheaper new competitor",
        "Because it costs nothing to implement",
        "Because customers always prefer new products regardless of competition",
        "Because increasing prices is illegal"
      ],
      correct: 0,
      explanation: "Diversifying spreads risk across products rather than reacting defensively on price, which is the more strategic long-term move."
    }
  },
  {
    company: "Fisher & Paykel Healthcare Corporation Limited",
    context: "Fisher & Paykel Healthcare Corporation Limited is a NZ-registered company operating and selling internationally.",
    factor: "Another pandemic occurs.",
    prompt: "What is a potential strategic response for Fisher & Paykel Healthcare to this external factor?",
    options: [
      { text: "Increase production", level: "Excellence", explanation: "This meets a genuine surge in demand for healthcare products and reflects manaakitanga - supporting the wider community - though it will raise costs initially." },
      { text: "Increase prices", level: "Achieved", explanation: "A relatively safe option only if increases stay modest - pushing prices too far during a health crisis risks reputational damage." },
      { text: "Maintain supply and prices", level: "Not Achieved", explanation: "This doesn't respond to a clear change in demand and is unlikely to be the strongest business decision." },
      { text: "Reduce supply to make goods scarcer", level: "Not Achieved", explanation: "Deliberately restricting essential health products during a pandemic is both poor strategy and ethically questionable." }
    ],
    correctIndex: 0,
    bonus: {
      prompt: "Why might increasing prices during a pandemic carry more risk for Fisher & Paykel Healthcare than increasing production?",
      options: [
        "Because it could damage brand reputation and appear opportunistic during a health crisis",
        "Because prices for healthcare products are fixed by law",
        "Because it always increases profit immediately",
        "Because production costs never change during a crisis"
      ],
      correct: 0,
      explanation: "Reputational risk matters more here because the company sells essential healthcare equipment - appearing to profit from a crisis can cause lasting brand damage."
    }
  },
  {
    company: "Mainfreight Limited",
    context: "Mainfreight Limited is a NZ-registered company operating internationally.",
    factor: "New emissions regulations mean transport companies must pay higher taxes (RUCs) based on their emissions.",
    prompt: "What is a potential strategic response for Mainfreight Limited to this external factor?",
    options: [
      { text: "Do nothing - absorb the extra cost", level: "Achieved", explanation: "This is the easiest option but doesn't address the underlying issue and leaves the business exposed to rising costs long-term." },
      { text: "Spend immediately on low-emission vehicles", level: "Merit", explanation: "This supports long-term sustainability but is costly upfront and could put pressure on cash flow." },
      { text: "Replace trucks with low-emission vehicles as they're decommissioned", level: "Excellence", explanation: "This balances environmental responsibility (kaitiakitanga) with cost, spreading the investment over time rather than all at once." },
      { text: "Buy more high-emission vehicles", level: "Not Achieved", explanation: "This directly increases exposure to the new tax and works against the direction of the regulation." }
    ],
    correctIndex: 2,
    bonus: {
      prompt: "Why is replacing trucks with low-emission vehicles as they're decommissioned often the strongest response here?",
      options: [
        "Because it balances the cost of transition against cash flow, spreading the investment over time",
        "Because it avoids the new regulations altogether",
        "Because it guarantees the lowest possible total cost",
        "Because government requires this specific approach"
      ],
      correct: 0,
      explanation: "Staging the investment against the vehicle replacement cycle manages both size (cost) and timeframe - the two things a strategic decision needs to weigh up."
    }
  }
];

/* ---------------------------------------------------------
   HELPERS
--------------------------------------------------------- */
function shuffle(arr){
  const a = arr.slice();
  for(let i = a.length - 1; i > 0; i--){
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

function pick(arr, n){
  return shuffle(arr).slice(0, n);
}

// Shuffle an options array while tracking the correct index
function shuffleOptions(options, correctIndex){
  const withFlag = options.map((opt, i) => ({ opt, isCorrect: i === correctIndex }));
  const shuffled = shuffle(withFlag);
  return {
    options: shuffled.map(x => x.opt),
    correctIndex: shuffled.findIndex(x => x.isCorrect)
  };
}

const checkSvg = `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="10" stroke="#2F6F5E" stroke-width="1.6"/><path d="M8 12.5l2.5 2.5L16 9.5" stroke="#2F6F5E" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`;
const crossSvg = `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" aria-hidden="true"><circle cx="12" cy="12" r="10" stroke="#8B3A3A" stroke-width="1.6"/><path d="M9 9l6 6M15 9l-6 6" stroke="#8B3A3A" stroke-width="1.8" stroke-linecap="round"/></svg>`;

/* ---------------------------------------------------------
   QUIZ STATE
--------------------------------------------------------- */
let steps = [];        // flat ordered list of every step (questions + bonus follow-ups)
let stepAnswers = [];  // parallel array: null until answered, then { chosenIndex, isCorrect }
let stepIndex = 0;
let scores = { recall: 0, maori: 0, business: 0, scenario: 0, bonus: 0 };
let totals = { recall: 0, maori: 0, business: 0, scenario: 0, bonus: 0 };

function buildQuiz(){
  scores = { recall: 0, maori: 0, business: 0, scenario: 0, bonus: 0 };

  const recallSteps = pick(recallBank, 3).map(q => {
    const s = shuffleOptions(q.options, q.correct);
    return { type: "main", section: "recall", scoreKey: "recall", prompt: q.prompt, options: s.options, correctIndex: s.correctIndex, explanation: q.explanation };
  });
  const maoriSteps = pick(maoriBank, 3).map(q => {
    const s = shuffleOptions(q.options, q.correct);
    return { type: "main", section: "maori", scoreKey: "maori", prompt: q.prompt, options: s.options, correctIndex: s.correctIndex, explanation: q.explanation };
  });
  const businessSteps = pick(businessBank, 3).map(q => {
    const s = shuffleOptions(q.options, q.correct);
    return { type: "main", section: "business", scoreKey: "business", prompt: q.prompt, options: s.options, correctIndex: s.correctIndex, explanation: q.explanation };
  });

  const scenarioSteps = [];
  shuffle(scenarios).forEach(sc => {
    const opts = sc.options.map(o => o.text);
    const s = shuffleOptions(opts, sc.correctIndex);
    const levelByNewIndex = s.options.map(text => sc.options.find(o => o.text === text));
    const contextInfo = { company: sc.company, context: sc.context, factor: sc.factor };

    scenarioSteps.push({
      type: "main", section: "scenario", scoreKey: "scenario",
      prompt: sc.prompt, options: s.options, correctIndex: s.correctIndex,
      levels: levelByNewIndex.map(o => o.level),
      explanations: levelByNewIndex.map(o => o.explanation),
      context: contextInfo
    });

    const bonusShuffled = shuffleOptions(sc.bonus.options, sc.bonus.correct);
    scenarioSteps.push({
      type: "bonus", scoreKey: "bonus",
      prompt: sc.bonus.prompt, options: bonusShuffled.options, correctIndex: bonusShuffled.correctIndex,
      explanation: sc.bonus.explanation,
      context: contextInfo
    });
  });

  steps = [...recallSteps, ...maoriSteps, ...businessSteps, ...scenarioSteps];

  let qn = 0;
  steps.forEach(s => { if(s.type === "main"){ qn += 1; s.questionNumber = qn; } });

  totals = {
    recall: recallSteps.length,
    maori: maoriSteps.length,
    business: businessSteps.length,
    scenario: scenarioSteps.filter(s => s.type === "main").length,
    bonus: scenarioSteps.filter(s => s.type === "bonus").length
  };

  stepAnswers = steps.map(() => null);
  stepIndex = 0;
  renderIntro();
}

/* ---------------------------------------------------------
   RENDERING
--------------------------------------------------------- */
const app = document.getElementById('app');

function renderIntro(){
  app.innerHTML = `
    <h2>📝 Practice quiz: 3.2 External Factors</h2>
    <p>Twelve questions covering recall, Māori business concepts, business knowledge, and strategic responses to real NZ company scenarios. This attempt is a random mix - no two attempts are quite the same.</p>
    <div class="btn-row" style="justify-content:flex-start;">
      <button class="btn" id="startBtn">Start quiz</button>
    </div>
  `;
  document.getElementById('startBtn').addEventListener('click', () => {
    renderStep(0);
  });
}

function sectionLabel(section){
  if(section === "recall") return "🧠 Recall";
  if(section === "maori") return "🌿 Māori Concepts";
  if(section === "business") return "💼 Business Knowledge";
  return "🏢 Scenario";
}

const totalMainQuestions = () => totals.recall + totals.maori + totals.business + totals.scenario;

function renderStep(i){
  stepIndex = i;
  const step = steps[i];
  const pct = Math.round((i / steps.length) * 100);
  const answered = stepAnswers[i];

  const tagLabel = step.type === "main" ? sectionLabel(step.section) : "⭐ Bonus - justify it";
  const progressText = step.type === "main"
    ? `Question ${step.questionNumber} of ${totalMainQuestions()}`
    : `Bonus round`;

  let contextHtml = "";
  if(step.context){
    contextHtml = `
      <div class="quote-box">
        <strong>${step.context.company}</strong><br>
        <span class="small">${step.context.context}</span><br><br>
        <em>External factor: ${step.context.factor}</em>
      </div>
    `;
  }

  app.innerHTML = `
    <div class="progress-label">
      <span>${progressText}</span>
      <span>${pct}% complete</span>
    </div>
    <div class="progress-track" role="progressbar" aria-valuenow="${i}" aria-valuemin="0" aria-valuemax="${steps.length}">
      <div class="progress-fill" style="width:${pct}%"></div>
    </div>
    <span class="section-tag">${tagLabel}</span>
    ${contextHtml}
    <div>
      <fieldset>
        <legend>${step.prompt}</legend>
        <div id="optionsWrap"></div>
      </fieldset>
      <div class="btn-row" id="actionRow"></div>
    </div>
    <div id="feedbackWrap"></div>
  `;

  const wrap = document.getElementById('optionsWrap');
  step.options.forEach((optText, idx) => {
    const id = `opt${idx}`;
    const label = document.createElement('label');
    label.className = 'option';
    label.setAttribute('for', id);
    label.innerHTML = `<input type="radio" name="answer" id="${id}" value="${idx}"><span>${optText}</span>`;
    wrap.appendChild(label);
  });

  const radios = wrap.querySelectorAll('input[type=radio]');
  const actionRow = document.getElementById('actionRow');

  if(answered){
    // Already answered earlier - show it locked, in review mode, with feedback.
    radios.forEach((r, idx) => {
      r.disabled = true;
      if(idx === answered.chosenIndex) r.checked = true;
      const label = r.closest('label');
      if(idx === step.correctIndex) label.classList.add('correct-answer');
      else if(idx === answered.chosenIndex) label.classList.add('wrong-answer');
    });
    showFeedback(step, answered.chosenIndex, answered.isCorrect, i);
  } else {
    // Not yet answered - interactive mode.
    if(i > 0){
      const backBtn = document.createElement('button');
      backBtn.type = 'button';
      backBtn.className = 'btn secondary';
      backBtn.id = 'backBtn';
      backBtn.textContent = '◀ Previous question';
      backBtn.addEventListener('click', () => renderStep(i - 1));
      actionRow.appendChild(backBtn);
    }
    const submitBtn = document.createElement('button');
    submitBtn.type = 'button';
    submitBtn.className = 'btn';
    submitBtn.id = 'submitBtn';
    submitBtn.disabled = true;
    submitBtn.textContent = 'Submit answer';
    actionRow.appendChild(submitBtn);

    radios.forEach(r => {
      r.addEventListener('change', () => { submitBtn.disabled = false; });
      r.addEventListener('click', () => { submitBtn.disabled = false; });
    });

    submitBtn.addEventListener('click', () => {
      const chosen = wrap.querySelector('input[name=answer]:checked');
      if(!chosen) return;
      submitStep(i, parseInt(chosen.value, 10));
    });
  }
}

function submitStep(i, chosenIndex){
  const step = steps[i];
  const isCorrect = chosenIndex === step.correctIndex;
  stepAnswers[i] = { chosenIndex, isCorrect };
  if(isCorrect) scores[step.scoreKey] += 1;

  document.querySelectorAll('#optionsWrap input').forEach((r, idx) => {
    r.disabled = true;
    const label = r.closest('label');
    if(idx === step.correctIndex) label.classList.add('correct-answer');
    else if(idx === chosenIndex) label.classList.add('wrong-answer');
  });
  document.getElementById('actionRow').innerHTML = '';

  showFeedback(step, chosenIndex, isCorrect, i);
}

function showFeedback(step, chosenIndex, isCorrect, i){
  const isBonus = step.type === "bonus";
  const isScenarioMain = step.type === "main" && step.section === "scenario";
  const explanation = isScenarioMain ? step.explanations[chosenIndex] : step.explanation;
  const levelChip = isScenarioMain ? `<span class="level-chip">${step.levels[chosenIndex]}</span>` : "";
  const isLastStep = i === steps.length - 1;

  let headText;
  if(isBonus) headText = isCorrect ? '⭐ Bonus point earned' : 'No bonus point this time';
  else headText = isCorrect ? 'Correct' : 'Not quite';

  const nextLabel = isLastStep ? 'See my results' : (isScenarioMain ? 'Continue' : 'Next question');

  const fb = document.getElementById('feedbackWrap');
  fb.innerHTML = `
    <div class="feedback">
      <div class="feedback-head ${isCorrect ? 'correct' : 'incorrect'}">
        ${isCorrect ? checkSvg : crossSvg}
        <span>${headText} ${levelChip}</span>
      </div>
      <p>${explanation}</p>
      ${(!isCorrect && !isBonus) ? `<p class="small muted">Best response: <strong>${step.options[step.correctIndex]}</strong>${isScenarioMain ? ' - ' + step.explanations[step.correctIndex] : ''}</p>` : ""}
      <div class="btn-row">
        ${i > 0 ? `<button class="btn secondary" id="backBtn">◀ Previous question</button>` : ""}
        <button class="btn" id="nextBtn">${nextLabel}</button>
      </div>
    </div>
  `;

  if(i > 0){
    document.getElementById('backBtn').addEventListener('click', () => renderStep(i - 1));
  }
  document.getElementById('nextBtn').addEventListener('click', () => {
    if(isLastStep) renderSummary();
    else renderStep(i + 1);
  });
}

function performanceEmoji(pct){
  if(pct >= 80) return "🌟";
  if(pct >= 50) return "👍";
  return "🌱";
}

function renderSummary(){
  // Core sections - each drawn from its own question bank and scored independently.
  const coreSections = [
    { key: 'recall', label: '🧠 Recall', total: totals.recall },
    { key: 'maori', label: '🌿 Māori Concepts', total: totals.maori },
    { key: 'business', label: '💼 Business Knowledge', total: totals.business },
    { key: 'scenario', label: '🏢 Strategic Responses', total: totals.scenario },
  ];

  const withPct = coreSections.map(s => ({ ...s, score: scores[s.key], pct: Math.round((scores[s.key] / s.total) * 100) }));
  const strongest = withPct.reduce((a, b) => (b.pct > a.pct ? b : a));
  const weakest = withPct.reduce((a, b) => (b.pct < a.pct ? b : a));

  const totalCore = totals.recall + totals.maori + totals.business + totals.scenario;
  const scoreCore = scores.recall + scores.maori + scores.business + scores.scenario;
  const bonusPct = Math.round((scores.bonus / totals.bonus) * 100);

  const barsHtml = withPct.map(s => `
    <div class="bar-row">
      <div class="label-line">
        <span>${performanceEmoji(s.pct)} ${s.label}</span>
        <span class="muted">${s.score} / ${s.total}</span>
      </div>
      <div class="bar-track"><div class="bar-fill" style="width:${s.pct}%"></div></div>
    </div>
  `).join("");

  const bonusBarHtml = `
    <div class="bar-row" style="margin-top:26px; padding-top:18px; border-top:1px dashed var(--border);">
      <div class="label-line">
        <span>⭐ Bonus - justifying scenario answers <span class="muted small">(extra credit, not counted above)</span></span>
        <span class="muted">${scores.bonus} / ${totals.bonus}</span>
      </div>
      <div class="bar-track"><div class="bar-fill" style="width:${bonusPct}%; background: var(--wrong);"></div></div>
    </div>
  `;

  let guidance;
  if(strongest.pct === weakest.pct){
    guidance = "Your results were even across all four sections - solid, consistent understanding.";
  } else {
    guidance = `You're strongest on <strong>${strongest.label.replace(/^[^\s]+\s/, '')}</strong> (${strongest.pct}%). Focus your next study session on <strong>${weakest.label.replace(/^[^\s]+\s/, '')}</strong> (${weakest.pct}%).`;
  }

  app.innerHTML = `
    <h2>🎉 Your results</h2>
    <p class="muted">Score: ${scoreCore} / ${totalCore} core questions.</p>
    ${barsHtml}
    ${bonusBarHtml}
    <p style="margin-top:20px;">${guidance}</p>
    <p class="small muted">Remember: getting an answer right here is a good sign, but the exam asks you to explain your reasoning in writing. Use this to check your knowledge, then practise writing full responses to scenarios like these.</p>
    <div class="btn-row" style="justify-content:flex-start;">
      <button class="btn" id="restartBtn">Try another mix of questions</button>
    </div>
  `;
  document.getElementById('restartBtn').addEventListener('click', buildQuiz);
}

/* ---------------------------------------------------------
   INIT
--------------------------------------------------------- */
buildQuiz();
</script>
</body>
</html>
