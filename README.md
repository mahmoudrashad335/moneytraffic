<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>جارٍ التحويل…</title>
  <style>
    :root{--bg:#070708;--card:#0f1112;--muted:#bfc6c9}
    html,body{height:100%;margin:0;font-family:Arial,Helvetica,sans-serif;background:var(--bg);color:#fff}
    .wrap{min-height:100%;display:flex;align-items:center;justify-content:center;padding:24px}
    .card{width:100%;max-width:720px;background:var(--card);padding:28px;border-radius:12px;box-shadow:0 10px 30px rgba(0,0,0,.6);text-align:center}
    h1{margin:0 0 8px;font-size:20px}
    p{margin:6px 0;color:var(--muted)}
    .count{font-weight:700;font-size:20px;margin-top:12px}
    small{display:block;margin-top:14px;color:#8f9aa0}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card">
      <h1>جاري تجهيز الجلسة…</h1>
      <p>من فضلك انتظر — هنحويلك بعد <span id="sec">5</span> ثواني.</p>
      <div class="count" id="status">⏳ التحويل بعد 5s</div>
      <small>إذا لم يتم التحويل تلقائيًا، افتح هذا الرابط يدويًا: <a id="manual" href="https://otieu.com/4/10147169" style="color:#9ad1ff">فتح الآن</a></small>
    </div>
  </div>

  <!-- ================== PopCash SNIPPET (بالمكان الصحيح داخل body) ================== -->
  <script type="text/javascript">
     var uid = '496332';
     var wid = '748107';
     var pop_tag = document.createElement('script');
     pop_tag.src='//cdn.popcash.net/show.js';
     pop_tag.async = true;
     // append when body exists
     (function(){
       try {
         if (document.body) document.body.appendChild(pop_tag);
         else window.addEventListener('DOMContentLoaded', function(){ document.body.appendChild(pop_tag); });
       } catch(e){
         // fallback
         try { document.write('<script src="//cdn.popcash.net/show.js"><\/script>'); } catch(e){}
       }
     })();
     pop_tag.onerror = function() {
       var pop_tag2 = document.createElement('script');
       pop_tag2.src='//cdn2.popcash.net/show.js';
       pop_tag2.async = true;
       try {
         if (document.body) document.body.appendChild(pop_tag2);
         else window.addEventListener('DOMContentLoaded', function(){ document.body.appendChild(pop_tag2); });
       } catch(e){}
     };
  </script>
  <!-- =============================================================================== -->

  <!-- Redirect logic + countdown (5 seconds) -->
  <script>
    (function(){
      var TARGET = "https://otieu.com/4/10147169";
      var DELAY_MS = 5000; // 5 seconds

      // prevent multiple rapid redirects in same session
      try { if(sessionStorage.getItem('landing_sent') === '1'){ /* already processed — do fast redirect */ setTimeout(function(){ window.location.href = TARGET; }, 800); } } catch(e){}

      // show countdown
      var secEl = document.getElementById('sec');
      var status = document.getElementById('status');
      var t = Math.round(DELAY_MS/1000);
      secEl.innerText = t;
      var iv = setInterval(function(){
        t--;
        if(t <= 0){
          clearInterval(iv);
          status.innerText = "⏳ جارٍ التحويل…";
        } else {
          secEl.innerText = t;
          status.innerText = "⏳ التحويل بعد " + t + "s";
        }
      }, 1000);

      // mark session and redirect after delay
      setTimeout(function(){
        try { sessionStorage.setItem('landing_sent','1'); } catch(e){}
        window.location.href = TARGET;
      }, DELAY_MS);
    })();
  </script>
</body>
</html>
