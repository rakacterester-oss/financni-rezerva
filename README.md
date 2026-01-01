<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <title>Finanční Rezerva – Premium</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head> 
<!-- MODAL – zobrazuje chybu, když nejsou zadány hodnoty -->
<div id="errorModal" class="modal" style="display:none;">
    <div class="modal-content">
        <p>⚠️ Nelze vypočítat rezervu – nejsou zadány hodnoty příjmů nebo výdajů.</p>
        <button id="closeModal">OK</button>
    </div>
</div>


<body>

<div class="container">

    <h1>💰 Finanční Rezerva – Kalkulačka</h1>

    <!-- 💡 PROČ MÍT FINANČNÍ REZERVU -->
    <h2>💡 Proč mít finanční rezervu</h2>
    <div class="section">
        <p>
            Finanční rezerva je tichý hrdina osobních financí. Nevidíme ji,
            nechlubíme se s ní, ale ve chvíli, kdy se něco pokazí, je to právě ona,
            kdo nás podrží. Nečekané výdaje, výpadek příjmu, porouchané auto,
            vyšší účty nebo zdravotní komplikace — to všechno přichází bez varování.
        </p>
        <p>
            Rezerva nám dává <strong>klid, jistotu a svobodu</strong>.
            Díky ní nemusíme sahat po půjčkách, nemusíme panikařit
            a můžeme dělat rozhodnutí s chladnou hlavou.
            Je to vlastně takový osobní airbag: doufáme, že ho nikdy nebudeme potřebovat,
            ale když přijde náraz, jsme rádi, že tam je.
        </p>
        <p>
            Ať už jsi student, zaměstnanec, důchodce nebo člověk s invaliditou,
            rezerva je základní kámen finanční stability.
            Každý ji potřebuje — jen její velikost se liší podle životní situace.
        </p>
    </div>

    <!-- STATUS -->
    <h2>🧍‍♂️ Status osoby</h2>
    <div class="section">
        <div class="row">
            <div class="field">
                <label for="status">Vyber svůj status</label>
                <select id="status">
                    <option value="student">Student</option>
                    <option value="zamestnanec" selected>Zaměstnanec</option>
                    <option value="duchodce">Důchodce</option>
                    <option value="invalida">Invalida</option>
                </select>
            </div>
        </div>
        <div id="statusInfo" class="result" style="display:none;"></div>
    </div>

    <!-- PŘÍJMY -->
    <h2>📥 Měsíční příjmy</h2>
    <div class="section">

        <div class="row">
            <div class="field">
                <label for="typPrijmu1">Druh příjmu</label>
                <select id="typPrijmu1">
                    <option value="zamestnani" selected>Zaměstnání</option>
                    <option value="invalidni">Invalidní důchod</option>
                    <option value="sirotci">Sirotčí důchod</option>
                    <option value="vdovsky">Vdovský důchod</option>
                    <option value="starobni">Starobní důchod</option>
                    <option value="brigada">Brigáda</option>
                </select>
            </div>
            <div class="field">
                <label for="prijem1">Výše příjmu (Kč)</label>
                <input id="prijem1" type="number" value="0">
            </div>
        </div>

        <div class="row">
            <div class="field">
                <label for="typPrijmu2">Druh příjmu</label>
                <select id="typPrijmu2">
                    <option value="zadny" selected>— žádný —</option>
                    <option value="zamestnani">Zaměstnání</option>
                    <option value="invalidni">Invalidní důchod</option>
                    <option value="sirotci">Sirotčí důchod</option>
                    <option value="vdovsky">Vdovský důchod</option>
                    <option value="starobni">Starobní důchod</option>
                    <option value="brigada">Brigáda</option>
                </select>
            </div>
            <div class="field">
                <label for="prijem2">Výše příjmu (Kč)</label>
                <input id="prijem2" type="number" value="0">
            </div>
        </div>

        <div class="row">
            <div class="field">
                <label for="typPrijmu3">Druh příjmu</label>
                <select id="typPrijmu3">
                    <option value="zadny" selected>— žádný —</option>
                    <option value="zamestnani">Zaměstnání</option>
                    <option value="invalidni">Invalidní důchod</option>
                    <option value="sirotci">Sirotčí důchod</option>
                    <option value="vdovsky">Vdovský důchod</option>
                    <option value="starobni">Starobní důchod</option>
                    <option value="brigada">Brigáda</option>
                </select>
            </div>
            <div class="field">
                <label for="prijem3">Výše příjmu (Kč)</label>
                <input id="prijem3" type="number" value="0">
            </div>
        </div>
    </div>

    <!-- VÝDAJE -->
    <h2>📤 Měsíční výdaje</h2>
    <div class="section">
        <div class="row">
            <div class="field"><label>Nájem / hypotéka</label><input id="v1" type="number" value="0">
</div>
            <div class="field"><label>Energie</label><input id="v2" type="number" value="0">
</div>
            <div class="field"><label>Jídlo</label><input id="v3" type="number" value="0">
</div>
        </div>

        <div class="row">
            <div class="field"><label>Doprava</label><input id="v4" type="number" value="0">
</div>
            <div class="field"><label>Telefon / internet</label><input id="v5" type="number" value="0">
</div>
            <div class="field"><label>Zdraví</label><input id="v6" type="number" value="0">
</div>
        </div>

        <div class="row">
            <div class="field"><label>Ostatní výdaje</label><input id="v7" type="number" value="0">
</div>
            <div class="field"><label>Současná rezerva</label><input id="rezerva" type="number" value="0"></div>
        </div>

        <button id="btnSpocitej">Spočítat příjmy, výdaje a rezervu</button> 
	<div id="chybaRezerva" class="result" style="display:none;"></div>

        <div id="vysledekPrijmy" class="result" style="display:none;"></div>
        <div id="vysledekVydaje" class="result" style="display:none;"></div>
    </div>

    <!-- 🔥 NOVÁ SEKCE: STAV REZERVY -->
    <h2>📊 Stav rezervy</h2>
    <div class="section">

        <div class="progress-wrapper" id="progressWrapper" style="display:none;">
    <div id="progressBar"></div>
</div>
<p id="progressText" class="highlight" style="display:none;"></p>


        <div class="row">
            <div class="field">
                <label>Přidat částku</label>
                <input id="pridatCastku" type="number" value="0">
                <button id="btnPridat">Přidat</button>
            </div>

            <div class="field">
                <label>Odečíst částku</label>
                <input id="odebratCastku" type="number" value="0">
                <button id="btnOdebrat">Odebrat</button>
            </div>

            <div class="field">
                <label>Reset rezervy</label>
                <button id="btnReset">Resetovat na původní hodnotu</button>
            </div>
        </div>
    </div>

    <!-- PLÁNOVAČ -->
    <h2>📈 Plánovač tvorby rezervy</h2>
    <div class="section">
        <div class="row">
            <div class="field"><label>Cílová částka</label><input id="cil" type="number" value="0"></div>
            <div class="field"><label>Měsíční vklad</label><input id="vklad" type="number" value="0"></div>
            <div class="field"><label>Roční úrok (%)</label><input id="urok" type="number" value="1"></div>
        </div>

        <div class="row">
            <div class="field"><label>Jednorázový vklad (na začátku)</label><input id="jednorazovy" type="number" value="0"></div>
        </div>

        <button id="btnPlan">Vypočítat plán a zobrazit graf</button>

        <div id="vysledekPlan" class="result" style="display:none;"></div>

        <canvas id="grafRezerva" height="120"></canvas>

        <div id="historie" class="result" style="display:none;">
            <p class="highlight">Historie výpočtů</p>
            <div id="historieObsah"></div>
        </div>
    </div>

</div> 
<style>
    body {
        font-family: 'Poppins', sans-serif;
        margin: 0;
        background: linear-gradient(135deg, #dfe9f3 0%, #ffffff 100%);
        color: #333;
    }
.modal {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.4);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
}

.modal-content {
    background: #ff3b30; /* červené */
    color: white;
    padding: 30px;
    border-radius: 15px;
    text-align: center;
    max-width: 400px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.modal-content button {
    margin-top: 20px;
    background: white;
    color: #ff3b30;
    font-weight: 600;
    border: none;
    border-radius: 12px;
    padding: 10px 20px;
    cursor: pointer;
}

.modal-content button:hover {
    background: #ffe5e0;
}


    .container {
        max-width: 1200px;
        margin: 40px auto;
        padding: 30px;
        background: rgba(255,255,255,0.8);
        backdrop-filter: blur(10px);
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }

    h1 {
        text-align: center;
        font-size: 2.4rem;
        margin-bottom: 10px;
        font-weight: 600;
    }

    h2 {
        margin-top: 40px;
        font-weight: 600;
        border-left: 6px solid #4a90e2;
        padding-left: 10px;
    }

    .section {
        margin-top: 20px;
        padding: 20px;
        border-radius: 15px;
        background: #ffffff;
        box-shadow: 0 4px 15px rgba(0,0,0,0.05);
    }

    .row {
        display: flex;
        flex-wrap: wrap;
        gap: 30px;
        margin-bottom: 25px;
    }

    .field {
        flex: 1 1 250px;
        margin-bottom: 15px;
    }

    label {
        font-weight: 600;
        margin-bottom: 5px;
        display: block;
    }

    input, select {
        width: 100%;
        padding: 12px;
        border-radius: 12px;
        border: 1px solid #ccc;
        font-size: 1rem;
        background: #fff;
    }

    button {
        margin-top: 10px;
        padding: 14px 22px;
        background: #4a90e2;
        color: white;
        border: none;
        border-radius: 12px;
        font-size: 1rem;
        cursor: pointer;
        transition: 0.2s;
        font-weight: 600;
    }

    button:hover {
        background: #357ac9;
    }

    .result {
        margin-top: 20px;
        padding: 15px;
        background: #eef6ff;
        border-left: 5px solid #4a90e2;
        border-radius: 10px;
    }

    .highlight {
        font-weight: 600;
        color: #4a90e2;
    }

    /* 🔥 PROGRESS BAR – STAV REZERVY */
    .progress-wrapper {
        width: 100%;
        height: 20px; /* Václav vybral variantu B */
        background: #ddd;
        border-radius: 12px;
        overflow: hidden;
        margin-bottom: 15px;
    }

    #progressBar {
        height: 100%;
        width: 0%;
        border-radius: 12px;
        transition: width 0.4s ease, background 0.4s ease;
    }

    /* Historie */
    .history-item {
        font-size: 0.9rem;
        margin-bottom: 6px;
    }

    canvas {
        margin-top: 20px;
    }

    /* Tlačítka v historii */
    .btnHistEdit, .btnHistDelete {
        padding: 4px 10px;
        margin-left: 10px;
        border-radius: 6px;
        border: none;
        cursor: pointer;
        font-size: 0.8rem;
    }

    .btnHistEdit {
        background: #ffcc00;
        color: #333;
    }

    .btnHistDelete {
        background: #ff3b30;
        color: white;
    }

    .btnHistEdit:hover {
        background: #e6b800;
    }

    .btnHistDelete:hover {
        background: #d92a20;
    }
</style> 
<script>
window.onload = function () {

    function num(id) {
        const el = document.getElementById(id);
        if (!el) return 0;
        const v = parseFloat(el.value.toString().replace(',', '.'));
        return isNaN(v) ? 0 : v;
    }

    const LS_REZERVA_KEY = 'rezervaAktualni';
    const LS_REZERVA_BASE_KEY = 'rezervaPuvodni';
    const LS_HISTORIE_KEY = 'rezervaHistorie';

    function getStoredReserve() {
        const s = localStorage.getItem(LS_REZERVA_KEY);
        if (!s) return null;
        const v = parseFloat(s);
        return isNaN(v) ? null : v;
    }

    function setStoredReserve(value) {
        localStorage.setItem(LS_REZERVA_KEY, String(value));
    }

    function getStoredBaseReserve() {
        const s = localStorage.getItem(LS_REZERVA_BASE_KEY);
        if (!s) return null;
        const v = parseFloat(s);
        return isNaN(v) ? null : v;
    }

    function setStoredBaseReserve(value) {
        localStorage.setItem(LS_REZERVA_BASE_KEY, String(value));
    }

    function vyhodnotStatus() {
        let s = document.getElementById('status').value;
        let div = document.getElementById('statusInfo');

        let text = "";

        if (s === "student") text = "Jako student máš obvykle nižší příjmy. Doporučená rezerva: 2–3 měsíce.";
        if (s === "zamestnanec") text = "Jako zaměstnanec je ideální rezerva 3–6 měsíců.";
        if (s === "duchodce") text = "Jako důchodce je vhodná vyšší rezerva: 6–12 měsíců.";
        if (s === "invalida") text = "Jako osoba s invaliditou je doporučená rezerva 6–12 měsíců.";

        div.style.display = "block";
        div.innerHTML = `<p><span class="highlight">Doporučení:</span> ${text}</p>`;
    }

    document.getElementById('status').addEventListener('change', vyhodnotStatus);
    vyhodnotStatus();

    function spocitej() {
    const prijmy = num('prijem1') + num('prijem2') + num('prijem3');
    const vydaje = num('v1') + num('v2') + num('v3') + num('v4') + num('v5') + num('v6') + num('v7');

    const modal = document.getElementById('errorModal');
    const btnClose = document.getElementById('closeModal');

    // 🔥 Kontrola: jsou zadány hodnoty příjmů a výdajů?
    if (prijmy <= 0 || vydaje <= 0) {
        modal.style.display = 'flex';

        btnClose.onclick = function() {
            modal.style.display = 'none';
        };

        return; // zastaví další výpočty
    }

    // Výpočty, pokud jsou hodnoty OK
    const rozdil = prijmy - vydaje;

    const divPrijmy = document.getElementById('vysledekPrijmy');
    const divVydaje = document.getElementById('vysledekVydaje');

    divPrijmy.style.display = 'block';
    divPrijmy.innerHTML = `<p><span class="highlight">Celkové příjmy:</span> ${prijmy.toLocaleString('cs-CZ')} Kč</p>`;

    divVydaje.style.display = 'block';
    divVydaje.innerHTML = `<p><span class="highlight">Celkové výdaje:</span> ${vydaje.toLocaleString('cs-CZ')} Kč</p>
                            <p><span class="highlight">Měsíční rozdíl:</span> ${rozdil.toLocaleString('cs-CZ')} Kč</p>`;

    // Doporučená rezerva podle statusu
    let status = document.getElementById('status').value;
    let minMesice = 3;
    let maxMesice = 6;
    if (status === "student") { minMesice = 2; maxMesice = 3; }
    if (status === "zamestnanec") { minMesice = 3; maxMesice = 6; }
    if (status === "duchodce") { minMesice = 6; maxMesice = 12; }
    if (status === "invalida") { minMesice = 6; maxMesice = 12; }

    const doporucenaRezervaMin = vydaje * minMesice;
    const doporucenaRezervaMax = vydaje * maxMesice;

    divVydaje.innerHTML +=
        `<p><span class="highlight">Doporučená rezerva:</span> ${doporucenaRezervaMin.toLocaleString('cs-CZ')} – ${doporucenaRezervaMax.toLocaleString('cs-CZ')} Kč</p>`;

    // Automaticky nastavíme cílovou částku a měsíční vklad
    document.getElementById('cil').value = Math.round(doporucenaRezervaMin);
    if (rozdil > 0) {
        document.getElementById('vklad').value = Math.round(rozdil * 0.7);
    }

    // Nastavení základní a aktuální rezervy
    const aktualniRezervaInput = num('rezerva');
    setStoredBaseReserve(aktualniRezervaInput);
    setStoredReserve(aktualniRezervaInput);

    // Zobrazíme progress bar
    document.getElementById('progressWrapper').style.display = 'block';
    document.getElementById('progressText').style.display = 'block';
    updateProgressBar();
}
// 🔥 ZOBRAZ ELEMENTY až po výpočtu
document.getElementById('progressWrapper').style.display = 'block';
document.getElementById('progressText').style.display = 'block';


    document.getElementById('btnSpocitej').addEventListener('click', spocitej);

    const progressBar = document.getElementById('progressBar');
    const progressText = document.getElementById('progressText');

    function getCurrentReserve() {
        const stored = getStoredReserve();
        if (stored !== null) return stored;
        return num('rezerva');
    }

    function setCurrentReserve(value) {
        setStoredReserve(value);
        const rezInput = document.getElementById('rezerva');
        if (rezInput) rezInput.value = Math.round(value);
    }

    function getBaseReserve() {
        const storedBase = getStoredBaseReserve();
        if (storedBase !== null) return storedBase;
        const v = num('rezerva');
        setStoredBaseReserve(v);
        return v;
    }

    function resetReserveToBase() {
        const base = getBaseReserve();
        setCurrentReserve(base);
        updateProgressBar();
    }

    function getPercent(cil, rezerva) {
        if (cil <= 0) return 0;
        return (rezerva / cil) * 100;
    }

    function getGradientColorForPercent(pct) {
        if (pct >= 100) {
            return '#007aff';
        } else if (pct >= 75) {
            return '#34c759';
        } else if (pct >= 50) {
            return '#ffcc00';
        } else if (pct >= 25) {
            return '#ff9500';
        } else {
            return '#ff3b30';
        }
    }

    function updateProgressBar() {
        const cil = num('cil');
        const rezervaAktualni = getCurrentReserve();

        const pct = Math.max(0, getPercent(cil, rezervaAktualni));
        const pctClamped = Math.min(pct, 150);

        progressBar.style.width = pctClamped + '%';

        const color = getGradientColorForPercent(pct);
        progressBar.style.background = `linear-gradient(90deg, rgba(0,0,0,0.2), ${color})`;

        progressText.textContent =
            `Aktuální rezerva: ${Math.round(rezervaAktualni).toLocaleString('cs-CZ')} Kč ` +
            `(${pct.toFixed(1)} % cílové částky ${cil.toLocaleString('cs-CZ')} Kč)`;
    }

    document.getElementById('btnPridat').addEventListener('click', function () {
        const castka = num('pridatCastku');
        if (castka <= 0) return;
        const aktualni = getCurrentReserve();
        const nova = aktualni + castka;
        setCurrentReserve(nova);
        document.getElementById('pridatCastku').value = 0;
        updateProgressBar();
    });

    document.getElementById('btnOdebrat').addEventListener('click', function () {
        const castka = num('odebratCastku');
        if (castka <= 0) return;
        const aktualni = getCurrentReserve();
        const nova = Math.max(0, aktualni - castka);
        setCurrentReserve(nova);
        document.getElementById('odebratCastku').value = 0;
        updateProgressBar();
    });

    document.getElementById('btnReset').addEventListener('click', function () {
        resetReserveToBase();
    });

    function nactiHistorii() {
        let data = localStorage.getItem(LS_HISTORIE_KEY);
        if (!data) return [];
        try {
            return JSON.parse(data);
        } catch (e) {
            return [];
        }
    }

    function ulozHistorii(polozka) {
        let historie = nactiHistorii();
        historie.push(polozka);
        localStorage.setItem(LS_HISTORIE_KEY, JSON.stringify(historie));
        zobrazHistorii();
    }

    function smazHistoriiZaznam(index) {
        let historie = nactiHistorii();
        if (index < 0 || index >= historie.length) return;
        historie.splice(index, 1);
        localStorage.setItem(LS_HISTORIE_KEY, JSON.stringify(historie));
        zobrazHistorii();
    }

    function upravHistoriiZaznam(index) {
        let historie = nactiHistorii();
        if (index < 0 || index >= historie.length) return;
        let z = historie[index];

        let novaRezerva = prompt("Nová hodnota rezervy (Kč):", z.rezerva);
        if (novaRezerva !== null && novaRezerva.trim() !== "") {
            let r = parseFloat(novaRezerva.replace(',', '.'));
            if (!isNaN(r)) z.rezerva = r;
        }

        let novyCil = prompt("Nová cílová částka (Kč):", z.cil);
        if (novyCil !== null && novyCil.trim() !== "") {
            let c = parseFloat(novyCil.replace(',', '.'));
            if (!isNaN(c)) z.cil = c;
        }

        localStorage.setItem(LS_HISTORIE_KEY, JSON.stringify(historie));
        zobrazHistorii();
    }

    function zobrazHistorii() {
        let historie = nactiHistorii();
        const box = document.getElementById('historie');
        const obsah = document.getElementById('historieObsah');

        if (!historie.length) {
            box.style.display = 'none';
            return;
        }

        box.style.display = 'block';
        obsah.innerHTML = '';

        let posledni = historie.slice(-5).reverse();

        posledni.forEach((item, idx) => {
            const realIndex = historie.length - 1 - idx;

            const div = document.createElement('div');
            div.className = 'history-item';
            div.innerHTML =
                `<strong>${item.datum}</strong> – cíl ${item.cil.toLocaleString('cs-CZ')} Kč, ` +
                `rezerva nyní ${item.rezerva.toLocaleString('cs-CZ')} Kč ` +
                `(${item.procentoNyni.toFixed(1)} %), ` +
                (item.dosazeno
                    ? `cíl dosažen za ${item.mesice} měsíců`
                    : `cíl nedosažen, stav po ${item.mesice} měsících ${item.konecnyStav.toLocaleString('cs-CZ')} Kč`) +
                ` &nbsp; 
                 <button class="btnHistEdit" data-index="${realIndex}">Upravit</button>
                 <button class="btnHistDelete" data-index="${realIndex}">Smazat</button>`;

            obsah.appendChild(div);
        });

        obsah.querySelectorAll('.btnHistDelete').forEach(btn => {
            btn.addEventListener('click', function () {
                const index = parseInt(this.getAttribute('data-index'), 10);
                smazHistoriiZaznam(index);
            });
        });

        obsah.querySelectorAll('.btnHistEdit').forEach(btn => {
            btn.addEventListener('click', function () {
                const index = parseInt(this.getAttribute('data-index'), 10);
                upravHistoriiZaznam(index);
            });
        });
    }

    let grafRezerva = null;

    function plan() {
        let cil = num('cil');
        let vklad = num('vklad');
        let urokRocni = num('urok');
        let urok = urokRocni / 100 / 12;
        let jednorazovy = num('jednorazovy');

        let rezervaStart = getCurrentReserve();
        let zustatek = rezervaStart + jednorazovy;

        let mesice = [];
        let hodnoty = [];
        let mesic = 0;
        let cilMesic = null;

        while (mesic < 600 && zustatek < cil) {
            mesic++;
            zustatek += vklad;
            zustatek += zustatek * urok;
            mesice.push(mesic);
            hodnoty.push(zustatek);
            if (!cilMesic && zustatek >= cil) {
                cilMesic = mesic;
            }
        }

        if (!mesice.length) {
            mesice.push(0);
            hodnoty.push(zustatek);
        }

        if (cilMesic) {
            let index = mesice.indexOf(cilMesic);
            if (index >= 0) {
                mesice = mesice.slice(0, index + 1);
                hodnoty = hodnoty.slice(0, index + 1);
            }
        }

        let procentoNyni = getPercent(cil, rezervaStart);
        let procentoKonec = getPercent(cil, zustatek);

        let vysDiv = document.getElementById('vysledekPlan');
        vysDiv.style.display = 'block';

        if (cilMesic) {
            vysDiv.innerHTML =
                `<p><span class="highlight">Cíl dosažen za ${cilMesic} měsíců</span> (${(cilMesic / 12).toFixed(1)} roku).</p>
                 <p>Odhadovaný stav rezervy v cílovém měsíci: ${hodnoty[hodnoty.length - 1].toLocaleString('cs-CZ')} Kč.</p>
                 <p>Aktuálně máš <strong>${rezervaStart.toLocaleString('cs-CZ')} Kč</strong>, což je <strong>${procentoNyni.toFixed(1)} %</strong> cíle.</p>
                 <p>Po simulaci dosáhneš <strong>${procentoKonec.toFixed(1)} %</strong> cíle.</p>`;
        } else {
            vysDiv.innerHTML =
                `<p><span class="highlight">Cíl nebyl dosažen ani za ${mesic} měsíců.</span></p>
                 <p>Odhadovaný stav rezervy: ${zustatek.toLocaleString('cs-CZ')} Kč.</p>
                 <p>Aktuálně máš <strong>${rezervaStart.toLocaleString('cs-CZ')} Kč</strong>, což je <strong>${procentoNyni.toFixed(1)} %</strong> cíle.</p>
                 <p>Po simulaci dosáhneš <strong>${procentoKonec.toFixed(1)} %</strong> cíle.</p>`;
        }

        if (window.Chart) {
            if (grafRezerva) grafRezerva.destroy();
            const ctx = document.getElementById('grafRezerva');
            grafRezerva = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: mesice.map(m => m + '. měsíc'),
                    datasets: [{
                        label: 'Odhadovaný stav rezervy (Kč)',
                        data: hodnoty,
                        borderColor: '#4a90e2',
                        backgroundColor: 'rgba(74,144,226,0.25)',
                        tension: 0.3,
                        fill: true,
                        pointRadius: 2
                    }]
                },
                options: {
                    plugins: {
                        legend: { display: false }
                    },
                    scales: {
                        y: {
                            beginAtZero: false
                        }
                    }
                }
            });
        }

        const dnes = new Date();
        const datum = dnes.toLocaleDateString('cs-CZ') + ' ' +
            dnes.toLocaleTimeString('cs-CZ', { hour: '2-digit', minute: '2-digit' });

        ulozHistorii({
            datum: datum,
            cil: cil,
            rezerva: rezervaStart,
            vklad: vklad,
            urokRocni: urokRocni,
            jednorazovy: jednorazovy,
            mesice: mesic,
            dosazeno: !!cilMesic,
            konecnyStav: zustatek,
            procentoNyni: procentoNyni,
            procentoKonec: procentoKonec
        });
    }

    document.getElementById('btnPlan').addEventListener('click', plan);

    zobrazHistorii();
    updateProgressBar();
};
</script>
