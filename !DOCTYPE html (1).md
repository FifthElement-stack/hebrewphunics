<!DOCTYPE html>  
<html lang="en" dir="ltr">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>HebrewPhunics - Master Modern Hebrew with Joy</title>  
    <link href="https://fonts.googleapis.com/css2?family=Assistant:wght@400;600;700&family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">  
    <style>  
        :root {  
            --israeli-blue: #003087;  
            --sky-blue: #40C4FF;  
            --energetic-orange: #FF6F61;  
            --celebration-gold: #F9A825;  
            --playful-pink: #FF006E;  
            --success-green: #64DD17;  
            --gentle-red: #EF476F;  
            --white: #FFFFFF;  
            --dark-bg: #001219;  
            --sidebar-width: 80px;  
            --sidebar-expanded: 240px;  
        }  
  
        * { margin:0; padding:0; box-sizing:border-box; }  
        body {  
            font-family: 'Poppins', sans-serif;  
            background: linear-gradient(135deg, #E3F2FD 0%, #F3E5F5 50%, #FFF9C4 100%);  
            min-height: 100vh; color:#333; overflow-x:hidden;  
        }  
        .app-container { display:flex; min-height:100vh; }  
        * { transition: all 0.3s cubic-bezier(0.4,0,0.2,1); }  
  
        /* === IMPROVED PREMIUM ALEPH MASCOT === */  
        .aleph-mascot {  
            position: relative; width:80px; height:110px; animation: mascotFloat 5s ease-in-out infinite;  
        }  
        .aleph-mascot.small  { width:70px; height:95px; }  
        .aleph-mascot.medium { width:90px; height:120px; }  
        .aleph-mascot.large  { width:110px; height:145px; }  
  
        .mascot-body {  
            position:absolute; inset:25% 8% 8% 8%;  
            background: linear-gradient(135deg, var(--sky-blue), var(--israeli-blue));  
            border-radius: 50% 50% 40% 40%; box-shadow: 0 8px 25px rgba(0,48,135,0.4), inset 0 -6px 12px rgba(255,255,255,0.2);  
        }  
        .mascot-head {  
            position:absolute; width:70%; height:70%; top:0; left:50%; transform:translateX(-50%);  
            background: #fff; border-radius:50%; box-shadow: inset 0 -8px 15px rgba(0,0,0,0.1), 0 8px 25px rgba(0,48,135,0.25);  
            border: 5px solid rgba(255,255,255,0.9);  
        }  
        .mascot-eye {  
            position:absolute; width:20%; height:32%; background:#0d1b4c; border-radius:50%; top:25%; animation:mascotBlink 6s infinite;  
        }  
        .mascot-eye-left  { left:18%; }  
        .mascot-eye-right { right:18%; }  
        .mascot-pupil { width:45%; height:55%; background:#fff; border-radius:50%; position:absolute; top:18%; left:25%; box-shadow: inset 0 2px 4px rgba(0,0,0,0.3); }  
        .mascot-smile {  
            width:60%; height:35%; border-bottom:6px solid #0d1b4c; border-radius:0 0 100px 100px;  
            position:absolute; bottom:18%; left:50%; transform:translateX(-50%);  
        }  
        .mascot-kippah {  
            width:60%; height:28%; background:linear-gradient(135deg, #F9A825, #DAA520);  
            border-radius:50% 50% 0 0; position:absolute; top:-15%; left:50%; transform:translateX(-50%);  
            box-shadow: 0 4px 12px rgba(249,168,37,0.5);  
        }  
        .mascot-arm {  
            position:absolute; width:20%; height:45%; background:linear-gradient(var(--sky-blue), var(--israeli-blue));  
            border-radius:15px; top:40%;  
        }  
        .mascot-arm-left  { left:-12%; transform:rotate(-30deg); }  
        .mascot-arm-right { right:-12%; transform:rotate(30deg); animation:mascotWave 4s infinite; }  
  
        @keyframes mascotFloat { 0%,100% { transform:translateY(0) rotate(0deg); } 50% { transform:translateY(-12px) rotate(2deg); } }  
        @keyframes mascotWave   { 0%,100% { transform:rotate(30deg); } 50% { transform:rotate(50deg); } }  
        @keyframes mascotBlink  { 0%,90%,100% { transform:scaleY(1); } 92%,98% { transform:scaleY(0.1); } }  
  
        /* === SIDEBAR & HEADER (your original, slightly polished) === */  
        .sidebar {  
            width:var(--sidebar-width); background:linear-gradient(180deg, var(--israeli-blue), #001F5C);  
            position:fixed; left:0; top:0; height:100vh; display:flex; flex-direction:column; align-items:center;  
            padding:20px 0; box-shadow:4px 0 25px rgba(0,0,0,0.12); z-index:1000; overflow:hidden;  
        }  
        .sidebar:hover { width:var(--sidebar-expanded); }  
        .sidebar-logo { margin-bottom:30px; cursor:pointer; display:flex; justify-content:center; }  
  
        /* ... your full original sidebar, header, content-card, modal, etc. styles go here ... */  
        /* I'm not repeating the entire 1000+ lines — keep your original and only replace the mascot part above */  
  
        /* === ROOT POPOVER (improved) === */  
        .root-popover {  
            position:fixed; background:white; border:3px solid var(--celebration-gold); border-radius:14px;  
            padding:18px; box-shadow:0 12px 35px rgba(0,0,0,0.3); z-index:10003; min-width:320px; max-width:420px;  
            display:none; font-size:15px; direction:rtl; text-align:right;  
        }  
        .root-popover.active { display:block; }  
        .root-word { padding:10px 0; border-bottom:1px solid #eee; display:flex; align-items:center; gap:14px; }  
        .root-word img { width:60px; height:60px; object-fit:cover; border-radius:8px; }  
  
        /* === WORD CARD IMAGE === */  
        .word-image img { width:90px; height:90px; object-fit:cover; border-radius:12px; }  
    </style>  
</head>  
<body>  
    <!-- Your full HTML structure (sidebar, header, tabs, modals) remains exactly the same except: -->  
  
    <!-- Replace your old aleph-character / header-aleph with this -->  
    <div class="sidebar-logo" onclick="switchTab('home')">  
        <div class="aleph-mascot small">  
            <div class="mascot-kippah"></div>  
            <div class="mascot-head">  
                <div class="mascot-eye mascot-eye-left"><div class="mascot-pupil"></div></div>  
                <div class="mascot-eye mascot-eye-right"><div class="mascot-pupil"></div></div>  
                <div class="mascot-smile"></div>  
            </div>  
            <div class="mascot-body"></div>  
            <div class="mascot-arm mascot-arm-left"></div>  
            <div class="mascot-arm mascot-arm-right"></div>  
        </div>  
    </div>  
  
    <!-- In header-left -->  
    <div class="header-left">  
        <div class="aleph-mascot medium">  
            <!-- same structure as above -->  
        </div>  
        <div class="header-title">  
            <h1>Hebrew<span style="color:var(--energetic-orange);">Phunics</span></h1>  
            <p>Master Hebrew with Joy & Phonics! 🎉</p>  
        </div>  
    </div>  
  
    <!-- Example: Alphabet modal now uses real images -->  
    <script>  
        // Updated exampleWords with real URLs  
        const exampleWords = {  
            'א': [  
                { heb: 'אַבָּא', trans: 'abba', eng: 'father', root: 'א-ב', img: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?w=200' },  
                { heb: 'אִמָּא', trans: 'ima', eng: 'mother', root: 'א-מ', img: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=200' },  
                { heb: 'אֹכֶל', trans: 'okhel', eng: 'food', root: 'א-כ-ל', img: 'https://images.unsplash.com/photo-1606857521015-7f9fcf423740?w=200' },  
                { heb: 'אָדוֹם', trans: 'adom', eng: 'red', root: 'א-ד-ם', img: 'https://images.unsplash.com/photo-1557683316-973673baf926?w=200' }  
            ],  
            // Add 150+ more as needed  
        };  
  
        // Improved showRootWords (real popover)  
        function showRootWords(root, event) {  
            event.stopPropagation();  
            const popover = document.createElement('div');  
            popover.className = 'root-popover active';  
            popover.style.left = `${event.clientX + 10}px`;  
            popover.style.top  = `${event.clientY + 10}px`;  
  
            // Example related words per root (expand this object)  
            const related = {  
                'א-ב': [  
                    { heb: 'אָב', eng: 'father (formal)', img: 'https://images.unsplash.com/photo-1552058544-f2b08422138a?w=100' },  
                    { heb: 'אֵם', eng: 'mother (formal)', img: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=100' }  
                ],  
                // add more roots here  
            }[root] || [];  
  
            popover.innerHTML = `  
                <strong>שורש: ${root}</strong><br><br>  
                ${related.map(w => `  
                    <div class="root-word">  
                        <img src="${w.img}" alt="${w.eng}">  
                        <div>${w.heb} – ${w.eng}</div>  
                    </div>  
                `).join('')}  
                <button onclick="this.parentElement.remove()" style="margin-top:12px; padding:8px 16px; background:var(--gentle-red); color:white; border:none; border-radius:8px; cursor:pointer;">סגור</button>  
            `;  
            document.body.appendChild(popover);  
  
            // Close on outside click  
            setTimeout(() => {  
                const handler = e => {  
                    if (!popover.contains(e.target)) {  
                        popover.remove();  
                        document.removeEventListener('click', handler);  
                    }  
                };  
                document.addEventListener('click', handler);  
            }, 100);  
        }  
  
        // Fixed modal close  
        function closeModal() {  
            document.getElementById('letter-modal').classList.remove('active');  
            document.querySelectorAll('.root-popover').forEach(p => p.remove());  
        }  
  
        document.addEventListener('click', e => {  
            const modal = document.getElementById('letter-modal');  
            if (modal.classList.contains('active') && !e.target.closest('.modal-content') && !e.target.closest('.letter-card')) {  
                closeModal();  
            }  
        });  
    </script>  
</body>  
</html>  
