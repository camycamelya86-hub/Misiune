<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cami & Emi - Connect</title>
    
    <!-- Pictograme pentru ecranul principal (Home Screen Icon) -->
    <link rel="apple-touch-icon" sizes="180x180" href="https://img.icons8.com/fluent/180/000000/hearts.png">
    <link rel="icon" type="image/png" sizes="32x32" href="https://img.icons8.com/fluent/32/000000/hearts.png">
    
    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #ff758c 0%, #ff7eb3 100%);
            --bg-color: #faf6f7;
            --card-bg: #ffffff;
            --text-main: #2d3436;
            --text-muted: #636e72;
            --accent-pink: #ffeef1;
            --border-radius: 24px;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            padding-bottom: 40px;
            -webkit-font-smoothing: antialiased;
        }

        /* Login Screen */
        #loginScreen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            padding: 20px;
            box-sizing: border-box;
        }

        .login-card {
            background: var(--card-bg);
            padding: 40px 24px;
            border-radius: var(--border-radius);
            box-shadow: 0 20px 40px rgba(255, 117, 140, 0.08);
            text-align: center;
            width: 100%;
            max-width: 340px;
        }

        .login-card h2 {
            font-size: 1.8rem;
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .login-card p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 25px;
        }

        .login-card input {
            width: 100%;
            padding: 16px;
            border: 1px solid #f3e6e8;
            border-radius: 30px;
            margin-bottom: 20px;
            font-size: 1rem;
            text-align: center;
            outline: none;
            box-sizing: border-box;
            background-color: #fffdfd;
            transition: all 0.3s ease;
        }

        .login-card input:focus {
            border-color: #ff758c;
            box-shadow: 0 0 10px rgba(255, 117, 140, 0.15);
        }

        .login-card button {
            background: var(--primary-gradient);
            color: white;
            border: none;
            padding: 16px 30px;
            border-radius: 30px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            box-shadow: 0 8px 20px rgba(255, 117, 140, 0.25);
            transition: transform 0.2s ease;
        }

        .login-card button:active {
            transform: scale(0.98);
        }

        .error-msg {
            color: #e17055;
            font-size: 0.85rem;
            margin-top: 15px;
            min-height: 18px;
        }

        /* App Screen */
        #appScreen {
            display: none;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        header {
            width: 100%;
            text-align: center;
            padding: 35px 0;
            background: var(--primary-gradient);
            color: white;
            border-bottom-left-radius: 32px;
            border-bottom-right-radius: 32px;
            box-shadow: 0 10px 25px rgba(255, 117, 140, 0.15);
        }

        header h1 {
            margin: 0;
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: -0.5px;
        }

        header p {
            margin: 8px 0 0 0;
            font-size: 0.95rem;
            opacity: 0.9;
        }

        .container {
            width: 92%;
            max-width: 420px;
            margin-top: 25px;
        }

        .section-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 24px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(165, 100, 110, 0.04);
        }

        h2 {
            font-size: 1.2rem;
            margin-top: 0;
            font-weight: 600;
            color: var(--text-main);
            padding-bottom: 12px;
            letter-spacing: -0.3px;
        }

        /* User Selector */
        .user-toggle {
            display: flex;
            background: #f1f2f6;
            padding: 4px;
            border-radius: 20px;
            margin-bottom: 15px;
        }
        .user-btn {
            flex: 1;
            padding: 10px;
            border: none;
            background: transparent;
            border-radius: 16px;
            font-weight: 600;
            color: var(--text-muted);
            cursor: pointer;
            transition: all 0.2s;
        }
        .user-btn.active {
            background: white;
            color: #ff758c;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
        }

        /* Calendar */
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin-top: 15px;
        }

        .day-box {
            padding: 15px 5px;
            background-color: #f9f9fb;
            border-radius: 16px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-size: 0.85rem;
            font-weight: 500;
            color: var(--text-muted);
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid #f1f1f5;
        }

        .day-box .date-num {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--text-main);
            margin-top: 4px;
        }

        .day-box.checked {
            background: var(--primary-gradient);
            color: white;
            text-decoration: line-through;
            transform: scale(0.96);
            border-color: transparent;
            box-shadow: 0 6px 15px rgba(255, 117, 140, 0.2);
        }

        .day-box.checked .date-num {
            color: white;
        }

        /* Foto Portret Aspectoase */
        .photo-section {
            display: flex;
            flex-direction: column;
            gap: 24px;
        }

        .photo-container-title {
            font-size: 0.95rem;
            font-weight: 600;
            margin-bottom: 8px;
            display: block;
            color: var(--text-main);
        }

        .photo-preview {
            width: 100%;
            height: 420px;
            background: #faf6f7;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border: 1px dashed #f3d1d6;
            box-shadow: inset 0 4px 10px rgba(0,0,0,0.01);
            position: relative;
        }

        .photo-preview span {
            font-size: 0.9rem;
            color: var(--text-muted);
            font-style: italic;
        }

        .photo-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @webkit-keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .upload-btn {
            background-color: var(--accent-pink);
            color: #ff758c;
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            margin-top: 12px;
            display: inline-block;
            transition: all 0.2s;
        }

        .upload-btn:active {
            transform: scale(0.97);
            background-color: #ffdce2;
        }

        input[type="file"] {
            display: none;
        }

        /* Inimioara */
        .heart-container {
            text-align: center;
            padding: 15px 0;
        }

        .heart-button {
            font-size: 5rem;
            background: none;
            border: none;
            cursor: pointer;
            animation: pulse 2.5s infinite cubic-bezier(0.4, 0, 0.2, 1);
            outline: none;
            transition: transform 0.1s ease;
        }

        .heart-button:active {
            transform: scale(0.85) !important;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.08); }
            100% { transform: scale(1); }
        }

        .status-message {
            margin-top: 15px;
            font-weight: 600;
            color: #ff758c;
            min-height: 24px;
            font-size: 1.1rem;
            letter-spacing: -0.2px;
        }
    </style>
</head>
<body>

    <!-- ECRAN DE LOGARE -->
    <div id="loginScreen">
        <div class="login-card">
            <h2>Cami & Emi ❤️</h2>
            <p>Introduceți parola secretă</p>
            <input type="password" id="passwordInput" placeholder="Parola...">
            <button onclick="checkPassword()">Intră în aplicație</button>
            <div class="error-msg" id="errorMsg"></div>
        </div>
    </div>

    <!-- APLICAȚIA PROPRIU-ZISĂ -->
    <div id="appScreen" style="display:none;">
        <header>
            <h1>Cami ❤️ Emi</h1>
            <p>Misiune: 7 Iulie - 13 Iulie 2026</p>
        </header>

        <div class="container">
            
            <!-- SELECTARE UTILIZATOR CURENT -->
            <div class="section-card" style="padding: 15px;">
                <span class="photo-container-title" style="text-align:center; margin-bottom:10px;">Cine folosește aplicația acum?</span>
                <div class="user-toggle">
                    <button class="user-btn active" id="btnCami" onclick="setUser('Cami')">Cami</button>
                    <button class="user-btn" id="btnEmi" onclick="setUser('Emi')">Emi</button>
                </div>
            </div>
            
            <!-- 1. CALENDAR -->
            <div class="section-card">
                <h2>Zile de trecut în revistă</h2>
                <div class="calendar-grid" id="calendarGrid"></div>
            </div>

            <!-- 2. FOTO DIAR PORTRET -->
            <div class="section-card">
                <h2>Fotografia Zilei</h2>
                <div class="photo-section">
                    <div>
                        <span class="photo-container-title">Amintirea trimisă de Cami:</span>
                        <div class="photo-preview" id="previewCami"><span>Nicio fotografie adăugată</span></div>
                        <label class="upload-btn" id="uploadBtnCami">
                            Schimbă poza
                            <input type="file" accept="image/*" onchange="uploadPhoto(this, 'Cami')">
                        </label>
                    </div>
                    
                    <div style="margin-top: 10px;">
                        <span class="photo-container-title">Amintirea trimisă de Emi:</span>
                        <div class="photo-preview" id="previewEmi"><span>Nicio fotografie adăugată</span></div>
                        <label class="upload-btn" id="uploadBtnEmi" style="display:none;">
                            Schimbă poza
                            <input type="file" accept="image/*" onchange="uploadPhoto(this, 'Emi')">
                        </label>
                    </div>
                </div>
            </div>

            <!-- 3. INIMIOARĂ SMART DUAL -->
            <div class="section-card">
                <h2>Trimite-i un gând</h2>
                <div class="heart-container">
                    <button class="heart-button" onclick="sendHeart()">❤️</button>
                    <div class="status-message" id="statusMessage"></div>
                </div>
            </div>

        </div>
    </div>

    <script>
        const CORECT_PASSWORD = "TEIUBESC2026";
        const SYNC_URL = 'https://kvstore.psty.io/v1/baskets/cami_emi_secure_9842a7b3c21d84e2';
        
        let currentUser = 'Cami';

        function checkPassword() {
            const input = document.getElementById('passwordInput').value;
            if (input === CORECT_PASSWORD) {
                document.getElementById('loginScreen').style.display = 'none';
                document.getElementById('appScreen').style.display = 'block';
                localStorage.setItem('cami_emi_auth', 'true');
                initApp();
            } else {
                document.getElementById('errorMsg').innerText = "Parolă incorectă! Încearcă din nou.";
            }
        }

        if (localStorage.getItem('cami_emi_auth') === 'true') {
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('appScreen').style.display = 'block';
            window.addEventListener('DOMContentLoaded', initApp);
        }

        function initApp() {
            if(localStorage.getItem('cami_emi_preferred_user')) {
                setUser(localStorage.getItem('cami_emi_preferred_user'));
            }
            loadDataOnline();
            setInterval(loadDataOnline, 4000);
        }

        function setUser(user) {
            currentUser = user;
            localStorage.setItem('cami_emi_preferred_user', user);
            
            document.getElementById('btnCami').classList.toggle('active', user === 'Cami');
            document.getElementById('btnEmi').classList.toggle('active', user === 'Emi');
            
            document.getElementById('uploadBtnCami').style.display = user === 'Cami' ? 'inline-block' : 'none';
            document.getElementById('uploadBtnEmi').style.display = user === 'Emi' ? 'inline-block' : 'none';
        }

        const missionDays = [
            { id: "ziua1", label: "Marți", date: "7 Iul" },
            { id: "ziua2", label: "Mie", date: "8 Iul" },
            { id: "ziua3", label: "Joi", date: "9 Iul" },
            { id: "ziua4", label: "Vin", date: "10 Iul" },
            { id: "ziua5", label: "Sâm", date: "11 Iul" },
            { id: "ziua6", label: "Dum", date: "12 Iul" },
            { id: "ziua7", label: "Luni", date: "13 Iul" }
        ];

        const calendarGrid = document.getElementById('calendarGrid');

        missionDays.forEach(day => {
            const dayBox = document.createElement('div');
            dayBox.classList.add('day-box');
            dayBox.id = day.id;
            dayBox.innerHTML = `<div>${day.label}</div><div class="date-num">${day.date}</div>`;
            
            dayBox.addEventListener('click', () => {
                dayBox.classList.toggle('checked');
                saveDataOnline();
            });

            calendarGrid.appendChild(dayBox);
        });

        function saveDataOnline() {
            let checkedIds = [];
            missionDays.forEach(day => {
                if(document.getElementById(day.id).classList.contains('checked')) {
                    checkedIds.push(day.id);
                }
            });

            const dataToSave = {
                checked: checkedIds,
                heartMsg: document.getElementById('statusMessage').innerText,
                photoCami: localStorage.getItem('p_Cami') || '',
                photoEmi: localStorage.getItem('p_Emi') || ''
            };

            fetch(SYNC_URL, {
                method: 'PUT',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(dataToSave)
            }).catch(err => console.log("Eroare salvare:", err));
        }

        function loadDataOnline() {
            fetch(SYNC_URL)
            .then(res => res.json())
            .then(data => {
                if(!data) return;
                
                missionDays.forEach(day => {
                    const el = document.getElementById(day.id);
                    if(data.checked && data.checked.includes(day.id)) {
                        el.classList.add('checked');
                    } else {
                        el.classList.remove('checked');
                    }
                });

                if(data.heartMsg && data.heartMsg !== "") {
                    document.getElementById('statusMessage').innerText = data.heartMsg;
                }

                if(data.photoCami && data.photoCami !== localStorage.getItem('p_Cami')) {
                    localStorage.setItem('p_Cami', data.photoCami);
                    document.getElementById('previewCami').innerHTML = `<img src="${data.photoCami}">`;
                }
                if(data.photoEmi && data.photoEmi !== localStorage.getItem('p_Emi')) {
                    localStorage.setItem('p_Emi', data.photoEmi);
                    document.getElementById('previewEmi').innerHTML = `<img src="${data.photoEmi}">`;
                }
            }).catch(err => console.log("Eroare incarcare: ", err));
        }

        function uploadPhoto(input, user) {
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = new Image();
                    img.src = e.target.result;
                    img.onload = function() {
                        const canvas = document.createElement('canvas');
                        const ctx = canvas.getContext('2d');
                        
                        canvas.width = 400; 
                        canvas.height = 550;
                        
                        let srcX = 0, srcY = 0, srcW = img.width, srcH = img.height;
                        const targetRatio = 400 / 550;
                        const currentRatio = img.width / img.height;
                        
                        if (currentRatio > targetRatio) {
                            srcW = img.height * targetRatio;
                            srcX = (img.width - srcW) / 2;
                        } else {
                            srcH = img.width / targetRatio;
                            srcY = (img.height - srcH) / 2;
                        }

                        ctx.drawImage(img, srcX, srcY, srcW, srcH, 0, 0, 400, 550);
                        const compressedData = canvas.toDataURL('image/jpeg', 0.75);
                        
                        localStorage.setItem('p_' + user, compressedData);
                        document.getElementById('preview' + user).innerHTML = `<img src="${compressedData}">`;
                        saveDataOnline();
                    }
                }
                reader.readAsDataURL(input.files[0]);
            }
        }

        function sendHeart() {
            const currentHour = new Date().toLocaleTimeString('ro-RO', {hour: '2-digit', minute:'2-digit'});
            let destinationEmail = '';
            let subjectText = '';
            let senderName = '';

            if (currentUser === 'Cami') {
                destinationEmail = 'emi.rotaru666@gmail.com';
                senderName = 'Cami';
                subjectText = 'Cami se gândește la tine! 🥰';
            } else {
                destinationEmail = 'camycamelya86@gmail.com';
                senderName = 'Emi';
                subjectText = 'Emi se gândește la tine! 🥰';
            }

            document.getElementById('statusMessage').innerText = `❤️ ${senderName}: Mi-e dor de tine! (${currentHour})`;
            
            if (navigator.vibrate) {
                navigator.vibrate([200, 100, 200]);
            }
            saveDataOnline();

            const formData = new FormData();
            formData.append('Expeditor', senderName);
            formData.append('Mesaj', 'Mi-e dor de tine! ❤️');
            formData.append('Ora Trimiterii', currentHour);
            formData.append('_subject', subjectText);
            formData.append('_captcha', 'false');

            fetch(`https://formsubmit.co/ajax/${destinationEmail}`, {
                method: 'POST',
                body: formData
            })
            .then(res => console.log(`Inimioară trimisă cu succes către ${destinationEmail}!`))
            .catch(err => console.log('Eroare rețea notificare:', err));
        }
    </script>
</body>
</html>
