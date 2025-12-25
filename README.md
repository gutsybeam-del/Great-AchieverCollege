<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Great Achiever International College | Elite Student Portal</title>
    <script src="https://remitademo.net/payment/v1/remita-pay-inline.bundle.js"></script>
    <style>
        /* --- INTEGRATED GITHUB & SCHOOL STYLES --- */
        :root { 
            --primary: #800000; 
            --navy: #001f3f; 
            --gold: #daa520; 
            --light: #f6f8fa; 
            --white: #ffffff;
            --color-accent-fg: #0969da;
            --color-success-fg: #1a7f37;
            --color-attention-fg: #9a6700;
            --color-danger-fg: #d1242f;
            --color-border-default: #d0d7de;
        }
        
        body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif; background: var(--light); margin: 0; display: flex; flex-direction: column; height: 100vh; overflow: hidden; color: #1F2328; }

        header { background: var(--primary); color: white; padding: 18px 30px; display: flex; justify-content: space-between; align-items: center; border-bottom: 4px solid var(--gold); box-shadow: 0 4px 10px rgba(0,0,0,0.1); z-index: 100; }
        .main-container { display: flex; flex: 1; overflow: hidden; }
        
        .sidebar { width: 280px; background: var(--navy); color: white; display: none; flex-direction: column; padding-top: 20px; border-right: 1px solid var(--color-border-default); }
        .sidebar a { padding: 16px 25px; color: #cbd5e1; text-decoration: none; display: flex; align-items: center; gap: 12px; cursor: pointer; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 14px; transition: 0.2s; }
        .sidebar a:hover { background: rgba(255,255,255,0.1); color: var(--gold); }

        .content { flex: 1; padding: 30px; overflow-y: auto; box-sizing: border-box; }
        .card { background: var(--white); padding: 30px; border-radius: 12px; box-shadow: 0 8px 24px rgba(149,157,165,0.2); margin-bottom: 25px; border: 1px solid var(--color-border-default); }
        .screen { display: none; max-width: 900px; margin: 0 auto; }
        .active-screen { display: block; animation: fadeIn 0.3s ease-in; }

        /* GITHUB MARKDOWN ALERTS */
        .markdown-alert { padding: 8px 16px; margin-bottom: 16px; color: inherit; border-left: .25em solid var(--color-border-default); background: #ffffff; border-radius: 6px; border-top: 1px solid var(--color-border-default); border-right: 1px solid var(--color-border-default); border-bottom: 1px solid var(--color-border-default); }
        .markdown-alert .markdown-alert-title { display: flex; font-weight: 600; align-items: center; line-height: 1; margin-bottom: 8px; }
        .markdown-alert.markdown-alert-note { border-left-color: var(--color-accent-fg); }
        .markdown-alert.markdown-alert-note .markdown-alert-title { color: var(--color-accent-fg); }
        .markdown-alert.markdown-alert-tip { border-left-color: var(--color-success-fg); }
        .markdown-alert.markdown-alert-tip .markdown-alert-title { color: var(--color-success-fg); }
        .markdown-alert.markdown-alert-warning { border-left-color: var(--color-attention-fg); }
        .markdown-alert.markdown-alert-warning .markdown-alert-title { color: var(--color-attention-fg); }

        /* UI ELEMENTS */
        .profile-pic { width: 120px; height: 120px; border-radius: 50%; border: 4px solid var(--gold); object-fit: cover; background: #eee; margin: 0 auto 15px; display: block; }
        input, select { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid var(--color-border-default); border-radius: 6px; font-size: 14px; box-sizing: border-box; }
        .btn { padding: 12px 20px; border: none; border-radius: 6px; cursor: pointer; font-weight: 600; width: 100%; transition: 0.2s; font-size: 14px; }
        .btn-primary { background: var(--primary); color: white; }
        .btn-gold { background: var(--gold); color: var(--navy); }
        .btn-success { background: var(--color-success-fg); color: white; }

        /* SPIN WHEEL */
        .wheel-container { text-align: center; }
        .wheel { width: 220px; height: 220px; border-radius: 50%; border: 10px solid var(--navy); margin: 20px auto; position: relative; transition: transform 4s cubic-bezier(0.15, 0, 0.15, 1); background: conic-gradient(#800000 0% 12%, #daa520 12% 25%, #001f3f 25% 37%, #10b981 37% 50%, #800000 50% 62%, #daa520 62% 75%, #001f3f 75% 87%, #10b981 87% 100%); }
        .wheel-pointer { width: 0; height: 0; border-left: 15px solid transparent; border-right: 15px solid transparent; border-top: 25px solid #000; position: absolute; top: -15px; left: 50%; transform: translateX(-50%); z-index: 10; }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @media print { .no-print { display: none !important; } .content { padding: 0; } .card { border: 1px solid #000; box-shadow: none; } }
    </style>
</head>
<body>

<header>
    <div style="font-weight: 800; font-size: 18px; letter-spacing: 1px;">GREAT ACHIEVER INTERNATIONAL COLLEGE</div>
    <div id="wallet-balance" style="background: rgba(255,255,255,0.15); padding: 8px 16px; border-radius: 20px; font-weight: 700; border: 1px solid var(--gold);">Wallet: ₦0.00</div>
</header>

<div class="main-container">
    <div class="sidebar" id="sidebar">
        <a onclick="showScreen('s-home')">🏠 Student Dashboard</a>
        <a onclick="showScreen('s-reg')">📝 Course Registration</a>
        <a onclick="showScreen('s-results')">📊 Academic Transcript</a>
        <a onclick="showScreen('s-spin')">🎡 Spin & Win Money</a>
        <a onclick="showScreen('s-withdraw')">💰 Fund Withdrawal</a>
        <a onclick="showScreen('s-settings')">⚙️ Portal Settings</a>
        <a onclick="location.reload()" style="color: #ff8080;">🚪 Secure Logout</a>
    </div>

    <div class="content">
        <div id="login-screen" class="screen active-screen card" style="max-width: 400px; margin-top: 50px;">
            <h2 style="text-align:center; color: var(--primary);">Student Portal Login</h2>
            <div class="markdown-alert markdown-alert-note">
                <p class="markdown-alert-title">Notice</p>
                <p style="font-size: 12px; margin:0;">Enter your Admission ID and the default password (1234) to begin.</p>
            </div>
            <input type="text" id="l-id" placeholder="Admission ID">
            <input type="password" id="l-pass" placeholder="Password">
            <button class="btn btn-primary" onclick="doLogin()">Login to Dashboard</button>
            <p onclick="adminGate()" style="text-align:center; cursor:pointer; color:gray; font-size:11px; margin-top:20px;">Administrator Entry</p>
        </div>

        <div id="admin-screen" class="screen card">
            <h2>Registrar: Enroll Student</h2>
            <input type="text" id="r-name" placeholder="Full Student Name">
            <input type="text" id="r-id" placeholder="Admission ID (e.g. 2025/001)">
            <select id="r-dept">
                <option value="Science">Senior Science</option>
                <option value="Art">Senior Art</option>
                <option value="Commerce">Senior Commerce</option>
                <option value="JSS">Junior Secondary (JSS)</option>
            </select>
            <button class="btn btn-primary" onclick="enroll()">Register Student</button>
            <button class="btn" style="margin-top:10px;" onclick="showScreen('login-screen')">Back to Login</button>
        </div>

        <div id="s-home" class="screen card" style="text-align:center;">
            <img src="" id="h-img" class="profile-pic">
            <h1 id="h-name" style="color:var(--primary); margin:0;">...</h1>
            <p id="h-dept" style="font-weight:bold; color:var(--gold); letter-spacing: 1px;">...</p>
            
            <div class="markdown-alert markdown-alert-tip" style="text-align:left; margin-top:30px;">
                <p class="markdown-alert-title">Welcome Back</p>
                <p>Welcome to Great Achiever International College. You can now register your courses or play the spinning game to earn rewards.</p>
            </div>
        </div>

        <div id="s-spin" class="screen card">
            <div class="wheel-container">
                <h2>Wheel of Fortune</h2>
                <div class="markdown-alert markdown-alert-note" style="text-align:left;">
                    <p class="markdown-alert-title">Rules</p>
                    <p style="font-size: 13px;">Each spin costs <b>₦10</b>. Use your 5 daily free spins first! Highest reward is <b>₦100</b>.</p>
                </div>
                <p>Spins Left: <b id="spin-count" style="color:var(--primary); font-size: 20px;">0</b></p>
                <div style="position:relative; width:fit-content; margin:auto;">
                    <div class="wheel-pointer"></div>
                    <div class="wheel" id="wheel"></div>
                </div>
                <button class="btn btn-success" id="btn-spin" onclick="startSpin()">SPIN NOW (₦10)</button>
                <button class="btn btn-gold" style="margin-top:10px;" onclick="buySpins()">Buy 30 Spins (₦500 via Remita)</button>
            </div>
        </div>

        <div id="s-withdraw" class="screen card">
            <h2>Withdraw Earnings</h2>
            <div class="markdown-alert markdown-alert-warning">
                <p class="markdown-alert-title">Important</p>
                <p>The minimum withdrawal amount is <b>₦2,000</b>. Ensure bank details are correct.</p>
            </div>
            <label>Amount (₦)</label>
            <input type="number" id="w-amt" placeholder="0.00">
            <label>Bank Name</label>
            <input type="text" id="w-bank" placeholder="e.g. Zenith Bank">
            <label>Account Number</label>
            <input type="text" id="w-acct" placeholder="10 Digits">
            <button class="btn btn-primary" onclick="handleWithdraw()">Submit Request</button>
        </div>

        <div id="s-reg" class="screen card">
            <h2>Course Registration Form</h2>
            <div id="sub-box" style="display:grid; grid-template-columns:1fr 1fr; gap:15px; background: #f9f9f9; padding: 20px; border-radius: 8px;"></div>
            <button class="btn btn-primary" onclick="saveCourses()" style="margin-top:20px;">Save Course List</button>
        </div>

        <div id="s-results" class="screen card">
            <div style="display:flex; justify-content:space-between; align-items:center;" class="no-print">
                <h2>Term Transcript</h2>
                <button class="btn btn-primary" style="width:auto;" onclick="window.print()">Print Official PDF</button>
            </div>
            <hr>
            <div id="res-sheet" style="padding-top:20px;">Register courses to generate transcript.</div>
        </div>

        <div id="s-settings" class="screen card">
            <h2>Profile Settings</h2>
            <div style="text-align:center; padding-bottom: 20px;">
                <img src="" id="set-img" class="profile-pic">
                <p style="font-size: 12px; color: gray;">Upload a clear passport photograph</p>
                <input type="file" id="file-in" accept="image/*" onchange="previewImg()" style="width: 250px;">
                <button class="btn btn-primary" style="width:auto; display: block; margin: 10px auto;" onclick="savePhoto()">Save Passport</button>
            </div>
            <hr>
            <h3>Change Portal Password</h3>
            <input type="password" id="set-p1" placeholder="New Password">
            <input type="password" id="set-p2" placeholder="Confirm Password">
            <button class="btn btn-gold" onclick="savePass()">Update Security Details</button>
        </div>
    </div>
</div>

<script>
    let db = JSON.parse(localStorage.getItem('GAIC_ULTIMATE_DB')) || [];
    let user = null;
    let tempImg = "";

    const subjects = {
        "Science": ["Physics", "Chemistry", "Biology", "Further Maths", "General Maths", "English", "Geography", "Agric Science"],
        "Art": ["Government", "Literature", "History", "CRS/IRS", "General Maths", "English", "Yoruba/Igbo/Hausa", "Civic Education"],
        "Commerce": ["Financial Accounting", "Commerce", "Economics", "Marketing", "General Maths", "English", "Book Keeping"],
        "JSS": ["Basic Tech", "Basic Science", "Social Studies", "Home Economics", "Maths", "English", "Business Studies", "P.H.E"]
    };

    function showScreen(id) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active-screen'));
        document.getElementById(id).classList.add('active-screen');
        if(id === 's-reg') loadSubs();
        if(id === 's-results') loadResults();
        if(id === 's-settings') loadSettings();
        updateUI();
    }

    function doLogin() {
        const id = document.getElementById('l-id').value;
        const pass = document.getElementById('l-pass').value;
        user = db.find(x => x.id === id && x.pass === pass);
        if(user) {
            if(!user.wallet) user.wallet = 0;
            if(user.spins === undefined) user.spins = 5;
            document.getElementById('sidebar').style.display = 'flex';
            showScreen('s-home');
        } else alert("Invalid Admission ID or Password.");
    }

    function updateUI() {
        if(!user) return;
        document.getElementById('wallet-balance').innerText = "Wallet: ₦" + user.wallet.toLocaleString();
        document.getElementById('h-name').innerText = user.name;
        document.getElementById('h-dept').innerText = user.dept.toUpperCase() + " DEPARTMENT";
        document.getElementById('h-img').src = user.img || "https://via.placeholder.com/120";
        document.getElementById('spin-count').innerText = user.spins;
    }

    // --- SPIN LOGIC ---
    function startSpin() {
        if(user.spins <= 0 && user.wallet < 10) return alert("You need ₦10 to spin or buy more spins!");
        const btn = document.getElementById('btn-spin');
        const wheel = document.getElementById('wheel');
        btn.disabled = true;

        if(user.spins > 0) user.spins--; else user.wallet -= 10;

        const rotation = Math.floor(Math.random() * 360) + 1800; 
        wheel.style.transform = `rotate(${rotation}deg)`;

        setTimeout(() => {
            const prizes = [10, 50, 0, 100, 5, 20, 0, 2];
            const prize = prizes[Math.floor(Math.random() * prizes.length)];
            user.wallet += prize;
            saveData();
            updateUI();
            alert(prize > 0 ? `🎊 Congratulations! You won ₦${prize}.` : "Better luck next time!");
            btn.disabled = false;
        }, 4100);
    }

    function buySpins() {
        var paymentEngine = RmPaymentEngine.init({
            key: "REVXU0VSfDQwMjc1fGYzY2M0Y2VlYTNkM2IyZTM5YTZlMGRhNmU3YmU5YWVl", 
            transactionId: "GAIC-SPIN-" + Date.now(),
            amount: 500,
            firstName: user.name,
            email: user.id + "@school.com",
            onSuccess: function (response) {
                user.spins += 30;
                saveData();
                updateUI();
                alert("30 Extra Spins added to your account!");
            }
        });
        paymentEngine.showPaymentWidget();
    }

    // --- WITHDRAWAL ---
    function handleWithdraw() {
        const amt = document.getElementById('w-amt').value;
        if(user.wallet < 2000) return alert("You must reach ₦2,000 to withdraw.");
        if(amt < 2000 || amt > user.wallet) return alert("Invalid amount selected.");
        user.wallet -= amt;
        saveData();
        updateUI();
        alert("Withdrawal request for ₦" + amt + " has been sent to the bursary office.");
    }

    // --- SETTINGS ---
    function loadSettings() {
        document.getElementById('set-img').src = user.img || "https://via.placeholder.com/120";
    }

    function previewImg() {
        const file = document.getElementById('file-in').files[0];
        const reader = new FileReader();
        reader.onloadend = () => { tempImg = reader.result; document.getElementById('set-img').src = tempImg; };
        if(file) reader.readAsDataURL(file);
    }

    function savePhoto() {
        if(!tempImg) return alert("Please select a file first.");
        user.img = tempImg;
        saveData();
        alert("Passport Updated Successfully.");
    }

    function savePass() {
        const p1 = document.getElementById('set-p1').value;
        const p2 = document.getElementById('set-p2').value;
        if(p1.length < 4) return alert("Password too short.");
        if(p1 !== p2) return alert("Passwords do not match.");
        user.pass = p1;
        saveData();
        alert("Security Password Updated.");
    }

    // --- COURSES & RESULTS ---
    function loadSubs() {
        const box = document.getElementById('sub-box');
        box.innerHTML = "";
        subjects[user.dept].forEach(s => {
            const chk = (user.reg && user.reg.includes(s)) ? "checked" : "";
            box.innerHTML += `<div style="display:flex; align-items:center; gap:10px;">
                <input type="checkbox" value="${s}" ${chk} class="sub-ch" style="width:auto;"> <label>${s}</label>
            </div>`;
        });
    }

    function saveCourses() {
        let sel = [];
        document.querySelectorAll('.sub-ch:checked').forEach(i => sel.push(i.value));
        if(sel.length === 0) return alert("Select at least one subject.");
        user.reg = sel;
        saveData();
        alert("Course Registration Saved.");
    }

    function loadResults() {
        const box = document.getElementById('res-sheet');
        if(!user.reg || user.reg.length === 0) return;
        let html = `<div style="text-align:center;"><h3>GREAT ACHIEVER INTERNATIONAL COLLEGE</h3><p>Official Academic Transcript</p></div>`;
        html += `<p><b>Name:</b> ${user.name} | <b>ID:</b> ${user.id}</p>`;
        html += `<table border="1" style="width:100%; border-collapse:collapse; margin-top:20px;">
            <tr style="background:#eee;"><th>Subject</th><th>CA (30)</th><th>Exam (70)</th><th>Total (100)</th><th>Grade</th></tr>`;
        user.reg.forEach(s => {
            html += `<tr><td>${s}</td><td>28</td><td>54</td><td>82</td><td>A1</td></tr>`;
        });
        box.innerHTML = html + "</table><p style='margin-top:30px; font-size:11px;'>This document is electronically generated and requires no signature.</p>";
    }

    function enroll() {
        const name = document.getElementById('r-name').value;
        const id = document.getElementById('r-id').value;
        const dept = document.getElementById('r-dept').value;
        if(!name || !id) return alert("Fill all fields.");
        db.push({ name, id, dept, pass: "1234", wallet: 0, spins: 5, img: "", reg: [] });
        saveData();
        alert("Student Enrollment Successful!");
    }

    function saveData() { localStorage.setItem('GAIC_ULTIMATE_DB', JSON.stringify(db)); }
    function adminGate() { if(prompt("Admin Key:") === "777") showScreen('admin-screen'); }
</script>
</body>
</html>
