<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Double Hand</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@500;700;800&family=Source+Sans+3:wght@400;600&display=swap">
<style>
:root{
  --bg:#F6F4FF;--surface:#FFFFFF;--ink:#1E1B4B;--muted:#5A5683;--line:#DDD8F5;
  --brand:#5B3DF5;--brand-ink:#FFFFFF;--hot:#FF8A5B;--bubble-me:#E3DCFF;--bubble-bot:#FFFFFF;
  --band-a:#4B2FD0;--band-b:#3A55E0;
  box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){
  --bg:#12101F;--surface:#1D1A33;--ink:#EEEBFF;--muted:#A9A3D1;--line:#332E5C;
  --brand:#9A8CFF;--brand-ink:#12101F;--hot:#FFB547;--bubble-me:#2E2766;--bubble-bot:#251F4A;
  --band-a:#2F2680;--band-b:#243A9C;
}}
:root[data-theme="dark"]{
  --bg:#12101F;--surface:#1D1A33;--ink:#EEEBFF;--muted:#A9A3D1;--line:#332E5C;
  --brand:#9A8CFF;--brand-ink:#12101F;--hot:#FFB547;--bubble-me:#2E2766;--bubble-bot:#251F4A;
  --band-a:#2F2680;--band-b:#243A9C;
}
html{scroll-padding-top:env(safe-area-inset-top,0px);scroll-behavior:smooth;-webkit-text-size-adjust:100%;text-size-adjust:100%}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:400 18px/1.6 "Source Sans 3",system-ui,sans-serif}
h1,h2,h3{font-family:"Bricolage Grotesque",system-ui,sans-serif;line-height:1.1;margin:0;letter-spacing:-.02em}
.wrap{max-width:1040px;margin:0 auto;padding:0 max(20px,env(safe-area-inset-right,0px)) 0 max(20px,env(safe-area-inset-left,0px))}
section{padding:72px 0}
h2{font-size:clamp(28px,4vw,40px);font-weight:800;margin-bottom:18px;max-width:20ch}
p{margin:0 0 14px;max-width:62ch}
.muted{color:var(--muted)}
.hero{display:grid;grid-template-columns:1.1fr .9fr;gap:40px;align-items:center;padding:64px 0 48px}
h1{font-size:clamp(32px,7vw,64px);font-weight:800}
.lead{font-size:20px;margin-top:20px;color:var(--muted)}
.btn{display:inline-block;margin-top:14px;min-height:48px;padding:14px 24px;touch-action:manipulation;-webkit-tap-highlight-color:transparent;border-radius:999px;background:var(--brand);color:var(--brand-ink);font-weight:600;text-decoration:none;border:0;font-size:17px;cursor:pointer}
.btn:focus-visible,a:focus-visible{outline:3px solid var(--hot);outline-offset:3px}
.chat{background:var(--surface);border:1px solid var(--line);border-radius:22px;padding:16px;display:flex;flex-direction:column;gap:10px}
.chat-head{font-weight:600;font-size:15px;color:var(--muted);padding:2px 4px 8px;border-bottom:1px solid var(--line)}
.msg{max-width:86%;padding:10px 14px;border-radius:16px;font-size:16px;line-height:1.4}
.me{align-self:flex-end;background:var(--bubble-me);border-bottom-right-radius:4px}
.bot{align-self:flex-start;background:var(--bubble-bot);border:1px solid var(--line);border-bottom-left-radius:4px}
.tag{align-self:center;font-size:14px;color:var(--muted)}
.steps{list-style:none;padding:0;margin:28px 0 0;display:grid;gap:0;counter-reset:s}
.steps li{counter-increment:s;display:grid;grid-template-columns:48px 1fr;gap:16px;padding:20px 0;border-top:1px solid var(--line)}
.steps li::before{content:counter(s);font:800 28px "Bricolage Grotesque",sans-serif;color:var(--brand)}
.steps b{display:block;font-size:19px}
.cols{display:grid;grid-template-columns:repeat(3,1fr);gap:28px;margin-top:24px}
.cols h3{font-size:21px;margin-bottom:8px}
.band{background:linear-gradient(135deg,var(--band-a),var(--band-b));color:#fff}
.band .muted{color:inherit;opacity:.85}
.prices{display:grid;grid-template-columns:repeat(2,1fr);gap:18px;margin-top:26px;max-width:720px}
.plan{background:var(--surface);color:var(--ink);border-radius:18px;padding:24px;border:1px solid var(--line)}
.plan h3{font-size:22px}.plan .n{font:800 36px "Bricolage Grotesque",sans-serif;margin:8px 0}
.plan p{font-size:16px;color:var(--muted);margin:0}
.valid{display:grid;gap:12px;padding:0;list-style:none;margin:20px 0 0}
.valid li{display:flex;gap:12px;align-items:flex-start}
.valid li::before{content:"✓";font-weight:700;color:var(--brand);flex:none}
footer{padding:48px 0 64px;border-top:1px solid var(--line)}
section.platforms{padding:8px 0 0}
.platforms h2{font-size:18px;font-weight:700;margin-bottom:14px;max-width:none;color:var(--muted)}
.logos{display:flex;flex-wrap:wrap;gap:12px}
.logo{display:flex;align-items:center;gap:10px;padding:10px 18px 10px 12px;background:var(--surface);border:1px solid var(--line);border-radius:999px;font-weight:600;font-size:16px}
.logo svg{width:30px;height:30px;flex:none}
.logo .gen{color:var(--brand)}
.brand{padding-top:24px;font:800 24px "Bricolage Grotesque",system-ui,sans-serif;letter-spacing:-.02em;color:var(--brand)}
.agenda{margin-top:22px;background:var(--surface);border:1px solid var(--line);border-radius:20px;overflow:hidden;max-width:720px}
.agenda-head{padding:14px 20px;font:700 19px "Bricolage Grotesque",system-ui,sans-serif;border-bottom:1px solid var(--line)}
.slot{display:grid;grid-template-columns:64px 1fr auto;gap:14px;align-items:center;padding:14px 20px;border-top:1px solid var(--line)}
.agenda-head+.slot{border-top:0}
.slot time{font-weight:700;font-variant-numeric:tabular-nums}
.slot small{display:block;color:var(--muted);font-size:15px;line-height:1.4}
.slot.free{color:var(--muted)}
.chip{font-size:14px;font-weight:600;padding:5px 12px;border-radius:999px;white-space:nowrap}
.chip.ok{background:var(--bubble-me);color:var(--ink)}
.chip.warn{background:var(--hot);color:#2A1A00}
@media (max-width:760px){.slot{grid-template-columns:52px 1fr;padding:12px 14px;gap:8px 12px}.slot .chip{grid-column:2;justify-self:start}.agenda-head{padding:12px 14px}}
@media (max-width:760px){.logos{gap:10px}.logo{flex:1 1 calc(50% - 10px);min-width:0;padding:10px 12px 10px 10px;font-size:15px}}
@media (max-width:760px){
  body{font-size:17px;overflow-wrap:break-word}
  .hero,.cols,.prices{grid-template-columns:1fr}
  .hero{gap:28px;padding:36px 0 24px}
  .lead{font-size:18px;margin-top:14px}
  section{padding:44px 0}
  .btn{display:block;width:100%;text-align:center}
  .chat{padding:12px;border-radius:18px}
  .msg{max-width:92%;font-size:16px}
  .steps li{grid-template-columns:34px 1fr;gap:12px;padding:16px 0}
  .steps li::before{font-size:24px}
  .cols{gap:20px}
  .plan{padding:20px}
  h2{max-width:none}
}
@media (max-width:380px){
  body{font-size:16px}
  .wrap{padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}
}
@media (prefers-reduced-motion:reduce){html{scroll-behavior:auto}}
.dh-open[hidden],.dh-panel[hidden]{display:none}
.dh-open{position:fixed;right:max(16px,env(safe-area-inset-right,0px));bottom:max(16px,env(safe-area-inset-bottom,0px));z-index:50;display:flex;align-items:center;gap:8px;min-height:52px;padding:0 20px;border:0;border-radius:999px;background:var(--brand);color:var(--brand-ink);font:600 16px "Source Sans 3",system-ui,sans-serif;cursor:pointer;box-shadow:0 8px 24px rgba(30,27,75,.3);touch-action:manipulation}
.dh-open svg{width:22px;height:22px}
.dh-panel{position:fixed;right:max(16px,env(safe-area-inset-right,0px));bottom:max(16px,env(safe-area-inset-bottom,0px));z-index:60;width:min(390px,calc(100vw - 32px));height:min(580px,calc(100vh - 32px));height:min(580px,calc(100dvh - 32px - env(safe-area-inset-top,0px) - env(safe-area-inset-bottom,0px)));display:flex;flex-direction:column;background:var(--surface);border:1px solid var(--line);border-radius:20px;overflow:hidden;box-shadow:0 16px 48px rgba(30,27,75,.35)}
.dh-top{display:flex;justify-content:space-between;align-items:center;padding:6px 6px 6px 16px;background:linear-gradient(135deg,var(--band-a),var(--band-b));color:#fff;font:700 17px "Bricolage Grotesque",system-ui,sans-serif}
.dh-top button{width:44px;height:44px;border:0;background:none;color:inherit;font-size:20px;cursor:pointer;border-radius:50%}
.dh-log{flex:1;overflow-y:auto;padding:14px;display:flex;flex-direction:column;gap:10px;overscroll-behavior:contain}
.dh-log .msg{white-space:pre-wrap;overflow-wrap:anywhere}
.dh-chips{display:flex;flex-wrap:wrap;gap:8px;padding:0 14px 10px}
.dh-chips button{border:1px solid var(--line);background:var(--bg);color:var(--ink);border-radius:999px;padding:8px 12px;min-height:38px;font:600 14px "Source Sans 3",system-ui,sans-serif;cursor:pointer}
.dh-in{display:flex;gap:8px;padding:10px;border-top:1px solid var(--line)}
.dh-in input{flex:1;min-width:0;font:16px "Source Sans 3",system-ui,sans-serif;padding:12px 16px;border:1px solid var(--line);border-radius:999px;background:var(--bg);color:var(--ink)}
.dh-send{border:0;border-radius:999px;background:var(--brand);color:var(--brand-ink);font:600 16px "Source Sans 3",system-ui,sans-serif;padding:0 18px;min-height:44px;cursor:pointer}
.dh-send:disabled{opacity:.5;cursor:default}
.dh-open:focus-visible,.dh-top button:focus-visible,.dh-chips button:focus-visible,.dh-in input:focus-visible,.dh-send:focus-visible{outline:3px solid var(--hot);outline-offset:2px}
@media (max-width:480px){.dh-panel{width:calc(100vw - 24px);right:12px}}
</style>
</head>
<body>
<main>
<header class="wrap brand">Double Hand</header>
<div class="wrap hero">
  <div>
    <h1>Tu oficio, atendiendo clientes las 24 horas.</h1>
    <p class="lead">Un asistente de IA que piensa, cotiza y habla como tú. Responde por WhatsApp, Instagram o web, y agenda citas mientras trabajas.</p>
    <a class="btn" href="mailto:hola@ejemplo.com?subject=Negocio%20piloto">Quiero ser negocio piloto</a>
  </div>
  <div class="chat" aria-label="Ejemplo de conversación">
    <div class="chat-head">Taller Hernández · asistente</div>
    <div class="msg me">Hola, mi carro hace un ruido al frenar. Les mando un video.</div>
    <div class="msg bot">Gracias, Marcos. Por el sonido parece desgaste de pastillas. Revisión y cambio: entre $60 y $95. ¿Qué modelo y año es?</div>
    <div class="msg me">Corolla 2016</div>
    <div class="msg bot">Con ese modelo, $75 aprox. Tengo espacio mañana a las 9:00 o a las 14:00. ¿Cuál te sirve?</div>
    <div class="tag">Cita agendada en el calendario del dueño</div>
  </div>
</div>

<section class="platforms">
  <div class="wrap">
    <h2>Funciona con las plataformas que ya usan tus clientes</h2>
    <div class="logos">
      <div class="logo"><svg viewBox="0 0 48 48" aria-hidden="true"><circle cx="24" cy="24" r="23" fill="#25D366"/><path d="M24 11.5a12.5 12.5 0 0 0-10.8 18.8L11.5 36.5l6.4-1.7A12.5 12.5 0 1 0 24 11.5z" fill="none" stroke="#fff" stroke-width="2.6" stroke-linejoin="round"/><path d="M19.2 18.6c.5-.7 1.2-.7 1.6 0l1 2.100c.2.500 0 .900-.4 1.300l-.7.700c.9 1.800 2.300 3.200 4.300 4.200l.8-.8c.4-.4.9-.5 1.300-.3l2.100 1c.8.400.8 1.100.1 1.800-1.500 1.500-3.500 1.400-6.100-.1-2.600-1.500-4.300-3.400-4.800-5.500-.3-1.300 0-2.100.8-3.400z" fill="#fff"/></svg>WhatsApp</div>
      <div class="logo"><svg viewBox="0 0 48 48" aria-hidden="true"><defs><linearGradient id="ig" x1="0" y1="1" x2="1" y2="0"><stop offset="0" stop-color="#FEDA75"/><stop offset=".3" stop-color="#FA7E1E"/><stop offset=".55" stop-color="#D62976"/><stop offset=".8" stop-color="#962FBF"/><stop offset="1" stop-color="#4F5BD5"/></linearGradient></defs><rect width="48" height="48" rx="12" fill="url(#ig)"/><rect x="10" y="10" width="28" height="28" rx="8" fill="none" stroke="#fff" stroke-width="3"/><circle cx="24" cy="24" r="6.500" fill="none" stroke="#fff" stroke-width="3"/><circle cx="32.500" cy="15.500" r="2" fill="#fff"/></svg>Instagram</div>
      <div class="logo"><svg class="gen" viewBox="0 0 48 48" aria-hidden="true" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round"><circle cx="24" cy="24" r="18"/><ellipse cx="24" cy="24" rx="8" ry="18"/><path d="M6 24h36M9 15h30M9 33h30"/></svg>Tu página web</div>
      <div class="logo"><svg class="gen" viewBox="0 0 48 48" aria-hidden="true" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><rect x="7" y="10" width="34" height="31" rx="5"/><path d="M7 20h34M16 6v8M32 6v8"/><circle cx="17" cy="29" r="1.500" fill="currentColor"/><circle cx="24" cy="29" r="1.500" fill="currentColor"/><circle cx="31" cy="29" r="1.500" fill="currentColor"/></svg>Tu calendario</div>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <h2>Los negocios pequeños pierden clientes por no contestar a tiempo</h2>
    <p>Un electricista bajo un lavamanos no puede revisar el celular. Un salón lleno no puede responder mensajes. El cliente escribe a otro, y esa venta ya no vuelve.</p>
    <p>Un chatbot genérico no resuelve esto: no sabe cómo cotizas, qué casos rechazas ni cómo hablas. El gemelo digital sí.</p>
  </div>
</section>

<section style="padding-top:0">
  <div class="wrap">
    <h2>Cómo funciona</h2>
    <ol class="steps">
      <li><div><b>Te entrevistamos por voz</b>Unos 20 minutos: cómo cotizas, qué preguntas haces, qué casos rechazas y cómo hablas con tus clientes.</div></li>
      <li><div><b>La IA arma tu gemelo</b>Un asistente con tu criterio, tus precios y tu estilo, conectado a WhatsApp, Instagram o tu web.</div></li>
      <li><div><b>Atiende al cliente</b>Pregunta lo necesario, pide fotos del problema, da una cotización preliminar y agenda la cita en tu calendario.</div></li>
      <li><div><b>Tú solo intervienes cuando importa</b>Te avisa únicamente cuando un caso necesita tu atención.</div></li>
    </ol>
  </div>
</section>

<section style="padding-top:0">
  <div class="wrap">
    <h2>Así se ve tu agenda</h2>
    <p>El asistente llena los huecos con citas ya confirmadas. Tú solo revisas lo que aparece marcado.</p>
    <div class="agenda" role="table" aria-label="Ejemplo de agenda del lunes 19 de octubre">
      <div class="agenda-head">Lunes 19 de octubre</div>
      <div class="slot"><time>9:00</time><div>Marcos R.<small>Cambio de pastillas, Corolla 2016. Cotización: $75</small></div><span class="chip ok">Agendada por el asistente</span></div>
      <div class="slot"><time>11:00</time><div>Laura G.<small>Revisión del aire acondicionado</small></div><span class="chip ok">Agendada por el asistente</span></div>
      <div class="slot free"><time>13:00</time><div>Horario libre<small>El asistente puede ofrecerlo a nuevos clientes</small></div></div>
      <div class="slot"><time>14:00</time><div>Pedro S.<small>Ruido en el motor, el diagnóstico por fotos no fue claro</small></div><span class="chip warn">Requiere tu revisión</span></div>
      <div class="slot"><time>16:30</time><div>Ana M.<small>Cambio de aceite</small></div><span class="chip ok">Agendada por el asistente</span></div>
    </div>
  </div>
</section>

<section class="band">
  <div class="wrap">
    <h2>Por qué es distinto</h2>
    <div class="cols">
      <div><h3>Aprende tu criterio</h3><p class="muted">Lo valioso de un profesional es cómo decide, no solo qué sabe. Eso es lo que capturamos.</p></div>
      <div><h3>Entiende fotos</h3><p class="muted">Una gotera, un corte de pelo deseado o una pieza dañada: la IA de visión da un diagnóstico inicial.</p></div>
      <div><h3>Mejora con el sector</h3><p class="muted">Cada negocio que se une afina las plantillas de su industria, y eso es difícil de copiar.</p></div>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <h2>Para quién es</h2>
    <p>Artesanos, talleres, clínicas pequeñas, restaurantes y profesionales independientes: electricistas, fontaneros, peluqueros y cualquiera que venda su criterio y su tiempo.</p>
  </div>
</section>

<section class="band">
  <div class="wrap">
    <h2>Precios</h2>
    <div class="prices">
      <div class="plan"><h3>Suscripción</h3><div class="n">$29–79</div><p>Por mes, según el volumen de conversaciones.</p></div>
      <div class="plan"><h3>Comisión opcional</h3><div class="n">Por cita</div><p>Pagas un porcentaje solo por cada cita o venta cerrada.</p></div>
    </div>
  </div>
</section>

</main>
<footer><div class="wrap"><div class="brand" style="padding-top:0">Double Hand</div></div></footer>
<button id="dh-open" class="dh-open" hidden aria-expanded="false" aria-controls="dh-panel"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M21 12a8 8 0 0 1-11.6 7.1L4 20.500l1.400-4.600A8 8 0 1 1 21 12z"/></svg>Pregúntame</button>
<div id="dh-panel" class="dh-panel" hidden role="dialog" aria-label="Asistente virtual de Double Hand">
  <div class="dh-top"><span>Asistente de Double Hand</span><button id="dh-close" aria-label="Cerrar el asistente">✕</button></div>
  <div id="dh-log" class="dh-log" aria-live="polite"></div>
  <div id="dh-chips" class="dh-chips">
    <button type="button">¿Cómo funciona?</button>
    <button type="button">¿Cuánto cuesta?</button>
    <button type="button">¿Sirve para mi negocio?</button>
  </div>
  <div class="dh-in"><input id="dh-input" type="text" placeholder="Escribe tu pregunta" autocomplete="off" enterkeyhint="send" aria-label="Tu pregunta"><button id="dh-send" class="dh-send" type="button">Enviar</button></div>
</div>
<script>
(async function(){
  var sample=null;
  try{ if(window.claude&&window.claude.use){ sample=await window.claude.use("sample"); } }catch(e){}
  if(!sample) return;
  var $=function(id){return document.getElementById(id)};
  var openBtn=$("dh-open"),panel=$("dh-panel"),log=$("dh-log"),input=$("dh-input"),send=$("dh-send"),chips=$("dh-chips");
  var INSTR="Eres el asistente virtual de Double Hand, un servicio de IA para pequeños negocios locales (talleres, salones de belleza, clínicas pequeñas, restaurantes, artesanos, electricistas, fontaneros, peluqueros). Double Hand crea un gemelo digital del negocio: el dueño responde una entrevista guiada por voz de unos 20 minutos (cómo cotiza, qué preguntas hace, qué casos rechaza, cómo habla con sus clientes). Con eso la IA arma un asistente con su criterio, sus precios y su estilo que atiende por WhatsApp, Instagram o la página web del negocio las 24 horas: pide fotos del problema y las analiza con IA de visión, da una cotización preliminar, agenda la cita en el calendario y solo avisa al dueño cuando un caso requiere su atención. Precios: suscripción de $29 a $79 al mes según el volumen de conversaciones, más una comisión opcional por cada cita o venta cerrada. Double Hand está empezando y busca negocios piloto gratuitos a cambio de feedback y testimonios; para participar, se usa el botón Quiero ser negocio piloto de la página. Si te preguntan algo específico de Double Hand que no está aquí, dilo con honestidad y no inventes datos. También puedes responder cualquier otra pregunta general con precisión y amabilidad. Responde en el idioma de la persona, de forma clara y breve (máximo 4 frases salvo que pida más detalle), en texto plano sin markdown.";
  var H=[],busy=false;
  function add(cls,text){var d=document.createElement("div");d.className="msg "+cls;d.textContent=text;log.appendChild(d);log.scrollTop=log.scrollHeight;return d}
  function setOpen(o){panel.hidden=!o;openBtn.hidden=o;openBtn.setAttribute("aria-expanded",String(o));if(o){if(!log.children.length)add("bot","Hola, soy el asistente de Double Hand. Pregúntame lo que quieras sobre cómo funciona, los precios o si te sirve para tu negocio.");input.focus()}else{openBtn.focus()}}
  async function ask(q){
    q=q.trim();if(busy||!q)return;busy=true;send.disabled=true;chips.hidden=true;input.value="";
    add("me",q);H.push({role:"user",content:q});
    var b=add("bot","Pensando…");
    try{
      var msgs=H.slice(-8).map(function(m){return{role:m.role,content:m.content}});
      while(msgs.length&&msgs[0].role!=="user")msgs.shift();
      msgs[0].content=INSTR+"\n\n"+msgs[0].content;
      var r=await sample(msgs,{cache:false,onText:function(t){b.textContent=t.text;log.scrollTop=log.scrollHeight}});
      b.textContent=r.text;H.push({role:"assistant",content:r.text});
    }catch(e){
      H.pop();
      b.textContent=(e&&e.code==="not_granted")?"Para usar el asistente necesitas aceptar el permiso cuando se te pida.":(e&&e.code==="rate_limited")?"Hay muchas preguntas en este momento. Intenta de nuevo en unos segundos.":"No pude responder. Intenta de nuevo.";
    }
    busy=false;send.disabled=false;input.focus();log.scrollTop=log.scrollHeight;
  }
  openBtn.hidden=false;
  openBtn.addEventListener("click",function(){setOpen(true)});
  $("dh-close").addEventListener("click",function(){setOpen(false)});
  send.addEventListener("click",function(){ask(input.value)});
  input.addEventListener("keydown",function(e){if(e.key==="Enter"&&!e.isComposing){e.preventDefault();ask(input.value)}});
  chips.addEventListener("click",function(e){var t=e.target.closest("button");if(t)ask(t.textContent)});
  document.addEventListener("keydown",function(e){if(e.key==="Escape"&&!panel.hidden)setOpen(false)});
})();
</script>
</body>
</html>
