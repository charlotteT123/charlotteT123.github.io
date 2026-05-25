<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Character Builder — Bank Accounts Activity</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #ffffff;
      --bg-secondary: #f5f5f3;
      --bg-tertiary: #eeede9;
      --text-primary: #1a1a18;
      --text-secondary: #5f5e5a;
      --text-tertiary: #888780;
      --border: rgba(0,0,0,0.12);
      --border-strong: rgba(0,0,0,0.22);
      --radius-md: 8px;
      --radius-lg: 12px;
      --radius-xl: 16px;
      --accent: #1a1a18;
      --green-bg: #E1F5EE;
      --green-border: #9FE1CB;
      --green-text: #0F6E56;
      --blue-bg: #E6F1FB;
      --blue-border: #B5D4F4;
      --blue-text: #185FA5;
      --amber-bg: #FAEEDA;
      --amber-border: #FAC775;
      --amber-text: #854F0B;
    }

    @media (prefers-color-scheme: dark) {
      :root {
        --bg: #1e1e1c;
        --bg-secondary: #2a2a28;
        --bg-tertiary: #323230;
        --text-primary: #f0efeb;
        --text-secondary: #b4b2a9;
        --text-tertiary: #888780;
        --border: rgba(255,255,255,0.1);
        --border-strong: rgba(255,255,255,0.2);
        --green-bg: #04342C;
        --green-border: #0F6E56;
        --green-text: #9FE1CB;
        --blue-bg: #042C53;
        --blue-border: #185FA5;
        --blue-text: #B5D4F4;
        --amber-bg: #412402;
        --amber-border: #854F0B;
        --amber-text: #FAC775;
      }
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: var(--bg-tertiary);
      color: var(--text-primary);
      min-height: 100vh;
      padding: 2rem 1rem;
    }

    .page-wrap {
      max-width: 720px;
      margin: 0 auto;
    }

    .page-header {
      margin-bottom: 2rem;
    }

    .page-header h1 {
      font-size: 22px;
      font-weight: 500;
      color: var(--text-primary);
      margin-bottom: 6px;
    }

    .page-header p {
      font-size: 14px;
      color: var(--text-secondary);
      line-height: 1.6;
    }

    .card {
      background: var(--bg);
      border: 0.5px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 1.5rem;
      margin-bottom: 1.25rem;
    }

    .section-label {
      font-size: 11px;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--text-tertiary);
      margin-bottom: 10px;
    }

    .chip-group {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 1.5rem;
    }

    .chip {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 6px 14px;
      border-radius: 999px;
      border: 0.5px solid var(--border-strong);
      font-size: 13px;
      cursor: pointer;
      background: var(--bg);
      color: var(--text-secondary);
      transition: all 0.12s;
      user-select: none;
    }

    .chip:hover {
      border-color: var(--text-secondary);
      color: var(--text-primary);
    }

    .chip.active {
      background: var(--text-primary);
      color: var(--bg);
      border-color: var(--text-primary);
    }

    .chip .emoji { font-size: 15px; }

    .name-row {
      display: flex;
      gap: 10px;
      align-items: center;
      margin-bottom: 1.5rem;
    }

    .name-row input {
      flex: 1;
      padding: 9px 13px;
      font-size: 14px;
      border-radius: var(--radius-md);
      border: 0.5px solid var(--border-strong);
      background: var(--bg);
      color: var(--text-primary);
      outline: none;
    }

    .name-row input:focus {
      border-color: var(--text-secondary);
      box-shadow: 0 0 0 3px rgba(0,0,0,0.06);
    }

    .name-row .random-btn {
      padding: 9px 14px;
      font-size: 13px;
      border-radius: var(--radius-md);
      border: 0.5px solid var(--border-strong);
      background: var(--bg-secondary);
      color: var(--text-secondary);
      cursor: pointer;
      white-space: nowrap;
    }

    .name-row .random-btn:hover { background: var(--bg-tertiary); }

    .income-row {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 1.5rem;
    }

    .income-row label {
      font-size: 13px;
      color: var(--text-secondary);
      white-space: nowrap;
    }

    .income-row input[type=range] {
      flex: 1;
      -webkit-appearance: none;
      height: 4px;
      border-radius: 2px;
      background: var(--border-strong);
      outline: none;
      cursor: pointer;
    }

    .income-row input[type=range]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 18px;
      height: 18px;
      border-radius: 50%;
      background: var(--text-primary);
      cursor: pointer;
    }

    .income-val {
      font-size: 14px;
      font-weight: 500;
      min-width: 80px;
      text-align: right;
      color: var(--text-primary);
    }

    .section-divider {
      border: none;
      border-top: 0.5px solid var(--border);
      margin: 0.25rem 0 1.5rem;
    }

    /* Preview card */
    .preview-card {
      background: var(--bg);
      border: 0.5px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 1.25rem;
      min-height: 120px;
      margin-bottom: 1.25rem;
    }

    .empty-hint {
      color: var(--text-tertiary);
      font-size: 13px;
      padding: 16px 0;
    }

    .card-top {
      display: flex;
      align-items: flex-start;
      gap: 16px;
    }

    .avatar {
      width: 56px;
      height: 56px;
      border-radius: 50%;
      background: var(--bg-secondary);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 26px;
      flex-shrink: 0;
      border: 0.5px solid var(--border);
    }

    .card-name {
      font-size: 20px;
      font-weight: 500;
      color: var(--text-primary);
      margin-bottom: 3px;
    }

    .card-sub {
      font-size: 13px;
      color: var(--text-secondary);
      margin-bottom: 10px;
    }

    .card-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .tag {
      font-size: 12px;
      padding: 3px 10px;
      border-radius: 999px;
      border: 0.5px solid var(--border);
      color: var(--text-secondary);
      background: var(--bg-secondary);
    }

    .tag.money { color: var(--green-text); background: var(--green-bg); border-color: var(--green-border); }
    .tag.goal  { color: var(--blue-text);  background: var(--blue-bg);  border-color: var(--blue-border); }
    .tag.habit { color: var(--amber-text); background: var(--amber-bg); border-color: var(--amber-border); }

    .card-personality {
      margin-top: 12px;
      padding-top: 12px;
      border-top: 0.5px solid var(--border);
      font-size: 13px;
      color: var(--text-secondary);
      line-height: 1.5;
    }

    .personality-label {
      font-size: 11px;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      color: var(--text-tertiary);
      margin-bottom: 4px;
    }

    /* Actions */
    .actions {
      display: flex;
      gap: 10px;
      margin-bottom: 1.25rem;
      flex-wrap: wrap;
    }

    .btn-main {
      flex: 1;
      min-width: 200px;
      padding: 11px 16px;
      font-size: 14px;
      font-weight: 500;
      border-radius: var(--radius-md);
      border: 0.5px solid var(--text-primary);
      background: var(--text-primary);
      color: var(--bg);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      text-decoration: none;
    }

    .btn-main:hover { opacity: 0.85; }

    .btn-sec {
      padding: 11px 18px;
      font-size: 14px;
      border-radius: var(--radius-md);
      border: 0.5px solid var(--border-strong);
      background: var(--bg);
      color: var(--text-secondary);
      cursor: pointer;
    }

    .btn-sec:hover { background: var(--bg-secondary); }

    /* Profile summary */
    .profile-card {
      display: none;
      background: var(--bg-secondary);
      border: 0.5px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 1.25rem;
      margin-bottom: 1.25rem;
    }

    .profile-card.show { display: block; }

    .profile-title {
      font-size: 11px;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-tertiary);
      margin-bottom: 12px;
    }

    .profile-field {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      padding: 6px 0;
      border-bottom: 0.5px solid var(--border);
      font-size: 13px;
      gap: 16px;
    }

    .profile-field:last-child { border-bottom: none; }
    .profile-field span:first-child { color: var(--text-secondary); white-space: nowrap; }
    .profile-field span:last-child { color: var(--text-primary); font-weight: 500; text-align: right; }

    /* Copy box */
    .copy-box {
      display: none;
      background: var(--bg-secondary);
      border: 0.5px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 1.25rem;
      margin-bottom: 1.25rem;
    }

    .copy-box.show { display: block; }

    .copy-box-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
    }

    .copy-box-title {
      font-size: 11px;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-tertiary);
    }

    .copy-btn {
      font-size: 12px;
      padding: 4px 12px;
      border-radius: var(--radius-md);
      border: 0.5px solid var(--border-strong);
      background: var(--bg);
      color: var(--text-secondary);
      cursor: pointer;
    }

    .copy-btn:hover { background: var(--bg-tertiary); }

    .copy-text {
      font-size: 13px;
      color: var(--text-secondary);
      line-height: 1.7;
      white-space: pre-wrap;
      font-family: monospace;
      background: var(--bg);
      border: 0.5px solid var(--border);
      border-radius: var(--radius-md);
      padding: 12px;
    }

    .toast {
      display: none;
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--text-primary);
      color: var(--bg);
      font-size: 13px;
      padding: 8px 20px;
      border-radius: 999px;
      z-index: 999;
    }

    .toast.show { display: block; }

    @media (max-width: 500px) {
      body { padding: 1rem 0.75rem; }
      .card { padding: 1.1rem; }
      .btn-main { min-width: 160px; }
    }
  </style>
</head>
<body>
  <div class="page-wrap">

    <div class="page-header">
      <h1>Character builder</h1>
      <p>Year 9 financial literacy — bank accounts comic strip activity. Build your character by making selections below, then copy or print your character sheet to use in your comic.</p>
    </div>

    <div class="card">
      <div class="section-label">Character name</div>
      <div class="name-row">
        <input type="text" id="charName" placeholder="Type a name..." oninput="update()" />
        <button class="random-btn" onclick="randomName()">Random name</button>
      </div>

      <div class="section-label">Age</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'age','13')"><span class="emoji">🎒</span>13</div>
        <div class="chip" onclick="pick(this,'age','14')"><span class="emoji">🎒</span>14</div>
        <div class="chip" onclick="pick(this,'age','15')"><span class="emoji">🎒</span>15</div>
        <div class="chip" onclick="pick(this,'age','16')"><span class="emoji">🎒</span>16</div>
        <div class="chip" onclick="pick(this,'age','17')"><span class="emoji">🎒</span>17</div>
      </div>

      <div class="section-label">Job / income source</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'job','Barista')"><span class="emoji">☕</span>Barista</div>
        <div class="chip" onclick="pick(this,'job','Lawn mowing')"><span class="emoji">🌿</span>Lawn mowing</div>
        <div class="chip" onclick="pick(this,'job','Babysitter')"><span class="emoji">👶</span>Babysitter</div>
        <div class="chip" onclick="pick(this,'job','Retail assistant')"><span class="emoji">🛍️</span>Retail assistant</div>
        <div class="chip" onclick="pick(this,'job','Pizza delivery')"><span class="emoji">🍕</span>Pizza delivery</div>
        <div class="chip" onclick="pick(this,'job','Swim instructor')"><span class="emoji">🏊</span>Swim instructor</div>
        <div class="chip" onclick="pick(this,'job','Farm hand')"><span class="emoji">🌾</span>Farm hand</div>
        <div class="chip" onclick="pick(this,'job','Sells crafts online')"><span class="emoji">🎨</span>Sells crafts online</div>
        <div class="chip" onclick="pick(this,'job','Dog walker')"><span class="emoji">🐕</span>Dog walker</div>
        <div class="chip" onclick="pick(this,'job','Canteen assistant')"><span class="emoji">🥗</span>Canteen assistant</div>
      </div>

      <div class="section-label">How they're paid</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'pay','Always cash')"><span class="emoji">💵</span>Always cash</div>
        <div class="chip" onclick="pick(this,'pay','Mix of cash & transfer')"><span class="emoji">🔀</span>Mix of cash &amp; transfer</div>
        <div class="chip" onclick="pick(this,'pay','Employer wants to bank transfer')"><span class="emoji">🏦</span>Employer wants to bank transfer</div>
        <div class="chip" onclick="pick(this,'pay','Irregular / cash in hand')"><span class="emoji">🤝</span>Irregular / cash in hand</div>
      </div>

      <div class="section-label">Weekly income (approx)</div>
      <div class="income-row">
        <label>$</label>
        <input type="range" min="20" max="300" step="5" value="100" id="incomeSlider" oninput="update()" />
        <span class="income-val" id="incomeVal">$100 / week</span>
      </div>

      <hr class="section-divider" />

      <div class="section-label">Money personality</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'personality','Impulsive spender')"><span class="emoji">🛒</span>Impulsive spender</div>
        <div class="chip" onclick="pick(this,'personality','Careful saver')"><span class="emoji">🐷</span>Careful saver</div>
        <div class="chip" onclick="pick(this,'personality','Goal-driven')"><span class="emoji">🎯</span>Goal-driven</div>
        <div class="chip" onclick="pick(this,'personality','Disorganised')"><span class="emoji">😅</span>Disorganised</div>
        <div class="chip" onclick="pick(this,'personality','Entrepreneurial')"><span class="emoji">💡</span>Entrepreneurial</div>
        <div class="chip" onclick="pick(this,'personality','Sceptical of banks')"><span class="emoji">🤨</span>Sceptical of banks</div>
      </div>

      <div class="section-label">Saving towards...</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'goal','A car')"><span class="emoji">🚗</span>A car</div>
        <div class="chip" onclick="pick(this,'goal','A gaming PC / console')"><span class="emoji">🎮</span>Gaming PC / console</div>
        <div class="chip" onclick="pick(this,'goal','An overseas trip')"><span class="emoji">✈️</span>Overseas trip</div>
        <div class="chip" onclick="pick(this,'goal','A new phone')"><span class="emoji">📱</span>New phone</div>
        <div class="chip" onclick="pick(this,'goal','Driving lessons')"><span class="emoji">🪪</span>Driving lessons</div>
        <div class="chip" onclick="pick(this,'goal','Nothing specific yet')"><span class="emoji">🤷</span>Nothing specific</div>
        <div class="chip" onclick="pick(this,'goal','Helping with family bills')"><span class="emoji">🏠</span>Helping family</div>
        <div class="chip" onclick="pick(this,'goal','Growing their own business')"><span class="emoji">📈</span>Own business</div>
      </div>

      <div class="section-label">One key money habit (good or bad)</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'habit','Loses track of cash easily')"><span class="emoji">😬</span>Loses track of cash</div>
        <div class="chip" onclick="pick(this,'habit','Shops online constantly')"><span class="emoji">📦</span>Shops online constantly</div>
        <div class="chip" onclick="pick(this,'habit','Borrows from friends and forgets to repay')"><span class="emoji">😅</span>Forgets to repay friends</div>
        <div class="chip" onclick="pick(this,'habit','Tracks every dollar in a notebook')"><span class="emoji">📓</span>Tracks every dollar</div>
        <div class="chip" onclick="pick(this,'habit','Spends it all on the first day')"><span class="emoji">💸</span>Spends it all at once</div>
        <div class="chip" onclick="pick(this,'habit','Saves a fixed amount every week')"><span class="emoji">✅</span>Saves a fixed amount</div>
        <div class="chip" onclick="pick(this,'habit','Never knows their balance')"><span class="emoji">🙈</span>Never checks balance</div>
      </div>

      <div class="section-label">Character appearance</div>
      <div class="chip-group">
        <div class="chip" onclick="pick(this,'avatar','🧑')"><span class="emoji" style="font-size:20px">🧑</span></div>
        <div class="chip" onclick="pick(this,'avatar','👦')"><span class="emoji" style="font-size:20px">👦</span></div>
        <div class="chip" onclick="pick(this,'avatar','👧')"><span class="emoji" style="font-size:20px">👧</span></div>
        <div class="chip" onclick="pick(this,'avatar','🧒')"><span class="emoji" style="font-size:20px">🧒</span></div>
        <div class="chip" onclick="pick(this,'avatar','🧕')"><span class="emoji" style="font-size:20px">🧕</span></div>
        <div class="chip" onclick="pick(this,'avatar','👲')"><span class="emoji" style="font-size:20px">👲</span></div>
        <div class="chip" onclick="pick(this,'avatar','🧔')"><span class="emoji" style="font-size:20px">🧔</span></div>
        <div class="chip" onclick="pick(this,'avatar','👩')"><span class="emoji" style="font-size:20px">👩</span></div>
      </div>
    </div>

    <!-- Live preview -->
    <div class="section-label" style="padding: 0 2px; margin-bottom:8px;">Your character</div>
    <div class="preview-card" id="cardPreview">
      <p class="empty-hint">Start making selections above to build your character...</p>
    </div>

    <!-- Profile summary -->
    <div class="profile-card" id="profileCard">
      <div class="profile-title">Character summary</div>
      <div id="profileFields"></div>
    </div>

    <!-- Copy box -->
    <div class="copy-box" id="copyBox">
      <div class="copy-box-header">
        <span class="copy-box-title">Copy for your teacher / worksheet</span>
        <button class="copy-btn" onclick="copyText()">Copy to clipboard</button>
      </div>
      <pre class="copy-text" id="copyText"></pre>
    </div>

    <!-- Actions -->
    <div class="actions">
      <button class="btn-main" onclick="showCopy()">
        <i class="ti ti-copy" aria-hidden="true"></i> Copy character summary
      </button>
      <button class="btn-main" onclick="window.print()" style="background:var(--bg); color:var(--text-primary);">
        <i class="ti ti-printer" aria-hidden="true"></i> Print
      </button>
      <button class="btn-sec" onclick="resetAll()">Reset</button>
    </div>

  </div>

  <div class="toast" id="toast">Copied to clipboard!</div>

  <script>
    const state = { name:'', age:'', job:'', pay:'', personality:'', goal:'', habit:'', avatar:'🧑', income:100 };
    const names = ['Jordan','Mia','Dev','Aaliyah','Luca','Priya','Tane','Sophie','Marcus','Anika','Riley','Zara','Kai','Jess','Omar','Bella','Noah','Chloe','Felix','Maya','Sam','Ivy','Leo','Nadia'];

    function randomName() {
      const n = names[Math.floor(Math.random() * names.length)];
      document.getElementById('charName').value = n;
      state.name = n;
      update();
    }

    function pick(el, key, val) {
      document.querySelectorAll(`[onclick*=",'${key}',"]`).forEach(c => c.classList.remove('active'));
      el.classList.add('active');
      state[key] = val;
      update();
    }

    function update() {
      state.name = document.getElementById('charName').value.trim();
      state.income = parseInt(document.getElementById('incomeSlider').value);
      document.getElementById('incomeVal').textContent = '$' + state.income + ' / week';

      const preview = document.getElementById('cardPreview');
      const hasAny = state.name || state.job || state.age;

      if (!hasAny) {
        preview.innerHTML = '<p class="empty-hint">Start making selections above to build your character...</p>';
        document.getElementById('profileCard').classList.remove('show');
        document.getElementById('copyBox').classList.remove('show');
        return;
      }

      const displayName = state.name || 'Your character';
      const sub = [state.age ? 'Age ' + state.age : '', state.job].filter(Boolean).join(' · ');

      let tags = '';
      if (state.income) tags += `<span class="tag money">💰 $${state.income}/week</span>`;
      if (state.pay)    tags += `<span class="tag">💳 ${state.pay}</span>`;
      if (state.goal)   tags += `<span class="tag goal">🎯 ${state.goal}</span>`;
      if (state.habit)  tags += `<span class="tag habit">⚡ ${state.habit}</span>`;

      const personalityHTML = state.personality
        ? `<div class="card-personality"><div class="personality-label">Money personality</div>${state.personality}</div>`
        : '';

      preview.innerHTML = `
        <div class="card-top">
          <div class="avatar">${state.avatar}</div>
          <div style="flex:1">
            <div class="card-name">${displayName}</div>
            ${sub ? `<div class="card-sub">${sub}</div>` : ''}
            <div class="card-tags">${tags}</div>
          </div>
        </div>
        ${personalityHTML}
      `;

      buildProfile();
    }

    function buildProfile() {
      const fields = [
        ['Name',            state.name         || '—'],
        ['Age',             state.age          || '—'],
        ['Job',             state.job          || '—'],
        ["How they're paid", state.pay         || '—'],
        ['Weekly income',   state.income ? '$' + state.income + '/week' : '—'],
        ['Money personality', state.personality || '—'],
        ['Saving towards',  state.goal         || '—'],
        ['Key money habit', state.habit        || '—'],
      ];
      document.getElementById('profileFields').innerHTML =
        fields.map(([k,v]) => `<div class="profile-field"><span>${k}</span><span>${v}</span></div>`).join('');
      document.getElementById('profileCard').classList.add('show');
    }

    function showCopy() {
      const n = state.name || '(no name)';
      const text = `CHARACTER PROFILE — BANK ACCOUNTS ACTIVITY
==========================================
Name:              ${state.name || '—'}
Age:               ${state.age || '—'}
Job:               ${state.job || '—'}
How they're paid:  ${state.pay || '—'}
Weekly income:     $${state.income}/week
Money personality: ${state.personality || '—'}
Saving towards:    ${state.goal || '—'}
Key money habit:   ${state.habit || '—'}
==========================================`;
      document.getElementById('copyText').textContent = text;
      document.getElementById('copyBox').classList.add('show');
      document.getElementById('copyBox').scrollIntoView({ behavior: 'smooth', block: 'nearest' });
    }

    function copyText() {
      const text = document.getElementById('copyText').textContent;
      navigator.clipboard.writeText(text).then(() => {
        const toast = document.getElementById('toast');
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 2000);
      });
    }

    function resetAll() {
      Object.keys(state).forEach(k => { state[k] = k === 'avatar' ? '🧑' : k === 'income' ? 100 : ''; });
      document.getElementById('charName').value = '';
      document.getElementById('incomeSlider').value = 100;
      document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
      document.getElementById('copyBox').classList.remove('show');
      update();
    }

    update();
  </script>
</body>
</html>
