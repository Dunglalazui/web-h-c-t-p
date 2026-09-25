<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Địa Lí 12 — Học & Luyện</title>
  <style>
    :root{
      --navy:#0c1830;
      --navy2:#17253d;
      --green:#00a878;
      --green2:#00c896;
      --mint:#dff9f1;
      --bg:#f4f7fa;
      --text:#172033;
      --muted:#71809a;
      --border:#e1e8f0;
      --white:#fff;
      --orange:#ff9f00;
      --red:#ff7043;
      --shadow:0 8px 25px rgba(20,35,60,.08);
      --radius:18px;
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;background:var(--bg);color:var(--text)}
    button,input{font:inherit}
    button{cursor:pointer;border:0}
    .hidden{display:none!important}

    /* AUTH */
    .auth-screen{
      min-height:100vh;display:grid;place-items:center;padding:30px;
      background:linear-gradient(135deg,#071329 0%,#0d2d36 55%,#063e34 100%);
    }
    .auth-card{
      width:min(100%,980px);min-height:600px;background:white;border-radius:28px;
      overflow:hidden;display:grid;grid-template-columns:1.05fr .95fr;box-shadow:0 25px 70px rgba(0,0,0,.25)
    }
    .auth-brand{
      color:white;padding:55px;background:
      radial-gradient(circle at 80% 20%,rgba(0,200,150,.3),transparent 30%),
      linear-gradient(145deg,#0c1830,#003f3a);
      display:flex;flex-direction:column;justify-content:center
    }
    .brand-icon{width:58px;height:58px;border-radius:17px;background:var(--green2);display:grid;place-items:center;font-size:29px;margin-bottom:24px}
    .auth-brand h1{font-size:42px;line-height:1.05;margin:0 0 18px}
    .auth-brand p{color:#c8d7dd;line-height:1.7;max-width:450px}
    .feature-list{list-style:none;padding:0;margin:28px 0 0}
    .feature-list li{margin:15px 0;color:#e4eeee}
    .auth-form{padding:55px 50px;display:flex;flex-direction:column;justify-content:center}
    .auth-form h2{font-size:30px;margin:0 0 8px}
    .auth-sub{color:var(--muted);margin:0 0 28px}
    .tabs{display:flex;background:#f0f4f7;border-radius:12px;padding:4px;margin-bottom:25px}
    .tabs button{flex:1;background:transparent;padding:11px;border-radius:9px;color:var(--muted)}
    .tabs button.active{background:#fff;color:var(--green);font-weight:700;box-shadow:0 2px 8px #dce3e8}
    .field{margin-bottom:16px}
    .field label{display:block;font-size:13px;font-weight:700;margin-bottom:7px}
    .field input{width:100%;padding:13px 14px;border:1px solid var(--border);border-radius:11px;outline:none}
    .field input:focus{border-color:var(--green);box-shadow:0 0 0 3px rgba(0,168,120,.12)}
    .primary{background:var(--green);color:white;padding:13px 18px;border-radius:11px;font-weight:800}
    .primary:hover{background:#008e68}
    .message{min-height:20px;color:#d9534f;font-size:13px;margin-top:10px}
    .demo-note{font-size:12px;color:var(--muted);margin-top:18px;line-height:1.5}

    /* APP */
    .app{min-height:100vh}
    .sidebar{
      position:fixed;left:0;top:0;bottom:0;width:325px;background:var(--navy);color:white;padding:25px 12px;
      z-index:20;display:flex;flex-direction:column
    }
    .logo{display:flex;align-items:center;gap:13px;padding:0 9px 22px}
    .logo-icon{width:48px;height:48px;border-radius:14px;background:var(--green2);display:grid;place-items:center;font-size:24px}
    .logo-title{font-weight:900;font-size:16px}.logo-teacher{font-size:12px;color:#00dca5;margin-top:4px}
    .profile{background:#192741;border:1px solid #263753;border-radius:15px;padding:15px;margin-bottom:22px;display:flex;gap:12px;align-items:center}
    .avatar{width:43px;height:43px;border-radius:50%;background:#00a878;display:grid;place-items:center;font-weight:900}
    .profile strong{display:block}.level{font-size:12px;color:#9ee9d4;margin-top:5px}
    .section-label{font-size:12px;color:#93a2b9;font-weight:800;margin:0 10px 10px}
    .nav{display:grid;gap:5px}
    .nav button{color:#b9c5d5;background:transparent;text-align:left;padding:12px 14px;border-radius:11px;font-weight:600;display:flex;justify-content:space-between;align-items:center}
    .nav button:hover,.nav button.active{background:var(--green);color:white}
    .badge{font-size:11px;background:#22334e;color:#d9e3ee;padding:4px 8px;border-radius:7px}
    .nav button.active .badge{background:rgba(255,255,255,.15);color:#fff}
    .sidebar-bottom{margin-top:auto;padding:15px 10px;border-top:1px solid #203049;color:#92a0b6;font-size:12px;line-height:1.5}
    .logout{margin-top:8px;background:#202f48!important;color:#e5ebf1!important}

    .main{margin-left:325px;padding:0 34px 50px}
    .topbar{height:62px;display:flex;justify-content:flex-end;align-items:center;gap:15px;background:white;margin:0 -34px 0;padding:0 34px;border-bottom:1px solid var(--border)}
    .top-pill{border:1px solid #ffe0a2;border-radius:20px;padding:8px 13px;color:#db8700;font-size:13px;font-weight:700}
    .top-pill.fire{border-color:#ffd0bc;color:#ed6232}
    .hero{margin:0 auto;padding:42px 38px;border-radius:25px;background:linear-gradient(110deg,#0d1830,#003f3a);color:white;display:flex;justify-content:space-between;gap:30px;max-width:1260px;box-shadow:var(--shadow)}
    .hero-tag{display:inline-block;padding:7px 12px;border:1px solid #087e69;border-radius:18px;color:#50dfbd;background:rgba(0,170,130,.12);font-size:13px;font-weight:800}
    .hero h1{font-size:36px;margin:18px 0 10px}.hero p{color:#c7d4dc;max-width:720px;line-height:1.6}
    .hero-meta{display:flex;gap:10px;margin-top:18px}.hero-meta span{background:#18283f;border:1px solid #31415b;padding:7px 12px;border-radius:9px;font-size:13px}
    .next-card{width:350px;background:#192b42;border:1px solid #137f6c;border-radius:18px;padding:22px;flex-shrink:0}
    .next-label{color:#50dfbd;font-size:12px;font-weight:900}.next-card h3{margin:12px 0 7px}.next-card p{font-size:13px;color:#bac8d3;line-height:1.5}
    .next-card button{width:100%;padding:12px;border-radius:10px;background:#00a878;color:#fff;font-weight:800}

    .stats{display:grid;grid-template-columns:repeat(4,1fr);gap:18px;max-width:1260px;margin:28px auto}
    .stat{background:white;border:1px solid var(--border);border-radius:18px;padding:20px;display:flex;gap:14px;align-items:center;box-shadow:0 3px 12px rgba(20,35,60,.04)}
    .stat-icon{width:50px;height:50px;border-radius:13px;background:#fff7df;display:grid;place-items:center;font-size:24px}
    .stat:nth-child(2) .stat-icon{background:#e9fbf5}.stat:nth-child(3) .stat-icon{background:#fff0e8}.stat:nth-child(4) .stat-icon{background:#eafcfb}
    .stat small{color:var(--muted);font-weight:700}.stat strong{display:block;font-size:21px;margin-top:4px}.stat strong em{font-style:normal;color:#ee8d00;font-size:13px}

    .content-grid{display:grid;grid-template-columns:minmax(0,1fr) 390px;gap:26px;max-width:1260px;margin:auto}
    .panel{background:white;border:1px solid var(--border);border-radius:18px;padding:26px;box-shadow:0 3px 12px rgba(20,35,60,.04)}
    .panel+.panel{margin-top:26px}
    .panel-head{display:flex;justify-content:space-between;align-items:center;gap:10px}.panel h2{font-size:19px;margin:0}.panel-head a{color:#008d6b;font-weight:800;font-size:13px;cursor:pointer}
    .sub{color:var(--muted);font-size:13px;margin:6px 0 20px}
    .progress-track{height:14px;background:#edf2f6;border-radius:20px;overflow:hidden}.progress-fill{height:100%;width:0%;background:linear-gradient(90deg,#00ae84,#00c79a);border-radius:20px;transition:.4s}
    .progress-info{text-align:right;margin-top:-30px;margin-bottom:18px;color:#008f6c;font-weight:800;font-size:13px}
    .categories{display:grid;grid-template-columns:repeat(5,1fr);gap:10px}
    .category{border:1px solid #e5ebf1;border-radius:13px;padding:15px 8px;text-align:center}.category b{font-size:13px}.category strong{display:block;margin:8px 0;font-size:14px}.category span{background:#e8edf2;padding:4px 8px;border-radius:6px;font-size:11px;color:#617086}
    .lesson{display:flex;justify-content:space-between;align-items:center;border:1px solid #e6ebf0;border-radius:14px;padding:16px;margin-top:12px;gap:15px}
    .lesson-no{color:#00a67b;font-size:12px;font-weight:900}.lesson h3{font-size:15px;margin:4px 0}.lesson p{margin:0;color:var(--muted);font-size:12px}.lesson button{background:#00a878;color:white;padding:10px 15px;border-radius:9px;font-weight:800;white-space:nowrap}
    .side-card{background:white;border:1px solid var(--border);border-radius:18px;padding:26px}.side-card h2{margin:0 0 20px;font-size:19px}
    .empty{border:1px dashed #dbe4ec;border-radius:14px;padding:35px 20px;text-align:center;color:var(--muted)}
    .empty .medal{font-size:34px}.empty strong{display:block;color:#47546b;margin:10px 0 7px}
    .tip{border-left:4px solid #00a878;background:#f3fcf9;padding:13px 15px;border-radius:8px;margin-top:12px;font-size:13px;line-height:1.5}

    /* Other views */
    .view-title{max-width:1260px;margin:30px auto 20px}.view-title h1{margin:0 0 7px}.view-title p{color:var(--muted)}
    .course-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;max-width:1260px;margin:auto}
    .course{background:#fff;border:1px solid var(--border);border-radius:17px;padding:20px}.course .emoji{font-size:28px}.course h3{margin:12px 0 7px}.course p{font-size:13px;color:var(--muted);line-height:1.5}.course button{margin-top:12px;background:#e8faf4;color:#008e6c;padding:10px 13px;border-radius:9px;font-weight:800}
    .quiz-wrap{max-width:900px;margin:30px auto;background:#fff;border:1px solid var(--border);border-radius:20px;padding:28px}
    .option{display:block;width:100%;text-align:left;background:#f7f9fb;border:1px solid #e2e8ee;padding:14px;border-radius:10px;margin:10px 0}.option:hover{border-color:#00aa7f}.option.correct{background:#e8fbf4;border-color:#00a878}.option.wrong{background:#fff0ed;border-color:#ef775b}
    .score{text-align:center;padding:25px}.score strong{font-size:40px;color:#00a878}
    .admin-stat-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:15px;margin-bottom:20px}.admin-stat{background:#fff;border:1px solid var(--border);border-radius:15px;padding:20px}.admin-stat b{display:block;font-size:25px;margin-top:6px}.admin-table{width:100%;border-collapse:collapse}.admin-table th,.admin-table td{padding:12px;border-bottom:1px solid #e8edf2;text-align:left;font-size:13px}.admin-table th{color:#607089;background:#f7f9fb}.admin-form{display:grid;gap:12px}.admin-form input,.admin-form textarea,.admin-form select{width:100%;padding:11px;border:1px solid var(--border);border-radius:9px;outline:none}.admin-form textarea{min-height:90px;resize:vertical}.danger{background:#fff0ed!important;color:#c74d37!important}.admin-tag{display:inline-block;background:#e8faf4;color:#008e6c;border-radius:7px;padding:4px 8px;font-size:11px;font-weight:800}.admin-only{border-left:4px solid #00a878} 
    @media(max-width:1000px){
      .sidebar{width:235px}.main{margin-left:235px}.content-grid{grid-template-columns:1fr}.next-card{display:none}.stats{grid-template-columns:repeat(2,1fr)}.course-grid{grid-template-columns:1fr 1fr}.categories{grid-template-columns:repeat(3,1fr)}
    }
    @media(max-width:700px){
      .sidebar{position:static;width:100%;height:auto}.sidebar-bottom{display:none}.main{margin-left:0;padding:0 15px 35px}.topbar{margin:0 -15px;padding:0 15px}.hero{border-radius:0 0 18px 18px;padding:28px 20px}.hero h1{font-size:28px}.stats{grid-template-columns:1fr 1fr}.course-grid{grid-template-columns:1fr}.auth-card{grid-template-columns:1fr}.auth-brand{display:none}.auth-form{padding:35px 25px}.categories{grid-template-columns:1fr 1fr}.lesson{align-items:flex-start;flex-direction:column}.topbar{justify-content:center}
    }
  </style>
</head>
<body>

<!-- AUTH -->
<section id="authScreen" class="auth-screen">
  <div class="auth-card">
    <div class="auth-brand">
      <div class="brand-icon">◎</div>
      <h1>Địa Lí 12<br>Học thông minh.</h1>
      <p>Nền tảng luyện tư duy Địa lí theo chương trình GDPT 2018 — học bài, luyện tập, kiểm tra và theo dõi tiến độ.</p>
      <ul class="feature-list">
        <li>✓ 35 bài học được chia theo chuyên đề</li>
        <li>✓ Trắc nghiệm và luyện tập tức thì</li>
        <li>✓ XP, streak và huy hiệu học tập</li>
        <li>✓ Lưu tiến độ ngay trên tài khoản</li>
      </ul>
    </div>
    <div class="auth-form">
      <h2 id="authTitle">Chào mừng trở lại 👋</h2>
      <p class="auth-sub">Đăng nhập để tiếp tục hành trình học Địa lí.</p>
      <div class="tabs">
        <button id="loginTab" class="active" onclick="switchAuth('login')">Đăng nhập</button>
        <button id="registerTab" onclick="switchAuth('register')">Đăng ký</button>
      </div>
      <form id="authForm" onsubmit="handleAuth(event)">
        <div id="nameField" class="field hidden">
          <label>Họ và tên</label>
          <input id="name" type="text" placeholder="Nguyễn Văn A">
        </div>
        <div class="field">
          <label>Email</label>
          <input id="email" type="email" required placeholder="you@example.com">
        </div>
        <div class="field">
          <label>Mật khẩu</label>
          <input id="password" type="password" required minlength="6" placeholder="••••••••">
        </div>
        <button class="primary" type="submit" id="authButton">Đăng nhập</button>
        <div id="authMessage" class="message"></div>
      </form>
      <p class="demo-note">Demo front-end: tài khoản được lưu trong trình duyệt bằng localStorage. Khi triển khai thật, hãy thay bằng backend + database + mã hóa mật khẩu.</p>
    </div>
  </div>
</section>

<!-- APP -->
<div id="app" class="app hidden">
  <aside class="sidebar">
    <div class="logo">
      <div class="logo-icon">◎</div>
      <div><div class="logo-title">TƯ DUY ĐỊA LÍ 12</div><div class="logo-teacher">✦ Học & Luyện</div></div>
    </div>
    <div class="profile">
      <div class="avatar" id="avatar">D</div>
      <div><strong id="profileName">Dũng Nguyễn</strong><div class="level">Lớp 12D · ⭐ Lv.1</div></div>
    </div>
    <div class="section-label">HỌC TẬP & RÈN LUYỆN</div>
    <nav class="nav">
      <button class="active" data-view="home" onclick="showView('home',this)">⌂ <span>Trang chủ</span></button>
      <button data-view="lessons" onclick="showView('lessons',this)">▣ <span>Học theo bài</span><span class="badge">35 Bài</span></button>
      <button data-view="practice" onclick="showView('practice',this)">✎ <span>Luyện tập</span></button>
      <button data-view="review" onclick="showView('review',this)">♧ <span>Ôn tập</span><span class="badge">5 Phần</span></button>
      <button data-view="tests" onclick="showView('tests',this)">↪ <span>Kiểm tra</span><span class="badge">15p & HK</span></button>
      <button data-view="achievements" onclick="showView('achievements',this)">♜ <span>Thành tích</span></button>
      <button data-view="profile" onclick="showView('profile',this)">♙ <span>Hồ sơ</span></button>
      <button id="adminNav" data-view="admin" class="hidden" onclick="showView('admin',this)">⚙ <span>Quản trị</span><span class="admin-tag">ADMIN</span></button>
    </nav>
    <div class="sidebar-bottom">
      <div>Chương trình GDPT 2018</div>
      <div>Địa lí Việt Nam · THPT</div>
      <button class="nav logout" onclick="logout()">↩ Đăng xuất</button>
    </div>
  </aside>

  <main class="main">
    <div class="topbar">
      <div class="top-pill">⚡ <span id="xpTop">0</span> XP</div>
      <div class="top-pill fire">🔥 <span id="streakTop">1</span></div>
      <div>🔔</div>
      <div class="avatar" style="width:38px;height:38px" id="topAvatar">D</div>
    </div>

    <div id="view-home" class="view">
      <section class="hero">
        <div>
          <span class="hero-tag">◉ Chương trình Địa lí 12 · GDPT 2018</span>
          <h1>Xin chào, <span id="heroName">Dũng Nguyễn</span>! 👋</h1>
          <p>Chào mừng bạn trở lại rèn luyện tư duy Địa lí. Hãy tiếp tục mục tiêu chinh phục kiến thức và điểm số xuất sắc nhé!</p>
          <div class="hero-meta"><span>Lớp: <b>12D</b></span><span>Môn: <b>Địa lí</b></span></div>
        </div>
        <div class="next-card">
          <div class="next-label">✦ BÀI HỌC TIẾP THEO</div>
          <h3>Bài 1. Vị trí địa lí và phạm vi lãnh thổ</h3>
          <p>Đặc điểm vị trí địa lí, các điểm cực, 3 bộ phận lãnh thổ và ý nghĩa của vị trí.</p>
          <button onclick="startLesson(0)">Học tiếp ngay →</button>
        </div>
      </section>

      <section class="stats">
        <div class="stat"><div class="stat-icon">⚡</div><div><small>Điểm kinh nghiệm</small><strong><span id="xpStat">0</span> <em>XP</em></strong></div></div>
        <div class="stat"><div class="stat-icon">♙</div><div><small>Cấp độ học tập</small><strong id="levelStat">Cấp 1</strong></div></div>
        <div class="stat"><div class="stat-icon">🔥</div><div><small>Chuỗi ngày học</small><strong><span id="streakStat">1</span> <em>ngày</em></strong></div></div>
        <div class="stat"><div class="stat-icon">↗</div><div><small>Điểm trung bình</small><strong id="avgStat">Chưa kiểm tra</strong></div></div>
      </section>

      <div class="content-grid">
        <div>
          <section class="panel">
            <div class="panel-head"><h2>◎ Tiến độ hoàn thành chương trình</h2><a onclick="showView('lessons')">Xem tất cả 35 bài →</a></div>
            <p class="sub">Học theo hệ thống chuyên đề và theo dõi tiến độ của bạn.</p>
            <div class="progress-track"><div id="progressFill" class="progress-fill"></div></div>
            <div class="progress-info"><span id="progressText">0 / 35 bài (0%)</span></div>
            <div class="categories">
              <div class="category"><b>Địa lí Tự nhiên</b><strong id="c1">0/6 bài</strong><span>Đang học</span></div>
              <div class="category"><b>Địa lí Dân cư</b><strong id="c2">0/4 bài</strong><span>Đang học</span></div>
              <div class="category"><b>Địa lí Ngành KT</b><strong id="c3">0/13 bài</strong><span>Đang học</span></div>
              <div class="category"><b>Địa lí Vùng KT</b><strong id="c4">0/11 bài</strong><span>Đang học</span></div>
              <div class="category"><b>Địa lí Địa phương</b><strong id="c5">0/1 bài</strong><span>Đang học</span></div>
            </div>
          </section>

          <section class="panel">
            <div class="panel-head"><h2>▣ Bài học trọng tâm</h2><a onclick="showView('lessons')">Xem tất cả →</a></div>
            <p class="sub">Các bài mở đầu đầy đủ lý thuyết, sơ đồ tư duy và bài tập trắc nghiệm.</p>
            <div id="homeLessons"></div>
          </section>
        </div>

        <div>
          <section class="side-card">
            <div class="panel-head"><h2>🏅 Huy hiệu đạt được</h2><a onclick="showView('achievements')">Xem tất cả</a></div>
            <div class="empty"><div class="medal">🏅</div><strong id="badgeStatus">Chưa có huy hiệu nào</strong><span>Hoàn thành bài học và đạt điểm kiểm tra để mở khóa huy hiệu.</span></div>
          </section>
          <section class="side-card" style="margin-top:26px">
            <h2>ⓘ Lưu ý trọng tâm ôn tập</h2>
            <div class="tip"><b>1. Vị trí địa lí Việt Nam</b><br>Ghi nhớ phạm vi lãnh thổ và ý nghĩa của vị trí đối với tự nhiên, kinh tế – xã hội.</div>
            <div class="tip"><b>2. Biển Đông</b><br>Chú ý đặc điểm, tài nguyên, thiên tai và vấn đề khai thác bền vững.</div>
            <div class="tip"><b>3. Địa lí ngành kinh tế</b><br>Luôn kết hợp Atlat, số liệu và biểu đồ khi phân tích.</div>
          </section>
        </div>
      </div>
    </div>

    <div id="view-lessons" class="view hidden"></div>
    <div id="view-practice" class="view hidden"></div>
    <div id="view-review" class="view hidden"></div>
    <div id="view-tests" class="view hidden"></div>
    <div id="view-achievements" class="view hidden"></div>
    <div id="view-profile" class="view hidden"></div>
    <div id="view-admin" class="view hidden"></div>
  </main>
</div>

<script>
const lessons = [
  ["Bài 1","Vị trí địa lí và phạm vi lãnh thổ","Địa lí Tự nhiên"],
  ["Bài 2","Thiên nhiên nhiệt đới ẩm gió mùa","Địa lí Tự nhiên"],
  ["Bài 3","Sự phân hóa đa dạng của thiên nhiên","Địa lí Tự nhiên"],
  ["Bài 4","Vấn đề sử dụng và bảo vệ tài nguyên thiên nhiên","Địa lí Tự nhiên"],
  ["Bài 5","Vấn đề bảo vệ môi trường và phòng chống thiên tai","Địa lí Tự nhiên"],
  ["Bài 6","Đất và sinh vật","Địa lí Tự nhiên"],
  ["Bài 7","Dân số và gia tăng dân số","Địa lí Dân cư"],
  ["Bài 8","Cơ cấu dân số và phân bố dân cư","Địa lí Dân cư"],
  ["Bài 9","Đô thị hóa","Địa lí Dân cư"],
  ["Bài 10","Nguồn lao động và việc làm","Địa lí Dân cư"],
  ["Bài 11","Chuyển dịch cơ cấu kinh tế","Địa lí Ngành KT"],
  ["Bài 12","Nông nghiệp Việt Nam","Địa lí Ngành KT"],
  ["Bài 13","Lâm nghiệp và thủy sản","Địa lí Ngành KT"],
  ["Bài 14","Công nghiệp Việt Nam","Địa lí Ngành KT"],
  ["Bài 15","Giao thông vận tải","Địa lí Ngành KT"],
  ["Bài 16","Thông tin liên lạc","Địa lí Ngành KT"],
  ["Bài 17","Thương mại và du lịch","Địa lí Ngành KT"],
  ["Bài 18","Vùng Trung du và miền núi Bắc Bộ","Địa lí Vùng KT"],
  ["Bài 19","Vùng Đồng bằng sông Hồng","Địa lí Vùng KT"],
  ["Bài 20","Vùng Bắc Trung Bộ","Địa lí Vùng KT"],
  ["Bài 21","Vùng Duyên hải Nam Trung Bộ","Địa lí Vùng KT"],
  ["Bài 22","Vùng Tây Nguyên","Địa lí Vùng KT"],
  ["Bài 23","Vùng Đông Nam Bộ","Địa lí Vùng KT"],
  ["Bài 24","Vùng Đồng bằng sông Cửu Long","Địa lí Vùng KT"],
  ["Bài 25","Phát triển kinh tế biển","Địa lí Vùng KT"],
  ["Bài 26","Các trung tâm kinh tế","Địa lí Vùng KT"],
  ["Bài 27","Liên kết vùng và phát triển bền vững","Địa lí Vùng KT"],
  ["Bài 28","Phân tích số liệu dân cư","Địa lí Ngành KT"],
  ["Bài 29","Phân tích số liệu nông nghiệp","Địa lí Ngành KT"],
  ["Bài 30","Phân tích số liệu công nghiệp","Địa lí Ngành KT"],
  ["Bài 31","Phân tích biểu đồ Địa lí","Địa lí Ngành KT"],
  ["Bài 32","Kĩ năng sử dụng Atlat Địa lí Việt Nam","Địa lí Ngành KT"],
  ["Bài 33","Kĩ năng nhận xét bảng số liệu","Địa lí Ngành KT"],
  ["Bài 34","Kĩ năng vẽ và nhận xét biểu đồ","Địa lí Ngành KT"],
  ["Bài 35","Địa lí địa phương","Địa lí Địa phương"]
];

const questions = [
  {q:"Việt Nam nằm trong khu vực nào của châu Á?",a:["Đông Á","Đông Nam Á","Nam Á","Tây Á"],c:1},
  {q:"Lãnh thổ Việt Nam gồm những bộ phận nào?",a:["Vùng đất, vùng biển, vùng trời","Đất liền và hải đảo","Đất liền, vùng trời","Vùng đất và vùng biển"],c:0},
  {q:"Đặc điểm nổi bật của khí hậu Việt Nam là?",a:["Ôn đới hải dương","Nhiệt đới ẩm gió mùa","Hoang mạc","Cận cực"],c:1},
  {q:"Atlat Địa lí Việt Nam thường được sử dụng để?",a:["Tra cứu và phân tích không gian địa lí","Thay thế hoàn toàn số liệu","Chỉ học thuộc tên địa danh","Chỉ vẽ biểu đồ"],c:0}
];

let currentUser = null;
let state = {xp:0, completed:[], streak:1, avg:null, quizScore:null};

function getUsers(){ return JSON.parse(localStorage.getItem("geo_users") || "{}"); }
function saveUsers(u){ localStorage.setItem("geo_users", JSON.stringify(u)); }
function switchAuth(mode){
  const login = mode === "login";
  document.getElementById("loginTab").classList.toggle("active",login);
  document.getElementById("registerTab").classList.toggle("active",!login);
  document.getElementById("nameField").classList.toggle("hidden",login);
  document.getElementById("authTitle").textContent = login ? "Chào mừng trở lại 👋" : "Tạo tài khoản mới ✨";
  document.querySelector(".auth-sub").textContent = login ? "Đăng nhập để tiếp tục hành trình học Địa lí." : "Đăng ký miễn phí để lưu tiến độ học tập.";
  document.getElementById("authButton").textContent = login ? "Đăng nhập" : "Đăng ký";
  document.getElementById("authMessage").textContent = "";
  document.getElementById("authForm").dataset.mode = mode;
}
document.getElementById("authForm").dataset.mode="login";

const ADMIN_EMAIL = "admin@dialy12.local";
const ADMIN_PASSWORD = "Admin@123";
let isAdmin = false;

function handleAuth(e){
  e.preventDefault();
  const mode = document.getElementById("authForm").dataset.mode;
  const email = document.getElementById("email").value.trim().toLowerCase();
  const password = document.getElementById("password").value;
  const users = getUsers();
  const msg = document.getElementById("authMessage");

  if(mode==="login" && email===ADMIN_EMAIL && password===ADMIN_PASSWORD){
    currentUser=ADMIN_EMAIL;
    isAdmin=true;
    state={xp:0,completed:[],streak:1,avg:null,quizScore:null};
    enterApp("Quản trị viên");
    return;
  }

  if(mode==="register"){
    const name = document.getElementById("name").value.trim();
    if(!name){msg.textContent="Vui lòng nhập họ và tên.";return}
    if(users[email]){msg.textContent="Email này đã được đăng ký.";return}
    users[email] = {name,password,state:{...state}};
    saveUsers(users);
    currentUser=email; state={...users[email].state};
    enterApp(name);
  }else{
    if(!users[email] || users[email].password !== password){
      msg.textContent="Email hoặc mật khẩu không đúng.";return
    }
    currentUser=email; state={...users[email].state};
    enterApp(users[email].name);
  }
}
function enterApp(name){
  document.getElementById("authScreen").classList.add("hidden");
  document.getElementById("app").classList.remove("hidden");
  setNames(name); updateDashboard(); renderHomeLessons();
  document.getElementById("adminNav").classList.toggle("hidden", !isAdmin);
}
function setNames(name){
  document.getElementById("profileName").textContent=name;
  document.getElementById("heroName").textContent=name;
  const letter=(name.trim()[0]||"D").toUpperCase();
  document.getElementById("avatar").textContent=letter;
  document.getElementById("topAvatar").textContent=letter;
}
function persist(){
  const users=getUsers();
  if(currentUser && users[currentUser]){
    users[currentUser].state=state; saveUsers(users);
  }
}
function logout(){
  currentUser=null; isAdmin=false; state={xp:0,completed:[],streak:1,avg:null,quizScore:null};
  document.getElementById("app").classList.add("hidden");
  document.getElementById("authScreen").classList.remove("hidden");
  document.getElementById("authForm").reset(); switchAuth("login");
}
function showView(view,btn){
  document.querySelectorAll(".view").forEach(v=>v.classList.add("hidden"));
  document.getElementById("view-"+view).classList.remove("hidden");
  document.querySelectorAll(".nav button").forEach(b=>b.classList.remove("active"));
  if(btn) btn.classList.add("active");
  if(view==="lessons") renderLessons();
  if(view==="practice") renderPractice();
  if(view==="review") renderReview();
  if(view==="tests") renderTests();
  if(view==="achievements") renderAchievements();
  if(view==="profile") renderProfile();
  if(view==="admin") renderAdmin();
  window.scrollTo({top:0,behavior:"smooth"});
}
function updateDashboard(){
  const done=state.completed.length, pct=Math.round(done/35*100);
  ["xpTop","xpStat"].forEach(id=>document.getElementById(id).textContent=state.xp);
  ["streakTop","streakStat"].forEach(id=>document.getElementById(id).textContent=state.streak);
  document.getElementById("levelStat").textContent="Cấp "+(Math.floor(state.xp/100)+1);
  document.getElementById("avgStat").textContent=state.avg===null?"Chưa kiểm tra":state.avg+"/10";
  document.getElementById("progressFill").style.width=pct+"%";
  document.getElementById("progressText").textContent=`${done} / 35 bài (${pct}%)`;
  const cats=[
    [0,6,"c1"],[6,10,"c2"],[10,23,"c3"],[23,34,"c4"],[34,35,"c5"]
  ];
  cats.forEach(([start,end,id])=>{
    const count=state.completed.filter(i=>i>=start&&i<end).length;
    document.getElementById(id).textContent=`${count}/${end-start} bài`;
  });
  document.getElementById("badgeStatus").textContent=done>=10?"Đã mở khóa huy hiệu đầu tiên!":"Chưa có huy hiệu nào";
  persist();
}
function renderHomeLessons(){
  const box=document.getElementById("homeLessons");
  box.innerHTML=lessons.slice(0,3).map((l,i)=>lessonHTML(l,i)).join("");
}
function lessonHTML(l,i){
  const done=state.completed.includes(i);
  return `<div class="lesson">
    <div><div class="lesson-no">${l[0]} ${done?"· ✓ ĐÃ HOÀN THÀNH":""}</div><h3>${l[1]}</h3><p>${l[2]} · Lý thuyết · Sơ đồ tư duy · Trắc nghiệm</p></div>
    <button onclick="startLesson(${i})">${done?"Ôn lại":"Học ngay"} →</button>
  </div>`;
}
function renderLessons(){
  document.getElementById("view-lessons").innerHTML=`
    <div class="view-title"><h1>📚 Học theo bài</h1><p>35 bài học Địa lí 12 được tổ chức theo chủ đề.</p></div>
    <div class="panel" style="max-width:1260px;margin:auto">
      ${lessons.map((l,i)=>lessonHTML(l,i)).join("")}
    </div>`;
}
function startLesson(i){
  const l=lessons[i];
  const already=state.completed.includes(i);
  const box=document.getElementById("view-lessons");
  showView("lessons");
  box.innerHTML=`
    <div class="view-title"><h1>${l[0]}. ${l[1]}</h1><p>${l[2]} · Bài học Địa lí 12</p></div>
    <div class="panel" style="max-width:950px;margin:auto">
      <h2>🎯 Mục tiêu bài học</h2>
      <p style="line-height:1.7;color:#59677d">Nắm được các khái niệm cốt lõi, biết phân tích mối quan hệ giữa các yếu tố địa lí và vận dụng kiến thức vào câu hỏi thực tế.</p>
      <h2 style="margin-top:28px">🧠 Kiến thức trọng tâm</h2>
      <div class="tip"><b>Khái niệm:</b> Xác định các đặc điểm chính và từ khóa cần ghi nhớ.</div>
      <div class="tip"><b>Phân tích:</b> Liên hệ vị trí, điều kiện tự nhiên, dân cư và hoạt động kinh tế để giải thích hiện tượng.</div>
      <div class="tip"><b>Vận dụng:</b> Kết hợp Atlat, bảng số liệu, biểu đồ và kiến thức thực tế.</div>
      <div style="margin-top:25px;display:flex;gap:10px;flex-wrap:wrap">
        <button class="primary" onclick="completeLesson(${i})">${already?"Đã hoàn thành ✓":"Hoàn thành bài học +20 XP"}</button>
        <button class="primary" style="background:#e8edf2;color:#35445b" onclick="showView('practice')">Làm bài tập →</button>
      </div>
    </div>`;
}
function completeLesson(i){
  if(!state.completed.includes(i)){state.completed.push(i);state.xp+=20;state.streak=Math.max(1,state.streak);updateDashboard();}
  startLesson(i);
}
function renderPractice(){
  document.getElementById("view-practice").innerHTML=`
    <div class="view-title"><h1>✎ Luyện tập</h1><p>Kiểm tra nhanh kiến thức với các câu hỏi trắc nghiệm.</p></div>
    <div class="quiz-wrap">
      <div id="quizArea"></div>
    </div>`;
  runQuiz("practice");
}
function runQuiz(type){
  let index=0,score=0;
  const area=document.getElementById("quizArea");
  function showQ(){
    if(index>=questions.length){
      state.xp+=score*10; state.avg=(score/questions.length*10).toFixed(1); state.quizScore=score;
      updateDashboard();
      area.innerHTML=`<div class="score"><div style="font-size:50px">🎉</div><h2>Hoàn thành!</h2><p>Bạn đúng <b>${score}/${questions.length}</b> câu.</p><strong>${Math.round(score/questions.length*10)}/10</strong><br><button class="primary" style="margin-top:20px" onclick="runQuiz('practice')">Làm lại</button></div>`;
      return;
    }
    const q=questions[index];
    area.innerHTML=`<div style="color:#00a878;font-weight:800">CÂU ${index+1}/${questions.length}</div><h2 style="margin:12px 0 20px">${q.q}</h2>${q.a.map((x,i)=>`<button class="option" onclick="answer(${i})">${String.fromCharCode(65+i)}. ${x}</button>`).join("")}`;
  }
  window.answer=function(choice){
    const q=questions[index];
    document.querySelectorAll(".option").forEach((b,i)=>{b.disabled=true;if(i===q.c)b.classList.add("correct");if(i===choice&&choice!==q.c)b.classList.add("wrong")});
    if(choice===q.c)score++;
    setTimeout(()=>{index++;showQ()},650);
  };
  showQ();
}
function renderReview(){
  document.getElementById("view-review").innerHTML=`
    <div class="view-title"><h1>🧠 Ôn tập theo phần</h1><p>Ôn lại kiến thức trước khi bước vào bài kiểm tra.</p></div>
    <div class="course-grid">
      ${["Địa lí tự nhiên","Dân cư","Các ngành kinh tế","Các vùng kinh tế","Kĩ năng Địa lí"].map((x,i)=>`<div class="course"><div class="emoji">${["🌏","👥","🏭","🗺️","📊"][i]}</div><h3>${x}</h3><p>Tổng hợp kiến thức, từ khóa quan trọng và câu hỏi vận dụng.</p><button onclick="showView('practice')">Ôn tập →</button></div>`).join("")}
    </div>`;
}
function renderTests(){
  document.getElementById("view-tests").innerHTML=`
    <div class="view-title"><h1>📝 Kiểm tra</h1><p>Các bài kiểm tra mô phỏng theo thời lượng và dạng đề.</p></div>
    <div class="course-grid">
      <div class="course"><div class="emoji">⏱️</div><h3>Kiểm tra 15 phút</h3><p>10 câu · Kiến thức theo bài · Thời gian 15 phút.</p><button onclick="showView('practice')">Bắt đầu →</button></div>
      <div class="course"><div class="emoji">📄</div><h3>Kiểm tra 1 tiết</h3><p>30 câu · Tổng hợp nhiều chuyên đề.</p><button onclick="showView('practice')">Bắt đầu →</button></div>
      <div class="course"><div class="emoji">🏆</div><h3>Thi thử THPT</h3><p>40 câu · Luyện tư duy và kĩ năng xử lí số liệu.</p><button onclick="showView('practice')">Bắt đầu →</button></div>
    </div>`;
}
function renderAchievements(){
  const done=state.completed.length;
  const badges=[
    ["🌱","Bước đầu tiên","Hoàn thành bài học đầu tiên",done>=1],
    ["🔥","7 ngày bền bỉ","Duy trì chuỗi 7 ngày",state.streak>=7],
    ["📚","Chăm học","Hoàn thành 10 bài học",done>=10],
    ["🧭","Nhà địa lí trẻ","Hoàn thành 20 bài học",done>=20],
    ["🏆","Chinh phục Địa lí","Hoàn thành toàn bộ 35 bài",done>=35]
  ];
  document.getElementById("view-achievements").innerHTML=`
    <div class="view-title"><h1>🏅 Thành tích</h1><p>Những cột mốc bạn có thể chinh phục trong quá trình học.</p></div>
    <div class="course-grid">${badges.map(b=>`<div class="course" style="opacity:${b[3]?1:.55}"><div class="emoji">${b[0]}</div><h3>${b[1]} ${b[3]?"✓":""}</h3><p>${b[2]}</p></div>`).join("")}</div>`;
}
function renderAdmin(){
  if(!isAdmin){showView("home");return}
  const users=getUsers();
  const userEntries=Object.entries(users);
  document.getElementById("view-admin").innerHTML=`
    <div class="view-title"><h1>⚙️ Bảng quản trị</h1><p>Quản lý tài khoản, bài học và dữ liệu của website Địa Lí 12.</p></div>
    <div class="admin-stat-grid">
      <div class="admin-stat"><small>👥 Người dùng</small><b>${userEntries.length}</b></div>
      <div class="admin-stat"><small>📚 Bài học</small><b>${lessons.length}</b></div>
      <div class="admin-stat"><small>❓ Câu hỏi mẫu</small><b>${questions.length}</b></div>
      <div class="admin-stat"><small>💾 Lưu trữ</small><b>Local</b></div>
    </div>
    <section class="panel admin-only">
      <div class="panel-head"><h2>➕ Thêm bài học</h2><span class="admin-tag">ADMIN</span></div>
      <p class="sub">Bài học mới sẽ được lưu trong trình duyệt hiện tại.</p>
      <form class="admin-form" onsubmit="addLesson(event)">
        <input id="newLessonName" required placeholder="Tên bài, ví dụ: Bài 36. Địa lí kinh tế xanh">
        <select id="newLessonCat"><option>Địa lí Tự nhiên</option><option>Địa lí Dân cư</option><option>Địa lí Ngành KT</option><option>Địa lí Vùng KT</option><option>Địa lí Địa phương</option></select>
        <button class="primary">Thêm bài học</button>
      </form>
    </section>
    <section class="panel">
      <div class="panel-head"><h2>📚 Danh sách bài học</h2><span>${lessons.length} bài</span></div>
      <table class="admin-table"><thead><tr><th>#</th><th>Bài</th><th>Chuyên đề</th><th></th></tr></thead><tbody>
      ${lessons.map((l,i)=>`<tr><td>${i+1}</td><td>${l[1]}</td><td>${l[2]}</td><td><button class="primary danger" onclick="deleteLesson(${i})">Xóa</button></td></tr>`).join("")}
      </tbody></table>
    </section>
    <section class="panel">
      <div class="panel-head"><h2>👥 Tài khoản người học</h2><span>${userEntries.length} tài khoản</span></div>
      ${userEntries.length?`<table class="admin-table"><thead><tr><th>Họ tên</th><th>Email</th><th>Tiến độ</th><th>XP</th><th></th></tr></thead><tbody>${userEntries.map(([email,u])=>`<tr><td>${u.name}</td><td>${email}</td><td>${u.state.completed.length}/${lessons.length}</td><td>${u.state.xp}</td><td><button class="primary danger" onclick="deleteUser('${email.replace(/'/g,"\\'")}')">Xóa</button></td></tr>`).join("")}</tbody></table>`:`<div class="empty">Chưa có người học đăng ký.</div>`}
    </section>
    <section class="panel">
      <div class="panel-head"><h2>🧹 Công cụ dữ liệu</h2></div>
      <p class="sub">Dùng khi đang demo/prototype. Không dùng các nút này trên hệ thống thật nếu chưa có backup.</p>
      <button class="primary danger" onclick="clearAllUsers()">Xóa toàn bộ tài khoản người học</button>
    </section>`;
}
function addLesson(e){
  e.preventDefault();
  const name=document.getElementById("newLessonName").value.trim();
  const cat=document.getElementById("newLessonCat").value;
  if(!name)return;
  lessons.push([`Bài ${lessons.length+1}`,name,cat]);
  renderAdmin();
  alert("Đã thêm bài học.");
}
function deleteLesson(i){
  if(!confirm("Xóa bài học này?"))return;
  lessons.splice(i,1); renderAdmin();
}
function deleteUser(email){
  if(!confirm("Xóa tài khoản "+email+"?"))return;
  const users=getUsers(); delete users[email]; saveUsers(users); renderAdmin();
}
function clearAllUsers(){
  if(!confirm("Xóa TOÀN BỘ tài khoản người học?"))return;
  localStorage.removeItem("geo_users"); renderAdmin();
}

function renderProfile(){
  const name=document.getElementById("profileName").textContent;
  document.getElementById("view-profile").innerHTML=`
    <div class="view-title"><h1>👤 Hồ sơ</h1><p>Thông tin và tiến độ học tập của bạn.</p></div>
    <div class="panel" style="max-width:800px;margin:auto">
      <div style="display:flex;align-items:center;gap:18px;margin-bottom:25px"><div class="avatar" style="width:70px;height:70px;font-size:25px">${name[0].toUpperCase()}</div><div><h2 style="margin:0">${name}</h2><p style="color:#71809a">${currentUser}</p></div></div>
      <div class="categories" style="grid-template-columns:repeat(3,1fr)">
        <div class="category"><b>XP</b><strong>${state.xp}</strong><span>Điểm kinh nghiệm</span></div>
        <div class="category"><b>Bài học</b><strong>${state.completed.length}/35</strong><span>Hoàn thành</span></div>
        <div class="category"><b>Điểm TB</b><strong>${state.avg??"—"}</strong><span>Trắc nghiệm</span></div>
      </div>
    </div>`;
}

// Restore session
(function init(){
  const saved=localStorage.getItem("geo_current");
  if(saved===ADMIN_EMAIL){currentUser=ADMIN_EMAIL;isAdmin=true;state={xp:0,completed:[],streak:1,avg:null,quizScore:null};enterApp("Quản trị viên");return}
  if(saved){
    const users=getUsers();
    if(users[saved]){currentUser=saved;isAdmin=false;state={...users[saved].state};enterApp(users[saved].name);return}
  }
  // keep login screen
})();
</script>

<script>
const _oldEnterApp = enterApp;
enterApp = function(name){
  if(currentUser) localStorage.setItem("geo_current", currentUser);
  _oldEnterApp(name);
};
const _oldLogout = logout;
logout = function(){
  localStorage.removeItem("geo_current");
  _oldLogout();
};
</script>
</body>
</html>
