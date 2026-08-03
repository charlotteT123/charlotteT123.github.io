<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Year 9 Financial Literacy - Custom Character Mixer</title>
    <style>
        :root {
            --primary: #059669;
            --primary-hover: #047857;
            --background: #f1f5f9;
            --surface: #ffffff;
            --text: #0f172a;
            --text-light: #475569;
            --border: #cbd5e1;
            --accent: #d97706;
            --panel-bg: #f8fafc;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text);
            line-height: 1.5;
            padding: 2rem 1rem;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 2rem;
            border-bottom: 2px dashed var(--border);
            padding-bottom: 1.5rem;
        }

        h1 {
            font-size: 2rem;
            color: #064e3b;
            margin-bottom: 0.5rem;
        }

        .subtitle {
            color: var(--text-light);
            font-size: 1.05rem;
        }

        .grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
        }

        @media (min-width: 768px) {
            .grid {
                grid-template-columns: 1fr 1.2fr;
            }
        }

        .card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
            height: fit-content;
        }

        h2 {
            font-size: 1.15rem;
            margin-bottom: 1rem;
            padding-bottom: 0.4rem;
            border-bottom: 2px solid #e2e8f0;
            color: #0f172a;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .section-break {
            margin-top: 1.5rem;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        label {
            display: block;
            font-weight: 600;
            margin-bottom: 0.4rem;
            font-size: 0.85rem;
            color: #334155;
        }

        select, input {
            width: 100%;
            padding: 0.65rem;
            border: 1px solid var(--border);
            border-radius: 6px;
            background-color: #f8fafc;
            color: var(--text);
            font-size: 0.95rem;
            outline: none;
            transition: all 0.2s;
        }

        select:focus, input:focus {
            border-color: var(--primary);
            background-color: #fff;
            box-shadow: 0 0 0 3px rgba(5, 150, 105, 0.15);
        }

        button {
            width: 100%;
            padding: 0.8rem;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: background-color 0.2s;
            margin-top: 0.5rem;
        }

        button:hover {
            background-color: var(--primary-hover);
        }

        /* Profile Sheet Visuals */
        .profile-header {
            background: linear-gradient(135deg, #059669, #047857);
            color: white;
            padding: 1.25rem;
            border-radius: 8px;
            margin-bottom: 1.25rem;
        }

        .profile-header h3 {
            font-size: 1.6rem;
            margin-bottom: 0.25rem;
        }

        .meta-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem;
            margin-top: 0.75rem;
            font-size: 0.9rem;
            background: rgba(255, 255, 255, 0.15);
            padding: 0.75rem;
            border-radius: 6px;
        }

        .panel-guide {
            margin-top: 1rem;
        }

        .panel-box {
            background-color: var(--panel-bg);
            border: 1px solid var(--border);
            border-left: 5px solid var(--primary);
            padding: 1rem;
            border-radius: 4px;
            margin-bottom: 1rem;
        }

        .panel-title {
            font-weight: 700;
            font-size: 0.95rem;
            color: #1e293b;
            margin-bottom: 0.4rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .panel-tag {
            font-size: 0.7rem;
            background: #cbd5e1;
            padding: 0.15rem 0.4rem;
            border-radius: 4px;
            color: #334155;
            text-transform: uppercase;
            font-weight: 600;
        }

        .panel-box p {
            font-size: 0.9rem;
            color: #334155;
            line-height: 1.4;
        }

        .print-btn {
            background-color: #1e293b;
            margin-top: 0.5rem;
        }
        .print-btn:hover {
            background-color: #0f172a;
        }

        @media print {
            body { background: white; padding: 0; }
            .card:first-child, .print-btn { display: none; }
            .grid { grid-template-columns: 1fr; }
            .card { border: none; box-shadow: none; padding: 0; }
            .panel-box { page-break-inside: avoid; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>💸 Custom Character Profile Builder</h1>
        <p class="subtitle">Select individual pieces to generate a unique worksheet for your comic strip!</p>
    </header>

    <div class="grid">
        <!-- LEFT: Independent Selectors -->
        <div class="card">
            <h2>Step 1: Character Basics</h2>
            
            <div class="form-group">
                <label for="char-name">Character Name</label>
                <input type="text" id="char-name" value="Sam">
            </div>

            <div class="form-group">
                <label for="select-job">What is their job?</label>
                <select id="select-job">
                    <option value="Barista at a busy local café">Café Barista</option>
                    <option value="Babysitter and dog walker">Babysitter & Dog Walker</option>
                    <option value="Lawn mowing and neighborhood chores">Lawn Mowing Business</option>
                    <option value="Retail assistant at a clothing shop">Retail Assistant</option>
                    <option value="Pizza delivery rider">Pizza Delivery Rider</option>
                    <option value="Canteen assistant & online craft seller">Canteen & Craft Maker</option>
                    <option value="Weekend farm hand">Farm Hand</option>
                    <option value="Swim instructor at the aquatic center">Swim Instructor</option>
                </select>
            </div>

            <div class="form-group">
                <label for="select-income">Weekly Income Amount</label>
                <select id="select-income">
                    <option value="$50 - $100 per week">$50 - $100 per week</option>
                    <option value="$120 - $160 per week">$120 - $160 per week</option>
                    <option value="$180 - $220 per week">$180 - $220 per week</option>
                    <option value="An unpredictable amount depending on the season">Unpredictable (Seasonal)</option>
                </select>
            </div>

            <div class="form-group">
                <label for="select-personality">Money Personality</label>
                <select id="select-personality">
                    <option value="Spend now, stress later (Impulsive & loves online shopping)">Spend now, stress later</option>
                    <option value="Careful saver, but suspicious and doesn't trust the banking system">Careful saver (Suspicious)</option>
                    <option value="Informal and disorganized (Hides cash in random places)">Informal & disorganized</option>
                    <option value="Aspirational and style-conscious (Ready to scale up financially)">Aspirational & style-conscious</option>
                    <option value="Pulled in different directions (Wants to buy fun things but has bills to pay)">Pulled in different directions</option>
                    <option value="Entrepreneurial (Wants to split business money from personal money)">Entrepreneurial</option>
                    <option value="Goal-oriented and highly motivated (Saving for something big)">Goal-oriented & motivated</option>
                </select>
            </div>

            <h2 class="section-break">Step 2: Comic Plot Elements</h2>

            <div class="form-group">
                <label for="select-wall">The Big Problem (Panel 2 Wall)</label>
                <select id="select-wall">
                    <option value="wants to purchase concert tickets/sneakers online but has no debit card number.">Cannot buy online (No card)</option>
                    <option value="wants to register for their driver's license or a school trip but the portal won't accept physical cash.">Cannot pay digital portal (Cash refused)</option>
                    <option value="needs to send money quickly to a friend via app, but only has physical bills.">Cannot transfer money to a mate</option>
                    <option value="is told by their boss that they cannot get paid unless they provide a BSB and Account number.">Employer requires electronic transfer</option>
                    <option value="realizes a huge chunk of their saved cash went missing or was taken by a sibling from their hiding spot.">Cash gets lost or stolen</option>
                </select>
            </div>

            <div class="form-group">
                <label for="select-solution">The Chosen Banking Solution (Panel 4 & 6)</label>
                <select id="select-solution">
                    <option value="everyday">Everyday Transaction Account with a Debit Card</option>
                    <option value="savings">High-Interest Savings Account with 'Savings Buckets'</option>
                    <option value="combo">Everyday Account linked with an Automated Savings Vault</option>
                </select>
            </div>

            <button onclick="buildProfile()">Generate Comic Blueprint</button>
        </div>

        <!-- RIGHT: Blueprint Output Sheet -->
        <div class="card">
            <h2>📋 Student Character Profile Sheet</h2>
            
            <div id="profile-output">
                <div class="profile-header">
                    <h3 id="out-name">Sam</h3>
                    <div class="meta-grid">
                        <div><strong>Job:</strong> <span id="out-job">-</span></div>
                        <div><strong>Income:</strong> <span id="out-income">-</span></div>
                        <div style="grid-column: span 2;"><strong>Profile:</strong> <span id="out-personality">-</span></div>
                    </div>
                </div>

                <div class="panel-guide">
                    <div class="panel-box">
                        <div class="panel-title">Panel 1: Payday! Sort of... <span class="panel-tag">Scene Prompt</span></div>
                        <p id="p1-text"></p>
                    </div>

                    <div class="panel-box">
                        <div class="panel-title">Panel 2: I Just Want to Buy a Thing! <span class="panel-tag">The Conflict</span></div>
                        <p id="p2-text"></p>
                    </div>

                    <div class="panel-box">
                        <div class="panel-title">Panel 4: So Many Account Types?! <span class="panel-tag">The Strategy</span></div>
                        <p id="p4-text"></p>
                    </div>

                    <div class="panel-box">
                        <div class="panel-title">Panel 6: The Manager's Advice <span class="panel-tag">The Fix</span></div>
                        <p id="p6-text"></p>
                    </div>
                </div>
            </div>

            <button class="print-btn" onclick="window.print()">Print Blueprint for Class</button>
        </div>
    </div>
</div>

<script>
    const bankingText = {
        everyday: {
            p4: "Chooses an Everyday Transaction Account. This lets them safe-keep money, gives them a handy plastic Debit Card, and provides a clear BSB/Account number for digital tracks.",
            p6: "The manager recommends setting app spending alerts and checking mobile statements weekly to keep track of quick debit purchases before they add up."
        },
        savings: {
            p4: "Chooses a specialized High-Interest Savings Account. They decide to separate their basic cash from their goals by naming custom 'Digital Savings Buckets' in the app.",
            p6: "The manager explains that the bank safely protects and insures their money, meaning it can't be lost or stolen like hidden room cash—plus it earns interest!"
        },
        combo: {
            p4: "Sets up a linked account pair: an Everyday Account for receiving wages, immediately tethered to a secondary high-incentive Savings Account.",
            p6: "The manager suggests activating a 'Set & Forget' automatic scheduled transfer. On payday, 20% of their income automatically hops out of sight into the savings vault."
        }
    };

    function buildProfile() {
        // Capture individual field variables
        const name = document.getElementById('char-name').value || "The Character";
        const job = document.getElementById('select-job').value;
        const income = document.getElementById('select-income').value;
        const personality = document.getElementById('select-personality').value;
        const wall = document.getElementById('select-wall').value;
        const solutionKey = document.getElementById('select-solution').value;


        document.getElementById('out-name').innerText = name;
        document.getElementById('out-job').innerText = document.getElementById('select-job').options[document.getElementById('select-job').selectedIndex].text;
        document.getElementById('out-income').innerText = income.replace(' per week', '/wk');
        document.getElementById('out-personality').innerText = personality;

        document.getElementById('p1-text').innerText = `${name} gets paid for working as a ${job}. They pull in ${income}. Their money habit style is: ${personality}. In this panel, draw them holding physical money but thinking about where to hide it or how risky it feels to walk around with it.`;
        
        document.getElementById('p2-text').innerText = `Frustration points mount! ${name} tries to interact with the modern world, but everything stalls because they ${wall} Draw them looking stressed out while a computer error, a business manager, or a friend says no to their cash bills.`;
        
        document.getElementById('p4-text').innerText = `${name} does some research on account variations. ${bankingText[solutionKey].p4} Draw them selecting this account on their phone or app screen because it perfectly answers their lifestyle dilemma.`;
        
        document.getElementById('p6-text').innerText = `A professional bank manager sits down with them to map out an upgrade framework. ${bankingText[solutionKey].p6} Draw ${name} happily walking out of the bank or locking their phone with a secure, clear money plan in place!`;
    }

    window.onload = buildProfile;
</script>

</body>
</html>
