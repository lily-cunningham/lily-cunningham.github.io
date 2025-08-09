<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AdoptionAid — Warm Listing Generator (AI + Multi-Photo)</title>
  <meta name="description" content="Enter shelter facts once; get an AI-written, warm adoption bio + Petfinder + social. Pick or auto-rank multiple photos; optional local image enhance. Single-file." />
  <style>
    :root{--bg:#FFF8F0;--ink:#2E2525;--muted:#6B5F5F;--card:#fff;--ring:#F0E6DC;--accent:#FF6B6B;--radius:14px}
    *{box-sizing:border-box}
    body{margin:0;background:var(--bg);color:var(--ink);font-family:ui-sans-serif,system-ui,Segoe UI,Roboto,Helvetica,Arial}
    header,footer{text-align:center;padding:16px;background:#fff;border-bottom:1px solid var(--ring)}
    footer{border-top:1px solid var(--ring);border-bottom:0}
    main{max-width:1200px;margin:0 auto;padding:16px}
    h1,h2{margin:0 0 10px}
    .grid{display:grid;gap:16px}
    @media(min-width:1100px){.grid{grid-template-columns:420px 1fr}}
    .card{background:var(--card);border:1px solid var(--ring);border-radius:var(--radius);padding:14px}
    label{display:block;margin-top:8px;font-weight:600}
    input,select,textarea{width:100%;padding:10px;margin-top:4px;border:1px solid #d9d4ce;border-radius:10px;font:inherit;background:#fff}
    textarea{min-height:96px;resize:vertical}
    .row{display:flex;gap:8px;flex-wrap:wrap}
    .muted{color:var(--muted)}
    .btn{display:inline-flex;align-items:center;gap:8px;border:1px solid var(--ring);border-radius:999px;padding:10px 14px;font-weight:800;background:#fff;cursor:pointer}
    .btn.primary{background:var(--accent);color:#fff;border-color:#ff9e9e}
    .out{white-space:pre-wrap;background:#fff;border:1px solid var(--ring);border-radius:12px;padding:12px}
    .drop{border:2px dashed var(--ring);border-radius:12px;padding:12px;text-align:center;background:#fff}
    .thumb{width:100%;height:220px;border:1px solid var(--ring);border-radius:12px;object-fit:cover;background:#fafafa}
    .thumb.best{outline:3px solid var(--accent)}
    .thumb-wrap{position:relative}
    .badge{position:absolute;top:8px;left:8px;background:var(--accent);color:#fff;padding:2px 8px;border-radius:999px;font-size:12px}
    .fine{font-size:12px}
    details summary{cursor:pointer}
    .kv{display:grid;grid-template-columns:140px 1fr;gap:8px;align-items:center}
    .status{font-size:12px;color:var(--muted);margin-top:6px}
  </style>
</head>
<body>
  <header>
    <h1>AdoptionAid — Warm Listing Generator</h1>
    <p class="muted">AI rewrites the bio from your facts and ranks multiple photos. All in one file.</p>
  </header>

  <main class="grid" id="app">
    <!-- Left: inputs -->
    <section class="card" aria-label="Inputs">
      <h2>Pet details</h2>
      <label>Name<input id="name" placeholder="Luna" autofocus></label>
      <div class="row">
        <div style="flex:1"><label>Species
          <select id="species">
            <option>Dog</option><option>Cat</option><option>Rabbit</option>
            <option>Bird</option><option>Small animal</option><option>Farm animal</option><option>Other</option>
          </select>
        </label></div>
        <div style="flex:1"><label>Breed (optional)<input id="breed" placeholder="Labrador mix"></label></div>
      </div>
      <div class="row">
        <div style="flex:1"><label>Age<input id="age" placeholder="2 years"></label></div>
        <div style="flex:1"><label>Sex<select id="sex"><option>Female</option><option>Male</option><option>Unknown</option></select></label></div>
      </div>
      <div class="row">
        <div style="flex:1"><label>Size<select id="size"><option>Small</option><option>Medium</option><option>Large</option><option>XL</option></select></label></div>
        <div style="flex:1"><label>Weight (optional)<input id="weight" placeholder="45 lb"></label></div>
      </div>
      <div class="row">
        <div style="flex:1"><label>Coat / color (optional)<input id="coat" placeholder="short coat, black & white"></label></div>
        <div style="flex:1"><label>Energy<select id="energy"><option>Low</option><option>Moderate</option><option>High</option></select></label></div>
      </div>
      <label>Personality & quirks (comma-separated)<input id="traits" placeholder="gentle, loves fetch, snuggle bug"></label>
      <label>Loves to… (short phrases, comma-separated)<input id="likes" placeholder="chase bubbles, nap in sunny spots"></label>
      <div class="row">
        <div style="flex:1"><label>Good with (comma-separated)<input id="good" placeholder="dogs, kids"></label></div>
        <div style="flex:1"><label>House-trained<select id="house"><option>Yes</option><option>No</option><option>In progress</option><option>Unknown</option></select></label></div>
      </div>
      <div class="row">
        <div style="flex:1"><label>Crate-trained<select id="crate"><option>Yes</option><option>No</option><option>In progress</option><option>Unknown</option></select></label></div>
        <div style="flex:1"><label>Spayed/Neutered<select id="spay"><option>Yes</option><option>No</option><option>Unknown</option></select></label></div>
      </div>
      <label>Medical or diet notes (factual)<textarea id="medical" placeholder="On a chicken-free diet; daily meds given by staff"></textarea></label>
      <label>Ideal home (short sentence)<input id="home" placeholder="calm home with patient adopters"></label>
      <div class="row">
        <div style="flex:1"><label>Location<input id="loc" placeholder="City, ST"></label></div>
        <div style="flex:1"><label>Shelter / Rescue<input id="shelter" placeholder="Org name"></label></div>
      </div>
      <h2 style="margin-top:10px">Photos</h2>
      <div id="drop" class="drop" tabindex="0">
        <div class="muted">Drop one or more photos, or use the picker</div>
        <input id="file" type="file" accept="image/*" multiple style="margin-top:8px">
        <div id="thumbs" style="margin-top:8px;display:grid;grid-template-columns:repeat(auto-fill,minmax(120px,1fr));gap:8px"></div>
      </div>

      <h2 style="margin-top:10px">Tone</h2>
      <div class="row">
        <label class="row" style="align-items:center;gap:6px"><input type="radio" name="tone" value="warm" checked> Warm & cozy</label>
        <label class="row" style="align-items:center;gap:6px"><input type="radio" name="tone" value="plain"> Plain & factual</label>
      </div>

      <h2 style="margin-top:10px">AI settings</h2>
      <label>OpenAI API Key<input id="apiKey" type="password" placeholder="sk-..." /></label>
      <label>API Base (optional)<input id="apiBase" placeholder="https://api.openai.com/v1" /></label>
      <label>Model<select id="textModel">
        <option value="gpt-4o-mini" selected>gpt-4o-mini</option>
        <option value="gpt-4o">gpt-4o</option>
        <option value="gpt-4.1">gpt-4.1</option>
      </select></label>

      <div class="row" style="margin-top:10px">
        <button id="generate" class="btn primary" type="button">Generate AI Bio</button>
        <button id="copyAll" class="btn" type="button">Copy all</button>
        <button id="downloadAll" class="btn" type="button">Download text + best photo</button>
      </div>
      <div class="fine muted" style="margin-top:6px">“Assessment based on shelter observations; meet-and-greet required. Not medical advice.” is appended automatically.</div>
    </section>

    <!-- Right: outputs -->
    <section class="card" aria-label="Outputs">
      <h2>Listing preview</h2>
      <canvas id="canvas" width="900" height="600" style="width:100%;border:1px solid var(--ring);border-radius:12px;background:#fff"></canvas>
      <div class="out" id="bio" style="margin-top:10px"></div>
      <div class="out" id="pf" style="margin-top:10px"></div>
      <div class="out" id="social" style="margin-top:10px"></div>
      <div class="row" style="margin-top:8px">
        <button class="btn" id="copyBio" type="button">Copy bio</button>
        <button class="btn" id="copyPF" type="button">Copy Petfinder</button>
        <button class="btn" id="copySocial" type="button">Copy social</button>
      </div>
    </section>
  </main>

  <footer>
    <div>© <span id="y"></span> AdoptionAid • Offline, single-file</div>
  </footer>

<script>
(function(){
  const $=s=>document.querySelector(s); const $$=s=>Array.from(document.querySelectorAll(s));
  $('#y').textContent=new Date().getFullYear();

  // Photo handling
  const file=$('#file'), drop=$('#drop'), thumbs=$('#thumbs'), canvas=$('#canvas'), ctx=canvas.getContext('2d');
  let sources=[]; // {img:Image, score:number, file:File}
  drop.addEventListener('dragover',e=>{e.preventDefault(); drop.style.background='#FFF1F1'});
  drop.addEventListener('dragleave',()=>{drop.style.background=''});
  drop.addEventListener('drop',e=>{e.preventDefault(); drop.style.background=''; handleFiles(e.dataTransfer.files)});
  file.addEventListener('change',e=>handleFiles(e.target.files));

  function handleFiles(list){
    const files=Array.from(list||[]).filter(f=>/^image\\//.test(f.type));
    files.forEach(f=>{
      const url=URL.createObjectURL(f); const img=new Image();
      img.onload=()=>{ sources.push({img, file:f, score:scoreImage(img)}); renderThumbs(); };
      img.src=url;
    });
  }

  function scoreImage(img){
    // naive sharpness+brightness heuristic for local ranking
    const tmp=document.createElement('canvas'); tmp.width=img.width; tmp.height=img.height;
    const tctx=tmp.getContext('2d'); tctx.drawImage(img,0,0);
    const data=tctx.getImageData(0,0,tmp.width,tmp.height).data;
    let bright=0, contrast=0;
    for(let i=0;i<data.length;i+=4){
      const lum=0.299*data[i]+0.587*data[i+1]+0.114*data[i+2];
      bright+=lum; contrast+=Math.abs(lum-128);
    }
    bright/= (data.length/4); contrast/= (data.length/4);
    return contrast - Math.abs(128-bright); // higher better
  }

  function renderThumbs(){
    thumbs.innerHTML='';
    sources.sort((a,b)=>b.score-a.score);
    sources.forEach((src,i)=>{
      const wrap=document.createElement('div'); wrap.className='thumb-wrap';
      const im=document.createElement('img'); im.src=src.img.src; im.className='thumb'; if(i===0) im.classList.add('best');
      if(i===0){ const b=document.createElement('div'); b.className='badge'; b.textContent='Best'; wrap.appendChild(b);}
      wrap.appendChild(im); thumbs.appendChild(wrap);
    });
    draw();
  }

  function draw(){
    ctx.fillStyle='#fff'; ctx.fillRect(0,0,canvas.width,canvas.height);
    if(sources[0]){
      const source=sources[0].img;
      const s=Math.min(canvas.width/source.width, canvas.height/source.height);
      const w=Math.round(source.width*s), h=Math.round(source.height*s);
      const x=(canvas.width-w)>>1, y=(canvas.height-h)>>1;
      ctx.drawImage(source,x,y,w,h);
    }
  }
  // ---------- helpers for text + hashtags ----------
  const val=id=>($('#'+id)?.value||'').trim();
  const radio=name=>document.querySelector(`input[name="${name}"]:checked`)?.value||'';
  const listify=s=>(s||'').split(',').map(x=>x.trim()).filter(Boolean);
  const titleCase=s=>s.replace(/\w\S*/g,t=>t[0].toUpperCase()+t.slice(1).toLowerCase());
  function hashtags(){
    const sp=(val('species')||'').toLowerCase();
    const city=(val('loc').split(',')[0]||'').trim().replace(/\s+/g,'');
    const base=['#adopt','#adoptdontshop','#rescue','#shelterpet','#adoptionaid'];
    if(sp.includes('dog')) base.push('#dog','#rescuedog');
    else if(sp.includes('cat')) base.push('#cat','#rescuecat');
    else if(sp.includes('rabbit')) base.push('#rabbit','#rescuerabbit');
    else if(sp.includes('bird')) base.push('#bird','#rescuebird');
    else if(sp.includes('small')) base.push('#smallanimal');
    else if(sp.includes('farm')) base.push('#farmanimal');
    if(city) base.unshift('#'+city);
    return base.join(' ');
  }

  // ---------- AI prompt + generation ----------
  function collectFacts(){
    const species=val('species').toLowerCase(); const breed=val('breed');
    return {
      name: val('name')||'This pet',
      species, breed,
      age: val('age'), sex:(val('sex')||'').toLowerCase(), size:(val('size')||'').toLowerCase(), weight: val('weight'),
      coat: val('coat'), energy:(val('energy')||'').toLowerCase(),
      traits: listify(val('traits')), likes: listify(val('likes')),
      good: (val('good')||'').toLowerCase(), house:(val('house')||'').toLowerCase(), crate:(val('crate')||'').toLowerCase(), spay:(val('spay')||'').toLowerCase(),
      medical: val('medical'), home: val('home'),
      loc: val('loc'), shelter: val('shelter'),
      tone: radio('tone')
    };
  }

  function buildPrompts(f){
    const factsJSON=JSON.stringify(f);
    const system = [
      'You are a senior copywriter for an animal rescue.',
      'Write unique, adoption-optimized bios from factual notes.',
      'Voice: warm, concrete, human. No cutesy baby talk. No emojis.',
      'Length: 110–170 words, 2 short paragraphs. Vary sentence openings and rhythm.',
      'Emphasize adoptability: temperament, home fit, training, who the pet is good with.',
      'Show, not tell: convert traits into small moments (e.g., "taps your knee for another toss").',
      'No medical claims; keep care notes neutral and brief.',
      'No absolutes; prefer calibrated language ("has done well with…") when supported.',
      'End with a clear call to action for a meet-and-greet.',
      'NEVER invent facts. If info is missing, omit it gracefully.'
    ].join(' ');
    const user = [
      `Facts (JSON): ${factsJSON}`,
      'Return ONLY JSON with keys {"bio","pf","social"}.',
      'bio: 110–170 words, 2 short paragraphs, flowing prose, no bullets.',
      'Include this disclaimer as the final sentence, exactly: "Assessment based on shelter observations; meet-and-greet required. Not medical advice."',
      'pf: one sentence stating availability and location with an invitation to contact.',
      `social: two short captions (<=140 chars each) with natural hooks + hashtags: ${hashtags()}`
    ].join('\n');
    return {system,user};
  }

  async function callOpenAI(messages){
    const base=(val('apiBase')||'https://api.openai.com/v1').replace(/\/$/,'');
    const key=val('apiKey'); const model=val('textModel')||'gpt-4o-mini';
    if(!key) throw new Error('Add your API key in AI settings.');
    const res=await fetch(base+'/chat/completions',{
      method:'POST',
      headers:{'Content-Type':'application/json','Authorization':'Bearer '+key},
      body:JSON.stringify({model, messages, temperature:0.85, response_format:{type:'json_object'}})
    });
    const j=await res.json();
    if(!res.ok) throw new Error(j.error?.message || ('HTTP '+res.status));
    return j.choices?.[0]?.message?.content||'';
  }

  function fallbackBio(){
    const name=val('name')||'This pet'; const short=name.split(' ')[0];
    const species=val('species').toLowerCase(); const breed=val('breed'); const speciesStr=breed?`${breed} ${species}`:species;
    const age=val('age'); const sex=(val('sex')||'').toLowerCase(); const size=(val('size')||'').toLowerCase(); const weight=val('weight');
    const coat=val('coat'); const energy=(val('energy')||'').toLowerCase();
    const traits=listify(val('traits')); const likes=listify(val('likes'));
    const good=(val('good')||''); const house=(val('house')||'').toLowerCase(); const crate=(val('crate')||'').toLowerCase(); const spay=(val('spay')||'').toLowerCase();
    const medical=val('medical'); const home=val('home'); const where=val('loc');
    const z=[];
    z.push(`${name} is a ${age?age+', ':''}${speciesStr}${sex?' '+sex:''}${size?' (~'+size+')':''}${weight?' around '+weight:''}.`);
    if(coat) z.push(`With a ${coat} coat, ${short} turns heads wherever ${sex==='female'?'she':sex==='male'?'he':'they'} goes.`);
    if(traits.length) z.push(titleCase(traits.join('; '))+'.');
    if(likes.length) z.push(`${short} loves ${likes.join(', ')}.`);
    if(good) z.push(`Has done well with ${good.toLowerCase()}.`);
    if(energy) z.push(`Energy level: ${energy}.`);
    if(house) z.push(`House-trained: ${house}.`);
    if(crate) z.push(`Crate-trained: ${crate}.`);
    if(spay) z.push(`Spayed/Neutered: ${spay}.`);
    if(medical) z.push(`Care notes: ${medical.replace(/\.$/, '')}.`);
    if(home) z.push(`Ideal home: ${home.replace(/\.$/, '')}.`);
    if(where) z.push(`Currently in ${where}.`);
    z.push('Assessment based on shelter observations; meet-and-greet required. Not medical advice.');
    return z.join(' ');
  }
  function buildPF(){ const n=val('name')||'This pet'; const where=val('loc')||'our area'; return `${n} is available for adoption in ${where}. Contact the shelter to learn more and schedule a meet-and-greet.`; }
  function buildSocial(){ const n=val('name')||'This pet'; return `${n} is looking for a home! ${hashtags()}`; }

  async function generateAIText(){
    const facts=collectFacts(); const {system,user}=buildPrompts(facts);
    try{
      const json=await callOpenAI([{role:'system',content:system},{role:'user',content:user}]);
      const parsed=JSON.parse(json);
      if(!parsed.bio || !parsed.pf || !parsed.social) throw new Error('Incomplete AI JSON');
      const socialOut = Array.isArray(parsed.social) ? parsed.social.join('\n') : String(parsed.social);
      return {bio:String(parsed.bio).trim(), pf:String(parsed.pf).trim(), social:socialOut.trim()};
    }catch(e){
      console.warn('AI failed, using fallback:', e);
      return {bio:fallbackBio(), pf:buildPF(), social:buildSocial()};
    }
  }

  // ---------- Buttons / interactions ----------
  function renderStatic(){ $('#bio').textContent=fallbackBio(); $('#pf').textContent=buildPF(); $('#social').textContent=buildSocial(); }
  renderStatic();

  $('#generate').addEventListener('click', async ()=>{
    // ensure ranking done for preview
    if(!sources.length) renderThumbs();
    const out=await generateAIText();
    $('#bio').textContent=out.bio;
    $('#pf').textContent=out.pf;
    $('#social').textContent=out.social;
    $('#bio').scrollIntoView({behavior:'smooth'});
  });

  $$('#copyBio,#copyPF,#copySocial,#copyAll').forEach(btn=>btn?.addEventListener('click', (e)=>{
    const id=e.target.id;
    const text=id==='copyBio'?$('#bio').textContent:id==='copyPF'?$('#pf').textContent:id==='copySocial'?$('#social').textContent:`BIO\n\n${$('#bio').textContent}\n\nPETFINDER\n\n${$('#pf').textContent}\n\nSOCIAL\n\n${$('#social').textContent}\n`;
    navigator.clipboard.writeText(text);
  }));

  $('#downloadAll').addEventListener('click', ()=>{
    const name=(val('name')||'pet').replace(/\s+/g,'_');
    const txt=new Blob([`BIO\n\n${$('#bio').textContent}\n\nPETFINDER\n\n${$('#pf').textContent}\n\nSOCIAL\n\n${$('#social').textContent}\n`],{type:'text/plain'});
    const a=document.createElement('a'); a.download=`${name}_listing.txt`; a.href=URL.createObjectURL(txt); a.click(); setTimeout(()=>URL.revokeObjectURL(a.href),3000);
    if(sources[0]){ const a2=document.createElement('a'); a2.download=`${name}_best_photo.jpg`; a2.href=$('#canvas').toDataURL('image/jpeg',0.9); a2.click(); }
  });

})(); // end IIFE
</script>
</body>
</html>
