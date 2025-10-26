# researchingfeats.github.io

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Bubba's Gramama</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap" rel="stylesheet">
  <style>
    :root{--bg-mid:#0b0c2a;--accent:#00ffff;--panel:#1a1a3d;--muted:#cfc6ff}
    /* Ensure page only creates a single vertical scroll (no extra horizontal overflow) */
    html,body{height:100%;margin:0;padding:0;overflow-x:hidden;overflow-y:auto;-webkit-overflow-scrolling:touch;
      background:radial-gradient(ellipse at center,var(--bg-mid) 0%,#000 100%),linear-gradient(180deg, rgba(255,255,255,0.02) 0, transparent 100%);
      color:#fff;font-family:'Segoe UI',system-ui,-apple-system,"Orbitron",sans-serif;}
    .container{position:relative;z-index:3;display:flex;flex-direction:column;align-items:center;padding:40px 20px;max-width:1200px;margin:0 auto}
    h1.site-title{margin:10px 0 6px;font-size:2rem;color:var(--accent);text-shadow:0 0 12px rgba(0,255,255,0.14),0 6px 30px rgba(0,0,0,0.6);letter-spacing:1px}
    .user-badge {position: fixed; top: 18px; left: 18px; z-index: 40; background: linear-gradient(90deg, rgba(0,255,255,0.06), rgba(0,0,0,0.18)); border: 1px solid rgba(0,255,255,0.14); padding: 8px 12px; border-radius: 10px; color: var(--accent); font-family: 'Orbitron', sans-serif; font-weight: 700; box-shadow: 0 6px 26px rgba(0,255,255,0.06); display: flex; gap: 10px; align-items: center; min-width: 220px; }
    .user-badge .name { font-size: 14px; letter-spacing: 0.5px; cursor: pointer; }
    .user-badge .time { font-size: 13px; color: rgba(207,198,255,0.9); font-weight:600; }
    .user-badge input.edit-name { background: var(--panel); color: var(--accent); border: 1px solid rgba(0,255,255,0.06); padding:6px 8px; border-radius:6px; font-family:'Orbitron'; font-weight:700; width:140px; }
    .coin-container{position:fixed;top:20px;right:20px;z-index:14;display:flex;align-items:center;gap:10px}
    #coinDisplay{font-size:18px;background:rgba(0,255,255,0.08);padding:6px 12px;border-radius:8px;color:var(--accent);font-family:'Orbitron';box-shadow:0 0 10px rgba(0,255,255,0.06)}
    button.top-btn{padding:6px 12px;border-radius:8px;border:none;background:rgba(0,255,255,0.18);cursor:pointer;font-family:'Orbitron';transition:.2s}
    .panel{position:fixed;background:rgba(5,5,20,0.95);border:1px solid rgba(0,255,255,0.18);border-radius:12px;padding:12px;display:none;flex-direction:column;gap:10px;box-shadow:0 10px 40px rgba(0,255,255,0.06);z-index:13;width:320px;animation:dropdown .28s ease}
    .shop-panel{top:70px;right:20px}
    .leaderboard-panel{top:70px;right:360px;width:260px}
    .admin-panel{top:70px;right:20px;width:640px;max-height:70vh;overflow:auto}
    @keyframes dropdown{from{transform:translateY(-12px);opacity:0}to{transform:translateY(0);opacity:1}}
    .shop-item{display:flex;justify-content:space-between;align-items:center;color:var(--muted);font-family:'Orbitron'}
    .buy-button{background:linear-gradient(90deg,#00ffff,#008080);border:2px solid #00ffff;padding:8px 14px;border-radius:8px;font-weight:700;cursor:pointer;box-shadow:0 0 6px #00ffff;transition:all .18s;font-family:'Orbitron'}
    .buy-button.owned{background:linear-gradient(90deg,#ff4444,#cc0000);border-color:#ff4444;color:#fff;cursor:not-allowed}
    .admin-controls{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
    table.admin-table{width:100%;border-collapse:collapse;font-family:'Orbitron';color:#fff}
    table.admin-table th, table.admin-table td{border:1px solid rgba(255,255,255,0.06);padding:6px;font-size:14px;text-align:left;background:rgba(255,255,255,0.01)}
    table.admin-table input[type="text"], table.admin-table input[type="number"]{width:100%;padding:6px;border-radius:6px;border:1px solid rgba(255,255,255,0.06);background:var(--panel);color:var(--accent);font-family:'Orbitron'}
    .admin-actions{display:flex;gap:8px}
    .small-btn{padding:6px 10px;border-radius:8px;border:none;cursor:pointer;background:linear-gradient(180deg,#00baba,#00ffff);color:#001;font-weight:700}
    .danger-btn{background:linear-gradient(180deg,#ff6666,#ff3333);color:#fff}
    @keyframes pulseGlow{0%,100%{box-shadow:0 0 10px rgba(255,0,0,0.35),0 0 20px rgba(255,0,0,0.25)}50%{box-shadow:0 0 22px rgba(255,0,0,0.6),0 0 36px rgba(255,0,0,0.45)}}
    .leaderboard-panel .close-btn{margin-top:8px;padding:10px 16px;border-radius:8px;border:none;background:linear-gradient(180deg,#ff4444,#cc0000);color:#fff;font-family:'Orbitron';cursor:pointer;animation:pulseGlow 2s infinite}
    .leaderboard-panel .close-btn:hover{transform:translateY(-2px) scale(1.04)}
    .game-block{width:100%;display:flex;align-items:center;justify-content:space-between;gap:20px;padding:12px 16px;margin-bottom:12px;background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.005));border-radius:12px;border:1px solid rgba(255,255,255,0.03);box-shadow:0 6px 18px rgba(0,0,0,0.45)}
    .game-block h2{margin:0;font-size:1.05rem;color:var(--muted)}
    .game-block button.play-btn{padding:10px 16px;border-radius:10px;border:none;background:linear-gradient(180deg,var(--accent),#00cfcf);cursor:pointer}
    #backButton{position:fixed;left:20px;padding:10px 18px;border-radius:8px;border:none;background:rgba(85,85,85,0.9);color:#fff;display:none;z-index:30}
    iframe{width:1200px;max-width:100%;height:600px;border-radius:10px;border:2px solid rgba(255,255,255,0.06);box-shadow:0 10px 50px rgba(0,0,0,0.7);display:none;margin-top:20px;z-index:2}

    /* Fullscreen-friendly styles (when the iframe or its ancestor is in fullscreen) */
    :fullscreen iframe, :-webkit-full-screen iframe, :-ms-fullscreen iframe,
    iframe:fullscreen, iframe:-webkit-full-screen, iframe:-ms-fullscreen,
    :fullscreen > iframe, :-webkit-full-screen > iframe {
      width:100vw !important;
      height:100vh !important;
      position:fixed !important;
      top:0 !important;
      left:0 !important;
      margin:0 !important;
      border-radius:0 !important;
      border:none !important;
      box-shadow:none !important;
      z-index:99999 !important;
    }
    :fullscreen, :-webkit-full-screen, :-ms-fullscreen { background: #000; }

    /* Fix: make decorative star/nebula layers cover viewport without expanding document size */
    .stars, .stars2, .nebula {
      position:fixed;
      top:0;
      left:0;
      width:100vw;
      height:100vh;
      pointer-events:none;
      z-index:0;
      transform:none;
      overflow:hidden;
      mix-blend-mode:screen;
    }
    .stars::after{content:"";position:absolute;left:0;top:0;width:2px;height:2px;background:white;box-shadow:50px 100px white,200px 300px white,400px 150px white,600px 250px white,800px 100px white;animation:twinkle 2.5s infinite ease-in-out}
    .stars2::after{content:"";position:absolute;left:0;top:0;width:1px;height:1px;background:#aaf0ff;box-shadow:120px 80px #aaf0ff,320px 240px #aaf0ff;opacity:0.6;animation:twinkle2 3.5s infinite ease-in-out}
    @keyframes twinkle{0%,100%{opacity:.9}50%{opacity:.3}} @keyframes twinkle2{0%,100%{opacity:.6}50%{opacity:.2}}
    .nebula{background:radial-gradient(600px 300px at 10% 10%, rgba(0,200,255,0.06), transparent 10%),radial-gradient(500px 260px at 80% 70%, rgba(180,0,255,0.04), transparent 8%);opacity:.9;mix-blend-mode:overlay}

    .shooting-star{pointer-events:none;z-index:0;border-radius:2px;position:absolute;display:block}
    .modal-backdrop{position:fixed;inset:0;background:rgba(0,0,0,0.6);display:none;align-items:center;justify-content:center;z-index:20}
    .modal{background:linear-gradient(180deg,rgba(10,12,30,0.96),rgba(14,10,30,0.95));padding:18px;border-radius:12px;border:1px solid rgba(0,255,255,0.06);width:360px;max-width:96%;box-shadow:0 10px 40px rgba(0,0,0,0.6)}
    .modal h4{margin:0 0 8px;color:var(--accent);font-family:'Orbitron'}
    .modal input{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:var(--panel);color:var(--accent);margin-bottom:8px}
    .modal .modal-actions{Display:flex;gap:8px;justify-content:flex-end}
    .admin-note{font-size:13px;color:var(--muted);font-family:'Orbitron'}
    @media(max-width:900px){ .admin-panel{right:10px;left:10px;width:auto} iframe{height:80vh} }

    /* search results styles */
    .search-result { display:flex;justify-content:space-between;align-items:center;padding:10px;border-radius:8px;margin-bottom:8px;background:linear-gradient(180deg,rgba(255,255,255,0.01),rgba(255,255,255,0.005));border:1px solid rgba(255,255,255,0.03) }
    .search-result .meta { display:flex;flex-direction:column;gap:4px; }
    .search-result .meta .id { font-size:12px;color:rgba(207,198,255,0.7) }
    .search-result .actions { display:flex;gap:8px;align-items:center }
    .search-empty { color:var(--muted);font-size:14px;padding:8px }
  </style>
</head>
<body>
  <div class="stars"></div><div class="stars2"></div><div class="nebula"></div>

  <div id="userBadge" class="user-badge" aria-live="polite">
    <div class="name" id="userName" title="Click to edit name">Guest</div>
    <div class="time" id="userTime">00:00:00</div>
  </div>

  <div class="coin-container">
    <button id="dailyRewardBtn" class="top-btn" onclick="claimDailyReward()">🎁 Haha take that Byron</button>
    <button id="leaderboardToggle" class="top-btn" onclick="toggleLeaderboard()">🏆 Leaderboard</button>
    <span id="coinDisplay">🪙 0</span>
    <button id="shopToggle" class="top-btn" onclick="toggleShop()">🛒 Shop</button>
    <button id="adminToggle" class="top-btn" onclick="onAdminToggleClick()">📋 Admin</button>
    <!-- Fullscreen toggle (shows only while iframe visible) -->
    <button id="fullscreenToggle" class="top-btn" style="display:none" title="Make the game full screen" onclick="toggleFullscreen()">⛶ Fullscreen</button>
  </div>

  <div class="panel shop-panel" id="shopPanel" aria-hidden="true">
    <h3>Game Shop</h3>
    <div class="shop-item"><span>Drive Mad</span><button class="buy-button" data-game="drivemad" data-cost="300" onclick="buyGame('drivemad',300)">Buy - 300🪙</button></div>
    <div class="shop-item"><span>Hide and Smash</span><button class="buy-button" data-game="hideandsmash" data-cost="200" onclick="buyGame('hideandsmash',200)">Buy - 200🪙</button></div>
    <div class="shop-item"><span>void network V5</span><button class="buy-button" data-game="voidNetwork" data-cost="1000" onclick="buyGame('voidNetwork',1000)">Buy - 1000🪙</button></div>
    <div class="shop-item"><span>Drift Hunter</span><button class="buy-button" data-game="driftHunters" data-cost="1000" onclick="buyGame('driftHunters',1000)">Buy - 400🪙</button></div>
  </div>

  <div class="panel leaderboard-panel" id="leaderboardPanel" aria-hidden="true">
    <h3>🏆 Top Coin Holders</h3>
    <div id="leaderboardList" style="max-height:260px;overflow:auto"></div>
    <button class="close-btn" onclick="closeLeaderboard()">Close</button>
  </div>

  <div class="panel admin-panel" id="adminPanel" aria-hidden="true">
    <div style="display:flex;justify-content:space-between;align-items:center">
      <h3>Admin Spreadsheet — Edit Players' Coins & Time</h3>
      <div><button class="small-btn" onclick="adminLogout()" title="Log out admin session">Log out</button></div>
    </div>
    <div class="admin-controls">
      <div class="admin-actions">
        <button class="small-btn" onclick="adminAddRow()">+ Add Row</button>
        <button class="small-btn" onclick="adminSave()">Save Changes</button>
        <button class="small-btn" onclick="adminExportCSV()">Export CSV</button>
        <button class="small-btn danger-btn" onclick="adminResetAllTimes()">Reset All Times</button>
        <label style="display:inline-block">
          <input id="adminImportFile" type="file" accept=".csv" style="display:none" onchange="adminImportCSV(this)">
          <button class="small-btn" onclick="document.getElementById('adminImportFile').click()">Import CSV</button>
        </label>
        <!-- NEW: Manage custom games -->
        <button class="small-btn" onclick="openAddGameModal()">+ Add Game</button>
        <button class="small-btn" onclick="adminRenderGamesList()">Manage Games</button>
      </div>
    </div>
    <div>
      <table class="admin-table" id="adminTable">
        <thead><tr><th>#</th><th>Player Name</th><th>Coins</th><th>Time (total)</th><th>Actions</th></tr></thead>
        <tbody></tbody>
      </table>
    </div>

    <!-- NEW: Games management area -->
    <div style="margin-top:12px">
      <h4 style="color:var(--accent);margin:8px 0">Custom Games (admin-managed)</h4>
      <div id="adminGamesArea" style="max-height:200px;overflow:auto;padding:6px;border-radius:8px;background:rgba(255,255,255,0.01);border:1px solid rgba(255,255,255,0.03)"></div>
      <div class="admin-note" style="margin-top:8px">Add games via "Add Game". Mark "Admin Only" to make the game visible only when you're logged in as admin.</div>
    </div>

    <div class="admin-note">Tip: CSV format = name,coins — import will replace/add rows. Press Save to persist changes to localStorage. Use Reset Time to zero a student's cumulative time.</div>
  </div>

  <!-- Add Game Modal -->
  <div class="modal-backdrop" id="gameModalBackdrop" style="display:none;z-index:25">
    <div class="modal" role="dialog" aria-modal="true" id="gameModal">
      <h4 id="gameModalTitle">Add Game</h4>
      <input id="gameIdInput" placeholder="Unique ID (no spaces) — e.g. mygame1" />
      <input id="gameNameInput" placeholder="Game display name — e.g. Secret Race" />
      <input id="gameUrlInput" placeholder="Game URL — https://..." />
      <div style="display:flex;gap:8px;align-items:center;margin-bottom:8px">
        <label style="display:flex;gap:6px;align-items:center"><input type="checkbox" id="gameAdminOnly" /> Admin Only</label>
        <label style="display:flex;gap:6px;align-items:center"><input type="checkbox" id="gameShopProtected" /> Shop Protected</label>
        <input id="gameCostInput" placeholder="Cost (if shop protected) e.g. 300" style="width:120px" />
      </div>
      <div style="display:flex;justify-content:flex-end;gap:8px">
        <button class="small-btn" onclick="closeAddGameModal()">Cancel</button>
        <button class="small-btn" onclick="saveGameFromModal()">Save Game</button>
      </div>
    </div>
  </div>

  <button id="backButton" onclick="goBack()">⬅ Back</button>

  <div class="container">
    <h1 class="site-title">WELCOME to Bubba's Gramama</h1>

    <!-- Search bar (inserted under site title) -->
    <div style="width:100%;max-width:760px;margin:12px 0;display:flex;flex-direction:column;gap:8px;align-items:center">
      <div class="search-row" style="width:100%;display:flex;gap:8px;align-items:center">
        <input id="gameSearchInput" type="search" placeholder="Search games by name or id (try: drift, hide, minecraft) — 'secret' is hidden" 
               aria-label="Search games" style="flex:1;padding:10px 12px;border-radius:8px;border:none;background:var(--panel);color:var(--accent);font-family:'Orbitron';font-size:15px" />
        <button id="gameSearchClear" class="top-btn" style="padding:10px 12px" title="Clear search">✖</button>
      </div>
      <div id="searchResults" aria-live="polite" style="width:100%;max-height:220px;overflow:auto;padding:8px;border-radius:8px;background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);border:1px solid rgba(255,255,255,0.03)"></div>
    </div>

    <img class="gif" src="https://media1.tenor.com/m/0IixRqy4QoEAAAAC/a-fart-fart.gif" alt="gif" style="max-width:90%;border-radius:12px;box-shadow:0 8px 40px rgba(0,0,0,.6)">
    <div class="access-panel" aria-label="Galactic access panel" style="width:100%;max-width:760px;margin:18px 0;padding:16px;border-radius:12px;background:linear-gradient(180deg,rgba(10,12,30,0.6),rgba(14,10,30,0.35));border:1px solid rgba(0,255,255,0.06);display:flex;flex-direction:column;align-items:center;gap:12px">
      <h3>Enter Access Code</h3>
      <div class="code-row" style="display:flex;gap:12px;width:100%;justify-content:center;align-items:center">
        <input id="codeInput" type="text" inputmode="numeric" pattern="[0-9]*" placeholder="• • • •" aria-label="Access code" style="flex:1;padding:12px 14px;border-radius:8px;border:none;background:var(--panel);color:var(--accent);font-family:'Orbitron';text-align:center"/>
        <button class="submit-btn" onclick="checkCode()" style="padding:10px 14px;border-radius:8px;border:none;background:linear-gradient(180deg,var(--accent),#00cfcf);cursor:pointer;font-family:'Orbitron'">Submit</button>
      </div>
      <button id="unlockButton" style="display:none;padding:10px 16px;border-radius:8px;border:none;background:linear-gradient(180deg,#ffd48f,#ff9e3b);cursor:pointer">🚀 Launch Sequence Activated</button>
    </div>

    <!-- games -->
    <div id="staticGames">
      <div class="game-block"><h2>Geo Dash</h2><button class="play-btn" onclick="launchGame('GD')">Play Geo Dash</button></div>
      <div class="game-block"><h2>10 Minutes Till Dawn</h2><button class="play-btn" onclick="launchGame('10mTD')">Play 10 Minutes Till Dawn</button></div>
      <div class="game-block"><h2>1v1 LOL</h2><button class="play-btn" onclick="launchGame('1v1L')">Play 1v1 LOL</button></div>
      <div class="game-block"><h2>Time Shooter</h2><button class="play-btn" onclick="launchGame('TS')">Play Time Shooter</button></div>
      <div class="game-block"><h2>Void Network V5</h2><button class="play-btn" onclick="launchGame('VN')">Open Void Network V5</button></div>
      <div class="game-block"><h2>Steal a BrainRot Fake</h2><button class="play-btn" onclick="launchGame('StealABrainRot')">Play Steal A Brainrot Fake</button></div>
      <div class="game-block"><h2>Hide and Smash</h2><button class="play-btn" onclick="launchGame('hideandsmash')">Play Hide and Smash</button></div>
      <div class="game-block"><h2>Pixel Gun 3d</h2><button class="play-btn" onclick="launchGame('pixelgun')">Play Pixel Gun 3d</button></div>
      <div class="game-block"><h2>Idle Breakout</h2><button class="play-btn" onclick="launchGame('idle-breakout')">Play Idle Breakout</button></div>
      <div class="game-block"><h2>Crossy Road</h2><button class="play-btn" onclick="launchGame('crossyroad')">Play Crossy Road</button></div>
      <div class="game-block"><h2>Slope</h2><button class="play-btn" onclick="launchGame('slope')">Play Slope</button></div>
      <div class="game-block"><h2>Bit Life</h2><button class="play-btn" onclick="launchGame('bitlife')">Play Bit Life</button></div>
      <div class="game-block"><h2>Subway Surfers</h2><button class="play-btn" onclick="launchGame('subway-surfers')">Play Subway Surfers</button></div>
      <div class="game-block"><h2>Stickman Golf</h2><button class="play-btn" onclick="launchGame('stickman-golf')">Play Stickman Golf</button></div>
      <div class="game-block"><h2>Basketball Random</h2><button class="play-btn" onclick="launchGame('basketball-random')">Play Basketball Random</button></div>
      <div class="game-block"><h2>Minecraft</h2><button class="play-btn" onclick="launchGame('minecraft')">Play Minecraft</button></div>
      <div class="game-block"><h2>DRIFT HUNTERS</h2><button class="play-btn" onclick="launchGame('drifthunters')">Play Drift Hunters</button></div>
      <div class="game-block"><h2>Drive Mad!</h2><button class="play-btn" onclick="launchGame('drivemad')">Play Drive Mad</button></div>
      <div class="game-block"><h2>Opposite Day</h2><button class="play-btn" onclick="launchGame('oppositeday')">Don't play Opposite Day</button></div>
      <div class="game-block"><h2>❄️ Snow Rider 3D</h2><button class="play-btn" onclick="launchGame('snowrider')">Play Snow Rider 3D</button></div>
    </div>

    <!-- NEW: custom games container (dynamic) -->
    <div id="customGamesContainer" style="width:100%;max-width:900px;margin-top:18px"></div>

    <iframe id="gameFrame" src="" allowfullscreen allow="fullscreen"></iframe>
  </div>

  <div class="modal-backdrop" id="adminModalBackdrop" role="dialog" aria-modal="true" style="display:none">
    <div class="modal" role="document">
      <h4>Admin Login</h4>
      <div id="adminLoginMessage" style="color:var(--muted);margin-bottom:8px">Enter admin email and password to open the Admin panel.</div>
      <input id="adminEmailInput" type="email" placeholder="Admin email" aria-label="Admin email" />
      <input id="adminPasswordInput" type="password" placeholder="Password" aria-label="Admin password" />
      <div style="display:flex;justify-content:space-between;align-items:center">
        <div id="adminAttemptsInfo" style="color:var(--muted);font-size:13px"></div>
        <div class="modal-actions">
          <button class="small-btn" onclick="closeAdminModal()">Cancel</button>
          <button class="small-btn" onclick="checkAdminCredentials()">Log in</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    /* ---------------------------
       Config (edit here)
    --------------------------- */
    const ADMIN_EMAIL = 'bywhitley@s.sfusd.edu'.toLowerCase();
    const ADMIN_PASSWORD = 'timtimcheesssisgreat!423yesrolds!!';
    const ADMIN_MAX_ATTEMPTS = 4;
    const ADMIN_LOCK_MS = 60 * 1000; // 60 seconds

    /* ---------- state & helpers ---------- */
    const gameURLs = {
      'GD': "https://lolpopami2354.github.io/GeoDash/",
      '10mTD': "https://lolpopami2354.github.io/10mTD",
      '1v1L': "https://lolpopami2354.github.io/1v1L",
      'TS': "https://lolpopami2354.github.io/timeShooter",
      'VN': "https://iready.itafricagroup.com/g.html",
      'StealABrainRot': "https://lolpopami2354.github.io/StealABrainRot/",
      'hideandsmash': "https://gibbat2.github.io/Games/games/hideandsmash/",
      'pixelgun': "https://gibbat2.github.io/Games/games/pixelgun/",
      'idle-breakout': "https://gibbat2.github.io/Games/games/idle-breakout/",
      'crossyroad': "https://gibbat2.github.io/Games/games/crossyroad/",
      'slope': "https://gibbat2.github.io/Games/games/slope/",
      'bitlife': "https://gibbat2.github.io/Games/games/bitlife/",
      'subway-surfers': "https://gibbat2.github.io/Games/games/subway-surfers/",
      'stickman-golf': "https://gibbat2.github.io/Games/games/stickman-golf/",
      'basketball-random': "https://gibbat2.github.io/Games/games/basketball-random/",
      'minecraft': "https://daniezonmc.github.io/1.20/",
      'drifthunters': "https://gibbat2.github.io/Games/games/drifthunters/",
      'drivemad': "https://lolpopami2354.github.io/200LDM",
      'oppositeday': "https://www.hoodamath.com/games/oppositeday.html",
      'snowrider': "https://www.hoodamath.com/games/snowrider3d.html",
      'secret': "https://010203040641.studentvue.my.cdn.cloudflare.net/"
    };

    // Coins & owned games - persistent
    let coins = parseInt(localStorage.getItem('coins') || '0', 10);
    let ownedGames = JSON.parse(localStorage.getItem('ownedGames') || '{}');

    function saveData(){
      localStorage.setItem('coins', String(coins));
      localStorage.setItem('ownedGames', JSON.stringify(ownedGames));
    }

    function updateCoinDisplay(){
      const el = document.getElementById('coinDisplay');
      if (el) el.textContent = `🪙 ${coins}`;
    }

    function updateShopButtons(){
      document.querySelectorAll('.buy-button').forEach(btn=>{
        const gid = btn.dataset.game;
        const cost = btn.dataset.cost || '';
        if (gid && ownedGames[gid]) {
          btn.classList.add('owned');
          btn.textContent = 'Owned';
          btn.disabled = true;
        } else {
          btn.classList.remove('owned');
          btn.disabled = false;
          btn.textContent = cost ? `Buy - ${cost}🪙` : 'Buy';
        }
      });
      // also update any dynamic buy buttons in admin-managed lists
      document.querySelectorAll('.buy-button.dynamic').forEach(btn=>{
        const gid = btn.dataset.game;
        const cost = btn.dataset.cost || '';
        if (gid && ownedGames[gid]) {
          btn.classList.add('owned');
          btn.textContent = 'Owned';
          btn.disabled = true;
        } else {
          btn.classList.remove('owned');
          btn.disabled = false;
          btn.textContent = cost ? `Buy - ${cost}🪙` : 'Buy';
        }
      });
    }

    /* ---------------- Time storage per-user ---------------- */
    function loadTimeMapping() {
      try {
        const raw = localStorage.getItem('timeSpentByUser');
        if (!raw) {
          const legacy = localStorage.getItem('timeSpentSeconds');
          if (legacy) {
            const val = parseInt(legacy, 10) || 0;
            const name = localStorage.getItem('playerName') || 'Guest';
            const map = {};
            map[name] = val;
            localStorage.setItem('timeSpentByUser', JSON.stringify(map));
            localStorage.removeItem('timeSpentSeconds');
            return map;
          }
          return {};
        }
        return JSON.parse(raw || '{}');
      } catch (e) {
        return {};
      }
    }
    function saveTimeMapping(map) { localStorage.setItem('timeSpentByUser', JSON.stringify(map || {})); }

    function getPlayerName() {
      return (localStorage.getItem('playerName') || '').trim() || null;
    }

    function ensurePlayerName() {
      let name = getPlayerName();
      if (!name) {
        name = prompt("Enter your name (this will appear on the leaderboard and top-left badge):", "Guest") || "Guest";
        localStorage.setItem('playerName', name);
      }
      updateUserBadgeName();
    }

    /* ---------- USER BADGE & CUMULATIVE TIME ---------- */
    let sessionStart = Date.now();
    let sessionTimerInterval = null;

    function formatDuration(seconds) {
      seconds = Math.max(0, Math.floor(seconds));
      const days = Math.floor(seconds / 86400);
      seconds = seconds % 86400;
      const hrs = Math.floor(seconds / 3600);
      seconds = seconds % 3600;
      const mins = Math.floor(seconds / 60);
      const secs = seconds % 60;
      if (days > 0) return `${days}d ${String(hrs).padStart(2,'0')}:${String(mins).padStart(2,'0')}:${String(secs).padStart(2,'0')}`;
      return `${String(hrs).padStart(2,'0')}:${String(mins).padStart(2,'0')}:${String(secs).padStart(2,'0')}`;
    }

    function getStoredSecondsForName(name) {
      const map = loadTimeMapping();
      return Number(map[name] || 0);
    }

    function setStoredSecondsForName(name, seconds) {
      const map = loadTimeMapping();
      map[name] = Math.max(0, Math.floor(seconds));
      saveTimeMapping(map);
    }

    function addSecondsToName(name, secondsToAdd) {
      const map = loadTimeMapping();
      map[name] = Math.max(0, Math.floor((map[name] || 0) + secondsToAdd));
      saveTimeMapping(map);
    }

    function getTotalSecondsForCurrentUser() {
      const name = getPlayerName() || 'Guest';
      const stored = getStoredSecondsForName(name);
      const elapsedThisSession = Math.floor((Date.now() - sessionStart) / 1000);
      return stored + elapsedThisSession;
    }

    function updateUserBadgeName() {
      const name = getPlayerName() || 'Bubbas Guest';
      const elem = document.getElementById('userName');
      if (elem) elem.textContent = name;
      if (localStorage.getItem('playerName') !== name) localStorage.setItem('playerName', name);
      updateLeaderboard();
      positionBackButton();
    }

    function updateUserBadgeTime() {
      const total = getTotalSecondsForCurrentUser();
      const el = document.getElementById('userTime');
      if (el) el.textContent = formatDuration(total);
    }

    function startUserTimer() {
      if (sessionTimerInterval) clearInterval(sessionTimerInterval);
      sessionStart = Date.now();
      updateUserBadgeTime();
      sessionTimerInterval = setInterval(updateUserBadgeTime, 1000);
    }

    function persistSessionTimeOnUnload() {
      try {
        const name = getPlayerName() || 'Guest';
        const sessionSec = Math.floor((Date.now() - sessionStart) / 1000);
        addSecondsToName(name, sessionSec);
      } catch (e) {}
    }

    window.addEventListener('storage', (ev) => {
      if (ev.key === 'playerName') updateUserBadgeName();
      if (ev.key === 'timeSpentByUser') updateUserBadgeTime();
      if (ev.key === 'coins') {
        coins = parseInt(localStorage.getItem('coins') || '0', 10);
        updateCoinDisplay();
        updateShopButtons();
      }
      if (ev.key === 'customGames') {
        // when other tabs change custom games, re-render
        renderCustomGames();
        adminRenderGamesList();
      }
    });

    function attachBadgeEditHandlers() {
      const existing = document.getElementById('userName');
      if (!existing) return;
      existing.onclick = null;
      existing.addEventListener('click', () => {
        const oldName = getPlayerName() || 'Bubbas Guest';
        const input = document.createElement('input');
        input.className = 'edit-name';
        input.value = oldName;
        input.title = 'Press Enter to save, Escape to cancel';
        existing.replaceWith(input);
        input.focus();
        input.setSelectionRange(0, input.value.length);

        function finish(save) {
          const newNameRaw = input.value.trim() || 'Guest';
          const newName = newNameRaw;
          const span = document.createElement('div');
          span.id = 'userName';
          span.className = 'name';
          span.textContent = newName;
          input.replaceWith(span);
          attachBadgeEditHandlers();
          if (save) {
            if (oldName !== newName) {
              const map = loadTimeMapping();
              const oldSeconds = Number(map[oldName] || 0);
              const newSeconds = Number(map[newName] || 0);
              map[newName] = Math.max(0, oldSeconds + newSeconds);
              if (map.hasOwnProperty(oldName)) delete map[oldName];
              saveTimeMapping(map);
              localStorage.setItem('playerName', newName);
              const board = JSON.parse(localStorage.getItem('leaderboard') || '[]');
              let updated = false;
              for (const p of board) {
                if (p.name === oldName) { p.name = newName; updated = true; }
              }
              if (updated) localStorage.setItem('leaderboard', JSON.stringify(board));
              updateUserBadgeName();
              updateUserBadgeTime();
              updateLeaderboard();
              localStorage.setItem('timeSpentByUser', JSON.stringify(loadTimeMapping()));
              localStorage.setItem('playerName', newName);
            }
          } else {
            updateUserBadgeName();
          }
          positionBackButton();
        }

        input.addEventListener('keydown', (e) => {
          if (e.key === 'Enter') { finish(true); }
          else if (e.key === 'Escape') { finish(false); }
        });
        input.addEventListener('blur', () => finish(true));
      });
    }

    function positionBackButton() {
      const badge = document.getElementById('userBadge');
      const back = document.getElementById('backButton');
      if (!badge || !back) return;
      const rect = badge.getBoundingClientRect();
      const GAP = 8;
      const finalTop = Math.max(8, Math.round(rect.bottom + GAP));
      back.style.top = finalTop + 'px';
      back.style.left = '20px';
    }

    function initUserBadge() {
      ensurePlayerName();
      startUserTimer();
      attachBadgeEditHandlers();
      positionBackButton();
      window.addEventListener('beforeunload', persistSessionTimeOnUnload);
      window.addEventListener('pagehide', persistSessionTimeOnUnload);
      window.addEventListener('resize', positionBackButton);
    }

    // ---------- rest of site logic ----------
    updateCoinDisplay();
    updateShopButtons();

    // Helper: are we in fullscreen (covers multiple browser prefixes)
    function isInFullscreen() {
      return !!(
        document.fullscreenElement ||
        document.webkitFullscreenElement ||
        document.msFullscreenElement
      );
    }

    // Give 250 coins after 60 seconds for visit (and save)
    // but don't show the alert if the page/iframe is currently fullscreen.
    setTimeout(()=>{
      coins += 250;
      saveData();
      updateCoinDisplay();

      // only show alert if tab is visible AND not in fullscreen
      if (document.visibilityState !== 'hidden' && !isInFullscreen()) {
        alert("You earned 250 🪙 for visiting!");
      }
    }, 60000);

    /* shop / buy */
    function toggleShop(){
      const p=document.getElementById('shopPanel');
      p.style.display = (p.style.display==='flex') ? 'none' : 'flex';
      p.setAttribute('aria-hidden', p.style.display==='none');
    }

    function buyGame(gid,cost){
      if (ownedGames[gid]) { alert("You already own this game."); return; }
      if (coins >= cost) {
        coins -= cost;
        ownedGames[gid] = true;
        saveData();
        updateCoinDisplay();
        updateShopButtons();
        alert(`You bought ${gid} 🎮!`);
        // persist coins change so other tabs see it
        localStorage.setItem('coins', String(coins));
      } else alert("Not enough coins!");
    }

    /* iframe + fullscreen support */
    function launchGame(id){
      // resolve dynamic games (customGames) if needed
      const custom = getCustomGameById(id);
      const shopProtected = (custom && custom.shopProtected) || ['drivemad','hideandsmash','voidNetwork','driftHunters'].includes(id);
      if (shopProtected && !ownedGames[id]) {
        alert("You need to buy this game first 🛒");
        return;
      }
      const src = (custom && custom.url) || gameURLs[id];
      if (!src) {
        console.warn('Missing url for', id);
        alert('Could not find the requested game.');
        return;
      }
      const iframe = document.getElementById('gameFrame');
      iframe.src = src;
      iframe.style.display = 'block';

      // show back + fullscreen buttons
      const backBtn = document.getElementById('backButton');
      const fsBtn = document.getElementById('fullscreenToggle');
      backBtn.style.display = 'inline-block';
      fsBtn.style.display = 'inline-block';

      positionBackButton();

      // scroll so the BOTTOM of the iframe is visible.
      setTimeout(() => {
        try {
          iframe.scrollIntoView({ behavior: 'smooth', block: 'end' });
        } catch (e) {
          window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
        }
      }, 60);
    }

    function goBack(){
      const iframe = document.getElementById('gameFrame');
      iframe.style.display = 'none';
      iframe.src = '';
      const backBtn = document.getElementById('backButton');
      backBtn.style.display = 'none';
      const fsBtn = document.getElementById('fullscreenToggle');
      fsBtn.style.display = 'none';
      try { if (document.fullscreenElement) document.exitFullscreen(); } catch(e){}
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // helper to request fullscreen safely with fallbacks
    async function requestFsOnElement(el) {
      if (!el) return;
      try {
        if (el.requestFullscreen) await el.requestFullscreen();
        else if (el.webkitRequestFullscreen) el.webkitRequestFullscreen();
        else if (el.msRequestFullscreen) el.msRequestFullscreen();
      } catch (e) {
        console.warn('Primary fullscreen request failed, trying wrapper...', e);
        const wrapper = el.parentElement || document.documentElement;
        try {
          if (wrapper.requestFullscreen) await wrapper.requestFullscreen();
          else if (wrapper.webkitRequestFullscreen) wrapper.webkitRequestFullscreen();
          else if (wrapper.msRequestFullscreen) wrapper.msRequestFullscreen();
        } catch (err) {
          console.warn('Fallback fullscreen also failed', err);
          alert('Unable to enter fullscreen due to browser restrictions.');
        }
      }
    }

    function toggleFullscreen(){
      const iframe = document.getElementById('gameFrame');
      if (!iframe || iframe.style.display === 'none') return alert('Open a game first');
      const isFs = !!(document.fullscreenElement || document.webkitFullscreenElement || document.msFullscreenElement);
      if (isFs) {
        try { if (document.exitFullscreen) document.exitFullscreen(); else if (document.webkitExitFullscreen) document.webkitExitFullscreen(); } catch(e){}
      } else {
        requestFsOnElement(iframe);
      }
    }

    function onFullscreenChange(){
      const isFs = !!(document.fullscreenElement || document.webkitFullscreenElement || document.msFullscreenElement);
      const fsBtn = document.getElementById('fullscreenToggle');
      if (!fsBtn) return;
      if (isFs) {
        fsBtn.textContent = 'Exit Fullscreen ⤢';
      } else {
        fsBtn.textContent = '⛶ Fullscreen';
      }
    }
    document.addEventListener('fullscreenchange', onFullscreenChange);
    document.addEventListener('webkitfullscreenchange', onFullscreenChange);
    document.addEventListener('msfullscreenchange', onFullscreenChange);

    /* daily reward */
    function claimDailyReward(){
      const today = new Date().toDateString();
      const last = localStorage.getItem('lastDailyClaim');
      if (last === today) { alert("You already claimed today's reward! Come back tomorrow."); return; }
      coins += 250;
      saveData();
      updateCoinDisplay();
      localStorage.setItem('lastDailyClaim', today);
      alert("🎁 You received 250🪙 for your daily visit!");
    }

    /* leaderboard */
    function toggleLeaderboard(){
      const p = document.getElementById('leaderboardPanel');
      if (p.style.display === 'flex') { p.style.display = 'none'; p.setAttribute('aria-hidden','true'); }
      else { updateLeaderboard(); p.style.display = 'flex'; p.setAttribute('aria-hidden','false'); }
    }
    function closeLeaderboard(){ document.getElementById('leaderboardPanel').style.display = 'none'; document.getElementById('leaderboardPanel').setAttribute('aria-hidden','true'); }

    function updateLeaderboard(){
      let board = JSON.parse(localStorage.getItem('leaderboard') || '[]');
      const name = localStorage.getItem('playerName') || prompt("Enter your name for the leaderboard:") || "Guest";
      localStorage.setItem('playerName', name);

      const existing = board.find(p => p.name === name);
      if (existing) existing.coins = coins;
      else board.push({ name, coins });

      board.sort((a,b) => b.coins - a.coins);
      localStorage.setItem('leaderboard', JSON.stringify(board));

      const list = document.getElementById('leaderboardList');
      list.innerHTML = board.slice(0, 10).map((p, i) =>
        `<div>${i+1}. ${p.name} — ${p.coins}🪙</div>` ).join('');
    }

    /* access code */
    function checkCode(){
      const input = document.getElementById('codeInput').value.trim();
      const normalized = input.toLowerCase();
      // Acceptable codes (case-insensitive). This requires exact string match after trimming.
      const allowed = ['f-pres47', 'no-kings!', '!no-kings!'];
      const button = document.getElementById('unlockButton');
      if (allowed.includes(normalized)) {
        button.style.display = 'inline-block';
        button.animate([{ transform: 'scale(.96)' }, { transform: 'scale(1)' }], { duration: 220, easing: 'ease-out' });
        clearTimeout(window._unlockHideTimeout);
        window._unlockHideTimeout = setTimeout(()=>{ button.style.display = 'none'; }, 10000);
      } else {
        button.style.display = 'none';
        const el = document.getElementById('codeInput');
        el.animate([{ transform: 'translateX(0)' }, { transform: 'translateX(-8px)' }, { transform: 'translateX(8px)' }, { transform: 'translateX(0)' }], { duration: 260, iterations: 1 });
      }
    }
    document.getElementById('codeInput').addEventListener('keydown', function(e){ if (e.key === 'Enter') { e.preventDefault(); checkCode(); } });
    document.getElementById('unlockButton').addEventListener('click', function() {
      launchGame('secret');
      this.style.display = 'none';
    });

    /* ---------- ADMIN ---------- */
    function getAdminState(){ const raw = localStorage.getItem('admin_attempts') || '{}'; try { const a = JSON.parse(raw); return { attempts: Number(a.attempts || 0), lockedUntil: Number(a.lockedUntil || 0) }; } catch(e){ return { attempts:0, lockedUntil:0 }; } }
    function setAdminState(state){ localStorage.setItem('admin_attempts', JSON.stringify({ attempts: Number(state.attempts||0), lockedUntil: Number(state.lockedUntil||0) })); }

    function showAdminModal(message){
      const backdrop = document.getElementById('adminModalBackdrop');
      document.getElementById('adminLoginMessage').textContent = message || 'Enter admin email and password to open the Admin panel.';
      const info = document.getElementById('adminAttemptsInfo');
      const st = getAdminState();
      if (st.lockedUntil && Date.now() < st.lockedUntil) {
        const remaining = Math.ceil((st.lockedUntil - Date.now())/1000);
        info.textContent = `Locked for ${remaining}s`;
      } else {
        info.textContent = `Attempts left: ${Math.max(0, ADMIN_MAX_ATTEMPTS - st.attempts)}`;
      }
      backdrop.style.display = 'flex';
      document.getElementById('adminEmailInput').value = '';
      document.getElementById('adminPasswordInput').value = '';
      document.getElementById('adminEmailInput').focus();
    }
    function closeAdminModal(){ document.getElementById('adminModalBackdrop').style.display = 'none'; }
    document.getElementById('adminModalBackdrop').addEventListener('click', function(e){ if (e.target === this) closeAdminModal(); });

    function onAdminToggleClick(){
      if (sessionStorage.getItem('isAdmin') === 'true') {
        const p = document.getElementById('adminPanel');
        p.style.display = (p.style.display === 'flex') ? 'none' : 'flex';
        p.setAttribute('aria-hidden', p.style.display === 'none');
        if (p.style.display === 'flex') {
          adminRenderTable();
          adminRenderGamesList();
        }
        return;
      }
      const st = getAdminState();
      if (st.lockedUntil && Date.now() < st.lockedUntil) {
        showAdminModal('Too many failed attempts — admin locked temporarily.');
      } else {
        showAdminModal();
      }
    }

    function checkAdminCredentials(){
      const st = getAdminState();
      if (st.lockedUntil && Date.now() < st.lockedUntil) {
        showAdminModal('Locked due to many failed attempts. Try again later.');
        return;
      }
      const emailVal = (document.getElementById('adminEmailInput').value || '').trim().toLowerCase();
      const passVal = (document.getElementById('adminPasswordInput').value || '').trim();
      if (!emailVal || !passVal) { showAdminModal('Please enter both email and password.'); return; }

      if (emailVal === ADMIN_EMAIL && passVal === ADMIN_PASSWORD) {
        sessionStorage.setItem('isAdmin','true');
        setAdminState({ attempts: 0, lockedUntil: 0 });
        closeAdminModal();
        const p = document.getElementById('adminPanel');
        p.style.display = 'flex';
        p.setAttribute('aria-hidden','false');
        adminRenderTable();
        adminRenderGamesList();
        renderCustomGames(); // show admin-only games now that admin is logged in
        alert('Admin access granted for this session.');
      } else {
        st.attempts = (st.attempts || 0) + 1;
        if (st.attempts >= ADMIN_MAX_ATTEMPTS) {
          st.lockedUntil = Date.now() + ADMIN_LOCK_MS;
          showAdminModal('Too many failed attempts — admin locked temporarily.');
        } else {
          showAdminModal('Email or password not recognized. Try again.');
        }
        setAdminState(st);
      }
    }

    function adminLogout(){ sessionStorage.removeItem('isAdmin'); const p = document.getElementById('adminPanel'); p.style.display = 'none'; p.setAttribute('aria-hidden','true'); renderCustomGames(); alert('Admin session ended.'); }

    /* ---------- Admin spreadsheet code (with Reset Time buttons) ---------- */
    function adminRenderTable(){
      const tbody = document.querySelector('#adminTable tbody');
      tbody.innerHTML = '';
      let board = JSON.parse(localStorage.getItem('leaderboard') || '[]');
      if (!board.length) {
        const name = localStorage.getItem('playerName') || 'Guest';
        board = [{ name, coins }];
      }
      const timeMap = loadTimeMapping();
      board.forEach((row, idx) => {
        const tr = document.createElement('tr');

        const tdIndex = document.createElement('td');
        tdIndex.style.width = '40px';
        tdIndex.textContent = idx + 1;

        const tdName = document.createElement('td');
        const inputName = document.createElement('input');
        inputName.type = 'text';
        inputName.value = row.name || '';
        tdName.appendChild(inputName);

        const tdCoins = document.createElement('td');
        const inputCoins = document.createElement('input');
        inputCoins.type = 'number';
        inputCoins.min = 0;
        inputCoins.value = Number(row.coins) || 0;
        tdCoins.appendChild(inputCoins);

        const tdTime = document.createElement('td');
        const totalSeconds = Number(timeMap[row.name] || 0);
        tdTime.textContent = formatDuration(totalSeconds);

        const tdActions = document.createElement('td');
        tdActions.style.width = '200px';
        const delBtn = document.createElement('button');
        delBtn.className = 'small-btn';
        delBtn.textContent = 'Delete';
        delBtn.onclick = function(){ adminDeleteRow(this); };

        const resetBtn = document.createElement('button');
        resetBtn.className = 'small-btn danger-btn';
        resetBtn.style.marginLeft = '8px';
        resetBtn.textContent = 'Reset Time';
        resetBtn.title = `Zero ${row.name}'s cumulative time`;
        resetBtn.onclick = function(){ adminResetTimeForRow(row.name, tdTime); };

        tdActions.appendChild(delBtn);
        tdActions.appendChild(resetBtn);

        tr.appendChild(tdIndex);
        tr.appendChild(tdName);
        tr.appendChild(tdCoins);
        tr.appendChild(tdTime);
        tr.appendChild(tdActions);

        tbody.appendChild(tr);
      });
    }

    function adminAddRow(){
      const tbody = document.querySelector('#adminTable tbody');
      const tr = document.createElement('tr');
      const idx = tbody.children.length + 1;

      const tdIndex = document.createElement('td');
      tdIndex.style.width = '40px';
      tdIndex.textContent = idx;

      const tdName = document.createElement('td');
      const inputName = document.createElement('input');
      inputName.type = 'text';
      inputName.value = 'New Player';
      tdName.appendChild(inputName);

      const tdCoins = document.createElement('td');
      const inputCoins = document.createElement('input');
      inputCoins.type = 'number';
      inputCoins.min = 0;
      inputCoins.value = 0;
      tdCoins.appendChild(inputCoins);

      const tdTime = document.createElement('td');
      tdTime.textContent = formatDuration(0);

      const tdActions = document.createElement('td');
      tdActions.style.width = '200px';
      const delBtn = document.createElement('button');
      delBtn.className = 'small-btn';
      delBtn.textContent = 'Delete';
      delBtn.onclick = function(){ adminDeleteRow(this); };
      const resetBtn = document.createElement('button');
      resetBtn.className = 'small-btn danger-btn';
      resetBtn.style.marginLeft = '8px';
      resetBtn.textContent = 'Reset Time';
      resetBtn.onclick = function(){ adminResetTimeForRow(inputName.value.trim() || 'Guest', tdTime); };
      tdActions.appendChild(delBtn);
      tdActions.appendChild(resetBtn);

      tr.appendChild(tdIndex);
      tr.appendChild(tdName);
      tr.appendChild(tdCoins);
      tr.appendChild(tdTime);
      tr.appendChild(tdActions);

      tbody.appendChild(tr);
      const panel = document.getElementById('adminPanel');
      panel.scrollTop = panel.scrollHeight;
    }

    function adminDeleteRow(button){
      const tr = button.closest('tr');
      if (!tr) return;
      tr.remove();
      Array.from(document.querySelectorAll('#adminTable tbody tr')).forEach((r,i)=> r.children[0].textContent = i+1 );
    }

    function adminSave(){
      const rows = Array.from(document.querySelectorAll('#adminTable tbody tr'));
      const newBoard = [];
      for (const r of rows) {
        const name = (r.querySelector('input[type="text"]').value || '').trim() || 'Guest';
        let coinsVal = parseInt(r.querySelector('input[type="number"]').value, 10);
        if (Number.isNaN(coinsVal) || coinsVal < 0) coinsVal = 0;
        newBoard.push({ name, coins: coinsVal });
      }
      newBoard.sort((a,b)=> b.coins - a.coins);
      localStorage.setItem('leaderboard', JSON.stringify(newBoard));
      const myName = localStorage.getItem('playerName') || 'Guest';
      const me = newBoard.find(p => p.name === myName);
      if (me) { coins = me.coins; saveData(); updateCoinDisplay(); }
      updateLeaderboard(); updateShopButtons();
      adminRenderTable();
      alert('Saved leaderboard changes.');
    }

    function adminExportCSV(){
      const board = JSON.parse(localStorage.getItem('leaderboard') || '[]');
      if (!board.length) { alert('No leaderboard data to export.'); return; }
      const csv = board.map(r => `${escapeCsv(r.name)},${Number(r.coins)}`).join('\n');
      const blob = new Blob([csv], { type: 'text/csv' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = 'leaderboard.csv';
      document.body.appendChild(a); a.click(); a.remove();
      URL.revokeObjectURL(url);
    }

    function adminImportCSV(inputEl){
      const file = inputEl.files && inputEl.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e){
        const text = e.target.result;
        const rows = text.split(/\r?\n/).map(l => l.trim()).filter(Boolean);
        const parsed = [];
        for (const line of rows){
          const parts = line.split(',');
          if (!parts.length) continue;
          const name = parts[0].trim();
          const coinsVal = parseInt(parts[1] ? parts[1].trim() : '0', 10) || 0;
          parsed.push({ name, coins: coinsVal });
        }
        if (!parsed.length) { alert('No valid rows found in CSV.'); inputEl.value = ''; return; }
        parsed.sort((a,b)=> b.coins - a.coins);
        localStorage.setItem('leaderboard', JSON.stringify(parsed));
        adminRenderTable();
        updateLeaderboard();
        updateShopButtons();
        alert('Imported CSV into leaderboard (saved).');
        inputEl.value = '';
      };
      reader.readAsText(file);
    }

    function escapeCsv(s){ if (s.indexOf(',') !== -1 || s.indexOf('"') !== -1) { return '"' + String(s).replace(/"/g,'""') + '"'; } return s; }

    function adminResetTimeForRow(playerName, tdTimeCell) {
      if (!confirm(`Reset cumulative time for "${playerName}" to 0?`)) return;
      const map = loadTimeMapping();
      if (map.hasOwnProperty(playerName)) delete map[playerName];
      saveTimeMapping(map);
      if (tdTimeCell) tdTimeCell.textContent = formatDuration(0);
      if ((getPlayerName() || 'Guest') === playerName) {
        sessionStart = Date.now();
        updateUserBadgeTime();
      }
      adminRenderTable();
      alert(`Cumulative time for "${playerName}" has been reset.`);
    }

    function adminResetAllTimes() {
      if (!confirm('Reset cumulative time for ALL players to 0? This cannot be undone.')) return;
      saveTimeMapping({});
      sessionStart = Date.now();
      updateUserBadgeTime();
      adminRenderTable();
      alert('All cumulative times reset to 0.');
    }

    /* ---------- Admin: custom games support ---------- */
    function loadCustomGames() {
      try {
        const raw = localStorage.getItem('customGames') || '[]';
        return JSON.parse(raw);
      } catch (e) { return []; }
    }
    function saveCustomGames(arr) {
      localStorage.setItem('customGames', JSON.stringify(arr || []));
      // notify other tabs
      try { localStorage.setItem('customGames_sync', Date.now()); } catch(e){}
    }

    function getCustomGameById(id) {
      if (!id) return null;
      const arr = loadCustomGames();
      return arr.find(g => String(g.id) === String(id)) || null;
    }

    // Render custom games in the main page (only show adminOnly games when admin is logged in)
    function renderCustomGames() {
      const container = document.getElementById('customGamesContainer');
      container.innerHTML = '';
      const arr = loadCustomGames();
      if (!arr || !arr.length) return;
      const isAdmin = sessionStorage.getItem('isAdmin') === 'true';
      arr.forEach(g => {
        if (g.adminOnly && !isAdmin) return; // skip admin-only for non-admins
        const div = document.createElement('div');
        div.className = 'game-block';
        const h = document.createElement('h2');
        h.textContent = g.name + (g.adminOnly ? ' (admin)' : '');
        const btn = document.createElement('button');
        btn.className = 'play-btn';
        btn.textContent = g.shopProtected ? `Play (locked ${g.cost||'?'})` : 'Play';
        btn.onclick = function(){ launchGame(g.id); };
        div.appendChild(h);
        div.appendChild(btn);

        // If shop-protected and admin viewing, show buy button in admin area too
        if (g.shopProtected && (!g.adminOnly || isAdmin)) {
          const buyBtn = document.createElement('button');
          buyBtn.className = 'buy-button dynamic';
          buyBtn.style.marginLeft = '8px';
          buyBtn.dataset.game = g.id;
          buyBtn.dataset.cost = String(g.cost || 0);
          buyBtn.onclick = function(){ buyGame(g.id, Number(g.cost || 0)); };
          div.appendChild(buyBtn);
        }

        container.appendChild(div);
      });
      updateShopButtons();
    }

    // Admin: render games list inside admin panel with edit/delete
    function adminRenderGamesList() {
      const area = document.getElementById('adminGamesArea');
      area.innerHTML = '';
      const arr = loadCustomGames();
      if (!arr.length) { area.innerHTML = '<div style="color:var(--muted)">No custom games added yet.</div>'; return; }
      arr.forEach((g, idx) => {
        const wrapper = document.createElement('div');
        wrapper.style.display = 'flex';
        wrapper.style.justifyContent = 'space-between';
        wrapper.style.alignItems = 'center';
        wrapper.style.padding = '6px';
        wrapper.style.borderBottom = '1px solid rgba(255,255,255,0.03)';

        const left = document.createElement('div');
        left.style.flex = '1';
        left.innerHTML = `<div style="font-weight:700">${idx+1}. ${g.name}</div><div style="font-size:12px;color:var(--muted)">${g.url}</div>`;
        wrapper.appendChild(left);

        const right = document.createElement('div');
        right.style.display = 'flex';
        right.style.gap = '6px';

        const edit = document.createElement('button');
        edit.className = 'small-btn';
        edit.textContent = 'Edit';
        edit.onclick = () => openAddGameModal(g);

        const del = document.createElement('button');
        del.className = 'small-btn danger-btn';
        del.textContent = 'Delete';
        del.onclick = () => { if (!confirm('Delete this custom game?')) return; deleteCustomGame(g.id); };

        right.appendChild(edit);
        right.appendChild(del);
        wrapper.appendChild(right);

        area.appendChild(wrapper);
      });
    }

    function deleteCustomGame(id) {
      let arr = loadCustomGames();
      arr = arr.filter(g => String(g.id) !== String(id));
      saveCustomGames(arr);
      adminRenderGamesList();
      renderCustomGames();
      alert('Custom game deleted.');
    }

    function openAddGameModal(game) {
      document.getElementById('gameModalBackdrop').style.display = 'flex';
      document.getElementById('gameModalTitle').textContent = game ? 'Edit Game' : 'Add Game';
      document.getElementById('gameIdInput').value = game ? game.id : '';
      document.getElementById('gameIdInput').disabled = !!game; // don't change id when editing
      document.getElementById('gameNameInput').value = game ? game.name : '';
      document.getElementById('gameUrlInput').value = game ? game.url : '';
      document.getElementById('gameAdminOnly').checked = game ? !!game.adminOnly : true;
      document.getElementById('gameShopProtected').checked = game ? !!game.shopProtected : false;
      document.getElementById('gameCostInput').value = game ? (game.cost || '') : '';
    }

    function closeAddGameModal(){
      document.getElementById('gameModalBackdrop').style.display = 'none';
      document.getElementById('gameIdInput').disabled = false;
    }

    function saveGameFromModal(){
      const id = (document.getElementById('gameIdInput').value || '').trim();
      const name = (document.getElementById('gameNameInput').value || '').trim();
      const url = (document.getElementById('gameUrlInput').value || '').trim();
      const adminOnly = document.getElementById('gameAdminOnly').checked;
      const shopProtected = document.getElementById('gameShopProtected').checked;
      const costRaw = (document.getElementById('gameCostInput').value || '').trim();
      const cost = Number(costRaw) || 0;

      if (!id || !name || !url) { alert('Please provide id, name, and url.'); return; }

      let arr = loadCustomGames();
      const exists = arr.find(g => String(g.id) === String(id));
      if (exists) {
        // update
        exists.name = name;
        exists.url = url;
        exists.adminOnly = !!adminOnly;
        exists.shopProtected = !!shopProtected;
        exists.cost = cost;
      } else {
        // ensure unique id (don't overwrite built-in URLs unless intentionally using same id)
        arr.push({ id, name, url, adminOnly: !!adminOnly, shopProtected: !!shopProtected, cost: cost });
      }
      saveCustomGames(arr);
      closeAddGameModal();
      adminRenderGamesList();
      renderCustomGames();
      alert('Custom game saved.');
    }

    /* shooting stars (lightweight) */
    function spawnShootingStar() {
      const star = document.createElement('div');
      star.className = 'shooting-star';
      const size = Math.random() * 2 + 1; // size of the star
      star.style.width = `${size}px`;
      star.style.height = `${size}px`;
      star.style.background = 'white';
      star.style.opacity = Math.random() * 0.8 + 0.2;
      star.style.borderRadius = '50%';

      const startX = Math.random() * window.innerWidth;
      const startY = Math.random() * window.innerHeight;
      const endX = startX + (Math.random() * 300 + 200);
      const endY = startY + (Math.random() * 100 + 50);
      star.style.left = `${startX}px`;
      star.style.top = `${startY}px`;

      star.style.boxShadow = '0 0 6px 2px rgba(255,255,255,0.6), 0 0 12px 4px rgba(255,255,255,0.3)';

      document.body.appendChild(star);

      const duration = Math.random() * 2000 + 1500;
      star.animate([
        { transform: `translate(0px,0px)`, opacity: star.style.opacity },
        { transform: `translate(${endX - startX}px, ${endY - startY}px)`, opacity: 0 }
      ], { duration, easing: 'ease-out', iterations: 1 });

      setTimeout(() => star.remove(), duration);
    }

    setInterval(() => {
      if (Math.random() < 0.3) spawnShootingStar();
    }, 900);

    function shootingStarLoop(){ spawnShootingStar(); setTimeout(shootingStarLoop, Math.random()*5200+800); }
    setTimeout(shootingStarLoop, 1200);

    // initial setup
    initUserBadge();
    updateLeaderboard();

    // persist session time on unload
    window.addEventListener('beforeunload', persistSessionTimeOnUnload);
    window.addEventListener('pagehide', persistSessionTimeOnUnload);

    // expose helpers for debugging
    window._BG = { adminRenderTable, adminSave, adminExportCSV, adminImportCSV, adminLogout, loadTimeMapping, saveTimeMapping, loadCustomGames };

    // render custom games initially (only non-admin ones or admin-only if already admin)
    renderCustomGames();

    /* ---------- Game search (live) ---------- */
    (function(){
      const EXCLUDE_IDS = ['secret']; // always exclude secret
      const searchInput = document.getElementById('gameSearchInput');
      const searchClear = document.getElementById('gameSearchClear');
      const resultsEl = document.getElementById('searchResults');

      // Build an index of available games from #staticGames DOM + customGames; respects adminOnly and excludes EXCLUDE_IDS
      function buildGameIndex() {
        const list = [];
        // Static games: read DOM blocks
        document.querySelectorAll('#staticGames .game-block').forEach(block => {
          const h = block.querySelector('h2');
          const btn = block.querySelector('button.play-btn');
          let name = h ? h.textContent.trim() : '';
          // attempt to parse id from onclick attribute eg: launchGame('drivemad')
          let id = null;
          if (btn && btn.getAttribute) {
            const onclick = btn.getAttribute('onclick') || '';
            const m = onclick.match(/launchGame\(['"](.+?)['"]\)/);
            if (m) id = m[1];
          }
          // fallback: use lowercased name without spaces as id
          if (!id) id = name.toLowerCase().replace(/\s+/g,'-');
          if (EXCLUDE_IDS.includes(id)) return;
          list.push({ id, name, shopProtected: false, adminOnly: false, source: 'static' });
        });

        // Custom games (admin-managed)
        const customs = loadCustomGames();
        const isAdmin = sessionStorage.getItem('isAdmin') === 'true';
        customs.forEach(g => {
          if (!g || !g.id) return;
          if (EXCLUDE_IDS.includes(String(g.id))) return; // skip secret
          // only include adminOnly games if admin
          if (g.adminOnly && !isAdmin) return;
          list.push({
            id: String(g.id),
            name: g.name || String(g.id),
            url: g.url || '',
            shopProtected: !!g.shopProtected,
            cost: Number(g.cost || 0),
            adminOnly: !!g.adminOnly,
            source: 'custom'
          });
        });

        return list;
      }

      // Escape HTML helper
      function esc(s){ return String(s).replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c])); }

      // Render results given a query
      function renderSearchResults(query) {
        const q = (query || '').trim().toLowerCase();
        const idx = buildGameIndex();
        if (!q) {
          resultsEl.innerHTML = '<div class="search-empty">Type to search games by name or id. Results show playable games (secret hidden).</div>';
          return;
        }
        const matches = idx.filter(g => (g.name && g.name.toLowerCase().includes(q)) || (g.id && g.id.toLowerCase().includes(q)));
        if (!matches.length) {
          resultsEl.innerHTML = `<div class="search-empty">No games match "<strong>${esc(query)}</strong>".</div>`;
          return;
        }
        // create result nodes
        resultsEl.innerHTML = '';
        matches.forEach((g) => {
          const wrap = document.createElement('div');
          wrap.className = 'search-result';
          const meta = document.createElement('div');
          meta.className = 'meta';
          const title = document.createElement('div');
          title.innerHTML = `<strong>${esc(g.name)}</strong>`;
          const sub = document.createElement('div');
          sub.className = 'id';
          sub.textContent = `id: ${g.id} ${g.source === 'custom' ? '· custom' : ''}${g.shopProtected ? ` · cost: ${g.cost||'?' }🪙` : ''}${g.adminOnly ? ' · admin-only' : ''}`;
          meta.appendChild(title);
          meta.appendChild(sub);

          const actions = document.createElement('div');
          actions.className = 'actions';
          const playBtn = document.createElement('button');
          playBtn.className = 'play-btn';
          playBtn.textContent = g.shopProtected && !ownedGames[g.id] ? 'Locked' : 'Play';
          playBtn.title = g.shopProtected && !ownedGames[g.id] ? 'Buy to play' : 'Open game';
          playBtn.onclick = function(){
            // if locked and not owned, show buy flow
            if (g.shopProtected && !ownedGames[g.id]) {
              const buy = confirm(`"${g.name}" costs ${g.cost}🪙 — buy now?`);
              if (buy) buyGame(g.id, Number(g.cost || 0));
              renderSearchResults(searchInput.value);
              return;
            }
            // if custom and has url but locked to admin? launchGame handles protections
            launchGame(g.id);
          };

          actions.appendChild(playBtn);

          // if shop protected and not owned, show buy button
          if (g.shopProtected && !ownedGames[g.id]) {
            const buyBtn = document.createElement('button');
            buyBtn.className = 'buy-button';
            buyBtn.textContent = `Buy ${g.cost || '?'}🪙`;
            buyBtn.onclick = function(){ buyGame(g.id, Number(g.cost || 0)); renderSearchResults(searchInput.value); };
            actions.appendChild(buyBtn);
          }

          wrap.appendChild(meta);
          wrap.appendChild(actions);
          resultsEl.appendChild(wrap);
        });
      }

      // Input listeners
      if (searchInput) {
        searchInput.addEventListener('input', (e) => {
          renderSearchResults(e.target.value);
        });
        searchInput.addEventListener('keydown', (e) => {
          // Enter: auto-play first match if present
          if (e.key === 'Enter') {
            const q = searchInput.value.trim();
            const idx = buildGameIndex().filter(g => (g.name||'').toLowerCase().includes(q.toLowerCase()) || (g.id||'').toLowerCase().includes(q.toLowerCase()));
            if (idx.length) {
              const first = idx[0];
              if (first.shopProtected && !ownedGames[first.id]) {
                if (confirm(`${first.name} costs ${first.cost}🪙. Buy?`)) buyGame(first.id, Number(first.cost||0));
                renderSearchResults(searchInput.value);
              } else {
                launchGame(first.id);
              }
            }
          }
        });
        // Clear button
        if (searchClear) {
          searchClear.addEventListener('click', () => { searchInput.value = ''; renderSearchResults(''); searchInput.focus(); });
        }
        // initial placeholder state
        renderSearchResults('');
      }
    })();
  </script>
</body>
</html>
