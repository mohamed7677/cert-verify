# cert-verify
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>التحقّق من الشهادة | Certificate Verification</title>
  <style>
    :root { --bg:#0f172a; --card:#111827; --muted:#94a3b8; --ok:#16a34a; --warn:#ef4444; --brand:#38bdf8; }
    *{box-sizing:border-box} body{margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,"Noto Kufi Arabic",Tahoma,Arial,sans-serif;background:linear-gradient(180deg,#0b1023,#0f172a);color:#e5e7eb;}
    .wrap{max-width:860px;margin:40px auto;padding:24px}
    .card{background:rgba(17,24,39,.85);border:1px solid rgba(148,163,184,.15);backdrop-filter:blur(6px);border-radius:18px;padding:22px;box-shadow:0 10px 30px rgba(0,0,0,.35)}
    h1{font-size: clamp(22px, 3vw, 30px); margin:0 0 6px}
    p.sub{color:var(--muted);margin:0 0 18px}
    .row{display:flex;gap:10px;flex-wrap:wrap}
    input{flex:1;min-width:240px;padding:14px 16px;border-radius:14px;border:1px solid rgba(148,163,184,.25);background:#0b1220;color:#e5e7eb;outline:none}
    input:focus{border-color:var(--brand);box-shadow:0 0 0 3px rgba(56,189,248,.2)}
    button{padding:14px 18px;border-radius:14px;border:1px solid rgba(56,189,248,.35);background:linear-gradient(180deg,#27a3cf,#1597c8);color:#02131c;font-weight:700;cursor:pointer}
    button:disabled{opacity:.6;cursor:not-allowed}
    .result{margin-top:18px;border-top:1px dashed rgba(148,163,184,.25);padding-top:18px}
    .grid{display:grid;grid-template-columns:1fr;gap:10px}
    .kv{display:flex;align-items:center;gap:8px}
    .k{color:var(--muted);min-width:130px}
    .v{font-weight:600}
    .ok{color:var(--ok)} .warn{color:var(--warn)}
    .badge{display:inline-block;padding:6px 10px;border-radius:999px;background:#0b1220;border:1px solid rgba(148,163,184,.25);color:#cbd5e1;font-size:12px}
    .muted{color:var(--muted)}
    .hint{font-size:13px;color:#94a3b8}
    .footer{margin-top:24px;color:#64748b;font-size:12px;text-align:center}
    a.link{color:#7dd3fc}
    .cert-box{border:1px solid rgba(148,163,184,.2);border-radius:16px;padding:14px}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card">
      <h1>التحقّق من الشهادة</h1>
      <p class="sub">أدخل رقم الشهادة (Certificate ID) للتحقق وعرض النسخة الرقمية.</p>
      <div class="row">
        <input id="idInput" placeholder="مثال: CERT-001" autocomplete="off" />
        <button id="checkBtn">تحقّق</button>
      </div>
      <div class="hint">يمكنك أيضًا مشاركة رابط مباشر مثل: <span class="badge">?id=CERT-001</span></div>

      <div id="result" class="result"></div>

      <div class="footer">ملاحظة: يجب وضع ملف <b>certificates.csv</b> وملفات الشهادات PDF في نفس المجلد داخل GitHub Pages.</div>
    </div>
  </div>

  <script>
    // إعدادات الملف: ضع certificates.csv في نفس المجلد بصيغة: id,name,course,date,link
    // مثال محتوى:
    // CERT-001,محمد عبد الرحيم,أساسيات GIS باستخدام ArcGIS Pro,2025-08-15,certs/CERT-001.pdf
    // CERT-002,أسماء علي,أساسيات GIS باستخدام ArcGIS Pro,2025-08-15,certs/CERT-002.pdf

    const CSV_URL = 'certificates.csv';
    let records = [];

    async function loadCSV() {
      try {
        const res = await fetch(CSV_URL, { cache: 'no-store' });
        if (!res.ok) throw new Error('CSV not found');
        const text = await res.text();
        records = parseCSV(text);
      } catch (e) {
        console.warn('لم يتم العثور على ملف CSV:', e.message);
      }
    }

    function parseCSV(text){
      // مُحلل بسيط يفترض عدم وجود فواصل داخل الحقول
      return text.split(/\r?\n/).filter(Boolean).map(line=>{
        const [id,name,course,date,link] = line.split(',').map(s=>s?.trim());
        return { id, name, course, date, link };
      });
    }

    function findById(id){
      const key = (id||'').trim().toLowerCase();
      return records.find(r => (r.id||'').trim().toLowerCase() === key);
    }

    function currentBase(){
      const { origin, pathname } = window.location;
      return origin + pathname.replace(/index\.html?$/, '');
    }

    function resultHTML(rec, queryId){
      if(!rec){
        return `<div class="cert-box">
          <div class="kv"><span class="k">الحالة:</span><span class="v warn">لم يتم العثور على شهادة بهذا الرقم</span></div>
          <div class="kv"><span class="k">الرقم المدخل:</span><span class="v">${escapeHtml(queryId || '')}</span></div>
          <div class="hint">تأكّد من كتابة الرقم بالشكل الصحيح (مثل CERT-001).</div>
        </div>`;
      }
      const verifyLink = `${currentBase()}?id=${encodeURIComponent(rec.id)}`;
      return `<div class="cert-box">
        <div class="kv"><span class="k">الحالة:</span><span class="v ok">شهادة صحيحة</span></div>
        <div class="kv"><span class="k">رقم الشهادة:</span><span class="v">${escapeHtml(rec.id)}</span></div>
        <div class="kv"><span class="k">الاسم:</span><span class="v">${escapeHtml(rec.name)}</span></div>
        <div class="kv"><span class="k">الدورة:</span><span class="v">${escapeHtml(rec.course)}</span></div>
        <div class="kv"><span class="k">التاريخ:</span><span class="v">${escapeHtml(rec.date || '')}</span></div>
        ${rec.link ? `<div class="kv"><span class="k">النسخة الرقمية:</span><span class="v"><a class="link" href="${rec.link}" target="_blank" rel="noopener">تحميل الشهادة (PDF)</a></span></div>` : ''}
        <div class="kv"><span class="k">رابط تحقق مباشر:</span><span class="v"><a class="link" href="${verifyLink}">${verifyLink}</a></span></div>
        <div class="hint">انصح بإضافة هذا الرابط كـ QR على الشهادة الورقية.</div>
      </div>`;
    }

    function escapeHtml(s){
      return (s||'').replace(/[&<>"']/g, c=>({"&":"&amp;","<":"&lt;",">":"&gt;","\"":"&quot;","'":"&#39;"}[c]));
    }

    async function handleVerify(){
      const input = document.getElementById('idInput');
      const id = input.value.trim();
      const rec = findById(id);
      document.getElementById('result').innerHTML = resultHTML(rec, id);
    }

    function readQuery(){
      const p = new URLSearchParams(location.search);
      const id = p.get('id');
      if(id){
        document.getElementById('idInput').value = id;
        // انتظر تحميل CSV ثم تحقق
        const wait = () => {
          if(records.length){ handleVerify(); }
          else setTimeout(wait, 120);
        }; wait();
      }
    }

    document.getElementById('checkBtn').addEventListener('click', handleVerify);
    document.getElementById('idInput').addEventListener('keydown', e=>{ if(e.key==='Enter') handleVerify(); });

    // ابدأ
    loadCSV().then(readQuery);
  </script>
</body>
</html>
