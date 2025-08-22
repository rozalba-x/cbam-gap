# CBAM Gap Analysis

<!DOCTYPE html>
<html lang="sq">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CBAM Gap Analiza – Entrenovu Hub</title>
  <meta name="description" content="CBAM Gap Analiza për eksportuesit shqiptarë në BE. Vlerëso gatishmërinë, kostot dhe hapat për të ulur ekspozimin tuaj ndaj CBAM." />

  <!-- Roboto for crisp UI -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet"/>

  <!-- Styles -->
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    :root{
      --bg1:#2c3e50; --bg2:#34495e; --card:#ffffff; --muted:#f8f9fa;
      --accent:#3498db; --ok:#27ae60; --warn:#f39c12; --bad:#e74c3c;
      --ink:#2c3e50;
    }
    body{
      font-family: 'Inter', system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      line-height:1.6; background: linear-gradient(135deg, var(--bg1) 0%, var(--bg2) 100%);
      min-height:100vh; color:#333;
    }
    .container{ max-width: 1200px; margin: 0 auto; padding: 24px; }

    /* Cover header */
    .cover{
      background: linear-gradient(135deg, #0b1a2d, #132a45 60%, #0b1a2d 100%);
      color: #fff; border-radius: 18px; padding: 26px 26px 20px; margin: 0 0 24px;
      box-shadow: 0 10px 30px rgba(0,0,0,.18);
      display:flex; align-items:center; gap:18px; flex-wrap:wrap;
    }
    .cover img{ height:56px; width:auto; display:block; }
    .cover-title{ flex:1; }
    .cover-title h1{ font-size: clamp(22px, 3.2vw, 32px); font-weight:800; letter-spacing:.2px; }
    .cover-title p{ opacity:.9; margin-top:4px; }

    .deadline-warning{
      background: linear-gradient(135deg, #e74c3c, #c0392b);
      color: #fff; padding: 14px 16px; border-radius: 12px; margin: 16px 0 22px;
      font-weight:700; text-align:center;
      box-shadow: 0 10px 30px rgba(0,0,0,.12);
    }

    .financial-projection, .albania-advantage, .cost-comparison{
      color:#fff; border-radius:16px; padding:22px; margin:20px 0;
      box-shadow: 0 12px 30px rgba(0,0,0,.12);
    }
    .financial-projection{ background: linear-gradient(135deg, #8e44ad, #9b59b6); }
    .albania-advantage{ background: linear-gradient(135deg, #e74c3c, #c0392b); }
    .cost-comparison{ background: linear-gradient(135deg, #f39c12, #e67e22); }

    .projection-grid{ display:grid; grid-template-columns: repeat(auto-fit, minmax(280px,1fr)); gap:16px; margin-top:12px; }
    .projection-card, .comparison-card{
      background: rgba(255,255,255,.12); padding:16px; border-radius:12px; border-left:4px solid rgba(255,255,255,.9);
    }
    .comparison-table{ display:grid; grid-template-columns: repeat(auto-fit, minmax(280px,1fr)); gap:16px; margin:12px 0; }

    .sector-selector{
      display:grid; grid-template-columns: repeat(auto-fit, minmax(220px,1fr)); gap:14px; margin: 12px 0 20px;
    }
    .sector-btn{
      background:#fff; border: 3px solid #e0e0e0; border-radius:16px; padding:18px; text-align:center; cursor:pointer;
      transition: all .2s ease; box-shadow: 0 6px 16px rgba(0,0,0,.08);
    }
    .sector-btn:hover, .sector-btn.active{ border-color: var(--accent); background:#f8fbff; transform: translateY(-1px); }
    .sector-icon{ font-size: 26px; margin-bottom: 8px; }

    .gap-analysis{
      background:#fff; border-radius:16px; padding:22px; margin:16px 0 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,.10); display:none;
    }
    .gap-analysis.active{ display:block; }

    .question-block{
      background: var(--muted); border-left: 5px solid var(--accent);
      padding:16px; margin:14px 0; border-radius:8px;
    }
    .question-title{ font-weight:800; color:var(--ink); margin-bottom:6px; font-size:16px; }

    .status-grid{ display:grid; grid-template-columns: repeat(3,1fr); gap:10px; margin-top:10px; }
    .status-option{ padding:10px; border-radius:10px; text-align:center; cursor:pointer; border:2px solid transparent; transition: all .15s ease; font-weight:600; }
    .status-option small{ font-weight:400; opacity:.9; }
    .status-have{ background:#d4edda; color:#155724; }
    .status-partial{ background:#fff3cd; color:#7a5d00; }
    .status-need{ background:#f8d7da; color:#8a1c1c; }
    .status-option:hover, .status-option.selected{ border-color:#222; transform: scale(1.02); }

    .company-info{
      background:#e8f4fd; padding:18px; border-radius:12px; margin: 20px 0;
      box-shadow: 0 8px 20px rgba(0,0,0,.06);
    }
    .info-row{ display:grid; grid-template-columns: 220px 1fr; gap:12px; margin:8px 0; align-items:center; }
    .info-label{ font-weight:700; color:#1a2b3b; }
    .info-input{ padding:10px 12px; border:1px solid #d9e3ee; border-radius:8px; font-size:14px; outline:none; }

    .results-section{
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color:#fff; padding:22px; border-radius:16px; margin: 22px 0 10px;
      box-shadow: 0 12px 26px rgba(0,0,0,.14); display:none;
    }
    .action-item{ background: rgba(255,255,255,.12); padding:14px; border-radius:8px; margin: 10px 0; border-left:4px solid #fff; }
    .priority-high{ border-left-color: #e74c3c; }
    .priority-medium{ border-left-color: #f39c12; }
    .priority-low{ border-left-color: #27ae60; }

    .generate-btn, .pdf-btn{
      background: var(--ok); color:#fff; border:none; padding:14px 20px; border-radius:12px; font-size:16px; font-weight:800;
      cursor:pointer; display:block; margin:18px auto 0; transition: all .15s ease;
      box-shadow: 0 10px 20px rgba(39,174,96,.25);
    }
    .generate-btn:hover, .pdf-btn:hover{ transform: translateY(-1px); filter:brightness(1.03); }
    .pdf-btn{ background:#111827; box-shadow: 0 10px 20px rgba(17,24,39,.25); margin-top:12px; }

    .kosovo-note{ background:#d1ecf1; border:1px solid #bee5eb; padding:12px 14px; border-radius:10px; margin: 10px 0; }

    /* Hide-only-for-PDF template staging node */
    #pdf-staging{ position: fixed; left:-10000px; top:-10000px; width: 794px; background:#fff; padding:24px; }
    #pdf-staging .divider{ height:1px; background:#e9eef5; margin:14px 0; }

    /* Print overrides (optional fallback) */
    @media print{
      .generate-btn, .pdf-btn, .sector-selector, .deadline-warning { display:none !important; }
    }
  </style>

  <!-- html2pdf (bundled: html2canvas + jsPDF) for clean PDF export -->
  <script defer src="https://cdn.jsdelivr.net/npm/html2pdf.js@0.10.1/dist/html2pdf.bundle.min.js"></script>
</head>
<body>
  <div class="container">

    <!-- Cover header with logo -->
    <div class="cover">
      <img src="logo.png" alt="Entrenovu Hub" onerror="this.style.display='none'">
      <div class="cover-title">
        <h1>🎯 CBAM Gap Analiza – Eksportuesit Shqiptarë në BE</h1>
        <p>Framework praktik për gatishmëri, kosto dhe vendime – ju shkurton rrugën deri te rezultati.</p>
      </div>
    </div>

    <div class="deadline-warning">⚠️ Faza e rregullt e CBAM fillon më 1 Janar 2026 – Koha për përgatitje po mbaron!</div>

    <div class="financial-projection">
      <h2 style="margin-bottom: 12px;">💰 Prognoza Financiare CBAM 2026–2035</h2>
      <p><strong>Çmimi i CO₂:</strong> 120€/t (2026) → 180€/t (2035) – rritje ~5%/vit</p>
      <div class="projection-grid">
        <div class="projection-card">
          <h4>📊 Kostot CBAM (orientim)</h4>
          <ul style="margin:10px 0; line-height:1.8;">
            <li><strong>2026:</strong> 120 €/t CO₂</li>
            <li><strong>2028:</strong> 132 €/t CO₂</li>
            <li><strong>2030:</strong> 146 €/t CO₂</li>
            <li><strong>2032:</strong> 161 €/t CO₂</li>
            <li><strong>2035:</strong> 180 €/t CO₂</li>
          </ul>
        </div>
        <div class="projection-card">
          <h4>⚖️ Të dhëna reale vs. vlera default</h4>
          <p><strong>Me monitorim të saktë:</strong></p>
          <ul style="line-height:1.6;">
            <li>Kosto reale CBAM (më e ulët)</li>
            <li>Avantazh konkurrues</li>
            <li>Marrëdhënie më të mira me importuesit</li>
          </ul>
          <p><strong>Pa të dhëna (default):</strong></p>
          <ul style="line-height:1.6;">
            <li>+30–50% kosto shtesë</li>
            <li>Rënie konkurruese</li>
            <li>Rrezik humbje klientësh</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="cost-comparison">
      <h3>💸 Krahasimi i Kostove: Të Përgatitur vs. Jo të Përgatitur</h3>
      <div class="comparison-table">
        <div class="comparison-card">
          <h4>✅ Kompani të Përgatitura</h4>
          <p><strong>Çelik:</strong> ~1.5 t CO₂/t prod. = 180€ CBAM/t</p>
          <p><strong>Alumin:</strong> ~8 t CO₂/t prod. = 960€ CBAM/t</p>
          <p><strong>Çimento:</strong> ~0.8 t CO₂/t prod. = 96€ CBAM/t</p>
        </div>
        <div class="comparison-card">
          <h4>❌ Pa të dhëna (Default)</h4>
          <p><strong>Çelik:</strong> ~2.2 t CO₂/t = 264€ (+47%)</p>
          <p><strong>Alumin:</strong> ~12 t CO₂/t = 1440€ (+50%)</p>
          <p><strong>Çimento:</strong> ~1.2 t CO₂/t = 144€ (+50%)</p>
        </div>
      </div>
      <p style="text-align:center;margin-top:10px;font-size:1.06em;">
        <strong>📈 Për 1000 t/vit: Diferenca mund të jetë 50.000€ – 480.000€/vit për ata pa të dhëna!</strong>
      </p>
    </div>

    <div class="albania-advantage">
      <h2>🇦🇱 Avantazhi Strukturor i Shqipërisë</h2>
      <div style="background: rgba(255,255,255,0.12); padding: 14px; border-radius: 10px; margin: 12px 0;">
        <h3>⚡ Energjia e Rinovueshme</h3>
        <p><strong>Shqipëria:</strong> ~0.1 kg CO₂/kWh (hidro) | <strong>BE mesatare:</strong> ~0.4 kg CO₂/kWh → ~75% më pak CO₂ nga energjia!</p>
      </div>
      <div style="background: rgba(255,255,255,0.12); padding: 14px; border-radius: 10px; margin: 12px 0;">
        <h3>🔥 Jo gjithçka është “e gjelbër”</h3>
        <ul style="line-height:1.8; margin:10px 0;">
          <li>Gazi natyror, nafta/dieseli, qymyri → llogaritje veçmas për CBAM</li>
          <li>Proceset kimike → CO₂ nga reaksionet (kritike për çimenton & plehrat)</li>
        </ul>
        <p style="color: #ffeb3b; font-weight: 800;">⚠️ Hidro ndihmon vetëm për energjinë elektrike – CBAM kërkon ndarje të burimeve të energjisë!</p>
      </div>
      <div style="background: rgba(255,255,255,0.20); padding: 14px; border-radius: 10px; margin: 12px 0;">
        <h3>🎯 Si ju ndihmon Entrenovu Hub</h3>
        <ul style="line-height:1.8;">
          <li>✅ Ndarja e emisioneve: energji elektrike vs. termike vs. procese</li>
          <li>✅ Template & gjurmueshmëri të dhënash në standardin e BE</li>
          <li>✅ Strategji për ulje të intensitetit të CO₂ pa prishur output-in</li>
        </ul>
      </div>
    </div>

    <!-- Company information -->
    <div class="company-info">
      <h3 style="margin-bottom:10px; color:#2c3e50;">📋 Të Dhënat e Kompanisë</h3>
      <div class="info-row">
        <div class="info-label">Emri i firmës:</div>
        <input type="text" class="info-input" id="company-name" placeholder="p.sh. Albanian Steel Corp" />
      </div>
      <div class="info-row">
        <div class="info-label">Produkti kryesor:</div>
        <select class="info-input" id="main-product">
          <option value="">Zgjidhni...</option>
          <option value="steel">Çelik & Hekur</option>
          <option value="aluminium">Alumin</option>
          <option value="cement">Çimento</option>
          <option value="fertilizer">Pleh (azot)</option>
        </select>
      </div>
      <div class="info-row">
        <div class="info-label">Eksport në BE (t/vit):</div>
        <input type="number" class="info-input" id="export-volume" placeholder="p.sh. 10000" />
      </div>
      <div class="info-row">
        <div class="info-label">Blerësit kryesorë (BE):</div>
        <input type="text" class="info-input" id="eu-buyers" placeholder="p.sh. Gjermani, Itali" />
      </div>
    </div>

    <div class="kosovo-note"><strong>📍 Info për Kosovë:</strong> Ekspozimi total është më i ulët (~1% e BPV), por kërkesat CBAM te klientët e BE-së vlejnë njësoj.</div>

    <h3 style="color: #fff; text-align:center; margin: 18px 0;">Zgjidhni sektorin tuaj për analizën e detajuar:</h3>

    <div class="sector-selector">
      <div class="sector-btn" data-sector="steel">
        <div class="sector-icon">🏭</div>
        <h4>Çelik & Hekur</h4><p>Tuba, profile, fletë</p>
      </div>
      <div class="sector-btn" data-sector="aluminium">
        <div class="sector-icon">⚡</div>
        <h4>Alumin</h4><p>Pllaka, tela, profile</p>
      </div>
      <div class="sector-btn" data-sector="cement">
        <div class="sector-icon">🏗️</div>
        <h4>Çimento</h4><p>Klinker, çimento e gatshme</p>
      </div>
      <div class="sector-btn" data-sector="fertilizer">
        <div class="sector-icon">🌱</div>
        <h4>Pleh</h4><p>Bazuar në azot</p>
      </div>
    </div>

    <!-- STEEL -->
    <div id="steel-analysis" class="gap-analysis">
      <h2 style="color:#e74c3c; margin-bottom:10px;">🏭 Çelik & Hekur – Kontrolli i Gatishmërisë</h2>

      <div class="question-block">
        <div class="question-title">1. Rruga e Prodhimit & Emisionet e Drejtpërdrejta</div>
        <p><strong>CBAM:</strong> Furra e lartë/BOF, hark elektrik (EAF), DRI+EAF, apo tjetër? </p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Proces & djegës të gjurmuar</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Vetëm total vjetor</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa ndarje procesesh</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">2. Konsumi i Energjisë Elektrike & Emisionet e Tërthorta</div>
        <p><strong>CBAM:</strong> kWh për ton çelik + intensiteti CO₂ i energjisë (Shqipëria ~0.1 kg CO₂/kWh).</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Faturat & matjet</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Vetëm konsumi total</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa ndarje sipas linjave</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">3. Lëndë të Para Hyrëse & Emisionet e Integruara</div>
        <p>Origjina e xeherorit, qymyrit, skrapit; certifikata CO₂ nga furnizuesit.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Dokumentuar</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Origjinë e ditur</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa CO₂ nga furnizuesit</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">4. Template i BE & Komunikimi me Importuesit</div>
        <p>A mund ta plotësoni dhe dërgoni template-in standard CBAM?</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Template & prova dërgimi</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>E kemi parë</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Nuk është përdorur</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">5. Çmimi i Karbonit në Shqipëri (zbritje e mundshme)</div>
        <p>Paguhen taksa/çmime CO₂ që mund të zbriten në CBAM?</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ Po<br><small>E dokumentuar</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Të tjera taksa mjedisore</small></div>
          <div class="status-option status-need">❌ Jo<br><small>Pa zbritje</small></div>
        </div>
      </div>
    </div>

    <!-- ALUMINIUM -->
    <div id="aluminium-analysis" class="gap-analysis">
      <h2 style="color:#9b59b6; margin-bottom:10px;">⚡ Alumin – Kontrolli i Gatishmërisë</h2>

      <div class="question-block">
        <div class="question-title">1. Rruga e Prodhimit (Primar vs. Riciklim)</div>
        <p>Elektrolizë (primar) apo riciklim? Përqindje për secilën rrugë.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Ndarje e saktë</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Mix i përafërt</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa ndarje</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">2. Intensiteti i Energjisë (kritik për Aluminin)</div>
        <p>kWh/kg Al – burimi i energjisë (hidro = avantazh i madh në Shqipëri).</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Origjinë & kWh të matur</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Total vjetor</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa gjurmë</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">3. Emisionet PFC (CF₄/C₂F₆)</div>
        <p>Vetëm për aluminin primar – kërkohet monitorim i PFC.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>PFC të matura</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Vlerësime</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa të dhëna PFC</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">4. Origjina e Aluminës (CO₂ e integruar)</div>
        <p>CO₂ nga aluminë e importuar – kërkohen certifikata furnizuesish.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>CO₂ nga furnizuesit</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Origjinë e ditur</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa CO₂ të integruar</small></div>
        </div>
      </div>
    </div>

    <!-- CEMENT -->
    <div id="cement-analysis" class="gap-analysis">
      <h2 style="color:#95a5a6; margin-bottom:10px;">🏗️ Çimento – Kontrolli i Gatishmërisë</h2>

      <div class="question-block">
        <div class="question-title">1. Emisionet nga Procesi (CaCO₃ → CaO + CO₂)</div>
        <p>CO₂ i procesit (rreth 60% e totalit) – kërkohen të dhëna për klinkerin.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>CO₂ i klinkerit i matur</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Vlerësime</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa ndarje procesi</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">2. Emisionet nga Djegja</div>
        <p>CO₂ nga qymyr/gaz/alternativë për ton klinker.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Djegës & karte energjie</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Total vjetor</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa gjurmë</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">3. Raporti Klinker–Çimento</div>
        <p>Sa klinker për ton çimento? Shtesat (pozolana/slag) ulin CO₂/t produkt.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Receta & statistika</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Mesatare</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa ndarje</small></div>
        </div>
      </div>
    </div>

    <!-- FERTILIZER -->
    <div id="fertilizer-analysis" class="gap-analysis">
      <h2 style="color:#27ae60; margin-bottom:10px;">🌱 Pleh – Kontrolli i Gatishmërisë</h2>

      <div class="question-block">
        <div class="question-title">1. Emisionet e Azotit (N₂O) & CO₂</div>
        <p>N₂O nga acidi nitrik + CO₂ nga gazi natyror/amoniaku.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>N₂O & CO₂ të matura</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Vetëm njëra </small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa të dhëna</small></div>
        </div>
      </div>

      <div class="question-block">
        <div class="question-title">2. Origjina e Amoniakut (CO₂ e integruar)</div>
        <p>CO₂ në amoniakun e importuar – kërkohen certifikata furnizuesish.</p>
        <div class="status-grid">
          <div class="status-option status-have">✅ E kemi<br><small>Dokumentuar</small></div>
          <div class="status-option status-partial">⚠️ Pjesërisht<br><small>Furnizues të njohur</small></div>
          <div class="status-option status-need">❌ Na mungon<br><small>Pa tracking CO₂</small></div>
        </div>
      </div>
    </div>

    <button class="generate-btn" id="generate">📊 Gjenero Rezultatin e Analizës së Hendekut</button>

    <div id="results" class="results-section">
      <h2 style="margin-bottom:12px;">🎯 Harta juaj e Gatishmërisë CBAM</h2>
      <div id="action-plan"></div>

      <!-- Contact block (replaces the old program section) -->
      <div style="background: rgba(255,255,255,0.20); padding: 16px; border-radius: 10px; margin-top: 16px;">
        <h3>📞 Kontakt</h3>
        <p style="margin-top:8px;"><strong>Entrenovu Hub</strong><br>
        +43 650 6965 789 &nbsp;|&nbsp; <a href="mailto:info@entrenovu.com" style="color:#fff; text-decoration: underline;">info@entrenovu.com</a></p>
      </div>

      <button class="pdf-btn" id="download-pdf">🧾 Shkarko PDF (përmbledhje)</button>
    </div>

    <!-- Hidden PDF staging node (filled dynamically for export) -->
    <div id="pdf-staging" aria-hidden="true"></div>

  </div>

  <!-- Core Logic -->
  <script>
    let currentSector = '';
    let responses = {};

    // Helpers
    const qs = (sel, root=document) => root.querySelector(sel);
    const qsa = (sel, root=document) => Array.from(root.querySelectorAll(sel));

    // Sector UX
    function showSector(sector){
      qsa('.gap-analysis').forEach(a => a.classList.remove('active'));
      qsa('.sector-btn').forEach(b => b.classList.remove('active'));

      const target = qs('#' + sector + '-analysis');
      if (target) target.classList.add('active');

      const activeBtn = qsa('.sector-btn').find(b => b.dataset.sector === sector);
      if (activeBtn) activeBtn.classList.add('active');

      currentSector = sector;
      responses[sector] = responses[sector] || {};
      saveProgress();
    }

    // Click handling for sector buttons (event delegation)
    document.addEventListener('click', (e) => {
      const b = e.target.closest('.sector-btn');
      if (b && b.dataset.sector){
        showSector(b.dataset.sector);
      }

      const opt = e.target.closest('.status-option');
      if (opt){
        const siblings = qsa('.status-option', opt.parentNode);
        siblings.forEach(s => s.classList.remove('selected'));
        opt.classList.add('selected');

        const block = opt.closest('.question-block');
        const title = qs('.question-title', block).textContent.trim();
        const status = opt.classList.contains('status-have') ? 'have'
                     : opt.classList.contains('status-partial') ? 'partial' : 'need';
        if (!responses[currentSector]) responses[currentSector] = {};
        responses[currentSector][title] = status;
        saveProgress();
      }
    });

    // Generate results
    function generateResults(){
      if (!currentSector){ alert('Ju lutem zgjidhni një sektor fillimisht!'); return; }

      const sectorResponses = responses[currentSector] || {};
      const totalQuestions = Object.keys(sectorResponses).length;
      if (totalQuestions === 0){ alert('Ju lutem përgjigjuni pyetjeve fillimisht!'); return; }

      const vals = Object.values(sectorResponses);
      const haveCount = vals.filter(v => v === 'have').length;
      const partialCount = vals.filter(v => v === 'partial').length;
      const needCount = vals.filter(v => v === 'need').length;

      const readinessScore = Math.round(((haveCount * 2 + partialCount) / (totalQuestions * 2)) * 100);

      const exportVolume = Number(qs('#export-volume').value || 1000);
      let sectorEmissionFactor = 1.5; // steel default
      if (currentSector === 'aluminium') sectorEmissionFactor = 8;
      else if (currentSector === 'cement') sectorEmissionFactor = 0.8;
      else if (currentSector === 'fertilizer') sectorEmissionFactor = 3;

      const priceCO2 = 120; // €/t (2026 orientation)
      const preparedCost = Math.round(exportVolume * sectorEmissionFactor * priceCO2);
      const unpreparedCost = Math.round(preparedCost * 1.5);
      const savings = unpreparedCost - preparedCost;
      const totalSavings10Years = Math.round(savings * 8); // rough compounding proxy

      let plan = `
        <h3 style="margin-bottom:6px;">🎯 Rezultati i Gatishmërisë CBAM: ${readinessScore}%</h3>
        <div style="background: rgba(255,255,255,0.12); padding: 12px; border-radius: 10px; margin: 12px 0;">
          ✅ Gati: ${haveCount} | ⚠️ Pjesërisht: ${partialCount} | ❌ Mungon: ${needCount}
        </div>
      `;

      if (readinessScore >= 80){
        plan += `<div class="action-item priority-low"><strong>🎉 Shkëlqyeshëm!</strong> Jeni mirë të përgatitur. Fokus: standardizoni dorëzimin te importuesit dhe validoni certifikatat furnizuesve.</div>`;
      } else if (readinessScore >= 50){
        plan += `<div class="action-item priority-medium"><strong>⚠️ Fillim i mirë!</strong> Mbyllni boshllëqet e të dhënave dhe testoni template-in CBAM me klientët kyç brenda 2025.</div>`;
      } else {
        plan += `<div class="action-item priority-high"><strong>🚨 Urgjente!</strong> Duhet ngritur sistemi i të dhënave dhe komunikimit CBAM tani për të shmangur penalitete/kosto default.</div>`;
      }

      // Sector tips
      const sectorTips = {
        steel: "Dokumentoni rrugën e prodhimit, përqindjen e skrapit, dhe leverdini avantazhin e energjisë së pastër.",
        aluminium: "Certifikoni origjinën e energjisë (hidro) dhe implementoni monitorimin e PFC.",
        cement: "Ndani procesin nga djegja, ulni raportin klinker-çimento ku teknikisht e mundur.",
        fertilizer: "N₂O është kritike; siguroni CO₂ e integruar për amoniakun dhe zinxhirin e furnizimit."
      };
      plan += `<div class="action-item priority-medium"><strong>🔧 Specifike për sektorin:</strong> ${sectorTips[currentSector] || ''}</div>`;

      // Albania advantage + warning
      plan += `
        <div class="action-item priority-low"><strong>🇦🇱 Avantazhi i Shqipërisë:</strong> ~0.1 kg CO₂/kWh nga hidro – përdoreni për të ulur CO₂ të tërthorta.</div>
        <div class="action-item priority-high"><strong>⚠️ Kujdes:</strong> Proceset termike (gaz/naftë/qymyr) raportohen veç – shpesh janë burimi kryesor i CO₂.</div>
      `;

      plan += `
        <div class="action-item priority-high">
          <strong>💰 Analiza e Kostove (volum: ${exportVolume.toLocaleString()} t/vit):</strong>
          <ul style="line-height:1.7; margin:8px 0;">
            <li>✅ Me përgatitje: ${preparedCost.toLocaleString()} € /vit</li>
            <li>❌ Default (pa të dhëna): ${unpreparedCost.toLocaleString()} € /vit</li>
            <li>💸 Kursim vjetor i mundshëm: <strong>${savings.toLocaleString()} €</strong></li>
          </ul>
        </div>
      `;

      plan += `
        <div class="action-item priority-high">
          <strong>📈 Prognoza 10‑vjeçare:</strong>
          Kursim kumulativ i mundshëm: <strong style="color:#4ecdc4; font-size:1.1em;">${totalSavings10Years.toLocaleString()} €</strong>
          <div style="opacity:.85;"><small>Me çmim orientues CO₂ dhe rritje mesatare.</small></div>
        </div>
      `;

      qs('#action-plan').innerHTML = plan;
      qs('#results').style.display = 'block';
      qs('#results').scrollIntoView({behavior:'smooth'});

      saveProgress();
    }

    // PDF Export: builds a clean summary to hidden node, then exports
    async function exportPDF(){
      const staging = qs('#pdf-staging');
      const company = {
        name: qs('#company-name').value || '—',
        product: qs('#main-product').value || '—',
        volume: qs('#export-volume').value || '—',
        buyers: qs('#eu-buyers').value || '—'
      };
      const now = new Date();
      const dateStr = now.toLocaleString('sq-AL');

      // Read values from on-screen results
      const resultsNode = qs('#action-plan');
      if (!resultsNode || qs('#results').style.display === 'none'){
        alert('Gjeneroni fillimisht rezultatet dhe pastaj eksportoni PDF.'); return;
      }

      const htmlCover = `
        <div style="display:flex; align-items:center; gap:14px; margin-bottom:14px;">
          <img src="logo.png" style="height:48px" onerror="this.style.display='none'"/>
          <div>
            <div style="font-size:18px; font-weight:800; color:#0f172a;">Entrenovu Hub</div>
            <div style="font-size:13px; color:#334155;">CBAM Gap Analiza – Përmbledhje</div>
          </div>
        </div>
        <div style="font-size:22px; font-weight:800; color:#0b1324; margin:6px 0 4px;">Raport Përmbledhës</div>
        <div style="color:#334155; font-size:12px;">Data: ${dateStr}</div>
        <div class="divider"></div>
        <div style="display:grid; grid-template-columns: 170px 1fr; gap:8px; font-size:13px; color:#0b1324;">
          <div style="font-weight:700;">Kompania</div><div>${company.name}</div>
          <div style="font-weight:700;">Sektori</div><div>${currentSector || '—'}</div>
          <div style="font-weight:700;">Produkti</div><div>${qs('#main-product').selectedOptions[0]?.text || '—'}</div>
          <div style="font-weight:700;">Volumi eksporti</div><div>${company.volume} t/vit</div>
          <div style="font-weight:700;">Blerës kryesorë</div><div>${company.buyers}</div>
        </div>
        <div class="divider"></div>
      `;

      const htmlBody = `
        <div>${resultsNode.innerHTML}</div>
        <div class="divider"></div>
        <div style="font-size:13px; color:#0f172a;"><strong>Kontakt:</strong> +43 650 6965 789 &nbsp;|&nbsp; info@entrenovu.com</div>
      `;

      staging.innerHTML = htmlCover + htmlBody;

      const opt = {
        margin:       [10,10,10,10],
        filename:     'CBAM_Gap_Analiza_Entrenovu.pdf',
        image:        { type: 'jpeg', quality: 0.96 },
        html2canvas:  { scale: 2, useCORS: true },
        jsPDF:        { unit: 'mm', format: 'a4', orientation: 'portrait' }
      };
      await html2pdf().set(opt).from(staging).save();
    }

    // Persistence
    function saveProgress(){
      try{
        localStorage.setItem('cbam_gap_analysis', JSON.stringify({
          responses, currentSector,
          company:{
            name: qs('#company-name').value,
            product: qs('#main-product').value,
            volume: qs('#export-volume').value,
            buyers: qs('#eu-buyers').value
          }
        }));
      }catch(e){}
    }
    function loadProgress(){
      try{
        const saved = JSON.parse(localStorage.getItem('cbam_gap_analysis') || '{}');
        if (saved.company){
          qs('#company-name').value = saved.company.name || '';
          qs('#main-product').value = saved.company.product || '';
          qs('#export-volume').value = saved.company.volume || '';
          qs('#eu-buyers').value = saved.company.buyers || '';
        }
        responses = saved.responses || {};
        if (saved.currentSector) showSector(saved.currentSector);
      }catch(e){}
    }

    // Wire up buttons & autosave
    document.addEventListener('DOMContentLoaded', () => {
      loadProgress();

      // Auto-map dropdown change to sector
      qs('#main-product').addEventListener('change', function(){
        const sector = this.value;
        if (sector) showSector(sector);
        saveProgress();
      });

      // Default to first sector for UX if none selected
      if (!currentSector){
        const firstBtn = qs('.sector-btn');
        if (firstBtn) firstBtn.click();
      }

      qs('#generate').addEventListener('click', generateResults);
      qs('#download-pdf').addEventListener('click', exportPDF);
    });

    document.addEventListener('change', saveProgress);
    document.addEventListener('input', saveProgress);
  </script>
</body>
</html>
