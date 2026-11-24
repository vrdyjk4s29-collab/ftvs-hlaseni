[index.html](https://github.com/user-attachments/files/35347230/index.html)
<!doctype html>
<html lang="cs">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#142d4e">
<title>FTVS UK | Hlášení úrazů a škod</title>
<style>
:root{--navy:#142d4e;--blue:#245b91;--pale:#edf3f8;--line:#d9e1e9;--muted:#5c6b7a;--bg:#f5f7fa}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:#1d2935;font:16px/1.5 system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif}
header{background:var(--navy);color:white;padding:24px 18px}header .inner,main{max-width:760px;margin:auto}
.kicker{font-size:12px;letter-spacing:.12em;text-transform:uppercase;opacity:.8}h1{font-size:clamp(23px,4vw,32px);line-height:1.2;margin:8px 0 4px}header p{margin:0;color:#dbe6f1}
main{padding:28px 16px 48px}.panel{background:white;border:1px solid var(--line);border-radius:16px;padding:clamp(18px,4vw,30px);box-shadow:0 8px 24px #162b4510}
.progress{display:flex;gap:7px;margin-bottom:24px}.progress span{height:6px;flex:1;border-radius:10px;background:#e5eaf0}.progress span.active{background:var(--blue)}
h2{font-size:22px;margin:0 0 8px}.hint{color:var(--muted);margin:0 0 22px}
.field{margin:18px 0}.field>label,.legend{display:block;font-weight:650;margin-bottom:8px}input,textarea,select{font:inherit;width:100%;padding:12px 13px;border:1px solid #bdc9d5;border-radius:9px;background:white;color:#1d2935}textarea{min-height:110px;resize:vertical}
.choice{display:flex;gap:11px;align-items:flex-start;padding:13px;border:1px solid var(--line);border-radius:10px;margin:9px 0;cursor:pointer}.choice:has(input:checked){border-color:var(--blue);background:#f2f7fc}.choice input{width:auto;margin-top:5px;accent-color:var(--blue)}
.actions{display:flex;gap:10px;margin-top:24px}.btn{border:0;border-radius:9px;padding:12px 18px;font:inherit;font-weight:650;cursor:pointer}.primary{background:var(--navy);color:white}.secondary{background:#edf1f5;color:#263747}.btn:disabled{opacity:.45;cursor:not-allowed}
.route{background:var(--pale);border-left:4px solid var(--blue);padding:14px 16px;border-radius:8px;margin:18px 0}.route small{display:block;color:var(--muted)}.tag{display:inline-block;background:#e7f3ec;color:#17613a;border-radius:20px;padding:4px 10px;font-size:13px;font-weight:650}
.note{font-size:13px;color:var(--muted);margin-top:22px}.hidden{display:none!important}.summary{white-space:pre-wrap;background:#f5f7fa;padding:15px;border-radius:9px;font-size:14px;overflow-wrap:anywhere}
footer{text-align:center;color:var(--muted);font-size:12px;padding:18px}
@media(max-width:480px){.actions{flex-direction:column-reverse}.btn{width:100%}}
</style>
</head>
<body>
<header><div class="inner"><div class="kicker">Fakulta tělesné výchovy a sportu UK</div><h1>Hlášení úrazů a škod</h1><p>Jednoduché prvotní oznámení události</p></div></header>
<main><section class="panel">
<div class="progress" aria-label="Postup"><span id="p1" class="active"></span><span id="p2"></span><span id="p3"></span></div>
<div id="wizard">
<section class="step" data-step="1"><h2>1. Kde k události došlo?</h2><p class="hint">Nejprve vyberte místo události.</p>
<label class="choice"><input type="radio" name="country" value="Česká republika" checked> V České republice</label>
<label class="choice"><input type="radio" name="country" value="Zahraničí"> V zahraničí</label>
<div class="actions"><button class="btn primary" id="next1">Pokračovat</button></div></section>
<section class="step hidden" data-step="2"><h2>2. Koho se událost týká?</h2><p class="hint">Vyberte osobu nebo oblast, které se událost týká.</p>
<label class="choice"><input type="radio" name="person" value="Student" checked> Studenta</label>
<label class="choice"><input type="radio" name="person" value="Zaměstnanec"> Zaměstnance</label>
<label class="choice"><input type="radio" name="person" value="Majetek nebo jiná osoba"> Majetku nebo jiné osoby</label>
<div id="student-options" class="field"><span class="legend">Kdy k události došlo?</span>
<label class="choice"><input type="radio" name="studentType" value="Při výuce nebo studijní činnosti" checked> Při výuce nebo studijní činnosti</label>
<label class="choice"><input type="radio" name="studentType" value="Mimo výuku a studijní činnost"> Mimo výuku a studijní činnost</label></div>
<div id="work-options" class="field hidden"><label class="choice"><input type="checkbox" id="workRelated"> Událost souvisí s výkonem práce nebo pracovní cestou</label><small class="hint">Při pracovní události v zahraničí bude informováno také Personální oddělení.</small></div>
<div class="actions"><button class="btn secondary" id="back2">Zpět</button><button class="btn primary" id="next2">Pokračovat</button></div></section>
<section class="step hidden" data-step="3"><h2>3. Základní informace</h2><p class="hint">Vyplňte stručné prvotní oznámení. Příslušné oddělení se vám ozve s dalším postupem.</p>
<div class="route"><small>Předběžný příjemce</small><strong id="destination"></strong></div>
<div class="field"><label for="name">Jméno a příjmení *</label><input id="name" autocomplete="name" required></div>
<div class="field"><label for="email">E-mail *</label><input id="email" type="email" autocomplete="email" required></div>
<div class="field"><label for="phone">Telefon</label><input id="phone" type="tel" autocomplete="tel"></div>
<div class="field"><label for="date">Datum události *</label><input id="date" type="date" required></div>
<div class="field"><label for="place">Místo události *</label><input id="place" placeholder="Např. budova FTVS, tělocvična, adresa…" required></div>
<div class="field"><label for="description">Co se stalo? *</label><textarea id="description" placeholder="Stručně popište, co se stalo a koho se událost týká." required></textarea></div>
<div class="field"><span class="legend">Následek události</span><select id="consequence"><option>Zranění</option><option>Škoda na majetku</option><option>Zranění i škoda na majetku</option><option>Jiné / zatím není známo</option></select></div>
<p class="note">Nevkládejte v této fázi zbytečné citlivé zdravotní údaje. Další dokumenty si může oddělení vyžádat později.</p>
<div class="actions"><button class="btn secondary" id="back3">Zpět</button><button class="btn primary" id="submit">Připravit hlášení</button></div>
</section>
</div>
<section id="confirmation" class="hidden"><span class="tag">Náhled připraven</span><h2 style="margin-top:14px">Hlášení je připraveno</h2><p class="hint">V ostré verzi by bylo předáno příslušnému oddělení. Toto demo nic neodesílá ani neukládá.</p><div class="route"><small>Ukázkové evidenční číslo</small><strong id="case-number"></strong><small>V ostré verzi musí číslo přidělovat centrální evidence, aby bylo vždy jedinečné.</small></div><div class="summary" id="summary"></div><div class="actions"><button class="btn primary" id="copy">Zkopírovat hlášení</button><button class="btn secondary" id="restart">Nové hlášení</button></div></section>
<p class="note">Demonstrační prototyp. Údaje se nikam neposílají ani neukládají. Nezadávejte skutečné citlivé osobní nebo zdravotní údaje.</p>
</section></main><footer>FTVS UK · demonstrační verze</footer>
<script>
const $=id=>document.getElementById(id);
let step=1;
function val(name){return document.querySelector(`input[name="${name}"]:checked`)?.value||""}
function isAbroad(){return val("country")==="Zahraničí"}
function destination(){
 const person=val("person");
 if(isAbroad()) return person==="Zaměstnanec"&&$("workRelated").checked?"Pojistný koordinátor + Personální oddělení":"Pojistný koordinátor";
 if(person==="Student") return val("studentType")==="Při výuce nebo studijní činnosti"?"Studijní oddělení":"Pojistný koordinátor";
 if(person==="Zaměstnanec") return "Personální oddělení";
 return "Pojistný koordinátor";
}
function show(n){step=n;document.querySelectorAll(".step").forEach(el=>el.classList.toggle("hidden",+el.dataset.step!==n));[1,2,3].forEach(i=>$("p"+i).classList.toggle("active",i<=n));}
function updateOptions(){const abroad=isAbroad(),student=val("person")==="Student",employee=val("person")==="Zaměstnanec";$("student-options").classList.toggle("hidden",abroad||!student);$("work-options").classList.toggle("hidden",!abroad||!employee);}
document.querySelectorAll('input[name="country"],input[name="person"]').forEach(el=>el.addEventListener("change",updateOptions));
$("next1").onclick=()=>show(2);$("back2").onclick=()=>show(1);
$("next2").onclick=()=>{ $("destination").textContent=destination();show(3);};$("back3").onclick=()=>show(2);
$("submit").onclick=()=>{
 const required=["name","email","date","place","description"];for(const id of required){if(!$(id).value.trim()||($(id).type==="email"&&!$(id).checkValidity())){$(id).focus();alert("Zkontrolujte prosím povinná pole a správnost e-mailové adresy.");return;}}
 const dest=destination();const now=new Date();const demoNum="FTVS-"+now.getFullYear()+"-"+String(Math.floor(Math.random()*9000)+1000);
 const lines=["PRVOTNÍ HLÁŠENÍ UDÁLOSTI – FTVS UK","Evidenční číslo (ukázkové): "+demoNum,"Příjemce: "+dest,"Místo události: "+val("country"),"Kategorie: "+val("person"),"Datum: "+$("date").value,"Místo: "+$("place").value,"Následek: "+$("consequence").value,"Oznamovatel: "+$("name").value,"E-mail: "+$("email").value,"Telefon: "+$("phone").value,"Popis: "+$("description").value];
 $("case-number").textContent=demoNum;$("summary").textContent=lines.join("\n");$("wizard").classList.add("hidden");$("confirmation").classList.remove("hidden");[1,2,3].forEach(i=>$("p"+i).classList.add("active"));
};
$("copy").onclick=async()=>{try{await navigator.clipboard.writeText($("summary").textContent);$("copy").textContent="Zkopírováno";}catch(e){alert("Kopírování není dostupné. Označte a zkopírujte text ručně.");}};
$("restart").onclick=()=>location.reload();
updateOptions();
</script></body></html>
