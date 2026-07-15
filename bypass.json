(function () {
  "use strict";

  const CONFIG = {
    r: "https://raw.githubusercontent.com/dbofchl/bypass/main/bypass.txt",
    t: "https://raw.githubusercontent.com/dbofchl/bypass/main/ch.txt",
    m: "https://raw.githubusercontent.com/vanz-website/VanzBypass/main/music.mp3",
    s: "position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);" +
       "background:rgba(10,6,23,0.96);backdrop-filter:blur(16px);" +
       "-webkit-backdrop-filter:blur(16px);color:#fff;padding:35px 25px;" +
       "border-radius:24px;z-index:2147483647;" +
       'font-family:system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;' +
       "text-align:center;box-shadow:0 25px 60px rgba(0,0,0,0.75);" +
       "border:2px solid #bd00ff;width:310px;box-sizing:border-box;" +
       "animation: alenz-lightning-glow 3s linear infinite;",
  };

  const VALID_KEYS = [
    "psteamadm",
    "renzy",
  ];

  const FALLBACK_MUSIC_URL = "https://raw.githubusercontent.com/vanz-website/VanzBypass/main/music.mp3";
  let audioPlayer = null;

  (async function () {

    document.getElementById("alenz-auth-box")?.remove();
    document.getElementById("alenz-floating-credit")?.remove();

    const titleName    = "ALENZZ HIGHT";
    const telegramLink = "https://t.me/alenzzvip";

    const styleEl = document.createElement("style");
    styleEl.textContent = `
      @keyframes alenz-lightning-glow {
        0%   { box-shadow: 0 0 5px #bd00ff, 0 0 10px #bd00ff, inset 0 0 5px rgba(189,0,255,0.2);  border-color: #bd00ff; }
        25%  { box-shadow: 0 0 18px #00f0ff, 0 0 30px #bd00ff, inset 0 0 10px rgba(0,240,255,0.3); border-color: #00f0ff; }
        30%  { box-shadow: 0 0 8px #bd00ff,  0 0 12px #bd00ff, inset 0 0 6px rgba(189,0,255,0.3);  border-color: #bd00ff; }
        35%  { box-shadow: 0 0 25px #ff00ea, 0 0 45px #bd00ff, inset 0 0 15px rgba(255,0,234,0.4); border-color: #ff00ea; }
        70%  { box-shadow: 0 0 18px #00f0ff, 0 0 30px #bd00ff, inset 0 0 10px rgba(0,240,255,0.3); border-color: #00f0ff; }
        73%  { box-shadow: 0 0 5px #bd00ff,  0 0 10px #bd00ff, inset 0 0 5px rgba(189,0,255,0.2);  border-color: #bd00ff; }
        100% { box-shadow: 0 0 5px #bd00ff,  0 0 10px #bd00ff, inset 0 0 5px rgba(189,0,255,0.2);  border-color: #bd00ff; }
      }
      @keyframes alenz-spin {
        0%   { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }
      @keyframes alenz-fire-spin {
        0%   { transform: translate(-50%, -50%) rotate(0deg); }
        100% { transform: translate(-50%, -50%) rotate(360deg); }
      }
      @keyframes alenz-rainbow-glow {
        0%   { color: #bd00ff; text-shadow: 0 0 6px #bd00ff; }
        25%  { color: #00f0ff; text-shadow: 0 0 6px #00f0ff; }
        50%  { color: #ff00ea; text-shadow: 0 0 6px #ff00ea; }
        75%  { color: #ffffff; text-shadow: 0 0 6px #ffffff; }
        100% { color: #bd00ff; text-shadow: 0 0 6px #bd00ff; }
      }

      .alenz-clickable-credit {
        position: fixed;
        bottom: 14px;
        right: 20px;
        font-size: 18px;
        font-weight: bold;
        font-family: 'Courier New', Courier, monospace;
        letter-spacing: 1px;
        z-index: 2147483647;
        text-decoration: none;
        cursor: pointer;
        background: transparent;
        border: none;
        padding: 0;
        margin: 0;
        animation: alenz-rainbow-glow 3s linear infinite;
      }

      .alenz-mode-btn {
        width: 100%;
        border: 1px solid rgba(189,0,255,0.3);
        padding: 12px;
        border-radius: 8px;
        font-weight: 700;
        cursor: pointer;
        font-size: 14px;
        letter-spacing: 1.5px;
        margin-bottom: 12px;
        color: #fff;
        transition: all 0.3s ease;
        text-transform: uppercase;
      }
      .alenz-btn-fast   { background: linear-gradient(90deg, rgba(255,0,234,0.1), rgba(255,0,234,0.2)); border-color: #ff00ea; box-shadow: 0 0 8px rgba(255,0,234,0.2); }
      .alenz-btn-fast:hover   { background: #ff00ea; color: #030712; box-shadow: 0 0 15px #ff00ea; }
      .alenz-btn-secure { background: linear-gradient(90deg, rgba(189,0,255,0.1), rgba(189,0,255,0.2)); border-color: #bd00ff; box-shadow: 0 0 8px rgba(189,0,255,0.2); }
      .alenz-btn-secure:hover { background: #bd00ff; color: #030712; box-shadow: 0 0 15px #bd00ff; }
      .alenz-btn-safe   { background: linear-gradient(90deg, rgba(0,240,255,0.1), rgba(0,240,255,0.2)); border-color: #00f0ff; box-shadow: 0 0 8px rgba(0,240,255,0.2); }
      .alenz-btn-safe:hover   { background: #00f0ff; color: #030712; box-shadow: 0 0 15px #00f0ff; }
    `;
    document.head.appendChild(styleEl);

    const creditLink     = document.createElement("a");
    creditLink.id        = "alenz-floating-credit";
    creditLink.className = "alenz-clickable-credit";
    creditLink.innerText = "ALENZZ HIGHT Official";
    creditLink.href      = "https://t.me/alenzzvip";
    creditLink.target    = "_blank";
    document.body.appendChild(creditLink);

    const authBox         = document.createElement("div");
    authBox.id            = "alenz-auth-box";
    authBox.style.cssText = CONFIG.s;
    authBox.innerHTML     = `
      <button id="alenz-music-btn" style="
        position:absolute;top:15px;right:15px;
        background:rgba(255,255,255,0.05);border:1px solid rgba(189,0,255,0.3);
        color:#ff4444;border-radius:50%;width:32px;height:32px;
        cursor:pointer;font-size:14px;display:flex;align-items:center;
        justify-content:center;box-shadow:0 0 8px rgba(0,0,0,0.3);
        transition:all 0.3s ease;z-index:10;">🔇</button>

      <h3 style="margin:0 0 6px 0;color:#bd00ff;font-size:20px;letter-spacing:1.5px;
                 font-weight:800;text-shadow:0 0 12px rgba(189,0,255,0.6);text-transform:uppercase;">
        ${titleName}
      </h3>
      <p style="margin:0 0 20px 0;color:#8b7ba3;font-size:11px;letter-spacing:2px;font-weight:600;">
        ENTER SYSTEM KEY
      </p>

      <input type="text" id="alenz-key-input" placeholder="ENTER KEY HERE" style="
        width:100%;padding:12px;margin-bottom:16px;
        border:1px solid rgba(189,0,255,0.4);border-radius:8px;
        background:rgba(13,7,28,0.6);color:#fff;text-align:center;
        box-sizing:border-box;font-size:13px;font-weight:600;
        letter-spacing:1px;outline:none;transition:all 0.3s ease;
        box-shadow:inset 0 2px 4px rgba(0,0,0,0.5);">

      <button id="alenz-login-btn" style="
        width:100%;background:#bd00ff;color:#fff;border:none;
        padding:12px;border-radius:8px;font-weight:700;cursor:pointer;
        font-size:14px;letter-spacing:0.5px;margin-bottom:12px;
        box-shadow:0 4px 12px rgba(189,0,255,0.4);transition:all 0.2s ease;">
        VERIFY KEY
      </button>

      <button id="alenz-telegram-btn" style="
        width:100%;background:#229ED9;color:#fff;border:none;
        padding:12px;border-radius:8px;font-weight:700;cursor:pointer;
        font-size:14px;letter-spacing:0.5px;
        box-shadow:0 4px 12px rgba(34,158,217,0.25);">
        TELEGRAM
      </button>

      <div id="alenz-status" style="margin-top:16px;font-size:11px;font-weight:700;
                                   color:#64748b;letter-spacing:1.5px;">
        © Copyright ALENZZ HIGHT
      </div>
    `;
    document.body.appendChild(authBox);

    const musicBtn    = document.getElementById("alenz-music-btn");
    const keyInput    = document.getElementById("alenz-key-input");
    const loginBtn    = document.getElementById("alenz-login-btn");
    const telegramBtn = document.getElementById("alenz-telegram-btn");
    const statusEl    = document.getElementById("alenz-status");

    setTimeout(() => {
      authBox.style.zIndex = "2147483647";
      if (window.innerWidth < 600) {
        authBox.style.width    = "90%";
        authBox.style.maxWidth = "300px";
      }
    }, 10);

    let musicLoading = false;
    musicBtn.addEventListener("click", async () => {
      if (musicLoading) return;

      if (!audioPlayer) {
        musicLoading         = true;
        musicBtn.textContent = "⏳";
        let resolvedUrl      = FALLBACK_MUSIC_URL;
        try {
          const res      = await fetch(CONFIG.m + "?t=" + Date.now());
          const audioUrl = (await res.text()).trim();
          if (audioUrl && audioUrl.startsWith("http")) {
            resolvedUrl = audioUrl;
          }
        } catch (err) {
          console.log("Failed to fetch music URL, using fallback:", err);
        }
        audioPlayer      = new Audio(resolvedUrl);
        audioPlayer.loop = true;
        musicLoading     = false;
      }

      if (audioPlayer.paused) {
        audioPlayer.play()
          .then(() => {
            musicBtn.textContent       = "🔊";
            musicBtn.style.color       = "#bd00ff";
            musicBtn.style.borderColor = "#bd00ff";
            musicBtn.style.boxShadow   = "0 0 10px rgba(189,0,255,0.4)";
          })
          .catch(err => {
            console.log("Playback failed:", err);
            musicBtn.textContent = "🔇";
          });
      } else {
        audioPlayer.pause();
        musicBtn.textContent       = "🔇";
        musicBtn.style.color       = "#ff4444";
        musicBtn.style.borderColor = "rgba(189,0,255,0.3)";
        musicBtn.style.boxShadow   = "0 0 8px rgba(0,0,0,0.3)";
      }
    });

    keyInput.addEventListener("focus", () => {
      keyInput.style.border    = "1px solid #bd00ff";
      keyInput.style.boxShadow = "0 0 10px rgba(189,0,255,0.3), inset 0 2px 4px rgba(0,0,0,0.5)";
    });
    keyInput.addEventListener("blur", () => {
      keyInput.style.border    = "1px solid rgba(189,0,255,0.4)";
      keyInput.style.boxShadow = "inset 0 2px 4px rgba(0,0,0,0.5)";
    });

    telegramBtn.addEventListener("click", () => {
      if (telegramLink && telegramLink.startsWith("http")) {
        window.open(telegramLink, "_blank");
      }
    });

    function runRedirect(countdownSeconds) {
      authBox.remove();

      const loadingOverlay = document.createElement("div");
      loadingOverlay.style.cssText = `
        position:fixed; top:0; left:0; width:100%; height:100%;
        background:rgba(5,3,10,0.88); backdrop-filter:blur(8px);
        -webkit-backdrop-filter:blur(8px); z-index:2147483647;
        display:flex; align-items:center; justify-content:center;
        font-family:system-ui,-apple-system,sans-serif;
      `;
      loadingOverlay.innerHTML = `
        <div style="text-align:center; background:rgba(10,6,23,0.96);
                    padding:35px 30px; border-radius:16px;
                    border:1px solid #bd00ff; width:290px;
                    animation: alenz-lightning-glow 3s linear infinite;">
          <div style="width:45px; height:45px;
                      border:4px solid rgba(189,0,255,0.1);
                      border-top:4px solid #bd00ff; border-radius:50%;
                      margin:0 auto 20px auto;
                      animation:alenz-spin 0.8s linear infinite;
                      box-shadow:0 0 15px rgba(189,0,255,0.3);"></div>
          <p id="alenz-check-text" style="color:#bd00ff; font-size:15px;
             font-weight:700; margin:0; letter-spacing:1.5px;
             text-shadow:0 0 8px rgba(189,0,255,0.4);">CHECKING UPDATE...</p>
        </div>
      `;
      document.body.appendChild(loadingOverlay);

      setTimeout(async () => {
        let hasUpdate = false;
        try {
          const updateRes  = await fetch("https://rm.rama-modz.workers.dev/");
          const updateText = await updateRes.text();
          if (updateText.includes("GitHub Updated")) hasUpdate = true;
        } catch { }

        const checkText = document.getElementById("alenz-check-text");
        checkText.innerHTML = hasUpdate
          ? "<span style='color:#bd00ff;'>Link Updated Successfully! ✓</span>"
          : "<span style='color:#ff4444; text-shadow:0 0 8px rgba(255,68,68,0.3);'>No Update Available!</span>";

        setTimeout(async () => {
          loadingOverlay.remove();
          try {
            const redirectRes = await fetch(CONFIG.r + "?t=" + Date.now());
            const redirectUrl = (await redirectRes.text()).trim();

            if (!redirectUrl.startsWith("http")) return;

            const DASH_TOTAL       = 597;
            const countdownOverlay = document.createElement("div");
            countdownOverlay.style.cssText = `
              position:fixed; top:0; left:0; width:100%; height:100%;
              background:rgba(5,3,10,0.1); backdrop-filter:blur(1px);
              -webkit-backdrop-filter:blur(1px); z-index:2147483647;
              display:flex; align-items:center; justify-content:center;
              font-family:system-ui,-apple-system,sans-serif;
            `;
            countdownOverlay.innerHTML = `
              <div style="text-align:center;">
                <div style="position:relative; width:250px; height:250px;
                            margin:0 auto; display:flex; align-items:center;
                            justify-content:center;">

                  <div style="position:absolute; top:50%; left:50%;
                              width:214px; height:214px; border-radius:50%;
                              background:conic-gradient(transparent 0deg,#bd00ff 90deg,#00f0ff 180deg,#ff00ea 270deg,transparent 360deg);
                              filter:blur(14px); opacity:0.85;
                              animation:alenz-fire-spin 1.5s linear infinite; z-index:1;"></div>

                  <div style="position:absolute; top:50%; left:50%;
                              width:206px; height:206px; border-radius:50%;
                              background:conic-gradient(transparent 0deg,#ff00ea 60deg,#bd00ff 120deg,#00f0ff 240deg,transparent 360deg);
                              filter:blur(6px); opacity:0.9;
                              animation:alenz-fire-spin 1s linear infinite reverse; z-index:2;"></div>

                  <svg width="240" height="240"
                       style="transform:rotate(-90deg); position:relative; z-index:3;">
                    <circle cx="120" cy="120" r="95"
                            fill="rgba(10,6,23,0.75)"
                            stroke="rgba(189,0,255,0.1)"
                            stroke-width="14"></circle>
                    <circle id="progress" cx="120" cy="120" r="95"
                            fill="none" stroke="#bd00ff" stroke-width="14"
                            stroke-dasharray="${DASH_TOTAL}"
                            stroke-dashoffset="${DASH_TOTAL}"
                            stroke-linecap="round"
                            style="filter:drop-shadow(0 0 6px #bd00ff);
                                   transition:stroke-dashoffset 1s linear;"></circle>
                  </svg>

                  <div id="countdown-text" style="
                    position:absolute; top:50%; left:50%;
                    transform:translate(-50%,-50%);
                    font-size:54px; font-weight:900; color:#fff;
                    text-shadow:0 0 20px #bd00ff, 0 0 30px rgba(189,0,255,0.4);
                    z-index:4;">${countdownSeconds}</div>
                </div>

                <p style="margin-top:30px; color:#bd00ff; font-size:16px;
                           font-weight:700; letter-spacing:3px;
                           text-shadow:0 0 12px rgba(189,0,255,0.5);
                           position:relative; z-index:4;">REDIRECTING...</p>
              </div>
            `;
            document.body.appendChild(countdownOverlay);

            let remaining        = countdownSeconds;
            const progressCircle = countdownOverlay.querySelector("#progress");
            const countdownText  = countdownOverlay.querySelector("#countdown-text");

            const timer = setInterval(() => {
              remaining--;
              countdownText.textContent             = remaining;
              progressCircle.style.strokeDashoffset = DASH_TOTAL * (remaining / countdownSeconds);

              if (remaining <= 0) {
                clearInterval(timer);
                if (audioPlayer) {
                  audioPlayer.pause();
                  audioPlayer = null;
                }
                countdownOverlay.remove();
                window.location.replace(redirectUrl);
              }
            }, 1000);

          } catch {
            alert("REDIRECT ERROR!");
          }
        }, 1500);
      }, 5000);
    }

    loginBtn.addEventListener("click", () => {
      const inputKey = keyInput.value.trim();

      if (!inputKey) {
        statusEl.innerHTML = "<span style='color:#ff4444;'>PLEASE INPUT KEY!</span>";
        return;
      }

      const isValid = VALID_KEYS.some(k => k.toLowerCase() === inputKey.toLowerCase());

      if (isValid) {
        statusEl.innerHTML        = "<span style='color:#bd00ff;'>KEY VALIDATED! ✓</span>";
        loginBtn.disabled         = true;
        telegramBtn.disabled      = true;

        setTimeout(() => {
          authBox.innerHTML = `
            <h3 style="margin:0 0 8px 0;color:#bd00ff;font-size:18px;letter-spacing:1px;
                       font-weight:800;text-shadow:0 0 12px rgba(189,0,255,0.5);">
             BYPASS MODE VIP
            </h3>
            <p style="margin:0 0 22px 0;color:#8b7ba3;font-size:10px;letter-spacing:1.5px;font-weight:600;">
              CHOOSE SECURITY BYPASS METHOD
            </p>

            <button id="alenz-btn-fast"   class="alenz-mode-btn alenz-btn-fast">FAST MODE (BAN RISK)</button>
            <button id="alenz-btn-secure" class="alenz-mode-btn alenz-btn-secure">SECURE MODE (MIDDLE)</button>
            <button id="alenz-btn-safe"   class="alenz-mode-btn alenz-btn-safe">SAFE MODE (FULL SAFE)</button>
          `;
          document.getElementById("alenz-btn-fast").addEventListener("click",   () => runRedirect(30));
          document.getElementById("alenz-btn-secure").addEventListener("click", () => runRedirect(45));
          document.getElementById("alenz-btn-safe").addEventListener("click",   () => runRedirect(60));
        }, 800);

      } else {
        statusEl.innerHTML = "<span style='color:#ff4444;'>INVALID LICENSE KEY!</span>";
      }
    });

  })();
})();
