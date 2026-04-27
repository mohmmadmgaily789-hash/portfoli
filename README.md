<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>نور - طريق العبادة</title>
<link href="https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&family=Tajawal:wght@300;400;500;700;800;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
:root {
  --primary: #0B6E4F;
  --primary-light: #10A37F;
  --primary-dark: #074A35;
  --accent: #D4A843;
  --accent-light: #E8C76A;
  --bg: #060B08;
  --bg2: #0B140E;
  --card: #0F1D15;
  --card2: #132318;
  --fg: #EDE6D6;
  --fg2: #B8B0A0;
  --muted: #5A6B60;
  --border: #1A2E22;
  --success: #2ECC71;
  --warning: #F0A030;
  --danger: #E74C3C;
  --radius: 16px;
  --radius-sm: 10px;
  --shadow: 0 4px 24px rgba(0,0,0,0.4);
  --transition: 0.3s cubic-bezier(0.4,0,0.2,1);
}

.comfort-mode {
  --bg: #0C0E08;
  --bg2: #10140C;
  --card: #161C12;
  --card2: #1A2216;
  --fg: #D8D0B8;
  --fg2: #A09880;
  --primary: #1A7A55;
  --accent: #C89A30;
}

* { margin:0; padding:0; box-sizing:border-box; }
html { font-size:16px; }
body {
  font-family:'Tajawal',sans-serif;
  background:var(--bg);
  color:var(--fg);
  min-height:100vh;
  overflow-x:hidden;
  -webkit-tap-highlight-color:transparent;
}

/* الخلفية الإسلامية الهندسية */
.geo-bg {
  position:fixed; top:0; left:0; width:100%; height:100%;
  z-index:0; pointer-events:none; opacity:0.03;
}
.geo-bg svg { width:100%; height:100%; }

/* التطبيق الرئيسي */
#app {
  position:relative; z-index:1;
  max-width:480px; margin:0 auto;
  min-height:100vh; padding-bottom:80px;
}

/* الرأس */
.app-header {
  padding:16px 20px 8px;
  display:flex; justify-content:space-between; align-items:center;
  position:sticky; top:0; z-index:50;
  background:linear-gradient(to bottom, var(--bg) 60%, transparent);
  backdrop-filter:blur(12px);
}
.app-logo {
  display:flex; align-items:center; gap:10px;
}
.app-logo-icon {
  width:36px; height:36px; border-radius:10px;
  background:linear-gradient(135deg, var(--primary), var(--primary-light));
  display:flex; align-items:center; justify-content:center;
  font-family:'Amiri',serif; font-weight:700; font-size:18px;
  color:var(--accent); box-shadow:0 2px 12px rgba(11,110,79,0.4);
}
.app-logo-text { font-weight:800; font-size:18px; color:var(--fg); }
.header-actions { display:flex; gap:8px; }
.header-btn {
  width:38px; height:38px; border-radius:var(--radius-sm);
  background:var(--card); border:1px solid var(--border);
  color:var(--fg2); display:flex; align-items:center; justify-content:center;
  cursor:pointer; transition:var(--transition); font-size:14px;
}
.header-btn:hover, .header-btn:active { background:var(--card2); color:var(--accent); }

/* التاريخ الهجري */
.date-bar {
  padding:4px 20px 12px; display:flex; align-items:center; gap:12px;
}
.hijri-date {
  font-size:13px; color:var(--accent); font-weight:500;
  background:rgba(212,168,67,0.08); padding:4px 12px;
  border-radius:20px; border:1px solid rgba(212,168,67,0.15);
}
.greg-date { font-size:12px; color:var(--muted); }

/* التبويبات */
.tab-content { display:none; animation:fadeUp 0.4s ease; }
.tab-content.active { display:block; }
@keyframes fadeUp {
  from { opacity:0; transform:translateY(16px); }
  to { opacity:1; transform:translateY(0); }
}

/* البطاقات */
.card {
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius); padding:20px;
  margin:0 20px 14px; position:relative; overflow:hidden;
  transition:var(--transition);
}
.card:active { transform:scale(0.98); }
.card-accent {
  border-top:2px solid var(--primary);
}
.card-gold { border-top:2px solid var(--accent); }
.card-pattern::before {
  content:''; position:absolute; top:0; right:0;
  width:120px; height:120px; opacity:0.03;
  background:radial-gradient(circle at center, var(--accent) 1px, transparent 1px);
  background-size:12px 12px;
}
.card-title {
  font-size:14px; font-weight:700; color:var(--fg2);
  margin-bottom:12px; display:flex; align-items:center; gap:8px;
}
.card-title i { color:var(--primary-light); font-size:13px; }

/* ===== تبويب الصلاة ===== */
.next-prayer-card {
  background:linear-gradient(135deg, var(--primary-dark), #0A3D2B);
  border:1px solid rgba(16,163,127,0.2);
  padding:28px 24px; text-align:center;
}
.next-prayer-label { font-size:13px; color:rgba(255,255,255,0.5); margin-bottom:4px; }
.next-prayer-name {
  font-size:32px; font-weight:900; color:#fff;
  margin-bottom:4px; font-family:'Amiri',serif;
}
.next-prayer-time { font-size:40px; font-weight:900; color:var(--accent-light); letter-spacing:2px; }
.next-prayer-countdown {
  margin-top:12px; font-size:15px; color:rgba(255,255,255,0.7);
  display:flex; align-items:center; justify-content:center; gap:6px;
}
.countdown-num {
  background:rgba(0,0,0,0.3); padding:4px 10px; border-radius:8px;
  font-weight:700; color:var(--accent-light); font-size:18px;
  min-width:42px; text-align:center;
}
.countdown-sep { color:rgba(255,255,255,0.3); font-weight:300; }

/* أوقات الصلاة */
.prayer-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin:0 20px 14px; }
.prayer-item {
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius-sm); padding:14px;
  display:flex; align-items:center; gap:10px;
  transition:var(--transition); cursor:pointer;
}
.prayer-item.active-prayer {
  border-color:var(--primary); background:rgba(11,110,79,0.1);
}
.prayer-item.passed { opacity:0.45; }
.prayer-icon {
  width:36px; height:36px; border-radius:10px;
  display:flex; align-items:center; justify-content:center;
  font-size:14px;
}
.prayer-icon.fajr { background:rgba(240,160,48,0.12); color:#F0A030; }
.prayer-icon.shuruq { background:rgba(243,156,18,0.12); color:#F39C12; }
.prayer-icon.dhuhr { background:rgba(241,196,15,0.12); color:#F1C40F; }
.prayer-icon.asr { background:rgba(230,126,34,0.12); color:#E67E22; }
.prayer-icon.maghrib { background:rgba(231,76,60,0.12); color:#E74C3C; }
.prayer-icon.isha { background:rgba(52,73,94,0.15); color:#7F8C8D; }
.prayer-info { flex:1; }
.prayer-name { font-size:13px; font-weight:600; color:var(--fg); }
.prayer-time-val { font-size:15px; font-weight:700; color:var(--fg); margin-top:2px; }
.prayer-check {
  width:22px; height:22px; border-radius:50%;
  border:2px solid var(--border); display:flex;
  align-items:center; justify-content:center;
  font-size:10px; color:transparent; transition:var(--transition);
  cursor:pointer;
}
.prayer-check.done {
  border-color:var(--success); background:var(--success);
  color:#fff;
}

/* إجراءات سريعة */
.quick-actions {
  display:grid; grid-template-columns:repeat(4,1fr); gap:10px;
  margin:0 20px 14px;
}
.quick-action {
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius-sm); padding:14px 8px;
  text-align:center; cursor:pointer; transition:var(--transition);
}
.quick-action:active { transform:scale(0.95); background:var(--card2); }
.quick-action-icon {
  width:40px; height:40px; border-radius:12px; margin:0 auto 8px;
  display:flex; align-items:center; justify-content:center; font-size:16px;
}
.quick-action span { font-size:11px; font-weight:500; color:var(--fg2); }

/* المحتوى اليومي */
.daily-hadith {
  font-family:'Amiri',serif; font-size:16px; line-height:2;
  color:var(--fg); text-align:right;
}
.daily-hadith-source {
  margin-top:8px; font-size:12px; color:var(--accent);
  font-family:'Tajawal',sans-serif;
}

/* ===== تبويب القرآن ===== */
.quran-search {
  margin:0 20px 14px; position:relative;
}
.quran-search input {
  width:100%; padding:12px 16px 12px 40px;
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius-sm); color:var(--fg);
  font-family:'Tajawal',sans-serif; font-size:14px;
  outline:none; transition:var(--transition);
}
.quran-search input:focus { border-color:var(--primary); }
.quran-search input::placeholder { color:var(--muted); }
.quran-search i {
  position:absolute; left:14px; top:50%; transform:translateY(-50%);
  color:var(--muted); font-size:14px;
}

.last-read-card {
  background:linear-gradient(135deg, var(--primary-dark), #0D4A34);
  border:1px solid rgba(16,163,127,0.15);
}
.last-read-info { display:flex; justify-content:space-between; align-items:center; }
.last-read-name { font-size:20px; font-weight:700; color:#fff; font-family:'Amiri',serif; }
.last-read-ayah { font-size:13px; color:rgba(255,255,255,0.6); margin-top:4px; }
.last-read-btn {
  background:rgba(255,255,255,0.12); border:none; color:#fff;
  padding:8px 16px; border-radius:8px; font-size:13px;
  font-family:'Tajawal',sans-serif; cursor:pointer;
  font-weight:500; transition:var(--transition);
}
.last-read-btn:hover { background:rgba(255,255,255,0.2); }

.surah-list { margin:0 20px; }
.surah-item {
  display:flex; align-items:center; gap:14px;
  padding:14px 0; border-bottom:1px solid var(--border);
  cursor:pointer; transition:var(--transition);
}
.surah-item:active { opacity:0.7; }
.surah-item:last-child { border-bottom:none; }
.surah-num {
  width:36px; height:36px; display:flex; align-items:center; justify-content:center;
  font-size:12px; font-weight:700; color:var(--primary-light);
  position:relative;
}
.surah-num::before {
  content:''; position:absolute; inset:0;
  background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 36 36'%3E%3Cpolygon points='18,2 33,10 33,26 18,34 3,26 3,10' fill='none' stroke='%230B6E4F' stroke-width='1.5'/%3E%3C/svg%3E") center/contain no-repeat;
}
.surah-details { flex:1; }
.surah-name-ar { font-size:16px; font-weight:700; font-family:'Amiri',serif; }
.surah-meta { font-size:11px; color:var(--muted); margin-top:2px; }
.surah-type { font-size:10px; color:var(--accent); background:rgba(212,168,67,0.1); padding:2px 8px; border-radius:4px; }

/* عرض السورة */
.surah-view {
  display:none; position:fixed; inset:0; z-index:100;
  background:var(--bg); overflow-y:auto;
  animation:slideIn 0.3s ease;
}
.surah-view.active { display:block; }
@keyframes slideIn {
  from { transform:translateX(-30px); opacity:0; }
  to { transform:translateX(0); opacity:1; }
}
.surah-header {
  position:sticky; top:0; z-index:10;
  background:linear-gradient(to bottom, var(--bg) 70%, transparent);
  padding:16px 20px; display:flex; align-items:center; gap:12px;
  backdrop-filter:blur(10px);
}
.surah-back {
  width:36px; height:36px; border-radius:10px;
  background:var(--card); border:1px solid var(--border);
  color:var(--fg); display:flex; align-items:center; justify-content:center;
  cursor:pointer; font-size:14px;
}
.surah-title-bar { font-size:18px; font-weight:700; font-family:'Amiri',serif; }
.surah-body { padding:0 24px 100px; }
.bismillah {
  text-align:center; font-family:'Amiri',serif; font-size:22px;
  color:var(--accent); margin-bottom:24px; padding-bottom:24px;
  border-bottom:1px solid var(--border);
}
.ayah-container { line-height:2.4; font-family:'Amiri',serif; font-size:20px; text-align:justify; }
.ayah-text { color:var(--fg); cursor:pointer; transition:var(--transition); padding:2px 0; }
.ayah-text:hover { color:var(--accent-light); }
.ayah-text.highlighted { background:rgba(212,168,67,0.1); border-radius:4px; }
.ayah-num {
  display:inline-flex; width:28px; height:28px; align-items:center; justify-content:center;
  font-size:10px; font-family:'Tajawal',sans-serif; font-weight:700;
  color:var(--accent); vertical-align:middle; margin:0 4px;
  background:rgba(212,168,67,0.08); border-radius:50%;
}
.ayah-actions {
  display:flex; gap:8px; margin-top:8px; padding-bottom:8px;
  border-bottom:1px dashed var(--border);
}
.ayah-action-btn {
  background:var(--card); border:1px solid var(--border);
  color:var(--fg2); padding:4px 10px; border-radius:6px;
  font-size:11px; font-family:'Tajawal',sans-serif;
  cursor:pointer; display:flex; align-items:center; gap:4px;
  transition:var(--transition);
}
.ayah-action-btn:hover { border-color:var(--primary); color:var(--primary-light); }

/* ===== تبويب الأذكار ===== */
.adhkar-tabs {
  display:flex; gap:8px; margin:0 20px 14px; overflow-x:auto;
  scrollbar-width:none; -ms-overflow-style:none;
}
.adhkar-tabs::-webkit-scrollbar { display:none; }
.adhkar-tab {
  padding:8px 18px; border-radius:20px; font-size:13px;
  font-weight:600; white-space:nowrap; cursor:pointer;
  background:var(--card); border:1px solid var(--border);
  color:var(--fg2); transition:var(--transition);
}
.adhkar-tab.active {
  background:var(--primary); border-color:var(--primary);
  color:#fff;
}

.dhikr-card {
  padding:20px;
}
.dhikr-text {
  font-family:'Amiri',serif; font-size:18px; line-height:2.2;
  color:var(--fg); text-align:right; margin-bottom:16px;
}
.dhikr-count-row {
  display:flex; align-items:center; justify-content:space-between;
}
.dhikr-target { font-size:12px; color:var(--muted); }
.dhikr-progress {
  flex:1; height:4px; background:var(--border); border-radius:2px;
  margin:0 12px; overflow:hidden;
}
.dhikr-progress-bar {
  height:100%; background:var(--primary-light); border-radius:2px;
  transition:width 0.3s ease;
}
.dhikr-tap-area {
  width:100%; padding:20px; margin-top:14px;
  background:rgba(11,110,79,0.08); border:2px dashed rgba(11,110,79,0.3);
  border-radius:var(--radius-sm); text-align:center;
  cursor:pointer; transition:var(--transition);
  user-select:none;
}
.dhikr-tap-area:active { background:rgba(11,110,79,0.2); transform:scale(0.98); }
.dhikr-tap-count { font-size:36px; font-weight:900; color:var(--primary-light); }
.dhikr-tap-label { font-size:12px; color:var(--muted); margin-top:4px; }

/* السبحة الإلكترونية */
.tasbih-section { margin:0 20px 14px; }
.tasbih-container {
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius); padding:24px; text-align:center;
}
.tasbih-display {
  font-size:56px; font-weight:900; color:var(--accent-light);
  margin-bottom:8px; transition:var(--transition);
}
.tasbih-label { font-size:13px; color:var(--fg2); margin-bottom:20px; }
.tasbih-btn {
  width:120px; height:120px; border-radius:50%;
  background:linear-gradient(135deg, var(--primary), var(--primary-light));
  border:none; color:#fff; font-size:24px; cursor:pointer;
  box-shadow:0 8px 32px rgba(11,110,79,0.4);
  transition:var(--transition); margin:0 auto 16px; display:flex;
  align-items:center; justify-content:center;
}
.tasbih-btn:active { transform:scale(0.92); box-shadow:0 4px 16px rgba(11,110,79,0.3); }
.tasbih-btn.anim { animation:tasbihPulse 0.15s ease; }
@keyframes tasbihPulse {
  0% { transform:scale(1); }
  50% { transform:scale(0.9); }
  100% { transform:scale(1); }
}
.tasbih-controls { display:flex; gap:10px; justify-content:center; }
.tasbih-ctrl-btn {
  padding:8px 16px; border-radius:8px; background:var(--card2);
  border:1px solid var(--border); color:var(--fg2);
  font-family:'Tajawal',sans-serif; font-size:12px;
  cursor:pointer; transition:var(--transition);
}
.tasbih-ctrl-btn:hover { border-color:var(--primary); color:var(--primary-light); }
.tasbih-dhikr-select {
  display:flex; gap:6px; margin-bottom:16px; justify-content:center; flex-wrap:wrap;
}
.tasbih-dhikr-opt {
  padding:4px 12px; border-radius:12px; font-size:11px;
  background:var(--bg2); border:1px solid var(--border);
  color:var(--fg2); cursor:pointer; transition:var(--transition);
  font-family:'Amiri',serif;
}
.tasbih-dhikr-opt.active { background:var(--primary); border-color:var(--primary); color:#fff; }

/* ===== تبويب القبلة ===== */
.qibla-section { text-align:center; padding:20px; }
.qibla-label { font-size:14px; color:var(--fg2); margin-bottom:20px; }
.qibla-compass {
  width:260px; height:260px; margin:0 auto 24px;
  position:relative; border-radius:50%;
  background:radial-gradient(circle, var(--card2) 0%, var(--card) 100%);
  border:2px solid var(--border);
  box-shadow:0 0 60px rgba(11,110,79,0.15), inset 0 0 30px rgba(0,0,0,0.3);
}
.compass-ring {
  position:absolute; inset:8px; border-radius:50%;
  border:1px solid var(--border);
}
.compass-directions {
  position:absolute; inset:0; font-size:12px; font-weight:700;
  color:var(--muted);
}
.compass-dir {
  position:absolute; transform:translate(-50%,-50%);
}
.compass-dir.n { top:16px; left:50%; color:var(--fg); }
.compass-dir.s { bottom:8px; left:50%; }
.compass-dir.e { right:8px; top:50%; }
.compass-dir.w { left:12px; top:50%; }
.qibla-needle {
  position:absolute; top:50%; left:50%;
  width:4px; height:100px; margin-left:-2px; margin-top:-100px;
  transform-origin:bottom center;
  transition:transform 0.6s cubic-bezier(0.4,0,0.2,1);
}
.qibla-needle::before {
  content:''; position:absolute; top:0; left:50%;
  transform:translateX(-50%);
  width:0; height:0;
  border-left:10px solid transparent;
  border-right:10px solid transparent;
  border-bottom:80px solid var(--primary-light);
  filter:drop-shadow(0 0 8px rgba(16,163,127,0.5));
}
.qibla-needle::after {
  content:''; position:absolute; bottom:-80px; left:50%;
  transform:translateX(-50%);
  width:0; height:0;
  border-left:6px solid transparent;
  border-right:6px solid transparent;
  border-top:60px solid var(--muted);
  opacity:0.3;
}
.compass-center {
  position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
  width:16px; height:16px; border-radius:50%;
  background:var(--primary); border:2px solid var(--accent);
  z-index:2;
}
.qibla-degree {
  font-size:24px; font-weight:700; color:var(--primary-light);
}
.qibla-degree small { font-size:13px; color:var(--muted); font-weight:400; }
.qibla-kaaba {
  margin-top:16px; font-size:48px; color:var(--accent);
  animation:kaabaGlow 3s ease infinite;
}
@keyframes kaabaGlow {
  0%,100% { filter:drop-shadow(0 0 4px rgba(212,168,67,0.3)); }
  50% { filter:drop-shadow(0 0 16px rgba(212,168,67,0.6)); }
}

/* ===== تبويب المزيد ===== */
.more-section { padding:0 20px; }
.more-card {
  background:var(--card); border:1px solid var(--border);
  border-radius:var(--radius); padding:18px; margin-bottom:12px;
  cursor:pointer; transition:var(--transition);
}
.more-card:active { transform:scale(0.98); }
.more-card-header { display:flex; align-items:center; gap:12px; }
.more-card-icon {
  width:42px; height:42px; border-radius:12px;
  display:flex; align-items:center; justify-content:center;
  font-size:16px;
}
.more-card-title { font-size:15px; font-weight:600; }
.more-card-desc { font-size:12px; color:var(--muted); margin-top:2px; }
.more-card-arrow { margin-right:auto; color:var(--muted); font-size:12px; }

/* الإنجازات / الجاميفيكشن */
.gamify-card {
  background:linear-gradient(135deg, #1A1408, #1A1A08);
  border:1px solid rgba(212,168,67,0.2);
}
.gamify-stats { display:grid; grid-template-columns:repeat(3,1fr); gap:12px; margin-top:14px; }
.gamify-stat { text-align:center; }
.gamify-stat-val { font-size:22px; font-weight:900; color:var(--accent-light); }
.gamify-stat-label { font-size:10px; color:var(--muted); margin-top:2px; }
.level-bar {
  margin-top:14px; height:6px; background:var(--border);
  border-radius:3px; overflow:hidden;
}
.level-bar-fill {
  height:100%; border-radius:3px;
  background:linear-gradient(90deg, var(--accent), var(--accent-light));
  transition:width 0.6s ease;
}
.level-info { display:flex; justify-content:space-between; margin-top:6px; font-size:11px; color:var(--muted); }
.level-name { color:var(--accent); font-weight:600; }

/* الأشرطة */
.streak-row { display:flex; gap:4px; margin-top:12px; direction:ltr; }
.streak-day {
  flex:1; height:28px; border-radius:4px;
  background:var(--border); position:relative;
  transition:var(--transition);
}
.streak-day.active { background:var(--primary-light); }
.streak-day.partial { background:var(--accent); opacity:0.5; }
.streak-day.today { border:2px solid var(--accent); }

/* نافذة الإعدادات */
.modal-overlay {
  display:none; position:fixed; inset:0; z-index:200;
  background:rgba(0,0,0,0.7); backdrop-filter:blur(6px);
  align-items:flex-end; justify-content:center;
}
.modal-overlay.active { display:flex; }
.modal-content {
  background:var(--bg2); border-radius:var(--radius) var(--radius) 0 0;
  width:100%; max-width:480px; max-height:80vh; overflow-y:auto;
  padding:24px; animation:modalUp 0.3s ease;
}
@keyframes modalUp {
  from { transform:translateY(100%); }
  to { transform:translateY(0); }
}
.modal-handle {
  width:40px; height:4px; background:var(--muted);
  border-radius:2px; margin:0 auto 20px;
}
.modal-title { font-size:18px; font-weight:700; margin-bottom:20px; }

.setting-row {
  display:flex; align-items:center; justify-content:space-between;
  padding:14px 0; border-bottom:1px solid var(--border);
}
.setting-label { font-size:14px; font-weight:500; }
.setting-desc { font-size:11px; color:var(--muted); margin-top:2px; }
.toggle-switch {
  width:48px; height:26px; border-radius:13px;
  background:var(--border); position:relative; cursor:pointer;
  transition:var(--transition);
}
.toggle-switch.active { background:var(--primary); }
.toggle-switch::after {
  content:''; position:absolute; top:3px; right:3px;
  width:20px; height:20px; border-radius:50%;
  background:#fff; transition:var(--transition);
}
.toggle-switch.active::after { right:25px; }

/* شريط التنقل السفلي */
.bottom-nav {
  position:fixed; bottom:0; left:50%; transform:translateX(-50%);
  width:100%; max-width:480px; z-index:80;
  background:rgba(8,14,11,0.92); backdrop-filter:blur(20px);
  border-top:1px solid var(--border);
  display:flex; padding:8px 12px 12px; gap:4px;
}
.nav-item {
  flex:1; display:flex; flex-direction:column; align-items:center;
  gap:3px; padding:6px 4px; border-radius:10px;
  cursor:pointer; transition:var(--transition);
  position:relative;
}
.nav-item:active { transform:scale(0.9); }
.nav-item i { font-size:18px; color:var(--muted); transition:var(--transition); }
.nav-item span { font-size:10px; color:var(--muted); font-weight:500; transition:var(--transition); }
.nav-item.active i { color:var(--primary-light); }
.nav-item.active span { color:var(--primary-light); }
.nav-item.active::before {
  content:''; position:absolute; top:-8px; left:50%;
  transform:translateX(-50%); width:20px; height:3px;
  border-radius:2px; background:var(--primary-light);
}

/* إشعار التوست */
.toast {
  position:fixed; top:20px; left:50%; transform:translateX(-50%) translateY(-80px);
  background:var(--card); border:1px solid var(--primary);
  padding:12px 20px; border-radius:12px; z-index:300;
  display:flex; align-items:center; gap:10px;
  box-shadow:0 8px 32px rgba(0,0,0,0.4);
  transition:transform 0.4s cubic-bezier(0.4,0,0.2,1);
  font-size:13px; font-weight:500;
}
.toast.show { transform:translateX(-50%) translateY(0); }
.toast i { color:var(--primary-light); }

/* جسيمات الاحتفال */
.confetti-container {
  position:fixed; inset:0; pointer-events:none; z-index:250;
}
.confetti {
  position:absolute; width:8px; height:8px; border-radius:2px;
  animation:confettiFall 1.5s ease forwards;
}
@keyframes confettiFall {
  0% { opacity:1; transform:translateY(0) rotate(0deg); }
  100% { opacity:0; transform:translateY(100vh) rotate(720deg); }
}

/* التحميل */
.loading-screen {
  position:fixed; inset:0; z-index:500;
  background:var(--bg); display:flex; flex-direction:column;
  align-items:center; justify-content:center;
  transition:opacity 0.6s ease;
}
.loading-screen.hide { opacity:0; pointer-events:none; }
.loading-pattern {
  width:80px; height:80px; margin-bottom:24px;
  animation:loadingSpin 3s linear infinite;
}
@keyframes loadingSpin {
  from { transform:rotate(0deg); }
  to { transform:rotate(360deg); }
}
.loading-text {
  font-family:'Amiri',serif; font-size:24px; font-weight:700;
  color:var(--accent); margin-bottom:8px;
}
.loading-sub { font-size:13px; color:var(--muted); }
.loading-bar {
  width:120px; height:3px; background:var(--border);
  border-radius:2px; margin-top:20px; overflow:hidden;
}
.loading-bar-inner {
  height:100%; background:var(--primary-light); border-radius:2px;
  animation:loadingProgress 2s ease forwards;
}
@keyframes loadingProgress {
  from { width:0%; }
  to { width:100%; }
}

@media (min-width:481px) {
  #app { border-left:1px solid var(--border); border-right:1px solid var(--border); }
}

@media (prefers-reduced-motion:reduce) {
  *, *::before, *::after {
    animation-duration:0.01ms !important;
    transition-duration:0.01ms !important;
  }
}
</style>
</head>
<body>

<!-- شاشة التحميل -->
<div class="loading-screen" id="loadingScreen">
  <svg class="loading-pattern" viewBox="0 0 100 100">
    <polygon points="50,5 61,35 95,35 68,57 79,90 50,70 21,90 32,57 5,35 39,35" fill="none" stroke="#D4A843" stroke-width="1.5"></polygon>
    <polygon points="50,18 57,35 76,35 61,48 66,68 50,57 34,68 39,48 24,35 43,35" fill="none" stroke="#0B6E4F" stroke-width="1"></polygon>
    <circle cx="50" cy="50" r="3" fill="#D4A843"></circle>
  </svg>
  <div class="loading-text">نـور</div>
  <div class="loading-sub">طريق العبادة</div>
  <div class="loading-bar"><div class="loading-bar-inner"></div></div>
</div>

<!-- الخلفية الهندسية -->
<div class="geo-bg">
  <svg viewBox="0 0 400 400" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <pattern id="islamicPattern" x="0" y="0" width="80" height="80" patternUnits="userSpaceOnUse">
        <path d="M40 0 L80 40 L40 80 L0 40Z" fill="none" stroke="#0B6E4F" stroke-width="0.5"></path>
        <circle cx="40" cy="40" r="16" fill="none" stroke="#D4A843" stroke-width="0.3"></circle>
        <path d="M24 40 L40 24 L56 40 L40 56Z" fill="none" stroke="#0B6E4F" stroke-width="0.4"></path>
      </pattern>
    </defs>
    <rect width="400" height="400" fill="url(#islamicPattern)"></rect>
  </svg>
</div>

<!-- التوست -->
<div class="toast" id="toast"><i class="fas fa-check-circle"></i><span id="toastText"></span></div>

<!-- جسيمات الاحتفال -->
<div class="confetti-container" id="confetti"></div>

<div id="app">
  <!-- الرأس -->
  <header class="app-header">
    <div class="app-logo">
      <div class="app-logo-icon">ن</div>
      <span class="app-logo-text">نـور</span>
    </div>
    <div class="header-actions">
      <button class="header-btn" onclick="toggleComfort()" id="comfortBtn" title="وضع مريح للعين" aria-label="وضع مريح للعين">
        <i class="fas fa-eye"></i>
      </button>
      <button class="header-btn" onclick="openSettings()" title="الإعدادات" aria-label="الإعدادات">
        <i class="fas fa-cog"></i>
      </button>
    </div>
  </header>

  <!-- التاريخ -->
  <div class="date-bar">
    <span class="hijri-date" id="hijriDate">جاري التحميل...</span>
    <span class="greg-date" id="gregDate"></span>
  </div>

  <!-- ===== تبويب الصلاة ===== -->
  <section class="tab-content active" id="tab-home">
    <!-- الصلاة القادمة -->
    <div class="card next-prayer-card card-pattern">
      <div class="next-prayer-label">الصلاة القادمة</div>
      <div class="next-prayer-name" id="nextPrayerName">--</div>
      <div class="next-prayer-time" id="nextPrayerTime">--:--</div>
      <div class="next-prayer-countdown" id="nextPrayerCountdown">
        <span class="countdown-num" id="cdH">00</span>
        <span class="countdown-sep">:</span>
        <span class="countdown-num" id="cdM">00</span>
        <span class="countdown-sep">:</span>
        <span class="countdown-num" id="cdS">00</span>
      </div>
    </div>

    <!-- أوقات الصلاة -->
    <div class="prayer-grid" id="prayerGrid"></div>

    <!-- إجراءات سريعة -->
    <div class="quick-actions">
      <div class="quick-action" onclick="switchTab('quran')">
        <div class="quick-action-icon" style="background:rgba(11,110,79,0.12);color:var(--primary-light)">
          <i class="fas fa-book-open"></i>
        </div>
        <span>القرآن</span>
      </div>
      <div class="quick-action" onclick="switchTab('adhkar')">
        <div class="quick-action-icon" style="background:rgba(212,168,67,0.12);color:var(--accent)">
          <i class="fas fa-hands-praying"></i>
        </div>
        <span>الأذكار</span>
      </div>
      <div class="quick-action" onclick="switchTab('qibla')">
        <div class="quick-action-icon" style="background:rgba(46,204,113,0.12);color:var(--success)">
          <i class="fas fa-compass"></i>
        </div>
        <span>القبلة</span>
      </div>
      <div class="quick-action" onclick="openTasbih()">
        <div class="quick-action-icon" style="background:rgba(243,156,18,0.12);color:var(--warning)">
          <i class="fas fa-circle-dot"></i>
        </div>
        <span>السبحة</span>
      </div>
    </div>

    <!-- حديث اليوم -->
    <div class="card card-gold card-pattern">
      <div class="card-title"><i class="fas fa-star"></i> حديث اليوم</div>
      <div class="daily-hadith" id="dailyHadith">جاري التحميل...</div>
      <div class="daily-hadith-source" id="dailyHadithSource"></div>
    </div>

    <!-- دعاء اليوم -->
    <div class="card card-accent card-pattern">
      <div class="card-title"><i class="fas fa-hand-holding-heart"></i> دعاء اليوم</div>
      <div class="daily-hadith" id="dailyDua" style="font-size:15px;"></div>
    </div>
  </section>

  <!-- ===== تبويب القرآن ===== -->
  <section class="tab-content" id="tab-quran">
    <div class="quran-search">
      <input type="text" placeholder="ابحث عن سورة..." id="surahSearch" oninput="filterSurahs()" aria-label="بحث السور">
      <i class="fas fa-search"></i>
    </div>

    <div class="card last-read-card" id="lastReadCard" onclick="openLastRead()" style="display:none;">
      <div class="last-read-info">
        <div>
          <div class="last-read-name" id="lastReadName"></div>
          <div class="last-read-ayah" id="lastReadAyah"></div>
        </div>
        <button class="last-read-btn">متابعة القراءة</button>
      </div>
    </div>

    <div class="surah-list" id="surahList"></div>
  </section>

  <!-- عرض السورة -->
  <div class="surah-view" id="surahView">
    <div class="surah-header">
      <button class="surah-back" onclick="closeSurahView()"><i class="fas fa-arrow-right"></i></button>
      <span class="surah-title-bar" id="surahViewTitle"></span>
    </div>
    <div class="surah-body" id="surahViewBody"></div>
  </div>

  <!-- ===== تبويب الأذكار ===== -->
  <section class="tab-content" id="tab-adhkar">
    <div class="adhkar-tabs" id="adhkarTabs">
      <div class="adhkar-tab active" data-cat="morning" onclick="switchAdhkar('morning')">أذكار الصباح</div>
      <div class="adhkar-tab" data-cat="evening" onclick="switchAdhkar('evening')">أذكار المساء</div>
      <div class="adhkar-tab" data-cat="sleep" onclick="switchAdhkar('sleep')">أذكار النوم</div>
      <div class="adhkar-tab" data-cat="afterprayer" onclick="switchAdhkar('afterprayer')">أذكار بعد الصلاة</div>
    </div>

    <div id="adhkarContent"></div>

    <!-- السبحة الإلكترونية -->
    <div class="tasbih-section">
      <div class="tasbih-container">
        <div class="tasbih-dhikr-select" id="tasbihSelect"></div>
        <div class="tasbih-display" id="tasbihCount">0</div>
        <div class="tasbih-label" id="tasbihLabel">سبحان الله</div>
        <button class="tasbih-btn" id="tasbihBtn" onclick="tasbihTap()">
          <i class="fas fa-hand-pointer"></i>
        </button>
        <div class="tasbih-controls">
          <button class="tasbih-ctrl-btn" onclick="tasbihReset()"><i class="fas fa-redo"></i> إعادة</button>
          <button class="tasbih-ctrl-btn" onclick="tasbihUndo()"><i class="fas fa-undo"></i> تراجع</button>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== تبويب القبلة ===== -->
  <section class="tab-content" id="tab-qibla">
    <div class="qibla-section">
      <div class="qibla-label">اتجاه القبلة من موقعك</div>
      <div class="qibla-compass" id="qiblaCompass">
        <div class="compass-ring"></div>
        <div class="compass-directions">
          <span class="compass-dir n">ش</span>
          <span class="compass-dir s">ج</span>
          <span class="compass-dir e">شق</span>
          <span class="compass-dir w">غ</span>
        </div>
        <div class="qibla-needle" id="qiblaNeedle"></div>
        <div class="compass-center"></div>
      </div>
      <div class="qibla-kaaba"><i class="fas fa-kaaba"></i>🕋</div>
      <div class="qibla-degree" id="qiblaDegree">--° <small>من الشمال</small></div>
    </div>

    <div class="card card-pattern">
      <div class="card-title"><i class="fas fa-map-marker-alt"></i> موقعك</div>
      <div style="font-size:13px;color:var(--fg2)" id="userLocation">جاري تحديد الموقع...</div>
    </div>
  </section>

  <!-- ===== تبويب المزيد ===== -->
  <section class="tab-content" id="tab-more">
    <div class="more-section">
      <!-- الإنجازات -->
      <div class="card gamify-card card-pattern">
        <div class="card-title"><i class="fas fa-trophy" style="color:var(--accent)"></i> إنجازاتي</div>
        <div class="gamify-stats">
          <div class="gamify-stat">
            <div class="gamify-stat-val" id="gamifyPoints">0</div>
            <div class="gamify-stat-label">نقطة</div>
          </div>
          <div class="gamify-stat">
            <div class="gamify-stat-val" id="gamifyStreak">0</div>
            <div class="gamify-stat-label">يوم متتالي</div>
          </div>
          <div class="gamify-stat">
            <div class="gamify-stat-val" id="gamifyLevel">1</div>
            <div class="gamify-stat-label">المستوى</div>
          </div>
        </div>
        <div class="level-bar"><div class="level-bar-fill" id="levelBarFill" style="width:0%"></div></div>
        <div class="level-info">
          <span class="level-name" id="levelName">مبتدئ</span>
          <span id="levelProgress">0/100</span>
        </div>
        <div class="streak-row" id="streakRow"></div>
      </div>

      <!-- التقويم -->
      <div class="more-card" onclick="showCalendar()">
        <div class="more-card-header">
          <div class="more-card-icon" style="background:rgba(11,110,79,0.12);color:var(--primary-light)">
            <i class="fas fa-calendar-alt"></i>
          </div>
          <div>
            <div class="more-card-title">التقويم الهجري</div>
            <div class="more-card-desc">المناسبات الإسلامية</div>
          </div>
          <i class="fas fa-chevron-left more-card-arrow"></i>
        </div>
      </div>

      <!-- المفضلة -->
      <div class="more-card" onclick="showBookmarks()">
        <div class="more-card-header">
          <div class="more-card-icon" style="background:rgba(212,168,67,0.12);color:var(--accent)">
            <i class="fas fa-bookmark"></i>
          </div>
          <div>
            <div class="more-card-title">الآيات المفضلة</div>
            <div class="more-card-desc">محفوظاتك وملاحظاتك</div>
          </div>
          <i class="fas fa-chevron-left more-card-arrow"></i>
        </div>
      </div>

      <!-- طرق الحساب -->
      <div class="more-card" onclick="showCalcMethods()">
        <div class="more-card-header">
          <div class="more-card-icon" style="background:rgba(46,204,113,0.12);color:var(--success)">
            <i class="fas fa-sliders-h"></i>
          </div>
          <div>
            <div class="more-card-title">طريقة حساب الصلاة</div>
            <div class="more-card-desc" id="calcMethodDesc">أم القرى</div>
          </div>
          <i class="fas fa-chevron-left more-card-arrow"></i>
        </div>
      </div>

      <!-- الإشعارات -->
      <div class="more-card" onclick="showAlarmSettings()">
        <div class="more-card-header">
          <div class="more-card-icon" style="background:rgba(243,156,18,0.12);color:var(--warning)">
            <i class="fas fa-bell"></i>
          </div>
          <div>
            <div class="more-card-title">تنبيهات الصلاة</div>
            <div class="more-card-desc">تخصيص الأذان والتنبيهات</div>
          </div>
          <i class="fas fa-chevron-left more-card-arrow"></i>
        </div>
      </div>

      <!-- حول التطبيق -->
      <div class="more-card">
        <div class="more-card-header">
          <div class="more-card-icon" style="background:rgba(155,89,182,0.12);color:#9B59B6">
            <i class="fas fa-info-circle"></i>
          </div>
          <div>
            <div class="more-card-title">حول التطبيق</div>
            <div class="more-card-desc">نور - طريق العبادة v1.0</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- شريط التنقل -->
  <nav class="bottom-nav" role="navigation" aria-label="التنقل الرئيسي">
    <div class="nav-item active" data-tab="home" onclick="switchTab('home')">
      <i class="fas fa-mosque"></i><span>الصلاة</span>
    </div>
    <div class="nav-item" data-tab="quran" onclick="switchTab('quran')">
      <i class="fas fa-book-quran"></i><span>القرآن</span>
    </div>
    <div class="nav-item" data-tab="adhkar" onclick="switchTab('adhkar')">
      <i class="fas fa-hands-praying"></i><span>الأذكار</span>
    </div>
    <div class="nav-item" data-tab="qibla" onclick="switchTab('qibla')">
      <i class="fas fa-compass"></i><span>القبلة</span>
    </div>
    <div class="nav-item" data-tab="more" onclick="switchTab('more')">
      <i class="fas fa-ellipsis"></i><span>المزيد</span>
    </div>
  </nav>
</div>

<!-- نافذة الإعدادات -->
<div class="modal-overlay" id="settingsModal">
  <div class="modal-content">
    <div class="modal-handle"></div>
    <div class="modal-title">الإعدادات</div>

    <div class="setting-row">
      <div>
        <div class="setting-label">الوضع المريح للعين</div>
        <div class="setting-desc">ألوان أدفأ وتباين أقل</div>
      </div>
      <div class="toggle-switch" id="comfortToggle" onclick="toggleComfort()"></div>
    </div>

    <div class="setting-row">
      <div>
        <div class="setting-label">إشعارات الصلاة</div>
        <div class="setting-desc">تنبيه عند كل صلاة</div>
      </div>
      <div class="toggle-switch active" id="notifToggle" onclick="toggleNotif()"></div>
    </div>

    <div class="setting-row">
      <div>
        <div class="setting-label">تذكير الأذكار</div>
        <div class="setting-desc">تذكير بأذكار الصباح والمساء</div>
      </div>
      <div class="toggle-switch active" id="adhkarNotifToggle" onclick="this.classList.toggle('active')"></div>
    </div>

    <div class="setting-row" onclick="closeSettings()" style="justify-content:center;cursor:pointer;border:none;padding-top:20px;">
      <span style="color:var(--primary-light);font-weight:600;">إغلاق</span>
    </div>
  </div>
</div>

<!-- نافذة التقويم -->
<div class="modal-overlay" id="calendarModal">
  <div class="modal-content">
    <div class="modal-handle"></div>
    <div class="modal-title">التقويم الهجري</div>
    <div id="calendarContent"></div>
    <div class="setting-row" onclick="closeModal('calendarModal')" style="justify-content:center;cursor:pointer;border:none;padding-top:20px;">
      <span style="color:var(--primary-light);font-weight:600;">إغلاق</span>
    </div>
  </div>
</div>

<script>
// ===== بيانات التطبيق =====

// بيانات السور
const surahsData = [
  {id:1, name:"الفاتحة", nameEn:"Al-Fatiha", verses:7, type:"مكية", ayat:["بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ","الْحَمْدُ لِلَّهِ رَبِّ الْعَالَمِينَ","الرَّحْمَٰنِ الرَّحِيمِ","مَالِكِ يَوْمِ الدِّينِ","إِيَّاكَ نَعْبُدُ وَإِيَّاكَ نَسْتَعِينُ","اهْدِنَا الصِّرَاطَ الْمُسْتَقِيمَ","صِرَاطَ الَّذِينَ أَنْعَمْتَ عَلَيْهِمْ غَيْرِ الْمَغْضُوبِ عَلَيْهِمْ وَلَا الضَّالِّينَ"]},
  {id:108, name:"الكوثر", nameEn:"Al-Kawthar", verses:3, type:"مكية", ayat:["إِنَّا أَعْطَيْنَاكَ الْكَوْثَرَ","فَصَلِّ لِرَبِّكَ وَانْحَرْ","إِنَّ شَانِئَكَ هُوَ الْأَبْتَرُ"]},
  {id:109, name:"الكافرون", nameEn:"Al-Kafirun", verses:6, type:"مكية", ayat:["قُلْ يَا أَيُّهَا الْكَافِرُونَ","لَا أَعْبُدُ مَا تَعْبُدُونَ","وَلَا أَنتُمْ عَابِدُونَ مَا أَعْبُدُ","وَلَا أَنَا عَابِدٌ مَّا عَبَدتُّمْ","وَلَا أَنتُمْ عَابِدُونَ مَا أَعْبُدُ","لَكُمْ دِينُكُمْ وَلِيَ دِينِ"]},
  {id:110, name:"النصر", nameEn:"An-Nasr", verses:3, type:"مدنية", ayat:["إِذَا جَاءَ نَصْرُ اللَّهِ وَالْفَتْحُ","وَرَأَيْتَ النَّاسَ يَدْخُلُونَ فِي دِينِ اللَّهِ أَفْوَاجًا","فَسَبِّحْ بِحَمْدِ رَبِّكَ وَاسْتَغْفِرْهُ إِنَّهُ كَانَ تَوَّابًا"]},
  {id:111, name:"المسد", nameEn:"Al-Masad", verses:5, type:"مكية", ayat:["تَبَّتْ يَدَا أَبِي لَهَبٍ وَتَبَّ","مَا أَغْنَىٰ عَنْهُ مَالُهُ وَمَا كَسَبَ","سَيَصْلَىٰ نَارًا ذَاتَ لَهَبٍ","وَامْرَأَتُهُ حَمَّالَةَ الْحَطَبِ","فِي جِيدِهَا حَبْلٌ مِّن مَّسَدٍ"]},
  {id:112, name:"الإخلاص", nameEn:"Al-Ikhlas", verses:4, type:"مكية", ayat:["قُلْ هُوَ اللَّهُ أَحَدٌ","اللَّهُ الصَّمَدُ","لَمْ يَلِدْ وَلَمْ يُولَدْ","وَلَمْ يَكُن لَّهُ كُفُوًا أَحَدٌ"]},
  {id:113, name:"الفلق", nameEn:"Al-Falaq", verses:5, type:"مكية", ayat:["قُلْ أَعُوذُ بِرَبِّ الْفَلَقِ","مِن شَرِّ مَا خَلَقَ","وَمِن شَرِّ غَاسِقٍ إِذَا وَقَبَ","وَمِن شَرِّ النَّفَّاثَاتِ فِي الْعُقَدِ","وَمِن شَرِّ حَاسِدٍ إِذَا حَسَدَ"]},
  {id:114, name:"الناس", nameEn:"An-Nas", verses:6, type:"مكية", ayat:["قُلْ أَعُوذُ بِرَبِّ النَّاسِ","مَلِكِ النَّاسِ","إِلَٰهِ النَّاسِ","مِن شَرِّ الْوَسْوَاسِ الْخَنَّاسِ","الَّذِي يُوَسْوِسُ فِي صُدُورِ النَّاسِ","مِنَ الْجِنَّةِ وَالنَّاسِ"]},
  {id:36, name:"يس", nameEn:"Ya-Sin", verses:83, type:"مكية", ayat:["يس","وَالْقُرْآنِ الْحَكِيمِ","إِنَّكَ لَمِنَ الْمُرْسَلِينَ","عَلَىٰ صِرَاطٍ مُّسْتَقِيمٍ"]},
  {id:55, name:"الرحمن", nameEn:"Ar-Rahman", verses:78, type:"مدنية", ayat:["الرَّحْمَٰنُ","عَلَّمَ الْقُرْآنَ","خَلَقَ الْإِنسَانَ","عَلَّمَهُ الْبَيَانَ"]},
  {id:67, name:"الملك", nameEn:"Al-Mulk", verses:30, type:"مكية", ayat:["تَبَارَكَ الَّذِي بِيَدِهِ الْمُلْكُ وَهُوَ عَلَىٰ كُلِّ شَيْءٍ قَدِيرٌ","الَّذِي خَلَقَ الْمَوْتَ وَالْحَيَاةَ لِيَبْلُوَكُمْ أَيُّكُمْ أَحْسَنُ عَمَلًا"]},
];

// بيانات الأذكار
const adhkarData = {
  morning: [
    {text:"أَصْبَحْنَا وَأَصْبَحَ الْمُلْكُ لِلَّهِ، وَالْحَمْدُ لِلَّهِ، لَا إِلَٰهَ إِلَّا اللَّهُ وَحْدَهُ لَا شَرِيكَ لَهُ، لَهُ الْمُلْكُ وَلَهُ الْحَمْدُ وَهُوَ عَلَىٰ كُلِّ شَيْءٍ قَدِيرٌ", count:1, current:0},
    {text:"اللَّهُمَّ بِكَ أَصْبَحْنَا، وَبِكَ أَمْسَيْنَا، وَبِكَ نَحْيَا، وَبِكَ نَمُوتُ، وَإِلَيْكَ النُّشُورُ", count:1, current:0},
    {text:"اللَّهُمَّ أَنْتَ رَبِّي لَا إِلَٰهَ إِلَّا أَنْتَ، خَلَقْتَنِي وَأَنَا عَبْدُكَ، وَأَنَا عَلَىٰ عَهْدِكَ وَوَعْدِكَ مَا اسْتَطَعْتُ، أَعُوذُ بِكَ مِن شَرِّ مَا صَنَعْتُ، أَبُوءُ لَكَ بِنِعْمَتِكَ عَلَيَّ، وَأَبُوءُ بِذَنْبِي فَاغْفِرْ لِي فَإِنَّهُ لَا يَغْفِرُ الذُّنُوبَ إِلَّا أَنْتَ", count:1, current:0},
    {text:"سُبْحَانَ اللَّهِ وَبِحَمْدِهِ", count:100, current:0},
    {text:"لَا إِلَٰهَ إِلَّا اللَّهُ وَحْدَهُ لَا شَرِيكَ لَهُ، لَهُ الْمُلْكُ وَلَهُ الْحَمْدُ وَهُوَ عَلَىٰ كُلِّ شَيْءٍ قَدِيرٌ", count:10, current:0},
    {text:"اللَّهُمَّ إِنِّي أَسْأَلُكَ عِلْمًا نَافِعًا، وَرِزْقًا طَيِّبًا، وَعَمَلًا مُتَقَبَّلًا", count:1, current:0},
  ],
  evening: [
    {text:"أَمْسَيْنَا وَأَمْسَى الْمُلْكُ لِلَّهِ، وَالْحَمْدُ لِلَّهِ، لَا إِلَٰهَ إِلَّا اللَّهُ وَحْدَهُ لَا شَرِيكَ لَهُ، لَهُ الْمُلْكُ وَلَهُ الْحَمْدُ وَهُوَ عَلَىٰ كُلِّ شَيْءٍ قَدِيرٌ", count:1, current:0},
    {text:"اللَّهُمَّ بِكَ أَمْسَيْنَا، وَبِكَ أَصْبَحْنَا، وَبِكَ نَحْيَا، وَبِكَ نَمُوتُ، وَإِلَيْكَ الْمَصِيرُ", count:1, current:0},
    {text:"أَعُوذُ بِكَلِمَاتِ اللَّهِ التَّامَّاتِ مِن شَرِّ مَا خَلَقَ", count:3, current:0},
    {text:"اللَّهُمَّ إِنِّي أَسْأَلُكَ الْعَفْوَ وَالْعَافِيَةَ فِي الدُّنْيَا وَالْآخِرَةِ", count:1, current:0},
    {text:"بِسْمِ اللَّهِ الَّذِي لَا يَضُرُّ مَعَ اسْمِهِ شَيْءٌ فِي الْأَرْضِ وَلَا فِي السَّمَاءِ وَهُوَ السَّمِيعُ الْعَلِيمُ", count:3, current:0},
  ],
  sleep: [
    {text:"بِاسْمِكَ اللَّهُمَّ أَمُوتُ وَأَحْيَا", count:1, current:0},
    {text:"اللَّهُمَّ قِنِي عَذَابَكَ يَوْمَ تَبْعَثُ عِبَادَكَ", count:1, current:0},
    {text:"سُبْحَانَ اللَّهِ", count:33, current:0},
    {text:"الْحَمْدُ لِلَّهِ", count:33, current:0},
    {text:"اللَّهُ أَكْبَرُ", count:34, current:0},
  ],
  afterprayer: [
    {text:"أَسْتَغْفِرُ اللَّهَ", count:3, current:0},
    {text:"اللَّهُمَّ أَنْتَ السَّلَامُ وَمِنْكَ السَّلَامُ تَبَارَكْتَ يَا ذَا الْجَلَالِ وَالْإِكْرَامِ", count:1, current:0},
    {text:"سُبْحَانَ اللَّهِ", count:33, current:0},
    {text:"الْحَمْدُ لِلَّهِ", count:33, current:0},
    {text:"اللَّهُ أَكْبَرُ", count:33, current:0},
    {text:"لَا إِلَٰهَ إِلَّا اللَّهُ وَحْدَهُ لَا شَرِيكَ لَهُ، لَهُ الْمُلْكُ وَلَهُ الْحَمْدُ وَهُوَ عَلَىٰ كُلِّ شَيْءٍ قَدِيرٌ", count:1, current:0},
  ]
};

// بيانات الأحاديث
const ahadith = [
  {text:"إنَّما الأعمالُ بالنِّيَّاتِ، وإنَّما لكُلِّ امرئٍ ما نَوى", source:"متفق عليه"},
  {text:"لا يُؤمِنُ أحَدُكُم حتى يُحِبَّ لأخيهِ ما يُحِبُّ لنَفسِهِ", source:"متفق عليه"},
  {text:"مَن كانَ يُؤمِنُ باللهِ واليومِ الآخِرِ فلْيَقُلْ خَيرًا أو لِيَصمُتْ", source:"متفق عليه"},
  {text:"المُسلِمُ مَن سَلِمَ المُسلِمونَ مِن لِسانِهِ ويَدِهِ", source:"متفق عليه"},
  {text:"خَيرُكُم مَن تَعلَّمَ القُرآنَ وعَلَّمَهُ", source:"رواه البخاري"},
  {text:"الدُّعاءُ هو العِبادةُ", source:"رواه الترمذي"},
  {text:"إنَّ اللَّهَ لا يَنظُرُ إلى صُوَرِكُم وأموَالِكُم، ولكِن يَنظُرُ إلى قُلوبِكُم وأعمالِكُم", source:"رواه مسلم"},
  {text:"الطُّهورُ شَطرُ الإيمانِ، والحمدُ للهِ تَملأُ الميزانَ، وسُبحانَ اللهِ والحمدُ للهِ تَملآنِ ما بينَ السماءِ والأرضِ", source:"رواه مسلم"},
];

const dailyDuas = [
  "اللَّهُمَّ إني أسألُكَ الهدى والتُّقى والعفافَ والغِنى",
  "اللَّهُمَّ أعنِّي على ذِكرِكَ وشُكرِكَ وحُسنِ عِبادَتِكَ",
  "اللَّهُمَّ إنِّي أعوذُ بِكَ مِن زَوالِ نِعمَتِكَ وتَحَوُّلِ عافِيَتِكَ وفُجاءَةِ نِقمَتِكَ وجَميعِ سَخَطِكَ",
  "اللَّهُمَّ إنِّي أسألُكَ الفِردَوسَ الأعلى مِنَ الجنَّةِ",
  "رَبَّنا آتِنا في الدُّنيا حسَنةً وفي الآخِرَةِ حسَنةً وقِنا عَذابَ النَّارِ",
];

// المناسبات الإسلامية
const islamicEvents = [
  {month:1, day:1, name:"رأس السنة الهجرية"},
  {month:1, day:10, name:"يوم عاشوراء"},
  {month:3, day:12, name:"المولد النبوي"},
  {month:7, day:27, name:"الإسراء والمعراج"},
  {month:8, day:15, name:"ليلة النصف من شعبان"},
  {month:9, day:1, name:"بداية رمضان"},
  {month:9, day:27, name:"ليلة القدر"},
  {month:10, day:1, name:"عيد الفطر"},
  {month:10, day:2, name:"ثاني أيام العيد"},
  {month:12, day:8, name:"يوم التروية"},
  {month:12, day:9, name:"يوم عرفة"},
  {month:12, day:10, name:"عيد الأضحى"},
];

// ===== حالة التطبيق =====
let appState = {
  lat: 24.7136, lng: 46.6753, // الرياض كموقع افتراضي
  locationName: "الرياض، السعودية",
  prayerTimes: null,
  currentAdhkar: 'morning',
  tasbihCount: 0,
  tasbihDhikr: 0,
  gamification: {
    points: 0,
    streak: 0,
    level: 1,
    prayersDone: {},
    lastActiveDate: null
  },
  bookmarks: [],
  lastRead: null,
  comfortMode: false,
  calcMethod: 4, // أم القرى
};

// تحميل البيانات المحفوظة
function loadState() {
  try {
    const saved = localStorage.getItem('noor_app_state');
    if (saved) {
      const parsed = JSON.parse(saved);
      appState = {...appState, ...parsed};
    }
  } catch(e) {}
}
function saveState() {
  try { localStorage.setItem('noor_app_state', JSON.stringify(appState)); } catch(e) {}
}

// ===== حساب أوقات الصلاة =====
function toRad(d) { return d * Math.PI / 180; }
function toDeg(r) { return r * 180 / Math.PI; }

function calculatePrayerTimes(lat, lng, date) {
  const jd = julianDate(date);
  const D = jd - 2451545.0;
  const g = normalize(357.529 + 0.98560028 * D, 360);
  const q = normalize(280.459 + 0.98564736 * D, 360);
  const L = normalize(q + 1.915 * Math.sin(toRad(g)) + 0.020 * Math.sin(toRad(2*g)), 360);
  const e = 23.439 - 0.00000036 * D;
  const RA = toDeg(Math.atan2(Math.cos(toRad(e)) * Math.sin(toRad(L)), Math.cos(toRad(L)))) / 15;
  const Dec = toDeg(Math.asin(Math.sin(toRad(e)) * Math.sin(toRad(L))));
  const EqT = q/15 - normalize(RA, 24);

  const lngHour = lng / 15;
  let noon = 12 + lngHour - EqT;
  // توقيت غرينتش +3 للسعودية (تقريبي)
  const tz = 3;
  noon = noon; // حساب بالتوقيت العالمي

  // زاوية الفجر والعراء حسب طريقة أم القرى
  const fajrAngle = 18.5;
  const ishaAngle = 19; // أم القرى تستخدم 90 دقيقة بعد المغرب تقريباً

  const sunrise = noon - sunAngleTime(0.833, lat, Dec);
  const fajr = noon - sunAngleTime(fajrAngle, lat, Dec);
  const sunset = noon + sunAngleTime(0.833, lat, Dec);
  const maghrib = sunset;
  // العشاء: 90 دقيقة بعد المغرب (أم القرى في رمضان 120)
  const isha = maghrib + 1.5; // 90 دقيقة
  const asr = noon + sunAngleTime(asrAngle(lat, Dec, 'Shafi'), lat, Dec);

  const adjust = tz - lngHour;

  return {
    Fajr: formatTime(fajr + adjust),
    Sunrise: formatTime(sunrise + adjust),
    Dhuhr: formatTime(noon + adjust),
    Asr: formatTime(asr + adjust),
    Maghrib: formatTime(maghrib + adjust),
    Isha: formatTime(isha + adjust),
  };
}

function julianDate(date) {
  const y = date.getFullYear();
  const m = date.getMonth() + 1;
  const d = date.getDate();
  return 367*y - Math.floor(7*(y+Math.floor((m+9)/12))/4) + Math.floor(275*m/9) + d + 1721013.5;
}

function normalize(val, max) {
  val = val % max;
  return val < 0 ? val + max : val;
}

function sunAngleTime(angle, lat, dec) {
  const cosH = (Math.sin(toRad(-angle)) - Math.sin(toRad(lat)) * Math.sin(toRad(dec))) /
               (Math.cos(toRad(lat)) * Math.cos(toRad(dec)));
  if (cosH > 1) return 0; // شمس لا تغرب
  if (cosH < -1) return 12; // شمس لا تشرق
  return toDeg(Math.acos(cosH)) / 15;
}

function asrAngle(lat, dec, method) {
  const noonAlt = 90 - Math.abs(lat - dec);
  const factor = method === 'Hanafi' ? 2 : 1;
  return toDeg(Math.atan(1 / (factor + Math.tan(toRad(Math.abs(lat - dec))))));
}

function formatTime(hours) {
  if (hours < 0) hours += 24;
  if (hours >= 24) hours -= 24;
  const h = Math.floor(hours);
  const m = Math.floor((hours - h) * 60);
  return `${String(h).padStart(2,'0')}:${String(m).padStart(2,'0')}`;
}

// ===== التاريخ الهجري =====
function gregToHijri(gDate) {
  const d = gDate.getDate();
  const m = gDate.getMonth() + 1;
  const y = gDate.getFullYear();

  if (y > 1582 || (y === 1582 && m > 10) || (y === 1582 && m === 10 && d > 14)) {
    const jd = Math.floor(1461*(y+4800+Math.floor((m-14)/12))/4) +
               Math.floor(367*(m-2-12*Math.floor((m-14)/12))/12) -
               Math.floor(3*Math.floor((y+4900+Math.floor((m-14)/12))/100)/4) + d - 32075;
    const l = jd - 1948440 + 10632;
    const n = Math.floor((l-1)/10631);
    const l2 = l - 10631*n + 354;
    const j = Math.floor((10985-l2)/5316)*Math.floor((50*l2)/17719) + Math.floor(l2/5670)*Math.floor((43*l2)/15238);
    const l3 = l2 - Math.floor((30-j)/15)*Math.floor((17719*j)/50) - Math.floor(j/16)*Math.floor((15238*j)/43) + 29;
    const hm = Math.floor((24*l3)/709);
    const hd = l3 - Math.floor((709*hm)/24);
    const hy = 30*n + j - 30;
    return {year: hy, month: hm, day: hd};
  }
  return {year: 1446, month: 7, day: 1};
}

const hijriMonths = ['محرم','صفر','ربيع الأول','ربيع الثاني','جمادى الأولى','جمادى الآخرة','رجب','شعبان','رمضان','شوال','ذو القعدة','ذو الحجة'];

// ===== القبلة =====
function calculateQibla(lat, lng) {
  const kaabaLat = 21.4225;
  const kaabaLng = 39.8262;
  const latR = toRad(lat);
  const dLng = toRad(kaabaLng - lng);
  const y = Math.sin(dLng);
  const x = Math.cos(latR) * Math.tan(toRad(kaabaLat)) - Math.sin(latR) * Math.cos(dLng);
  return (toDeg(Math.atan2(y, x)) + 360) % 360;
}

// ===== تهيئة التطبيق =====
function initApp() {
  loadState();

  // محاولة الحصول على الموقع
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(
      pos => {
        appState.lat = pos.coords.latitude;
        appState.lng = pos.coords.longitude;
        appState.locationName = `${pos.coords.latitude.toFixed(2)}°, ${pos.coords.longitude.toFixed(2)}°`;
        saveState();
        updatePrayerTimes();
        updateQibla();
        document.getElementById('userLocation').textContent = appState.locationName;
      },
      err => {
        updatePrayerTimes();
        updateQibla();
        document.getElementById('userLocation').textContent = appState.locationName + " (افتراضي)";
      },
      {enableHighAccuracy: true, timeout: 8000}
    );
  }

  updateDates();
  updatePrayerTimes();
  updateQibla();
  renderSurahList();
  renderAdhkar('morning');
  renderTasbihSelect();
  updateDailyContent();
  updateGamification();
  startCountdown();

  // إخفاء شاشة التحميل
  setTimeout(() => {
    document.getElementById('loadingScreen').classList.add('hide');
    setTimeout(() => document.getElementById('loadingScreen').remove(), 600);
  }, 2000);
}

// ===== التحديثات =====
function updateDates() {
  const now = new Date();
  const hijri = gregToHijri(now);
  document.getElementById('hijriDate').textContent =
    `${hijri.day} ${hijriMonths[hijri.month-1]} ${hijri.year} هـ`;
  document.getElementById('gregDate').textContent =
    now.toLocaleDateString('ar-SA', {year:'numeric', month:'long', day:'numeric'});
}

function updatePrayerTimes() {
  const times = calculatePrayerTimes(appState.lat, appState.lng, new Date());
  appState.prayerTimes = times;

  const prayerNames = {
    Fajr: {ar:'الفجر', icon:'fa-sun', cls:'fajr'},
    Sunrise: {ar:'الشروق', icon:'fa-cloud-sun', cls:'shuruq'},
    Dhuhr: {ar:'الظهر', icon:'fa-sun', iconCls:'fa-solid', cls:'dhuhr'},
    Asr: {ar:'العصر', icon:'fa-cloud-sun', cls:'asr'},
    Maghrib: {ar:'المغرب', icon:'fa-moon', cls:'maghrib'},
    Isha: {ar:'العشاء', icon:'fa-star', cls:'isha'}
  };

  const grid = document.getElementById('prayerGrid');
  grid.innerHTML = '';
  const now = new Date();
  const currentMinutes = now.getHours() * 60 + now.getMinutes();

  let nextPrayer = null;
  const keys = Object.keys(times);

  keys.forEach(key => {
    const info = prayerNames[key];
    const [h,m] = times[key].split(':').map(Number);
    const pMinutes = h * 60 + m;
    const isPassed = currentMinutes > pMinutes;
    const isNext = !isPassed && !nextPrayer;

    if (isNext) nextPrayer = key;

    const item = document.createElement('div');
    item.className = `prayer-item ${isPassed ? 'passed' : ''} ${isNext ? 'active-prayer' : ''}`;

    const doneKey = `${new Date().toDateString()}_${key}`;
    const isDone = appState.gamification.prayersDone[doneKey];

    item.innerHTML = `
      <div class="prayer-icon ${info.cls}"><i class="fas ${info.icon}"></i></div>
      <div class="prayer-info">
        <div class="prayer-name">${info.ar}</div>
        <div class="prayer-time-val">${times[key]}</div>
      </div>
      ${key !== 'Sunrise' ? `<div class="prayer-check ${isDone ? 'done' : ''}" onclick="togglePrayerDone('${key}',event)">
        <i class="fas fa-check"></i>
      </div>` : ''}
    `;
    grid.appendChild(item);
  });

  // تحديث الصلاة القادمة
  if (nextPrayer) {
    document.getElementById('nextPrayerName').textContent = prayerNames[nextPrayer].ar;
    document.getElementById('nextPrayerTime').textContent = times[nextPrayer];
  } else {
    document.getElementById('nextPrayerName').textContent = 'الفجر';
    document.getElementById('nextPrayerTime').textContent = times.Fajr;
  }
}

function startCountdown() {
  setInterval(() => {
    if (!appState.prayerTimes) return;
    const now = new Date();
    const currentMinutes = now.getHours() * 60 + now.getMinutes() + now.getSeconds()/60;

    const keys = ['Fajr','Sunrise','Dhuhr','Asr','Maghrib','Isha'];
    let nextTime = null;

    for (const key of keys) {
      const [h,m] = appState.prayerTimes[key].split(':').map(Number);
      const pMin = h * 60 + m;
      if (pMin > currentMinutes) { nextTime = {key, minutes: pMin}; break; }
    }

    if (!nextTime) {
      // بعد العشاء - الفجر غداً
      const [h,m] = appState.prayerTimes.Fajr.split(':').map(Number);
      nextTime = {key:'Fajr', minutes: h*60+m+24*60};
    }

    const diff = nextTime.minutes - currentMinutes;
    const diffSec = Math.floor(diff * 60);
    const hours = Math.floor(diffSec / 3600);
    const mins = Math.floor((diffSec % 3600) / 60);
    const secs = diffSec % 60;

    document.getElementById('cdH').textContent = String(hours).padStart(2,'0');
    document.getElementById('cdM').textContent = String(mins).padStart(2,'0');
    document.getElementById('cdS').textContent = String(secs).padStart(2,'0');
  }, 1000);

  // تحديث أوقات الصلاة كل دقيقة
  setInterval(updatePrayerTimes, 60000);
}

function updateQibla() {
  const qibla = calculateQibla(appState.lat, appState.lng);
  document.getElementById('qiblaNeedle').style.transform = `rotate(${qibla}deg)`;
  document.getElementById('qiblaDegree').innerHTML = `${qibla.toFixed(1)}° <small>من الشمال</small>`;

  // محاولة استخدام بوصلة الجهاز
  if (window.DeviceOrientationEvent) {
    window.addEventListener('deviceorientation', e => {
      if (e.alpha !== null) {
        const heading = e.alpha;
        const adjustedQibla = (qibla - heading + 360) % 360;
        document.getElementById('qiblaNeedle').style.transform = `rotate(${adjustedQibla}deg)`;
      }
    });
  }
}

function updateDailyContent() {
  const dayIndex = new Date().getDate() % ahadith.length;
  const duaIndex = new Date().getDate() % dailyDuas.length;
  document.getElementById('dailyHadith').textContent = ahadith[dayIndex].text;
  document.getElementById('dailyHadithSource').textContent = ahadith[dayIndex].source;
  document.getElementById('dailyDua').textContent = dailyDuas[duaIndex];
}

// ===== التنقل =====
function switchTab(tab) {
  document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
  document.getElementById('tab-' + tab).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  document.querySelector(`.nav-item[data-tab="${tab}"]`).classList.add('active');
}

// ===== الصلاة - تحديد الإتمام =====
function togglePrayerDone(prayer, event) {
  event.stopPropagation();
  const doneKey = `${new Date().toDateString()}_${prayer}`;
  const wasDone = appState.gamification.prayersDone[doneKey];

  if (wasDone) {
    delete appState.gamification.prayersDone[doneKey];
    appState.gamification.points = Math.max(0, appState.gamification.points - 10);
  } else {
    appState.gamification.prayersDone[doneKey] = true;
    appState.gamification.points += 10;
    showToast(`تم تسجيل صلاة ${prayer === 'Fajr' ? 'الفجر' : prayer === 'Dhuhr' ? 'الظهر' : prayer === 'Asr' ? 'العصر' : prayer === 'Maghrib' ? 'المغرب' : 'العشاء'} +10 نقاط`);
  }

  appState.gamification.lastActiveDate = new Date().toDateString();
  saveState();
  updatePrayerTimes();
  updateGamification();
}

// ===== القرآن =====
function renderSurahList() {
  const list = document.getElementById('surahList');
  list.innerHTML = '';
  surahsData.forEach(s => {
    const item = document.createElement('div');
    item.className = 'surah-item';
    item.dataset.name = s.name;
    item.dataset.nameEn = s.nameEn;
    item.onclick = () => openSurah(s.id);
    item.innerHTML = `
      <div class="surah-num">${s.id}</div>
      <div class="surah-details">
        <div class="surah-name-ar">${s.name}</div>
        <div class="surah-meta">${s.verses} آية · ${s.nameEn}</div>
      </div>
      <span class="surah-type">${s.type}</span>
    `;
    list.appendChild(item);
  });
}

function filterSurahs() {
  const query = document.getElementById('surahSearch').value.trim();
  document.querySelectorAll('.surah-item').forEach(item => {
    const name = item.dataset.name || '';
    const nameEn = item.dataset.nameEn || '';
    const match = name.includes(query) || nameEn.toLowerCase().includes(query.toLowerCase());
    item.style.display = match ? 'flex' : 'none';
  });
}

function openSurah(id) {
  const surah = surahsData.find(s => s.id === id);
  if (!surah) return;

  document.getElementById('surahViewTitle').textContent = `سورة ${surah.name}`;
  const body = document.getElementById('surahViewBody');
  body.innerHTML = '';

  if (id !== 1 && id !== 9) {
    body.innerHTML += `<div class="bismillah">بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ</div>`;
  }

  const container = document.createElement('div');
  container.className = 'ayah-container';

  surah.ayat.forEach((ayah, i) => {
    const span = document.createElement('span');
    span.className = 'ayah-text';
    span.textContent = ayah + ' ';
    span.onclick = () => highlightAyah(span);
    container.appendChild(span);

    const num = document.createElement('span');
    num.className = 'ayah-num';
    num.textContent = i + 1;
    container.appendChild(num);
  });

  body.appendChild(container);
  document.getElementById('surahView').classList.add('active');

  // حفظ آخر قراءة
  appState.lastRead = {id: surah.id, name: surah.name, ayah: 1};
  saveState();
  updateLastRead();

  // نقاط الجاميفيكشن
  appState.gamification.points += 5;
  saveState();
  updateGamification();
}

function highlightAyah(el) {
  document.querySelectorAll('.ayah-text.highlighted').forEach(a => a.classList.remove('highlighted'));
  el.classList.add('highlighted');
}

function closeSurahView() {
  document.getElementById('surahView').classList.remove('active');
}

function updateLastRead() {
  if (appState.lastRead) {
    document.getElementById('lastReadCard').style.display = 'block';
    document.getElementById('lastReadName').textContent = `سورة ${appState.lastRead.name}`;
    document.getElementById('lastReadAyah').textContent = `الآية ${appState.lastRead.ayah}`;
  }
}

function openLastRead() {
  if (appState.lastRead) openSurah(appState.lastRead.id);
}

// ===== الأذكار =====
function switchAdhkar(cat) {
  appState.currentAdhkar = cat;
  document.querySelectorAll('.adhkar-tab').forEach(t => t.classList.remove('active'));
  document.querySelector(`.adhkar-tab[data-cat="${cat}"]`).classList.add('active');
  renderAdhkar(cat);
}

function renderAdhkar(cat) {
  const container = document.getElementById('adhkarContent');
  container.innerHTML = '';
  const data = adhkarData[cat] || [];

  data.forEach((dhikr, i) => {
    const card = document.createElement('div');
    card.className = 'card dhikr-card card-pattern';
    const progress = dhikr.count > 0 ? Math.min(100, (dhikr.current / dhikr.count) * 100) : 0;

    card.innerHTML = `
      <div class="dhikr-text">${dhikr.text}</div>
      <div class="dhikr-count-row">
        <span class="dhikr-target">${dhikr.current} / ${dhikr.count}</span>
        <div class="dhikr-progress"><div class="dhikr-progress-bar" style="width:${progress}%"></div></div>
      </div>
      <div class="dhikr-tap-area" onclick="dhikrTap('${cat}',${i},this)">
        <div class="dhikr-tap-count">${dhikr.current}</div>
        <div class="dhikr-tap-label">اضغط للعد</div>
      </div>
    `;
    container.appendChild(card);
  });
}

function dhikrTap(cat, index, el) {
  const dhikr = adhkarData[cat][index];
  if (dhikr.current < dhikr.count) {
    dhikr.current++;
    const progress = (dhikr.current / dhikr.count) * 100;
    el.querySelector('.dhikr-tap-count').textContent = dhikr.current;
    el.parentElement.querySelector('.dhikr-target').textContent = `${dhikr.current} / ${dhikr.count}`;
    el.parentElement.querySelector('.dhikr-progress-bar').style.width = progress + '%';

    if (dhikr.current >= dhikr.count) {
      el.style.borderColor = 'var(--success)';
      el.style.background = 'rgba(46,204,113,0.08)';
      el.querySelector('.dhikr-tap-label').textContent = 'تم';
      appState.gamification.points += 3;
      saveState();
      updateGamification();
      showToast('تم الذكر +3 نقاط');
    }
  }
}

// ===== السبحة =====
const tasbihDhikr = [
  "سبحان الله",
  "الحمد لله",
  "الله أكبر",
  "لا إله إلا الله",
  "أستغفر الله",
  "لا حول ولا قوة إلا بالله",
  "سبحان الله وبحمده",
  "سبحان الله العظيم"
];

function renderTasbihSelect() {
  const container = document.getElementById('tasbihSelect');
  container.innerHTML = '';
  tasbihDhikr.forEach((d, i) => {
    const opt = document.createElement('div');
    opt.className = `tasbih-dhikr-opt ${i === 0 ? 'active' : ''}`;
    opt.textContent = d;
    opt.onclick = () => {
      document.querySelectorAll('.tasbih-dhikr-opt').forEach(o => o.classList.remove('active'));
      opt.classList.add('active');
      appState.tasbihDhikr = i;
      appState.tasbihCount = 0;
      document.getElementById('tasbihCount').textContent = '0';
      document.getElementById('tasbihLabel').textContent = d;
      saveState();
    };
    container.appendChild(opt);
  });
}

function tasbihTap() {
  appState.tasbihCount++;
  document.getElementById('tasbihCount').textContent = appState.tasbihCount;
  const btn = document.getElementById('tasbihBtn');
  btn.classList.remove('anim');
  void btn.offsetWidth; // إعادة التحريك
  btn.classList.add('anim');

  // اهتزاز خفيف
  if (navigator.vibrate) navigator.vibrate(15);

  // نقاط كل 33
  if (appState.tasbihCount % 33 === 0) {
    appState.gamification.points += 5;
    showToast(`أتممت ${appState.tasbihCount} تسبيحة +5 نقاط`);
    showConfetti();
    saveState();
    updateGamification();
  }
  saveState();
}

function tasbihReset() {
  appState.tasbihCount = 0;
  document.getElementById('tasbihCount').textContent = '0';
  saveState();
}

function tasbihUndo() {
  if (appState.tasbihCount > 0) {
    appState.tasbihCount--;
    document.getElementById('tasbihCount').textContent = appState.tasbihCount;
    saveState();
  }
}

function openTasbih() {
  switchTab('adhkar');
  // التمرير إلى السبحة
  setTimeout(() => {
    document.querySelector('.tasbih-section').scrollIntoView({behavior:'smooth'});
  }, 300);
}

// ===== الجاميفيكشن =====
const levels = [
  {name:'مبتدئ', min:0, max:100},
  {name:'محافظ', min:100, max:300},
  {name:'مقيم', min:300, max:600},
  {name:'حافظ', min:600, max:1000},
  {name:'مخلص', min:1000, max:2000},
  {name:'مؤمن', min:2000, max:5000},
  {name:'مُحسن', min:5000, max:Infinity},
];

function updateGamification() {
  const g = appState.gamification;

  // حساب اليوم المتتالي
  const today = new Date().toDateString();
  if (g.lastActiveDate !== today) {
    const yesterday = new Date(Date.now() - 86400000).toDateString();
    if (g.lastActiveDate === yesterday) {
      g.streak++;
    } else if (g.lastActiveDate !== today) {
      g.streak = 1;
    }
    g.lastActiveDate = today;
    saveState();
  }

  // حساب المستوى
  let currentLevel = levels[0];
  let levelIndex = 0;
  for (let i = 0; i < levels.length; i++) {
    if (g.points >= levels[i].min) {
      currentLevel = levels[i];
      levelIndex = i;
    }
  }

  g.level = levelIndex + 1;

  document.getElementById('gamifyPoints').textContent = g.points;
  document.getElementById('gamifyStreak').textContent = g.streak;
  document.getElementById('gamifyLevel').textContent = g.level;
  document.getElementById('levelName').textContent = currentLevel.name;

  const progress = currentLevel.max === Infinity ? 100 :
    ((g.points - currentLevel.min) / (currentLevel.max - currentLevel.min)) * 100;
  document.getElementById('levelBarFill').style.width = progress + '%';
  document.getElementById('levelProgress').textContent =
    currentLevel.max === Infinity ? `${g.points} نقطة` :
    `${g.points}/${currentLevel.max}`;

  // شريط الأسبوع
  const streakRow = document.getElementById('streakRow');
  streakRow.innerHTML = '';
  const dayNames = ['س','أ','ث','أ','خ','ج','س'];
  const todayDay = new Date().getDay();
  for (let i = 0; i < 7; i++) {
    const d = document.createElement('div');
    d.className = 'streak-day';
    d.title = dayNames[i];

    // الأيام الماضية من هذا الأسبوع
    const daysAgo = (todayDay - i + 7) % 7;
    const checkDate = new Date(Date.now() - daysAgo * 86400000);
    const dateKey = checkDate.toDateString();

    if (i <= todayDay) {
      const hasPrayer = Object.keys(g.prayersDone).some(k => k.startsWith(dateKey));
      if (hasPrayer) d.classList.add('active');
      if (i === todayDay) d.classList.add('today');
    }

    streakRow.appendChild(d);
  }
}

// ===== الإعدادات =====
function openSettings() {
  document.getElementById('settingsModal').classList.add('active');
  document.getElementById('comfortToggle').classList.toggle('active', appState.comfortMode);
}
function closeSettings() {
  document.getElementById('settingsModal').classList.remove('active');
}

function toggleComfort() {
  appState.comfortMode = !appState.comfortMode;
  document.body.classList.toggle('comfort-mode', appState.comfortMode);
  document.getElementById('comfortToggle').classList.toggle('active', appState.comfortMode);
  document.getElementById('comfortBtn').style.color = appState.comfortMode ? 'var(--accent)' : '';
  saveState();
}

function toggleNotif() {
  const toggle = document.getElementById('notifToggle');
  toggle.classList.toggle('active');
  if (toggle.classList.contains('active') && 'Notification' in window) {
    Notification.requestPermission();
  }
}

// ===== النوافذ المنبثقة =====
function showCalendar() {
  const modal = document.getElementById('calendarModal');
  const content = document.getElementById('calendarContent');
  const hijri = gregToHijri(new Date());

  let html = `<div style="text-align:center;margin-bottom:20px;">
    <div style="font-family:'Amiri',serif;font-size:28px;color:var(--accent);font-weight:700;">
      ${hijri.year} هـ
    </div>
    <div style="color:var(--fg2);margin-top:4px;">${hijriMonths[hijri.month-1]}</div>
  </div>`;

  html += '<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">';
  islamicEvents.forEach(ev => {
    const isCurrentMonth = ev.month === hijri.month;
    html += `<div style="padding:10px;border-radius:8px;
      background:${isCurrentMonth ? 'rgba(212,168,67,0.1)' : 'var(--card)'};
      border:1px solid ${isCurrentMonth ? 'rgba(212,168,67,0.2)' : 'var(--border)'};">
      <div style="font-size:11px;color:var(--accent);font-weight:600;">${ev.day} ${hijriMonths[ev.month-1]}</div>
      <div style="font-size:12px;color:var(--fg);margin-top:2px;">${ev.name}</div>
    </div>`;
  });
  html += '</div>';

  content.innerHTML = html;
  modal.classList.add('active');
}

function closeModal(id) {
  document.getElementById(id).classList.remove('active');
}

// إغلاق النوافذ بالنقر خارجها
document.querySelectorAll('.modal-overlay').forEach(modal => {
  modal.addEventListener('click', e => {
    if (e.target === modal) modal.classList.remove('active');
  });
});

function showBookmarks() {
  showToast('آياتك المفضلة وملاحظاتك');
}
function showCalcMethods() {
  showToast('طريقة الحساب: أم القرى');
}
function showAlarmSettings() {
  showToast('إعدادات التنبيهات');
}

// ===== التوست =====
function showToast(msg) {
  const toast = document.getElementById('toast');
  document.getElementById('toastText').textContent = msg;
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 2500);
}

// ===== جسيمات الاحتفال =====
function showConfetti() {
  const container = document.getElementById('confetti');
  const colors = ['#D4A843','#10A37F','#E8C76A','#2ECC71','#0B6E4F'];
  for (let i = 0; i < 20; i++) {
    const c = document.createElement('div');
    c.className = 'confetti';
    c.style.left = Math.random() * 100 + 'vw';
    c.style.top = '-10px';
    c.style.background = colors[Math.floor(Math.random() * colors.length)];
    c.style.animationDelay = Math.random() * 0.5 + 's';
    c.style.animationDuration = (1 + Math.random()) + 's';
    container.appendChild(c);
    setTimeout(() => c.remove(), 2500);
  }
}

// ===== تشغيل التطبيق =====
document.addEventListener('DOMContentLoaded', initApp);
</script>
</body>
</html>
