<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>وردل عربي</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #121213;
    --surface: #1a1a1b;
    --surface-2: #232325;
    --text: #ffffff;
    --muted: #a1a1a3;
    --border: #3a3a3c;
    --border-filled: #565758;
    --correct: #538d4e;
    --present: #b59f3b;
    --absent: #3a3a3c;
    --key-bg: #818384;
    --key-text: #ffffff;
    --accent: #538d4e;
    --gold: #ffd86b;
    --silver: #c8c8c8;
    --bronze: #d59060;
  }

  html, body {
    height: 100%;
    background: var(--bg);
    color: var(--text);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Tahoma",
                 "Geeza Pro", "Damascus", "Al Bayan", system-ui, sans-serif;
    overflow: hidden;
    -webkit-tap-highlight-color: transparent;
  }

  body { display: flex; flex-direction: column; align-items: center; height: 100vh; height: 100dvh; }

  header {
    width: 100%; padding: 10px 12px; border-bottom: 1px solid var(--border);
    display: flex; align-items: center; justify-content: space-between; gap: 8px; flex-shrink: 0;
  }

  h1 { font-size: clamp(20px, 4.5vw, 28px); font-weight: 800; letter-spacing: 1px; flex: 1; text-align: center; }

  .header-actions { display: flex; gap: 6px; }

  .icon-btn {
    background: transparent; border: 1px solid var(--border-filled); color: var(--text);
    width: 38px; height: 38px; border-radius: 8px; cursor: pointer; font-size: 18px;
    display: flex; align-items: center; justify-content: center;
    transition: background 0.2s, border-color 0.2s; flex-shrink: 0;
  }
  .icon-btn:hover { background: rgba(255,255,255,0.08); border-color: var(--accent); }
  .icon-btn:active { transform: scale(0.94); }

  .name-pill {
    background: transparent; border: 1px solid var(--border-filled); color: var(--text);
    height: 38px; border-radius: 8px; padding: 0 12px; font-family: inherit; font-size: 13px;
    font-weight: 600; cursor: pointer; max-width: 130px; overflow: hidden;
    text-overflow: ellipsis; white-space: nowrap;
    transition: background 0.2s, border-color 0.2s; flex-shrink: 0;
  }
  .name-pill:hover { background: rgba(255,255,255,0.08); border-color: var(--accent); }

  main {
    flex: 1; width: 100%; max-width: 560px; display: flex; flex-direction: column;
    align-items: center; justify-content: space-between; padding: 6px;
    overflow: hidden; min-height: 0;
  }

  .info-bar { 
    width: 100%; text-align: center; color: var(--muted); font-size: 13px; 
    padding: 6px 0; flex-shrink: 0; display: flex; justify-content: center; align-items: center; gap: 10px;
  }
  .info-bar strong { color: var(--text); }
  
  .timer-badge {
    background: rgba(255,255,255,0.1); padding: 3px 10px; border-radius: 6px;
    font-weight: bold; color: var(--gold); direction: ltr; display: inline-block;
    font-variant-numeric: tabular-nums;
  }

  .board-wrap { 
    display: flex; align-items: center; justify-content: center; 
    flex: 1; width: 100%; padding: 6px 10px; min-height: 0; overflow: hidden;
  }

  .board {
    display: grid; grid-template-rows: repeat(6, 1fr); gap: 5px;
    width: 100%; max-width: 330px; aspect-ratio: 5 / 6;
    max-height: 100%; margin: 0 auto;
  }

  .row { display: grid; grid-template-columns: repeat(5, 1fr); gap: 5px; direction: rtl; }

  .tile {
    border: 2px solid var(--border); display: flex; align-items: center; justify-content: center;
    font-size: clamp(22px, 6.5vw, 32px); font-weight: 800; line-height: 1;
    user-select: none; transition: border-color 0.1s;
  }
  .tile.filled { border-color: var(--border-filled); animation: pop 0.12s ease; }
  .tile.flip { animation: flip 0.6s ease forwards; }
  .tile.correct { background: var(--correct); border-color: var(--correct); color: #fff; }
  .tile.present { background: var(--present); border-color: var(--present); color: #fff; }
  .tile.absent  { background: var(--absent);  border-color: var(--absent);  color: #fff; }

  .row.shake { animation: shake 0.45s ease; }
  .row.win .tile { animation: bounce 0.55s ease; }
  .row.win .tile:nth-child(1) { animation-delay: 0.0s; }
  .row.win .tile:nth-child(2) { animation-delay: 0.1s; }
  .row.win .tile:nth-child(3) { animation-delay: 0.2s; }
  .row.win .tile:nth-child(4) { animation-delay: 0.3s; }
  .row.win .tile:nth-child(5) { animation-delay: 0.4s; }

  @keyframes pop { 0% { transform: scale(0.85); } 60% { transform: scale(1.08); } 100% { transform: scale(1); } }
  @keyframes flip { 0% { transform: rotateX(0); } 50% { transform: rotateX(-90deg); } 100% { transform: rotateX(0); } }
  @keyframes shake { 0%,100% { transform: translateX(0); } 20%,60% { transform: translateX(-8px); } 40%,80% { transform: translateX(8px); } }
  @keyframes bounce { 0%,100% { transform: translateY(0); } 40% { transform: translateY(-18px); } 70% { transform: translateY(-4px); } }

  .keyboard { width: 100%; max-width: 560px; padding: 6px 4px 10px; direction: rtl; flex-shrink: 0; }
  .keyboard-row { display: flex; justify-content: center; gap: 4px; margin-bottom: 6px; }
  .keyboard-row:last-child { margin-bottom: 0; }

  .key {
    flex: 1; min-width: 0; height: 50px; border: none; border-radius: 6px;
    background: var(--key-bg); color: var(--key-text); font-family: inherit;
    font-size: clamp(14px, 3.8vw, 18px); font-weight: 700; cursor: pointer; user-select: none;
    transition: background 0.25s, transform 0.05s, opacity 0.1s;
  }
  .key:hover { opacity: 0.88; }
  .key:active { transform: scale(0.92); }
  .key.wide { flex: 1.7; font-size: clamp(11px, 3vw, 14px); }
  .key.correct { background: var(--correct); }
  .key.present { background: var(--present); }
  .key.absent  { background: var(--absent); color: #d7dadc; }

  .toast-container {
    position: fixed; top: 70px; left: 50%; transform: translateX(-50%);
    z-index: 300; display: flex; flex-direction: column; gap: 8px; pointer-events: none;
  }
  .toast {
    background: #ffffff; color: #000000; padding: 12px 22px; border-radius: 6px;
    font-weight: 700; font-size: 14px; animation: toastIn 0.2s ease;
    box-shadow: 0 6px 18px rgba(0,0,0,0.4); white-space: nowrap;
  }
  .toast.fade { animation: toastOut 0.45s ease forwards; }
  @keyframes toastIn  { from { opacity: 0; transform: translateY(-12px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes toastOut { from { opacity: 1; } to { opacity: 0; transform: translateY(-6px); } }

  .modal-overlay {
    position: fixed; inset: 0; background: rgba(0,0,0,0.78);
    display: none; align-items: center; justify-content: center;
    z-index: 200; padding: 16px; backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px); overflow-y: auto;
  }
  .modal-overlay.show { display: flex; animation: fadeIn 0.25s ease; }

  .modal {
    background: var(--surface); border: 1px solid var(--border-filled); border-radius: 14px;
    padding: 26px 22px 22px; max-width: 380px; width: 100%; text-align: center;
    animation: scaleIn 0.3s ease; max-height: calc(100vh - 32px); overflow-y: auto;
  }
  .modal h2 { font-size: 24px; margin-bottom: 8px; font-weight: 800; }
  .modal p  { margin-bottom: 6px; font-size: 14px; color: var(--muted); }

  .modal .word { font-size: 30px; font-weight: 800; color: var(--correct); margin: 14px 0 0px; letter-spacing: 2px; }
  .modal .word.lose { color: var(--present); }
  .modal .meaning { font-size: 14px; color: var(--gold); margin-bottom: 14px; font-weight: 600; }

  .stats { display: flex; justify-content: center; gap: 18px; margin: 14px 0 4px; font-size: 14px; color: var(--muted); }
  .stats strong { color: var(--text); font-weight: 700; }

  .stats-container { display: flex; justify-content: space-around; margin-top: 15px; margin-bottom: 20px; }
  .stat-box { display: flex; flex-direction: column; align-items: center; }
  .stat-num { font-size: 24px; font-weight: 800; color: var(--text); }
  .stat-label { font-size: 11px; color: var(--muted); text-align: center; }
  
  .dist-container { width: 100%; padding: 10px 0; }
  .dist-row { display: flex; align-items: center; margin-bottom: 4px; font-size: 12px; font-weight: bold; }
  .dist-label { width: 15px; text-align: left; margin-left: 5px; color: var(--text); }
  .dist-bar-bg { flex: 1; background: var(--surface-2); border-radius: 3px; display: flex; justify-content: flex-start; }
  .dist-bar { background: var(--absent); color: white; text-align: right; padding-right: 5px; border-radius: 3px; min-width: 15px; transition: width 0.5s ease; }
  .dist-bar.highlight { background: var(--correct); }

  .modal-btn {
    margin-top: 16px; background: var(--correct); color: #fff; border: none;
    padding: 12px 32px; border-radius: 8px; cursor: pointer; font-family: inherit;
    font-size: 15px; font-weight: 700; transition: opacity 0.2s, transform 0.08s; width: 100%;
  }
  .modal-btn:hover { opacity: 0.92; }
  .modal-btn:active { transform: scale(0.97); }
  .modal-btn.secondary { background: transparent; border: 1px solid var(--border-filled); margin-top: 8px; }
  .modal-btn.secondary:hover { background: rgba(255,255,255,0.06); }
  .modal-btn:disabled { opacity: 0.5; cursor: not-allowed; }

  .name-input {
    width: 100%; background: var(--surface-2); border: 1px solid var(--border-filled);
    color: var(--text); padding: 13px 14px; border-radius: 8px; font-family: inherit;
    font-size: 16px; font-weight: 600; text-align: center; margin: 14px 0 4px;
    direction: rtl; outline: none; transition: border-color 0.2s;
  }
  .name-input:focus { border-color: var(--accent); }
  .name-input::placeholder { color: var(--muted); font-weight: 400; }

  .lb-section { margin-top: 18px; padding-top: 16px; border-top: 1px solid var(--border); }
  .lb-section h3 { font-size: 15px; margin-bottom: 10px; font-weight: 700; color: var(--muted); }

  .lb-list { text-align: right; max-height: 240px; overflow-y: auto; }
  .lb-row {
    display: grid; grid-template-columns: 28px 1fr auto; align-items: center;
    gap: 8px; padding: 8px 10px; background: var(--surface-2); border-radius: 6px;
    margin-bottom: 4px; font-size: 13px;
  }
  .lb-row.me { background: rgba(83, 141, 78, 0.18); border: 1px solid var(--correct); }
  .lb-rank { font-weight: 800; text-align: center; color: var(--muted); }
  .lb-row:nth-child(1) .lb-rank { color: var(--gold); font-size: 16px; }
  .lb-row:nth-child(2) .lb-rank { color: var(--silver); font-size: 15px; }
  .lb-row:nth-child(3) .lb-rank { color: var(--bronze); font-size: 15px; }
  .lb-name { font-weight: 700; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
  .lb-meta { color: var(--muted); font-size: 12px; font-weight: 600; text-align: left; direction: ltr; font-variant-numeric: tabular-nums; }
  .lb-meta .res-win { color: #6dbf66; }
  .lb-meta .res-loss { color: #c46a6a; }

  .empty-lb { text-align: center; color: var(--muted); padding: 18px 0; font-size: 13px; }
  .lb-date { font-size: 12px; color: var(--muted); margin-bottom: 8px; font-variant-numeric: tabular-nums; direction: ltr; }

  @keyframes fadeIn  { from { opacity: 0; } to { opacity: 1; } }
  @keyframes scaleIn { from { opacity: 0; transform: scale(0.92); } to { opacity: 1; transform: scale(1); } }

  /* Media Queries for shorter/smaller screens */
  @media (max-width: 380px) {
    .key { height: 44px; font-size: 14px; }
    .key.wide { font-size: 11px; }
    h1 { font-size: 20px; }
    .icon-btn { width: 34px; height: 34px; font-size: 16px; }
    .name-pill { height: 34px; font-size: 12px; padding: 0 10px; max-width: 110px; }
  }

  @media (max-height: 680px) {
    .key { height: 42px; font-size: 14px; }
    .board { max-width: 280px; gap: 4px; }
    .row { gap: 4px; }
  }

  @media (max-height: 600px) {
    header { padding: 6px 12px; }
    h1 { font-size: 18px; }
    .info-bar { padding: 4px 0; }
    .key { height: 38px; font-size: 13px; }
    .board { max-width: 240px; gap: 3px; }
    .row { gap: 3px; }
    .icon-btn, .name-pill { height: 32px; }
  }
</style>
</head>
<body>
  <header>
    <div class="header-actions">
      <button class="icon-btn" id="lbBtn" title="لوحة المتصدرين">🏆</button>
      <button class="icon-btn" id="statsBtn" title="الإحصائيات">📊</button>
    </div>
    <h1>وردل عربي</h1>
    <button class="name-pill" id="namePill" title="تغيير الاسم">—</button>
  </header>

  <main>
    <div class="info-bar" id="infoBar">
      <span id="infoDateStr">لغز اليوم</span>
      <span class="timer-badge">التالي: <span id="mainTimer">00:00:00</span></span>
    </div>
    <div class="board-wrap"><div class="board" id="board"></div></div>
    <div class="keyboard" id="keyboard"></div>
  </main>

  <div class="toast-container" id="toastContainer"></div>

  <div class="modal-overlay show" id="nameModal">
    <div class="modal">
      <h2>وردل عربي</h2>
      <p>اكتب اسمك للظهور في لوحة المتصدرين</p>
      <input type="text" class="name-input" id="nameInput" maxlength="20" placeholder="اسم اللاعب" autocomplete="off">
      <button class="modal-btn" id="startBtn">ابدأ اللعب</button>
    </div>
  </div>

  <div class="modal-overlay" id="endModal">
    <div class="modal">
      <h2 id="endTitle"></h2>
      <p id="endText"></p>
      <div class="word" id="endWord"></div>
      <div class="meaning" id="endMeaning"></div>
      
      <div class="stats">
        <span>المحاولات: <strong id="endAttempts"></strong></span>
        <span>الوقت: <strong id="endTime"></strong></span>
      </div>
      <div class="lb-section">
        <h3>🏆 لوحة المتصدرين اليوم</h3>
        <div class="lb-date" id="endLbDate"></div>
        <div class="lb-list" id="endLbList"></div>
      </div>
      <button class="modal-btn secondary" id="closeEndBtn">إغلاق</button>
    </div>
  </div>

  <div class="modal-overlay" id="statsModal">
    <div class="modal">
      <h2>📊 إحصائياتك</h2>
      <div class="stats-container">
        <div class="stat-box"><span class="stat-num" id="statPlayed">0</span><span class="stat-label">لعب</span></div>
        <div class="stat-box"><span class="stat-num" id="statWinPct">0</span><span class="stat-label">% فوز</span></div>
        <div class="stat-box"><span class="stat-num" id="statStreak">0</span><span class="stat-label">سلسلة<br>الحالية</span></div>
        <div class="stat-box"><span class="stat-num" id="statMaxStreak">0</span><span class="stat-label">أقصى<br>سلسلة</span></div>
      </div>
      <div class="lb-section">
        <h3>توزيع المحاولات</h3>
        <div class="dist-container" id="distContainer"></div>
      </div>
      <button class="modal-btn secondary" id="closeStatsBtn">إغلاق</button>
    </div>
  </div>

  <div class="modal-overlay" id="lbModal">
    <div class="modal">
      <h2>🏆 لوحة المتصدرين</h2>
      <p>لغز اليوم</p>
      <div class="lb-date" id="lbDate"></div>
      <div class="lb-list" id="lbList"></div>
      <button class="modal-btn secondary" id="closeLbBtn">إغلاق</button>
    </div>
  </div>

<script>
  // ===== Top 500+ Solution words =====
  const WORDS = [
    'مدرسة','مكتبة','سيارة','طاولة','نافذة','دراجة','زجاجة','حقيبة','خزانة','نظارة',
    'مصباح','ملعقة','منشار','مسمار','تفاحة','زرافة','مدينة','حديقة','بحيرة','جزيرة',
    'بطاقة','ثلاجة','سفينة','صحيفة','فستان','قاموس','قبيلة','منديل','وسادة','ميدان',
    'مفتاح','بستان','ستارة','سجادة','بنطال','كنيسة','مذكرة','مزرعة','مصيدة','مكتوب',
    'حمامة','عصفور','فراشة','زيتون','وثيقة','وسيلة','مسطرة','هواية','هندسة','حضارة',
    'سحابة','سفارة','مهارة','منطقة','منظمة','نهاية','وزارة','مدارس','دفاتر','جوارب',
    'عربات','عناصر','فنانة','مكاتب','مقاعد','مناطق','متاجر','متاحف','مصانع','نوافذ',
    'طبيبة','مهندس','معلمة','جامعة','رسالة','جريدة','قصيدة','حبيبة','مساعد','مدافع',
    'مغامر','مقاتل','عروسة','حكاية','جريمة','عاصمة','ساعات','دقيقة','ثانية','ثلاثة',
    'مليون','مليار','يومية','جميلة','بسيطة','خفيفة','جديدة','قصيرة','طويلة','صغيرة',
    'كبيرة','لطيفة','قديمة','بعيدة','قريبة','سريعة','نظيفة','صحيحة','فقيرة','مرتاح',
    'رمادي','مثالي','متعدد','متنوع','متوسط','مثيرة','محمول','مرفوع','مزدحم','مستمر',
    'معروف','معلوم','مفقود','مكسور','موجود','موضوع','منشور','دجاجة','بطيخة','ثعبان',
    'طماطم','بطاطس','فاكهة','عربية','سعادة','عدالة','عبارة','عمارة','عملية','مشاعر',
    'مشاكل','مشروع','مشترك','نتيجة','نظافة','صداقة','فقاعة','قاعدة','كتابة','شريحة',
    'خياطة','رياضة','شجرات','ملابس','مرايا','نشرات','مبارك','نافعة','أسبوع','إجابة',
    'تاريخ','تجربة','تعاون','تفكير','ثقافة','جنازة','حكومة','حقيقة','خريطة','دكتور',
    'سياسة','طبيعة','طريقة','علاقة','فائدة','قانون','قيادة','كرامة','مرحلة','مسافة',
    'مشكلة','نصيحة','وظيفة','ياقوت','برامج','تذاكر','حقائب','دوافع','روابط','شبكات',
    'طوابع','عجائب','قواعد','كواكب','مبادئ','مخاطر','مراحل','مصادر','مطاعم','مقاطع',
    'ملاعب','مناهج','مواقف','نتائج','نماذج','هواتف','وثائق','أحلام','أخطاء','أرقام',
    'أسرار','أسلحة','أشجار','أصوات','أطفال','أفكار','أفلام','أقلام','ألوان','أموال',
    'أنواع','أهداف','أوراق','إنسان','إسلام','إيمان','إحسان','أستاذ','أخلاق','أسباب',
    'أعمال','أقوال','أفعال','أنباء','أسواق','أسماء','أطباء','أعضاء','أصدقاء','أشياء',
    'أجزاء','أحياء','أرجاء','أنحاء','أضواء','أسماك','أقمار','أبطال','أعماق','أشعار',
    'إبداع','إثبات','إجازة','إجماع','إحساس','إحباط','إدارة','إرادة','إشارة','إصابة',
    'إضافة','إضاءة','إطالة','إعادة','إعاقة','إعلان','إغاثة','إفادة','إقامة','إقناع',
    'إلهام','إمارة','إنتاج','إنذار','إنقاذ','إنهاء','إهانة','إيقاع','ابتسم','ابنته',
    'ابنها','اجتما','اختفى','ادعاء','ارتدى','استمر','اعتبر','اعتماد','اكتشف','التزم',
    'التقى','امتلك','انتظر','انتهى','بائعة','باحثة','بادرة','باردة','بارزة','باسمة',
    'باطنة','باقية','بالغة','باهظة','بترول','بطولة','بضائع','بطيئة','بكاءه','بكتري',
    'بلدان','بندقي','بنية','بوابة','بوصلة','بيانات','تأثير','تأجيل','تأكيد','تأليف',
    'تأمين','تبادل','تجاوز','تجديد','تجميع','تحالف','تحذير','تحرير','تحسين','تحصيل',
    'تحطيم','تحقيق','تحكمه','تحليل','تخفيف','تخطيط','تدخلت','تدمير','تراجع','تراكم',
    'تراجع','تراكم','تربية','ترجمة','ترشيح','تركيب','تزويد','تسامح','تسجيل','تسليم',
    'تسمية','تسويه','تشجيع','تشغيل','تشكيل','تصرفا','تصريح','تصميم','تصوير','تطبيق',
    'تطوير','تعبير','تعديل','تعزيز','تعليم','تغذية','تغيير','تفتيش','تفسير','تفضيل',
    'تقارب','تقاليد','تقديم','تقدير','تقسيم','تقليص','تقليل','تكاليف','تكنولوجيا','تكوين',
    'تلميذ','تمثيل','تمديد','تمويل','تنمية','تهديد','توزيع','توسيع','توضيح','توقيع',
    'توقيف','توليد','جائزة','جائعة','جاذبة','جاسوس','جاهزة','جبابرة','جدارن','جداول',
    'جدران','جراحة','جرائم','جزئية','جزيئا','جليدة','جماعة','جماجم','جمارك','جماليات',
    'جماهي','جنائن','جنايات','جنرال','جواهر','جودة','جيوشه','حاسبة','حاسوب','حافظة',
    'حافلة','حاكمة','حاملة','حاويات','حاوي','حبيبي','حجارة','حجرات','حرارة','حراسة',
    'حرمان','حريته','حريصة','حزينة','حسابا','حسناء','حشائش','حصانة','حضانة','حصيلة',
    'حقائق','حقوله','حكايات','حكماء','حلقات','حماية','حملات','حماقة','حمراء','حميمة',
    'حنجرة','حواشي','حوالى','حيوية','خادمة','خارطة','خاصية','خالصة','خالقة','خالية',
    'خامات','خامسة','خبراء','خبيثة','خدائع','خدمات','خرائب','خسائر','خسارة','خشونة',
    'خصائص','خصومة','خطابات','خطايا','خطوات','خطورة','خطيئة','خطيرة','خلايا','خلاصة',
    'خلافة','خليفة','خليلة','خمرية','خنازير','خناجر','خواتم','خيالة','خيام','خيارات',
    'دائرة','داكنة','دائمة','دافع','داكنة','دالته','دامية','دبلوماسي','دخول','درجات',
    'دروع','دعائم','دعاوى','دعوات','دعائم','دعاية','دعوات','دعائم','دقائق','دوافع'
  ];

  const EXTRA_GUESSES = [
    'كلمات','جمالة','رحلات','حروفي','بطاقي','ميتلر','حركات','منزلي','ولدنا',
    'كتبتم','شربتم','مرافق','مواعد','وحدها','جبهات','عقلية','رحبات','صفوفي',
    'سهلات','نشيطة','حقائق','صفحات','نوعية','مقارن','محبوب','محسوب','مدفوع','منفعة',
    'حاضرة','هابطة','حادثة','حالات','منازل','قافلة','سواحل','مساحة','منكسر',
    'فاتحة','رابعة','سادسة','عاشرة','ربيعة','نسائم','شهيرة','وفيرة','جزائر','قصائد',
    'منابر','مذابح','مكامن','مساند','معابر','مخارج','مدافن','مظاهر','مواعظ','مواقع',
    'مواهب','مياسر','نوادي','نواقص','نواهض','يبدأن','ينتظر','يجلسن','يدرسن','يلعبن',
    'يكتبن','يشربن','يفكرن','نشتري','نلعبون','يلعبون','يكتبون','دارسة','عاكفة','واصلة',
    'شامخة','سامية','زاهية','ساطعة','صامدة','نازحة','منتصر','منتظم','مهتز','محسود',
    'مرهف','معتدل','مفترش','مقرر','مكلف','ملتزم','شربنا','لعبنا','ذهبنا','بنينا',
    'مشينا','وجبات','فواتر','مشارع','كتبنا','يعملن','يأكلن','ينامون','يجلسون','يعملون'
  ];

  const WORD_MEANINGS = {
    'مدرسة': 'مكان يتلقى فيه الطلاب العلم والمعرفة',
    'مكتبة': 'مكان لجمع وحفظ الكتب وتسهيل قراءتها',
    'هندسة': 'تطبيق المعارف العلمية في تصميم البناء والآلات',
    'حضارة': 'مرحلة متقدمة من التطور الإنساني والثقافي',
    'جامعة': 'مؤسسة للتعليم العالي والبحث العلمي',
    'حديقة': 'مساحة مزروعة بالنباتات والأزهار للزينة أو الاستجمام',
    'قاموس': 'كتاب يضم مفردات اللغة ومعانيها',
    'مفتاح': 'أداة لفتح الأقفال أو تشغيل الآلات',
    'رسالة': 'نص مكتوب يُرسل من شخص لآخر للتواصل',
    'جزيرة': 'قطعة من اليابسة تحيط بها المياه من جميع الجهات',
    'سفينة': 'مركبة مائية كبيرة تستخدم للنقل في البحار',
    'عاصمة': 'المدينة الرئيسية في الدولة ومقر حكومتها',
    'تاريخ': 'دراسة الأحداث الماضية وتدوينها',
    'ثقافة': 'حصيلة التطور الفكري والفني والاجتماعي لمجتمع ما',
    'طبيعة': 'العالم المادي وما يضمه من ظواهر وكائنات',
    'وظيفة': 'عمل أو منصب يتولاه الشخص',
    'إنسان': 'كائن حي عاقل مفكر',
    'قانون': 'مجموعة قواعد تنظم سلوك الأفراد في المجتمع',
    'مشروع': 'عمل أو خطة يتم تنفيذها لتحقيق هدف معين',
    'سعادة': 'شعور بالرضا والبهجة والارتياح',
    'صداقة': 'علاقة مودة وثقة متبادلة بين الأشخاص',
    'نظافة': 'التخلص من الأوساخ والحفاظ على الطهارة',
    'كتابة': 'تدوين الكلمات والأفكار بواسطة الحروف',
    'طبيبة': 'امرأة متخصصة في تشخيص وعلاج الأمراض',
    'مهندس': 'شخص متخصص في تخطيط وتصميم وبناء المشاريع',
    'إبداع': 'القدرة على ابتكار أشياء جديدة ومفيدة',
    'تعليم': 'عملية تيسير التعلم ونقل المعرفة والمبادئ',
    'تصميم': 'التخطيط المسبق لعمل أو لشيء سيتم تنفيذه',
    'حاسوب': 'جهاز إلكتروني قادر على معالجة البيانات',
    'إسلام': 'دين سماوي مبني على الاستسلام لله وتوحيده',
    'أستاذ': 'معلم ومرشد للطلاب في المدارس أو الجامعات',
    'تجربة': 'عملية اختبار واكتشاف للوصول إلى الحقيقة'
  };

  const VALID_GUESSES = new Set([...WORDS, ...EXTRA_GUESSES]);

  const KEYBOARD_LAYOUT = [
    ['ض','ص','ث','ق','ف','غ','ع','ه','خ','ح','ج','د'],
    ['ش','س','ي','ب','ل','ا','ت','ن','م','ك','ط'],
    ['ENTER','ذ','ر','ة','و','ز','ظ','BACK']
  ];

  const WORD_LENGTH = 5;
  const MAX_GUESSES = 6;
  const LB_KEY = 'arabicWordle_leaderboard_v1';
  const NAME_KEY = 'arabicWordle_playerName';
  const STATE_KEY = 'arabicWordle_gameState';
  const STATS_KEY = 'arabicWordle_personalStats';

  function getSaudiDateString() {
    const fmt = new Intl.DateTimeFormat('en-CA', {
      timeZone: 'Asia/Riyadh', year: 'numeric', month: '2-digit', day: '2-digit'
    });
    return fmt.format(new Date());
  }

  function getDailyWordIndex() {
    const dateStr = getSaudiDateString();
    const epoch = Date.UTC(2024, 0, 1);
    const today = Date.UTC(
      parseInt(dateStr.slice(0, 4), 10),
      parseInt(dateStr.slice(5, 7), 10) - 1,
      parseInt(dateStr.slice(8, 10), 10)
    );
    const days = Math.floor((today - epoch) / 86400000);
    return ((days % WORDS.length) + WORDS.length) % WORDS.length;
  }
  function getDailyWord() { return WORDS[getDailyWordIndex()]; }

  function loadLeaderboard() { try { const r = localStorage.getItem(LB_KEY); const a = r ? JSON.parse(r) : []; return Array.isArray(a) ? a : []; } catch { return []; } }
  function saveLeaderboard(arr) { try { localStorage.setItem(LB_KEY, JSON.stringify(arr)); } catch {} }
  function loadName() { try { return (localStorage.getItem(NAME_KEY) || '').trim(); } catch { return ''; } }
  function saveName(n) { try { localStorage.setItem(NAME_KEY, n); } catch {} }
  
  function loadStats() {
    try { 
      const r = localStorage.getItem(STATS_KEY); 
      return r ? JSON.parse(r) : { played: 0, won: 0, currentStreak: 0, maxStreak: 0, distribution: [0,0,0,0,0,0] };
    } catch { return { played: 0, won: 0, currentStreak: 0, maxStreak: 0, distribution: [0,0,0,0,0,0] }; }
  }
  function saveStats(stats) { try { localStorage.setItem(STATS_KEY, JSON.stringify(stats)); } catch {} }

  function loadGameState() {
    try { const r = localStorage.getItem(STATE_KEY); return r ? JSON.parse(r) : null; } catch { return null; }
  }
  function saveGameState(stateObj) { try { localStorage.setItem(STATE_KEY, JSON.stringify(stateObj)); } catch {} }

  function compareEntries(a, b) {
    if (a.won !== b.won) return a.won ? -1 : 1;
    if (a.won) { if (a.attempts !== b.attempts) return a.attempts - b.attempts; return a.timeMs - b.timeMs; }
    return a.timeMs - b.timeMs;
  }
  function addToLeaderboard(entry) {
    const all = loadLeaderboard();
    const idx = all.findIndex(e => e.date === entry.date && e.name === entry.name);
    if (idx >= 0) { if (compareEntries(entry, all[idx]) < 0) all[idx] = entry; }
    else { all.push(entry); }
    saveLeaderboard(all);
  }
  function getDailyEntries(date) { return loadLeaderboard().filter(e => e.date === date).sort(compareEntries); }

  function splitArabic(word) { return Array.from(word); }
  function normalizeChar(ch) {
    if (ch === 'أ' || ch === 'إ' || ch === 'آ') return 'ا';
    if (ch === 'ى') return 'ي';
    return ch;
  }
  function isArabicLetter(ch) {
    if (!ch || ch.length !== 1) return false;
    const code = ch.charCodeAt(0);
    return (code >= 0x0621 && code <= 0x064A) || ch === 'ة' || ch === 'ى';
  }
  function isOnKeyboard(ch) { for (const row of KEYBOARD_LAYOUT) if (row.includes(ch)) return true; return false; }
  function formatTime(ms) {
    const totalSec = Math.max(0, Math.floor(ms / 1000));
    const m = Math.floor(totalSec / 60); const s = totalSec % 60;
    return `${m}:${s.toString().padStart(2, '0')}`;
  }

  let playerName = '';
  let targetWord = '';
  let targetLetters = [];
  let currentGuess = [];
  let boardState = [];
  let currentRow = 0;
  let gameOver = false;
  let gameWon = false;
  let isAnimating = false;
  let keyStates = {};
  let startTime = 0;
  let puzzleDate = '';
  let timerInterval = null;

  function buildBoard() {
    const board = document.getElementById('board');
    board.innerHTML = '';
    for (let r = 0; r < MAX_GUESSES; r++) {
      const row = document.createElement('div');
      row.className = 'row'; row.id = `row-${r}`;
      for (let c = 0; c < WORD_LENGTH; c++) {
        const tile = document.createElement('div');
        tile.className = 'tile'; tile.id = `tile-${r}-${c}`;
        row.appendChild(tile);
      }
      board.appendChild(row);
    }
  }

  function buildKeyboard() {
    const keyboard = document.getElementById('keyboard');
    keyboard.innerHTML = '';
    KEYBOARD_LAYOUT.forEach(rowKeys => {
      const row = document.createElement('div');
      row.className = 'keyboard-row';
      rowKeys.forEach(key => {
        const btn = document.createElement('button');
        btn.className = 'key'; btn.type = 'button';
        if (key === 'ENTER') { btn.textContent = 'إدخال'; btn.classList.add('wide'); btn.dataset.key = 'ENTER'; }
        else if (key === 'BACK') { btn.textContent = 'حذف'; btn.classList.add('wide'); btn.dataset.key = 'BACK'; }
        else { btn.textContent = key; btn.dataset.key = key; btn.id = `key-${key}`; }
        btn.addEventListener('click', (e) => { e.preventDefault(); handleKey(btn.dataset.key); btn.blur(); });
        row.appendChild(btn);
      });
      keyboard.appendChild(row);
    });
  }

  function handleKey(key) {
    if (gameOver || isAnimating) return;
    if (key === 'ENTER') submitGuess();
    else if (key === 'BACK') { if (currentGuess.length > 0) { currentGuess.pop(); updateRow(); } }
    else if (isArabicLetter(key) && isOnKeyboard(key)) {
      if (currentGuess.length < WORD_LENGTH) { currentGuess.push(key); updateRow(); }
    }
  }

  function updateRow() {
    for (let c = 0; c < WORD_LENGTH; c++) {
      const tile = document.getElementById(`tile-${currentRow}-${c}`);
      const letter = currentGuess[c];
      if (letter) { if (tile.textContent !== letter) { tile.textContent = letter; tile.classList.add('filled'); } }
      else { tile.textContent = ''; tile.classList.remove('filled'); }
    }
  }

  function showToast(message, duration = 1400) {
    const container = document.getElementById('toastContainer');
    const toast = document.createElement('div');
    toast.className = 'toast'; toast.textContent = message;
    container.appendChild(toast);
    setTimeout(() => { toast.classList.add('fade'); setTimeout(() => toast.remove(), 450); }, duration);
  }

  function shakeRow() {
    const row = document.getElementById(`row-${currentRow}`);
    row.classList.remove('shake'); void row.offsetWidth; row.classList.add('shake');
    setTimeout(() => row.classList.remove('shake'), 500);
  }

  function evaluateGuess(guessArr, target) {
    const result = new Array(WORD_LENGTH).fill('absent');
    const counts = {};
    for (let i = 0; i < WORD_LENGTH; i++) {
      if (guessArr[i] === target[i]) result[i] = 'correct';
      else counts[target[i]] = (counts[target[i]] || 0) + 1;
    }
    for (let i = 0; i < WORD_LENGTH; i++) {
      if (result[i] === 'correct') continue;
      const ch = guessArr[i];
      if (counts[ch] > 0) { result[i] = 'present'; counts[ch]--; }
    }
    return result;
  }

  function submitGuess() {
    if (currentGuess.length !== WORD_LENGTH) { showToast('يجب إدخال 5 أحرف'); shakeRow(); return; }
    
    const guessStr = currentGuess.join('');
    if (!VALID_GUESSES.has(guessStr)) { showToast('كلمة غير موجودة في القاموس'); shakeRow(); return; }

    isAnimating = true;
    const guessArr = currentGuess.slice();
    const result = evaluateGuess(guessArr, targetLetters);

    for (let c = 0; c < WORD_LENGTH; c++) {
      const tile = document.getElementById(`tile-${currentRow}-${c}`);
      setTimeout(() => {
        tile.classList.add('flip');
        setTimeout(() => { tile.classList.add(result[c]); }, 300);
      }, c * 220);
    }

    const totalAnimTime = WORD_LENGTH * 220 + 350;

    setTimeout(() => {
      for (let c = 0; c < WORD_LENGTH; c++) {
        const ch = guessArr[c]; const newState = result[c]; const cur = keyStates[ch];
        if (cur === 'correct') continue;
        if (cur === 'present' && newState === 'absent') continue;
        keyStates[ch] = newState;
        const keyEl = document.getElementById(`key-${ch}`);
        if (keyEl) { keyEl.classList.remove('correct','present','absent'); keyEl.classList.add(newState); }
      }
    }, totalAnimTime);

    const isWin = result.every(r => r === 'correct');
    boardState.push(guessStr);

    setTimeout(() => {
      if (isWin) {
        gameOver = true; gameWon = true;
        document.getElementById(`row-${currentRow}`).classList.add('win');
        persistCurrentState();
        recordResult(true, currentRow + 1);
        setTimeout(() => { isAnimating = false; showEndModal(true); }, 900);
      } else if (currentRow === MAX_GUESSES - 1) {
        gameOver = true; gameWon = false;
        persistCurrentState();
        recordResult(false, MAX_GUESSES);
        isAnimating = false;
        setTimeout(() => showEndModal(false), 400);
      } else {
        currentRow++; currentGuess = []; isAnimating = false;
        persistCurrentState();
      }
    }, totalAnimTime + 50);
  }

  function persistCurrentState() {
    const stateObj = {
      date: puzzleDate,
      guesses: boardState,
      gameOver: gameOver,
      gameWon: gameWon,
      startTime: startTime,
      endTime: gameOver ? Date.now() : null
    };
    saveGameState(stateObj);
  }

  function recordResult(won, attempts) {
    const totalTime = Date.now() - startTime;
    addToLeaderboard({ name: playerName, won, attempts, timeMs: totalTime, date: puzzleDate });
    
    let stats = loadStats();
    stats.played++;
    if (won) {
      stats.won++;
      stats.currentStreak++;
      if (stats.currentStreak > stats.maxStreak) stats.maxStreak = stats.currentStreak;
      stats.distribution[attempts - 1]++;
    } else {
      stats.currentStreak = 0;
    }
    saveStats(stats);
  }

  function attemptsText(n) {
    if (n === 1) return 'محاولة واحدة';
    if (n === 2) return 'محاولتين';
    if (n >= 3 && n <= 10) return `${n} محاولات`;
    return `${n} محاولة`;
  }

  function renderLeaderboardList(containerEl, dateEl) {
    const entries = getDailyEntries(puzzleDate);
    if (dateEl) dateEl.textContent = puzzleDate;
    if (!entries.length) { containerEl.innerHTML = '<div class="empty-lb">لا توجد نتائج بعد. كن أول لاعب!</div>'; return; }
    containerEl.innerHTML = '';
    entries.slice(0, 50).forEach((e, i) => {
      const div = document.createElement('div');
      div.className = 'lb-row' + (e.name === playerName ? ' me' : '');
      const rankEmoji = i === 0 ? '🥇' : i === 1 ? '🥈' : i === 2 ? '🥉' : (i + 1);
      const resCls = e.won ? 'res-win' : 'res-loss';
      const resText = e.won ? `${e.attempts}/6` : 'خسارة';
      div.innerHTML = `<div class="lb-rank">${rankEmoji}</div><div class="lb-name"></div><div class="lb-meta"><span class="${resCls}">${resText}</span> · ${formatTime(e.timeMs)}</div>`;
      div.querySelector('.lb-name').textContent = e.name;
      containerEl.appendChild(div);
    });
  }

  function startNextPuzzleTimer() {
    if (timerInterval) clearInterval(timerInterval);
    const mainTimerEl = document.getElementById('mainTimer');
    
    timerInterval = setInterval(() => {
      const now = new Date();
      const riyadhFmt = new Intl.DateTimeFormat('en-US', { timeZone: 'Asia/Riyadh', year: 'numeric', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false });
      const parts = riyadhFmt.formatToParts(now);
      const r_now = new Date(parts.find(p=>p.type==='year').value, parts.find(p=>p.type==='month').value-1, parts.find(p=>p.type==='day').value, parts.find(p=>p.type==='hour').value, parts.find(p=>p.type==='minute').value, parts.find(p=>p.type==='second').value);
      
      const tomorrow = new Date(r_now);
      tomorrow.setHours(24, 0, 0, 0);
      
      let diff = tomorrow - r_now;
      if (diff <= 0) {
        clearInterval(timerInterval);
        location.reload(); 
        return;
      }
      
      const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      const s = Math.floor((diff % (1000 * 60)) / 1000);
      
      mainTimerEl.textContent = `${h.toString().padStart(2, '0')}:${m.toString().padStart(2, '0')}:${s.toString().padStart(2, '0')}`;
    }, 1000);
  }

  function showEndModal(won) {
    const modal = document.getElementById('endModal');
    const title = document.getElementById('endTitle');
    const text  = document.getElementById('endText');
    const wordEl = document.getElementById('endWord');
    const meaningEl = document.getElementById('endMeaning'); 
    const attEl = document.getElementById('endAttempts');
    const timeEl = document.getElementById('endTime');
    
    if (won) {
      title.textContent = '🎉 أحسنت!';
      text.textContent = `لقد فزت في ${attemptsText(currentRow + (gameOver && boardState.length === currentRow ? 0 : 1))}`; 
      wordEl.textContent = targetWord; wordEl.classList.remove('lose');
      attEl.textContent = `${boardState.length}/6`;
    } else {
      title.textContent = '😔 انتهت المحاولات';
      text.textContent = 'الكلمة الصحيحة كانت:';
      wordEl.textContent = targetWord; wordEl.classList.add('lose');
      attEl.textContent = '—';
    }

    meaningEl.textContent = WORD_MEANINGS[targetWord] ? `المعنى: ${WORD_MEANINGS[targetWord]}` : '';

    const finalTimeMs = (loadGameState() && loadGameState().endTime) ? (loadGameState().endTime - loadGameState().startTime) : (Date.now() - startTime);
    timeEl.textContent = formatTime(finalTimeMs);
    
    renderLeaderboardList(document.getElementById('endLbList'), document.getElementById('endLbDate'));
    modal.classList.add('show');
  }

  function renderStatsModal() {
    const stats = loadStats();
    document.getElementById('statPlayed').textContent = stats.played;
    const winPct = stats.played > 0 ? Math.round((stats.won / stats.played) * 100) : 0;
    document.getElementById('statWinPct').textContent = winPct;
    document.getElementById('statStreak').textContent = stats.currentStreak;
    document.getElementById('statMaxStreak').textContent = stats.maxStreak;

    const distContainer = document.getElementById('distContainer');
    distContainer.innerHTML = '';
    const maxDist = Math.max(...stats.distribution, 1);
    
    stats.distribution.forEach((val, idx) => {
      const w = Math.max(5, Math.round((val / maxDist) * 100));
      const row = document.createElement('div');
      row.className = 'dist-row';
      const isCurrent = (gameOver && gameWon && boardState.length === idx + 1);
      row.innerHTML = `
        <div class="dist-label">${idx + 1}</div>
        <div class="dist-bar-bg">
          <div class="dist-bar ${isCurrent ? 'highlight' : ''}" style="width: ${w}%">${val}</div>
        </div>
      `;
      distContainer.appendChild(row);
    });
  }

  function showStatsModal() {
    renderStatsModal();
    document.getElementById('statsModal').classList.add('show');
  }

  function restoreGameState(savedState) {
    startTime = savedState.startTime;
    boardState = savedState.guesses;
    gameOver = savedState.gameOver;
    gameWon = savedState.gameWon;

    boardState.forEach((guessStr, idx) => {
      const guessArr = splitArabic(guessStr);
      const result = evaluateGuess(guessArr, targetLetters);
      
      for (let c = 0; c < WORD_LENGTH; c++) {
        const tile = document.getElementById(`tile-${idx}-${c}`);
        tile.textContent = guessArr[c];
        tile.classList.add('filled', result[c]);
        
        const ch = guessArr[c];
        const newState = result[c];
        if (keyStates[ch] !== 'correct' && !(keyStates[ch] === 'present' && newState === 'absent')) {
          keyStates[ch] = newState;
          const keyEl = document.getElementById(`key-${ch}`);
          if (keyEl) { keyEl.classList.remove('correct','present','absent'); keyEl.classList.add(newState); }
        }
      }
    });

    currentRow = boardState.length;
    if (gameOver) {
      if (gameWon) document.getElementById(`row-${currentRow-1}`).classList.add('win');
      setTimeout(() => showEndModal(gameWon), 500);
    }
  }

  function startGame() {
    puzzleDate = getSaudiDateString();
    targetWord = getDailyWord();
    targetLetters = splitArabic(targetWord);
    currentGuess = []; boardState = []; currentRow = 0; gameOver = false; gameWon = false; isAnimating = false; keyStates = {};
    startTime = Date.now();
    document.getElementById('endModal').classList.remove('show');
    document.getElementById('infoDateStr').innerHTML = `لغز اليوم · <strong>${puzzleDate}</strong>`;
    buildBoard();
    document.querySelectorAll('.key').forEach(k => k.classList.remove('correct', 'present', 'absent'));

    const savedState = loadGameState();
    if (savedState && savedState.date === puzzleDate) {
      restoreGameState(savedState);
    } else {
      saveGameState(null);
    }
  }

  function updateNamePill() { document.getElementById('namePill').textContent = playerName || '—'; }

  function showNameModal(initial) {
    const modal = document.getElementById('nameModal');
    const input = document.getElementById('nameInput');
    input.value = playerName || '';
    modal.classList.add('show'); setTimeout(() => input.focus(), 100);
    modal.dataset.initial = initial ? '1' : '0';
  }

  function commitName() {
    const input = document.getElementById('nameInput');
    const val = (input.value || '').trim().slice(0, 20);
    if (!val) {
      input.style.borderColor = '#c46a6a';
      setTimeout(() => { input.style.borderColor = ''; }, 600); return;
    }
    const wasInitial = document.getElementById('nameModal').dataset.initial === '1';
    playerName = val; saveName(playerName); updateNamePill();
    document.getElementById('nameModal').classList.remove('show');
    if (wasInitial) startGame();
  }

  // Initialize
  startNextPuzzleTimer(); 
  buildKeyboard();
  playerName = loadName();
  updateNamePill();
  if (playerName) { document.getElementById('nameModal').classList.remove('show'); startGame(); }
  else { showNameModal(true); }

  document.getElementById('startBtn').addEventListener('click', commitName);
  document.getElementById('nameInput').addEventListener('keydown', (e) => { if (e.key === 'Enter') { e.preventDefault(); commitName(); } });
  document.getElementById('namePill').addEventListener('click', () => showNameModal(false));
  
  document.getElementById('lbBtn').addEventListener('click', () => {
    renderLeaderboardList(document.getElementById('lbList'), document.getElementById('lbDate'));
    document.getElementById('lbModal').classList.add('show');
  });
  document.getElementById('closeLbBtn').addEventListener('click', () => document.getElementById('lbModal').classList.remove('show'));
  
  document.getElementById('statsBtn').addEventListener('click', showStatsModal);
  document.getElementById('closeStatsBtn').addEventListener('click', () => document.getElementById('statsModal').classList.remove('show'));
  document.getElementById('closeEndBtn').addEventListener('click', () => document.getElementById('endModal').classList.remove('show'));

  document.addEventListener('keydown', (e) => {
    if (e.ctrlKey || e.metaKey || e.altKey) return;
    const anyModal = document.querySelector('.modal-overlay.show');
    if (anyModal) return; 
    if (gameOver) return;
    if (e.key === 'Enter') { e.preventDefault(); handleKey('ENTER'); }
    else if (e.key === 'Backspace') { e.preventDefault(); handleKey('BACK'); }
    else if (e.key && e.key.length === 1) {
      const ch = normalizeChar(e.key);
      if (isArabicLetter(ch) && isOnKeyboard(ch)) handleKey(ch);
    }
  });

  document.addEventListener('contextmenu', (e) => { if (e.target.classList && e.target.classList.contains('key')) e.preventDefault(); });

  setInterval(() => {
    const nowDate = getSaudiDateString();
    if (puzzleDate && nowDate !== puzzleDate && !isAnimating) {
      location.reload(); 
    }
  }, 30000);
</script>
</body>
</html>
