# cbam-gap
Analiza e Hendekut CBAM per Bizneset Shqiptare

<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CBAM Gap Analiza Template</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .header {
            background: white;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        
        .header h1 {
            color: #2c3e50;
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        
        .deadline-warning {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin: 20px 0;
            text-align: center;
            font-weight: bold;
            font-size: 1.1em;
        }
        
        .financial-projection {
            background: linear-gradient(135deg, #8e44ad, #9b59b6);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin: 20px 0;
        }
        
        .projection-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        
        .projection-card {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 10px;
            border-left: 5px solid #fff;
        }
        
        .albania-advantage {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin: 20px 0;
        }
        
        .sector-selector {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .sector-btn {
            background: white;
            border: 3px solid #e0e0e0;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .sector-btn:hover, .sector-btn.active {
            border-color: #3498db;
            background: #f8f9fa;
            transform: translateY(-2px);
        }
        
        .sector-icon {
            font-size: 2em;
            margin-bottom: 10px;
        }
        
        .gap-analysis {
            background: white;
            border-radius: 15px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            display: none;
        }
        
        .gap-analysis.active {
            display: block;
        }
        
        .question-block {
            background: #f8f9fa;
            border-left: 5px solid #3498db;
            padding: 20px;
            margin: 15px 0;
            border-radius: 5px;
        }
        
        .question-title {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 1.1em;
        }
        
        .status-grid {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 10px;
            margin-top: 15px;
        }
        
        .status-option {
            padding: 10px;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .status-have { background: #d4edda; color: #155724; }
        .status-partial { background: #fff3cd; color: #856404; }
        .status-need { background: #f8d7da; color: #721c24; }
        
        .status-option:hover, .status-option.selected {
            border-color: #333;
            transform: scale(1.02);
        }
        
        .company-info {
            background: #e8f4fd;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }
        
        .info-row {
            display: grid;
            grid-template-columns: 200px 1fr;
            gap: 15px;
            margin: 10px 0;
            align-items: center;
        }
        
        .info-label {
            font-weight: bold;
            color: #2c3e50;
        }
        
        .info-input {
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 14px;
        }
        
        .results-section {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin-top: 30px;
        }
        
        .action-item {
            background: rgba(255,255,255,0.1);
            padding: 15px;
            border-radius: 8px;
            margin: 10px 0;
            border-left: 4px solid #fff;
        }
        
        .priority-high { border-left-color: #e74c3c; }
        .priority-medium { border-left-color: #f39c12; }
        .priority-low { border-left-color: #27ae60; }
        
        .generate-btn {
            background: #27ae60;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 1.1em;
            cursor: pointer;
            margin: 20px auto;
            display: block;
            transition: all 0.3s ease;
        }
        
        .generate-btn:hover {
            background: #229954;
            transform: scale(1.05);
        }
        
        .kosovo-note {
            background: #d1ecf1;
            border: 1px solid #bee5eb;
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
        }
        
        .cost-comparison {
            background: linear-gradient(135deg, #f39c12, #e67e22);
            color: white;
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
        }
        
        .comparison-table {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin: 15px 0;
        }
        
        .comparison-card {
            background: rgba(255,255,255,0.1);
            padding: 15px;
            border-radius: 8px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎯 Analiza e Hendekut CBAM</h1>
            <p>Për eksportuesit shqiptarë në BE</p>
        </div>
        
        <div class="deadline-warning">
            ⚠️ Faza e rregullt e CBAM fillon më 1 Janar 2026 - Koha për përgatitje po mbaron!
        </div>
        
        <div class="financial-projection">
            <h2 style="margin-bottom: 20px;">💰 Prognoza Financiare CBAM 2026-2035</h2>
            <p><strong>Çmimi i CO₂:</strong> 120€/ton (2026) → 180€/ton (2035) - Rritje 5% vjetore</p>
            
            <div class="projection-grid">
                <div class="projection-card">
                    <h4>📊 Kostot CBAM për 10 vjet</h4>
                    <ul style="margin: 10px 0; line-height: 1.8;">
                        <li><strong>2026:</strong> 120€/ton CO₂</li>
                        <li><strong>2028:</strong> 132€/ton CO₂</li>
                        <li><strong>2030:</strong> 146€/ton CO₂</li>
                        <li><strong>2032:</strong> 161€/ton CO₂</li>
                        <li><strong>2035:</strong> 180€/ton CO₂</li>
                    </ul>
                </div>
                
                <div class="projection-card">
                    <h4>⚖️ Eksportues me Të dhëna vs Pa Të dhëna</h4>
                    <p><strong>Me monitorim të përpiktë:</strong></p>
                    <ul style="line-height: 1.6;">
                        <li>Kosto reale CBAM (më e ulët)</li>
                        <li>Avantazh konkurrues</li>
                        <li>Marrëdhënie më të mira me importues</li>
                    </ul>
                    <p><strong>Pa të dhëna (vlera default):</strong></p>
                    <ul style="line-height: 1.6;">
                        <li>+30-50% kosto shtesë CBAM</li>
                        <li>Humbje konkurruese</li>
                        <li>Rrezik humbje klientësh</li>
                    </ul>
                </div>
            </div>
        </div>
        
        <div class="cost-comparison">
            <h3>💸 Krahasimi i Kostove: Të Përgatitur vs Jo të Përgatitur</h3>
            <div class="comparison-table">
                <div class="comparison-card">
                    <h4>✅ Kompani të Përgatitura</h4>
                    <p><strong>Çelik:</strong> ~1.5 ton CO₂/ton produkt = 180€ CBAM/ton</p>
                    <p><strong>Alumin:</strong> ~8 ton CO₂/ton produkt = 960€ CBAM/ton</p>
                    <p><strong>Çimento:</strong> ~0.8 ton CO₂/ton produkt = 96€ CBAM/ton</p>
                </div>
                <div class="comparison-card">
                    <h4>❌ Kompani Jo të Përgatitura (Vlera Default)</h4>
                    <p><strong>Çelik:</strong> ~2.2 ton CO₂/ton = 264€ CBAM/ton (+47%)</p>
                    <p><strong>Alumin:</strong> ~12 ton CO₂/ton = 1440€ CBAM/ton (+50%)</p>
                    <p><strong>Çimento:</strong> ~1.2 ton CO₂/ton = 144€ CBAM/ton (+50%)</p>
                </div>
            </div>
            <p style="text-align: center; margin-top: 15px; font-size: 1.1em;">
                <strong>📈 Për 1000 ton eksport/vit: Dallimi mund të jetë 50,000€ - 480,000€ më shumë për ata pa të dhëna!</strong>
            </p>
        </div>
        
        <div class="albania-advantage">
            <h2>🇦🇱 Informacion Special për Kompanitë Shqiptare</h2>
            <div style="background: rgba(255,255,255,0.1); padding: 20px; border-radius: 10px; margin: 15px 0;">
                <h3>⚡ Avantazhi i Energjisë së Rinovueshme</h3>
                <p><strong>Shqipëria:</strong> ~0.1 kg CO₂/kWh (hidrocentralet)</p>
                <p><strong>Mesatarja e BE:</strong> ~0.4 kg CO₂/kWh</p>
                <p><strong>Avantazh konkurrues:</strong> 75% më pak emisione nga energjia elektrike!</p>
            </div>
            
            <div style="background: rgba(255,255,255,0.1); padding: 20px; border-radius: 10px; margin: 15px 0;">
                <h3>🔥 KUJDES: Jo Gjithçka është E Gjelbër!</h3>
                <p><strong>Energjia elektrike:</strong> E pastër nga hidroelektriket ✅</p>
                <p><strong>Proceset industriale:</strong></p>
                <ul style="line-height: 1.8; margin: 10px 0;">
                    <li>🔥 <strong>Gazi natyror:</strong> Duhet llogaritur veçmas</li>
                    <li>🛢️ <strong>Nafta/Diesel:</strong> Kosto e plotë CO₂</li>
                    <li>⚫ <strong>Qymyri:</strong> Emisione shumë të larta</li>
                    <li>🏭 <strong>Proceset kimike:</strong> CO₂ nga reaksionet</li>
                </ul>
                <p style="color: #ffeb3b; font-weight: bold;">
                    ⚠️ Shumë kompani shqiptare gabojnë: Mendojnë se hidrocentralet i bëjnë 100% të gjelbra, por CBAM llogarit çdo burim energjie veçmas!
                </p>
            </div>
            
            <div style="background: rgba(255,255,255,0.2); padding: 20px; border-radius: 10px; margin: 15px 0;">
                <h3>🎯 Kjo është Pika e Shitjes së Entrenovu Hub</h3>
                <p><strong>"Ne dimë si të ndajmë emisionet tuaja:"</strong></p>
                <ul style="line-height: 1.8;">
                    <li>✅ Energjia elektrike (avantazhi i Shqipërisë)</li>
                    <li>❌ Energjia termike (duhet optimizuar)</li>
                    <li>⚖️ Proceset industriale (strategji të posaçme)</li>
                </ul>
                <p style="color: #4ecdc4; font-weight: bold;">
                    💡 Rezultat: Minimizon kostot CBAM duke përdorur avantazhet dhe optimizuar dobësitë!
                </p>
            </div>
        </div>
        
        <div class="company-info">
            <h3 style="margin-bottom: 15px; color: #2c3e50;">📋 Të Dhënat e Kompanisë</h3>
            <div class="info-row">
                <div class="info-label">Emri i firmës:</div>
                <input type="text" class="info-input" id="company-name" placeholder="p.sh. Albanian Steel Corp">
            </div>
            <div class="info-row">
                <div class="info-label">Produkti kryesor:</div>
                <select class="info-input" id="main-product">
                    <option value="">Zgjidhni...</option>
                    <option value="steel">Çelik & Hekur</option>
                    <option value="aluminium">Alumin</option>
                    <option value="cement">Çimento</option>
                    <option value="fertilizer">Pleh</option>
                </select>
            </div>
            <div class="info-row">
                <div class="info-label">Eksport në BE (ton/vit):</div>
                <input type="number" class="info-input" id="export-volume" placeholder="p.sh. 10000">
            </div>
            <div class="info-row">
                <div class="info-label">Blerës kryesor në BE:</div>
                <input type="text" class="info-input" id="eu-buyers" placeholder="p.sh. Gjermani, Itali">
            </div>
        </div>
        
        <div class="kosovo-note">
            <strong>📍 Info speciale për Kosovë:</strong> Eksportuesit e Kosovës janë më pak të prekur (~1% e BPV), por duhet të jenë të përgatitur për tregjet në rritje të BE-së.
        </div>
        
        <h3 style="color: white; text-align: center; margin: 20px 0;">Zgjidhni sektorin tuaj për analizën e detajuar:</h3>
        
        <div class="sector-selector">
            <div class="sector-btn" onclick="showSector('steel')">
                <div class="sector-icon">🏭</div>
                <h4>Çelik & Hekur</h4>
                <p>Tuba, profile, fletë</p>
            </div>
            <div class="sector-btn" onclick="showSector('aluminium')">
                <div class="sector-icon">⚡</div>
                <h4>Alumin</h4>
                <p>Pllaka, tela, profile</p>
            </div>
            <div class="sector-btn" onclick="showSector('cement')">
                <div class="sector-icon">🏗️</div>
                <h4>Çimento</h4>
                <p>Klinker, çimento i gatshëm</p>
            </div>
            <div class="sector-btn" onclick="showSector('fertilizer')">
                <div class="sector-icon">🌱</div>
                <h4>Pleh</h4>
                <p>Bazuar në azot</p>
            </div>
        </div>
        
        <!-- Çelik & Hekur Gap Analysis -->
        <div id="steel-analysis" class="gap-analysis">
            <h2 style="color: #e74c3c; margin-bottom: 20px;">🏭 Çelik & Hekur - Kontrolli i Gatishmërisë CBAM</h2>
            
            <div class="question-block">
                <div class="question-title">1. Rruga e Prodhimit & Emisionet e Drejtpërdrejta (CO₂)</div>
                <p><strong>CBAM kërkon:</strong> Cili proces prodhimi? Furra e lartë, harku elektrik, apo rrugë tjetër?</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Tracking i djegësve</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Konsumi i përgjithshëm i njohur</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna specifike</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">3. Raporti Klinker-Çimento</div>
                <p><strong>CBAM kërkon:</strong> Sa klinker për ton çimento të gatshëm? (Shtesa reduktojnë intensitetin e CO₂)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Recepturat e sakta</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vlerat mesatare</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi ndarje</small></div>
                </div>
            </div>
        </div>
        
        <!-- Pleh Gap Analysis -->
        <div id="fertilizer-analysis" class="gap-analysis">
            <h2 style="color: #27ae60; margin-bottom: 20px;">🌱 Pleh - Kontrolli i Gatishmërisë CBAM</h2>
            
            <div class="question-block">
                <div class="question-title">1. Emisionet e Azotit (N₂O & CO₂)</div>
                <p><strong>CBAM kërkon:</strong> N₂O nga prodhimi i acidit nitrik + CO₂ nga gazi natyror/amoniaku</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>N₂O & CO₂ të matura</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vetëm CO₂ ose N₂O</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna emisionesh</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">2. Origjina e Amoniakut</div>
                <p><strong>CBAM kërkon:</strong> CO₂ e integruar në amoniakun e importuar (nëse nuk prodhohet vetë)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Çertifikata CO₂ nga furnizuesit</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Furnizuesit e njohur</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi tracking CO₂</small></div>
                </div>
            </div>
        </div>
        
        <button class="generate-btn" onclick="generateResults()">📊 Gjenero Rezultatin e Analizës së Hendekut</button>
        
        <div id="results" class="results-section" style="display: none;">
            <h2 style="margin-bottom: 20px;">🎯 Harta Juaj e Gatishmërisë CBAM</h2>
            <div id="action-plan">
                <!-- Do të gjenerohet dinamikisht -->
            </div>
            
            <div style="background: rgba(255,255,255,0.2); padding: 20px; border-radius: 10px; margin-top: 20px;">
                <h3>💡 Hapat e ardhshëm me Entrenovu Hub:</h3>
                <p><strong>E disponueshme menjëherë:</strong> CBAM Quick-Check (500€) - Lista e detajuar e detyrave + mbështetje me template</p>
                <p><strong>Përgatitja 2025:</strong> Programi Pilot CBAM (8.000€) - Implementim i plotë deri në 2026</p>
                <p><strong>Avantazhi ynë:</strong> Dimë si të ndajmë emisionet tuaja - energji elektrike (e pastër) vs. procese termike (për optimizim)</p>
                <p><strong>Kontakt:</strong> info@entrenovu.com | +355 XX XXX XXX</p>
            </div>
        </div>
    </div>
    
    <script>
        let currentSector = '';
        let responses = {};
        
        function showSector(sector) {
            // Fsheh të gjitha analizat
            const analyses = document.querySelectorAll('.gap-analysis');
            analyses.forEach(analysis => analysis.classList.remove('active'));
            
            // Hiq aktive nga të gjitha butonat
            const buttons = document.querySelectorAll('.sector-btn');
            buttons.forEach(btn => btn.classList.remove('active'));
            
            // Trego analizën e zgjedhur
            document.getElementById(sector + '-analysis').classList.add('active');
            event.target.closest('.sector-btn').classList.add('active');
            
            currentSector = sector;
            responses[sector] = responses[sector] || {};
        }
        
        function selectStatus(element) {
            // Hiq të zgjedhurin nga elementet e afërm
            const siblings = element.parentNode.querySelectorAll('.status-option');
            siblings.forEach(sibling => sibling.classList.remove('selected'));
            
            // Shto të zgjedhurin te elementi i klikuar
            element.classList.add('selected');
            
            // Ruaj përgjigjen
            const questionBlock = element.closest('.question-block');
            const questionTitle = questionBlock.querySelector('.question-title').textContent;
            const status = element.classList.contains('status-have') ? 'have' : 
                          element.classList.contains('status-partial') ? 'partial' : 'need';
            
            if (!responses[currentSector]) responses[currentSector] = {};
            responses[currentSector][questionTitle] = status;
        }
        
        function generateResults() {
            if (!currentSector) {
                alert('Ju lutem zgjidhni një sektor fillimisht!');
                return;
            }
            
            const sectorResponses = responses[currentSector] || {};
            const totalQuestions = Object.keys(sectorResponses).length;
            
            if (totalQuestions === 0) {
                alert('Ju lutem përgjigjuni pyetjeve fillimisht!');
                return;
            }
            
            const haveCount = Object.values(sectorResponses).filter(v => v === 'have').length;
            const partialCount = Object.values(sectorResponses).filter(v => v === 'partial').length;
            const needCount = Object.values(sectorResponses).filter(v => v === 'need').length;
            
            const readinessScore = Math.round(((haveCount * 2 + partialCount) / (totalQuestions * 2)) * 100);
            
            let actionPlan = `
                <h3>🎯 Rezultati i Gatishmërisë CBAM: ${readinessScore}%</h3>
                <div style="background: rgba(255,255,255,0.1); padding: 15px; border-radius: 8px; margin: 15px 0;">
                    ✅ Gati: ${haveCount} fusha | ⚠️ Pjesërisht: ${partialCount} fusha | ❌ Mungon: ${needCount} fusha
                </div>
            `;
            
            if (readinessScore >= 80) {
                actionPlan += `
                    <div class="action-item priority-low">
                        <strong>🎉 Shkëlqyeshëm!</strong> Jeni mirë të përgatitur. Fokus në trajnimin e template dhe komunikimin me BE-në.
                    </div>
                `;
            } else if (readinessScore >= 50) {
                actionPlan += `
                    <div class="action-item priority-medium">
                        <strong>⚠️ Fillim i mirë!</strong> Mbyllni hendekun e të dhënave deri në fund të 2025. Rekomandohet programi pilot.
                    </div>
                `;
            } else {
                actionPlan += `
                    <div class="action-item priority-high">
                        <strong>🚨 Urgjent!</strong> Masa të menjëhershme të nevojshme. Programi Pilot CBAM i domosdoshëm për 2026.
                    </div>
                `;
            }
            
            // Rekomandime specifike për sektorin
            if (currentSector === 'steel') {
                actionPlan += `
                    <div class="action-item priority-medium">
                        <strong>🏭 Specifike për Çelik:</strong> Dokumentoni rrugën e prodhimit, gjurmoni përqindjen e skrapit, përdorni energjinë e pastër të Shqipërisë si avantazh.
                    </div>
                `;
            } else if (currentSector === 'aluminium') {
                actionPlan += `
                    <div class="action-item priority-medium">
                        <strong>⚡ Specifike për Alumin:</strong> Çertifikata e hidroenergjisë si avantazh i madh konkurrues! Implementoni matjen e PFC.
                    </div>
                `;
            } else if (currentSector === 'cement') {
                actionPlan += `
                    <div class="action-item priority-medium">
                        <strong>🏗️ Specifike për Çimento:</strong> Ndani emisionet nga procesi vs. nga djegja, dokumentoni djegësit alternativë.
                    </div>
                `;
            } else if (currentSector === 'fertilizer') {
                actionPlan += `
                    <div class="action-item priority-high">
                        <strong>🌱 Specifike për Pleh:</strong> Emisionet N₂O janë kritike! Bëni zinxhirin e furnizimit të amoniakut transparent për CO₂.
                    </div>
                `;
            }
            
            // Avantazhet specifike të Shqipërisë
            actionPlan += `
                <div class="action-item priority-low">
                    <strong>🇦🇱 Avantazhi i Shqipërisë:</strong> Emeisone të ulëta të energjisë falë hidroenergjisë (0,1 kg CO₂/kWh vs. mesatarja e BE 0,4 kg CO₂/kWh)!
                </div>
            `;
            
            // Paralajmërim për proceset jo elektrike
            actionPlan += `
                <div class="action-item priority-high">
                    <strong>⚠️ Kujdes:</strong> Edhe pse energjia elektrike është e pastër, proceset me gaz natyror, naftë apo qymyr duhen llogaritur veçmas dhe kanë kosto të lartë CBAM!
                </div>
            `;
            
            // Rekomandime për kohën
            actionPlan += `
                <div class="action-item priority-high">
                    <strong>⏰ Afati 2025:</strong>
                    <ul style="margin: 10px 0; padding-left: 20px;">
                        <li>T1 2025: Filloni mbledhjen e të dhënave</li>
                        <li>T2 2025: Testoni template-in e BE-së</li>
                        <li>T3 2025: Komunikim me furnizuesit</li>
                        <li>T4 2025: Provë me importuesit e BE-së</li>
                    </ul>
                </div>
            `;
            
            // Krahasimi i kostove
            const exportVolume = document.getElementById('export-volume').value || 1000;
            let sectorEmissionFactor = 1.5; // Default për çelik
            
            if (currentSector === 'aluminium') sectorEmissionFactor = 8;
            else if (currentSector === 'cement') sectorEmissionFactor = 0.8;
            else if (currentSector === 'fertilizer') sectorEmissionFactor = 3;
            
            const preparedCost = exportVolume * sectorEmissionFactor * 120; // Me të dhëna të sakta
            const unpreparedCost = exportVolume * sectorEmissionFactor * 120 * 1.5; // Vlera default (+50%)
            const savings = unpreparedCost - preparedCost;
            
            actionPlan += `
                <div class="action-item priority-high">
                    <strong>💰 Analiza e Kostove për ${exportVolume} ton/vit:</strong>
                    <ul style="line-height: 1.8; margin: 10px 0;">
                        <li>✅ <strong>Me përgatitje:</strong> ${preparedCost.toLocaleString()}€ CBAM/vit</li>
                        <li>❌ <strong>Pa përgatitje (vlera default):</strong> ${unpreparedCost.toLocaleString()}€ CBAM/vit</li>
                        <li>💸 <strong>Kursim vjetor:</strong> ${savings.toLocaleString()}€!</li>
                    </ul>
                </div>
            `;
            
            // Prognoza 10-vjeçare
            const totalSavings10Years = savings * 8; // Mesatarisht për 10 vjet (duke llogaritur rritjen e çmimit)
            actionPlan += `
                <div class="action-item priority-high">
                    <strong>📈 Prognoza 10-vjeçare (2026-2035):</strong>
                    <p>Kursimi total i mundshëm: <strong style="color: #4ecdc4; font-size: 1.2em;">${totalSavings10Years.toLocaleString()}€</strong></p>
                    <p><small>Duke llogaritur rritjen 5% vjetore të çmimit të CO₂ (120€ → 180€)</small></p>
                </div>
            `;
            
            document.getElementById('action-plan').innerHTML = actionPlan;
            document.getElementById('results').style.display = 'block';
            document.getElementById('results').scrollIntoView({ behavior: 'smooth' });
        }
        
        // Funksionaliteti i ruajtjes automatike
        function saveProgress() {
            localStorage.setItem('cbam_gap_analysis', JSON.stringify({
                responses: responses,
                sector: currentSector,
                company: {
                    name: document.getElementById('company-name').value,
                    product: document.getElementById('main-product').value,
                    volume: document.getElementById('export-volume').value,
                    buyers: document.getElementById('eu-buyers').value
                }
            }));
        }
        
        // Ngarkimi i progresit të ruajtur
        function loadProgress() {
            const saved = localStorage.getItem('cbam_gap_analysis');
            if (saved) {
                const data = JSON.parse(saved);
                responses = data.responses || {};
                currentSector = data.sector || '';
                
                if (data.company) {
                    document.getElementById('company-name').value = data.company.name || '';
                    document.getElementById('main-product').value = data.company.product || '';
                    document.getElementById('export-volume').value = data.company.volume || '';
                    document.getElementById('eu-buyers').value = data.company.buyers || '';
                }
            }
        }
        
        // Event listeners për ruajtjen automatike
        document.addEventListener('change', saveProgress);
        document.addEventListener('input', saveProgress);
        document.addEventListener('DOMContentLoaded', loadProgress);
    </script>
</body>
</html>Status(this)">✅ E kemi<br><small>E dokumentuar & e matshme</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vlerësime të përafërta</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">2. Konsumi i Energjisë Elektrike & Emisionet e Tërthorta</div>
                <p><strong>CBAM kërkon:</strong> kWh për ton çelik + intensiteti CO₂ i energjisë (Shqipëria: ~0,1 kg CO₂/kWh falë hidrocentraleve!)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Fatura e energjisë në dispozicion</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vetëm konsumi i përgjithshëm</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna specifike</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">3. Lëndë të Para Hyrëse</div>
                <p><strong>CBAM kërkon:</strong> Nga vjen xeherori, qymyri, skrapi? Çfarë emisionesh janë të integruara aty?</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Çertifikata nga furnizuesit</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Dimë origjinën</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna CO₂</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">4. Komunikimi me BE & Template</div>
                <p><strong>CBAM kërkon:</strong> A mund ta plotësoni template-in Excel të BE-së dhe ta dërgoni te importuesit e BE-së?</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Template-i i njohur</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Dimë për të</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Kurrë nuk e kemi parë</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">5. Çmimi i Karbonit në Shqipëri</div>
                <p><strong>Avantazhi CBAM:</strong> A paguani tashmë çmime CO₂ në Shqipëri? (Mund të zbritet nga CBAM!)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ Paguajmë çmim CO₂<br><small>E dokumentuar</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Taksa të tjera mjedisore</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Asnjë çmim CO₂<br><small>Çmim i plotë CBAM</small></div>
                </div>
            </div>
        </div>
        
        <!-- Alumin Gap Analysis -->
        <div id="aluminium-analysis" class="gap-analysis">
            <h2 style="color: #9b59b6; margin-bottom: 20px;">⚡ Alumin - Kontrolli i Gatishmërisë CBAM</h2>
            
            <div class="question-block">
                <div class="question-title">1. Rruga e Prodhimit (Primar vs. Riciklim)</div>
                <p><strong>CBAM kërkon:</strong> Elektroliza (alumini primar) apo riciklim? Profile të ndryshme CO₂!</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Rruga e qartë e përcaktuar</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Prodhim i përzier</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi ndarje</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">2. Intensiteti i Energjisë (kritike për aluminin!)</div>
                <p><strong>CBAM kërkon:</strong> kWh eksakte për kg alumin + burimi (hidroenergjia = avantazhi i madh i Shqipërisë!)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Hidroenergjia e çertifikuar</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Konsumi i energjisë i njohur</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna specifike</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">3. Emisionet Perfluorokarbon (PFC)</div>
                <p><strong>CBAM kërkon:</strong> Emisionet CF₄ dhe C₂F₆ nga procesi i elektrolizës (vetëm për aluminin primar)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>PFC të matura</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vlerësime</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna PFC</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">4. Origjina e Aluminës (Alumina)</div>
                <p><strong>CBAM kërkon:</strong> CO₂ e integruar në aluminën e importuar (nëse nuk prodhohet vetë)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>Të dhënat CO₂ nga furnizuesit</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Dimë origjinën</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna CO₂</small></div>
                </div>
            </div>
        </div>
        
        <!-- Çimento Gap Analysis -->
        <div id="cement-analysis" class="gap-analysis">
            <h2 style="color: #95a5a6; margin-bottom: 20px;">🏗️ Çimento - Kontrolli i Gatishmërisë CBAM</h2>
            
            <div class="question-block">
                <div class="question-title">1. Emisionet nga Procesi (Gëlqerori → Klinker)</div>
                <p><strong>CBAM kërkon:</strong> CO₂ nga dekompozimi i kalcium karbonit (~60% e emisioneve të çimentos)</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="selectStatus(this)">✅ E kemi<br><small>CO₂ e klinkerit të matur</small></div>
                    <div class="status-option status-partial" onclick="selectStatus(this)">⚠️ Pjesërisht<br><small>Vlerësime në dispozicion</small></div>
                    <div class="status-option status-need" onclick="selectStatus(this)">❌ Na mungon<br><small>Nuk kemi të dhëna procesi</small></div>
                </div>
            </div>
            
            <div class="question-block">
                <div class="question-title">2. Emisionet nga Djegja</div>
                <p><strong>CBAM kërkon:</strong> CO₂ nga djegësit (qymyr, gaz, djegës alternativë) për ton klinker</p>
                <div class="status-grid">
                    <div class="status-option status-have" onclick="select
