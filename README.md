# izy-kiosque-
Izy Kiosque shop 
<!DOCTYPE html>
<html lang="mg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IZY KIOSQUE | PRO GAMING</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root { 
            --p: #ff004c; --s: #00f2ff; --bg: #05070a; --c: #0d1117; --t: #ffffff; 
            --neon: 0 0 10px var(--s), 0 0 20px var(--s);
            --neon-p: 0 0 10px var(--p), 0 0 20px var(--p);
        }
        .light { --bg: #f0f2f5; --c: #ffffff; --t: #121212; }
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif; transition: 0.3s; }
        body { background: var(--bg); color: var(--t); overflow-x: hidden; }

        header { 
            padding: 15px; background: rgba(0,0,0,0.95); border-bottom: 3px solid var(--p); 
            display: flex; justify-content: space-between; align-items: center; 
            position: sticky; top: 0; z-index: 1000; box-shadow: var(--neon-p);
        }
        .logo { width: 50px; height: 50px; border-radius: 50%; border: 2px solid var(--s); box-shadow: var(--neon); }
        .nav-icons { display: flex; gap: 20px; font-size: 24px; cursor: pointer; }

        .container { padding: 20px; max-width: 800px; margin: auto; }
        .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        
        .card { 
            background: var(--c); border-radius: 15px; padding: 15px; text-align: center; 
            border: 2px solid rgba(0,242,255,0.1); cursor: pointer;
        }
        .card:hover { border-color: var(--s); box-shadow: var(--neon); transform: translateY(-5px); }
        .card img { width: 100%; border-radius: 12px; height: 120px; object-fit: cover; margin-bottom: 15px; }

        .overlay { position: fixed; inset: 0; background: rgba(5,7,10,0.98); display: none; z-index: 2000; padding: 20px; overflow-y: auto; }
        .step { 
            max-width: 420px; margin: 30px auto; background: var(--c); padding: 30px; 
            border-radius: 20px; border: 2px solid var(--s); text-align: center; box-shadow: var(--neon);
        }

        .btn { 
            background: linear-gradient(90deg, var(--p), #ff8a00); color: #fff; border: none; 
            padding: 14px; border-radius: 10px; width: 100%; font-weight: 900; cursor: pointer; 
            margin-top: 10px; text-transform: uppercase; font-family: 'Orbitron'; font-size: 0.85rem;
            display: flex; justify-content: center; align-items: center; letter-spacing: 1px;
        }
        .btn:active { transform: scale(0.95); }

        .input { 
            width: 100%; padding: 12px; margin: 10px 0; background: #000; border: 2px solid #333; 
            color: var(--s); border-radius: 8px; text-align: center; font-size: 1.1rem; font-family: 'Orbitron';
        }

        /* TABLE UI */
        table { width: 100%; border-collapse: separate; border-spacing: 0 10px; margin-bottom: 80px; }
        tr { background: rgba(255,255,255,0.05); }
        td { padding: 15px 10px; font-weight: bold; border-radius: 10px; vertical-align: middle; }
        .item-icon { width: 32px; height: 32px; vertical-align: middle; margin-right: 12px; border-radius: 5px; }
        .txt-s { color: var(--s); font-family: 'Orbitron'; text-shadow: var(--neon); }

        /* SCHEDULE UI */
        .sch-box { text-align: left; font-size: 0.9rem; line-height: 1.6; }
        .day-title { color: var(--s); font-weight: 900; font-family: 'Orbitron'; display: block; margin-top: 15px; border-left: 4px solid var(--p); padding-left: 10px; background: rgba(255,0,76,0.1); padding: 5px 10px; }

        /* ADMIN DASHBOARD */
        .admin-card { 
            background: #000; padding: 15px; border-radius: 12px; margin-bottom: 15px; 
            border: 1px solid var(--s); text-align: left; position: relative; box-shadow: inset 0 0 10px rgba(0,242,255,0.1);
        }
        .admin-btns { display: flex; gap: 10px; margin-top: 15px; }
        .btn-check { flex: 1; padding: 12px; border-radius: 8px; border: none; font-weight: bold; cursor: pointer; font-size: 1.3rem; }
        .b-ok { background: #28a745; color: white; box-shadow: 0 0 10px #28a745; }
        .b-no { background: #dc3545; color: white; box-shadow: 0 0 10px #dc3545; }
        .status-mark { position: absolute; top: 10px; right: 15px; font-size: 1.8rem; }

        .close-btn { position: fixed; bottom: 30px; right: 30px; background: var(--p); color: #fff; width: 60px; height: 60px; border-radius: 50%; display: none; align-items: center; justify-content: center; font-size: 30px; z-index: 5000; cursor: pointer; box-shadow: var(--neon-p); }
    </style>
</head>
<body>

<header>
    <div class="nav-icons">
        <span onclick="openAdmin()">🖥️</span>
        <span onclick="openTime()">🕓</span>
    </div>
    <div style="text-align: center;">
        <img src="https://i.supaimg.com/b5165604-a0b1-44eb-8a7e-04be8d9a067c/2f1acf12-9c31-4b4c-a46f-fd480fd2aacc.jpg" class="logo">
        <p style="font-family:'Orbitron'; font-size: 0.75rem; color: var(--s); letter-spacing: 2px; margin-top: 5px;">IZY KIOSQUE</p>
    </div>
    <div onclick="toggleTheme()" id="themeIcon" style="cursor: pointer; font-size: 24px; filter: drop-shadow(0 0 5px var(--s));">🌙</div>
</header>

<div class="container">
    <div class="grid">
        <div class="card" onclick="openMenu('ff')">
            <img src="https://i.supaimg.com/b5165604-a0b1-44eb-8a7e-04be8d9a067c/ea8e9490-5070-4d2f-a4e5-3d0e87b794c6.gif">
            <p style="font-family:'Orbitron'; font-weight:900; margin-bottom: 10px;">FREE FIRE</p>
            <button class="btn">HIDITRA</button>
        </div>
        <div class="card" onclick="openMenu('pubg')">
            <img src="https://i.supaimg.com/b5165604-a0b1-44eb-8a7e-04be8d9a067c/8028d2fb-ee1a-4a6f-a524-6c988d7cca6e.gif">
            <p style="font-family:'Orbitron'; font-weight:900; margin-bottom: 10px;">PUBG MOBILE</p>
            <button class="btn">HIDITRA</button>
        </div>
    </div>
</div>

<div id="timeOverlay" class="overlay">
    <div class="step">
        <h2 style="font-family:'Orbitron'; color:var(--s); margin-bottom:15px; letter-spacing: 2px;">🕓 HEURE D'OUVERTURE</h2>
        <div class="sch-box">
            <span class="day-title">🌅 LUNDI / MARDI / JEUDI / VENDREDI</span>
            🕛 12H00 – 13H45<br>🌙 18H00 – 23H00
            <span class="day-title">🌤️ MERCREDI</span>
            🕛 12H00 – 23H00
            <span class="day-title">🎉 SAMEDI / 🎊 DIMANCHE</span>
            🕛 24H/24
        </div>
        <button class="btn" onclick="closeAll()" style="margin-top:25px;">OK</button>
    </div>
</div>

<div id="menuOverlay" class="overlay">
    <div id="content" style="margin-top:40px; max-width: 600px; margin-left: auto; margin-right: auto;"></div>
</div>

<div id="checkOverlay" class="overlay" style="z-index:4000;">
    <div class="step" id="s1">
        <h2 id="c-name" style="font-family:'Orbitron'; color:var(--s)"></h2>
        <div class="txt-s" id="c-price" style="font-size: 2.2rem; margin:20px 0;"></div>
        <button class="btn" onclick="go(2)">HIDITRA</button>
    </div>
    <div class="step" id="s2" style="display:none;">
        <h2 style="font-family:'Orbitron'; color:var(--s)">PLAYER ID</h2>
        <input type="number" id="p-uid" class="input" placeholder="UID PLAYER">
        <input type="text" id="p-psd" class="input" placeholder="PSEUDO IN-GAME">
        <button class="btn" onclick="go(3)">HIDITRA</button>
    </div>
    <div class="step" id="s3" style="display:none;">
        <h2 style="font-family:'Orbitron'; color:var(--s)">PAYEMENT</h2>
        <div style="display:flex; gap:10px; margin-bottom:15px;">
            <button class="btn" onclick="setPay('orange')" style="margin:0; background:#ff6600">ORANGE</button>
            <button class="btn" onclick="setPay('mvola')" style="margin:0; background:#ffcc00; color:#000">M-VOLA</button>
        </div>
        <div id="payDetails" style="display:none; text-align:left; background:rgba(0,0,0,0.6); padding:15px; border-radius:12px; border:1px solid var(--s);">
            <p style="font-size:0.8rem; opacity:0.8;">Anarana handefasana:</p>
            <b id="p-own" style="color:var(--p); font-size:1.1rem; font-family:'Orbitron';"></b>
            <p style="font-size:0.8rem; opacity:0.8; margin-top:10px;">Laharana:</p>
            <b id="p-num" class="txt-s" style="font-size:1.4rem;"></b>
            <div id="ussd" style="font-family:monospace; font-size:0.8rem; margin:15px 0; border:1px dashed var(--s); padding:10px; color:var(--s); background:#000; text-align: center;"></div>
            <button class="btn" style="background:#28a745" onclick="dial()">🚀 TRANSFERT RAPIDE</button>
            <input type="text" id="p-ref" class="input" placeholder="REFERENCE TRANSACTION">
            <button class="btn" onclick="finish()">HIDITRA</button>
        </div>
    </div>
    <div class="step" id="s4" style="display:none;">
        <div style="font-size:5rem; margin-bottom: 10px;">⚡</div>
        <h2 style="font-family:'Orbitron'; color:var(--s)">COMMANDÉ !</h2>
        <button class="btn" onclick="sendSMS()">📩 ANDEFA SMS POROFO</button>
        <button class="btn" onclick="closeAll()" style="background:#333">OK</button>
    </div>
</div>

<div id="adminOverlay" class="overlay">
    <div class="step" id="adminLogin">
        <h2 style="font-family:'Orbitron'; color:var(--p)">🔐 ADMIN PANEL</h2>
        <input type="password" id="a-pass" class="input" placeholder="PASSCODE">
        <button class="btn" onclick="accessAdmin()">HIDITRA</button>
    </div>
    <div id="adminDash" style="display:none; max-width:500px; margin:auto;">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom: 20px;">
             <h2 style="font-family:'Orbitron'; color:var(--s)">🖥️ ORDERS</h2>
             <button onclick="clearAll()" style="background:none; border:1px solid red; color:red; padding:6px 12px; border-radius:5px; font-size:0.75rem; font-weight: bold; cursor: pointer;">RESET DATA</button>
        </div>
        <div id="feed"></div>
        <button class="btn" onclick="closeAll()" style="background:#333; margin-top: 30px;">HIALA</button>
    </div>
</div>

<div id="closeBtn" class="close-btn" onclick="closeAll()">×</div>

<script>
    let cur = {}; let pay = ''; let code = '';
    const PASS = "20202404";
    const TARGET = "0323148302";
    const IMG_DIA = "https://i.supaimg.com/b5165604-a0b1-44eb-8a7e-04be8d9a067c/6433f700-723c-42eb-8610-a0f8207d9490.png";
    const IMG_UC = "https://i.supaimg.com/b5165604-a0b1-44eb-8a7e-04be8d9a067c/723a2682-2f46-486e-82d6-d0f5713c7385.jpg";

    function toggleTheme() {
        document.body.classList.toggle('light');
        document.getElementById('themeIcon').innerText = document.body.classList.contains('light') ? '☀️' : '🌙';
    }

    function openTime() { document.getElementById('timeOverlay').style.display='block'; document.getElementById('closeBtn').style.display='flex'; }
    function closeAll() { document.querySelectorAll('.overlay').forEach(o => o.style.display='none'); document.getElementById('closeBtn').style.display='none'; reset(); }
    
    function openMenu(t) {
        document.getElementById('menuOverlay').style.display='block';
        document.getElementById('closeBtn').style.display='flex';
        let d = []; let img = (t==='ff') ? IMG_DIA : IMG_UC;
        if(t==='ff') d = [{q:"110 💎",p:"4 750 Ar"},{q:"220 💎",p:"9 500 Ar"},{q:"330 💎",p:"14 250 Ar"},{q:"440 💎",p:"19 000 Ar"},{q:"530 💎",p:"24 500 Ar"},{q:"1080 💎",p:"46 500 Ar"},{q:"2200 💎",p:"93 500 Ar"},{q:"5600 💎",p:"224 500 Ar"}];
        else d = [{q:"60 UC",p:"4 500 Ar"},{q:"180 UC",p:"12 500 Ar"},{q:"240 UC",p:"16 600 Ar"},{q:"325 UC",p:"20 700 Ar"},{q:"445 UC",p:"29 000 Ar"},{q:"505 UC",p:"33 000 Ar"},{q:"660 UC",p:"41 700 Ar"},{q:"840 UC",p:"53 700 Ar"}];
        
        let h = `<table>`;
        d.forEach(i => {
            h += `<tr><td><img src="${img}" class="item-icon">${i.q}</td><td class="txt-s" style="text-align:right">${i.p}</td><td style="text-align:right"><button class="btn" style="width:75px; margin:0; padding:8px;" onclick="start('${i.q}','${i.p}','${t.toUpperCase()}')">HIDITRA</button></td></tr>`;
        });
        document.getElementById('content').innerHTML = h + `</table>`;
    }

    function start(n, p, g) {
        cur = { n, p, g }; document.getElementById('c-name').innerText = n;
        document.getElementById('c-price').innerText = p;
        document.getElementById('checkOverlay').style.display='block';
    }

    function go(n) { document.querySelectorAll('.step').forEach(s => s.style.display='none'); document.getElementById('s'+n).style.display='block'; }

    function setPay(m) {
        pay = m; document.getElementById('payDetails').style.display='block';
        let pr = cur.p.replace(/[^0-9]/g, '');
        if(m==='orange') {
            document.getElementById('p-own').innerText = "JEAN PIERRE";
            document.getElementById('p-num').innerText = "032 31 483 02";
            code = `#144*1*1*0323148302*0323148302*${pr}*1#`;
        } else {
            document.getElementById('p-own').innerText = "ESSA ALIDA";
            document.getElementById('p-num').innerText = "034 54 004 08";
            code = `*111*1*2*1*0345400408*${pr}*1*0#`;
        }
        document.getElementById('ussd').innerText = code;
    }

    function dial() { window.location.href = "tel:" + encodeURIComponent(code); }

    function finish() {
        const ref = document.getElementById('p-ref').value;
        if(!ref) return alert("Ampidiro ny REFERENCE!");
        cur.uid = document.getElementById('p-uid').value; cur.psd = document.getElementById('p-psd').value;
        cur.ref = ref; cur.m = pay.toUpperCase();
        cur.id = Date.now(); cur.status = '';
        let os = JSON.parse(localStorage.getItem('izy_orders') || '[]');
        os.unshift({...cur}); localStorage.setItem('izy_orders', JSON.stringify(os));
        go(4);
    }

    function sendSMS() {
        const m = `IZY KIOSQUE\n${cur.g}\n${cur.n}\nID:${cur.uid}\nPSD:${cur.psd}\nREF:${cur.ref}\nPAY:${cur.m}`;
        window.location.href = `sms:${TARGET}?body=${encodeURIComponent(m)}`;
    }

    function openAdmin() { document.getElementById('adminOverlay').style.display='block'; document.getElementById('closeBtn').style.display='flex'; }
    
    function accessAdmin() {
        if(document.getElementById('a-pass').value === PASS) {
            document.getElementById('adminLogin').style.display='none';
            document.getElementById('adminDash').style.display='block'; renderAdmin();
        } else { alert("PASSCODE DISO!"); }
    }

    function setStatus(id, stat) {
        let os = JSON.parse(localStorage.getItem('izy_orders') || '[]');
        let i = os.findIndex(o => o.id === id);
        if(i !== -1) { os[i].status = stat; localStorage.setItem('izy_orders', JSON.stringify(os)); renderAdmin(); }
    }

    function renderAdmin() {
        const os = JSON.parse(localStorage.getItem('izy_orders') || '[]');
        let h = '';
        os.forEach(o => {
            let mark = o.status === 'ok' ? '✅' : (o.status === 'no' ? '❌' : '');
            h += `<div class="admin-card">
                <span class="status-mark">${mark}</span>
                <b style="color:var(--p); font-family:'Orbitron'; font-size:0.95rem;">${o.g} - ${o.n}</b><br>
                👤 ${o.psd} (${o.uid})<br>
                REF: <span style="color:var(--s); font-weight: bold;">${o.ref}</span> [${o.m}]
                <div class="admin-btns">
                    <button class="btn-check b-ok" onclick="setStatus(${o.id}, 'ok')">✅</button>
                    <button class="btn-check b-no" onclick="setStatus(${o.id}, 'no')">❌</button>
                </div>
            </div>`;
        });
        document.getElementById('feed').innerHTML = h || '<p style="text-align:center; opacity:0.5; margin-top: 20px;">Tsy misy commande voaray.</p>';
    }

    function clearAll() { if(confirm("Hofafana daholo ny commande rehetra?")) { localStorage.removeItem('izy_orders'); renderAdmin(); } }

    function reset() {
        for(let i=1;i<=4;i++) document.getElementById('s'+i).style.display='none';
        document.getElementById('s1').style.display='block';
        document.getElementById('payDetails').style.display='none';
        document.getElementById('a-pass').value='';
    }
</script>
</body>
</html>
