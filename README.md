<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shaffy Movies</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --red: #e50914;
      --dark-red: #b0060f;
      --bg: #0a0a0a;
      --card-bg: #161616;
      --nav-bg: rgba(10,10,10,0.95);
      --text: #ffffff;
      --muted: #888;
      --border: #2a2a2a;
    }

    * { margin:0; padding:0; box-sizing:border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
    }

    /* SCROLLBAR */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--red); border-radius: 3px; }

    /* NAVBAR */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 60px;
      background: var(--nav-bg);
      position: sticky;
      top: 0;
      z-index: 100;
      border-bottom: 1px solid var(--border);
      backdrop-filter: blur(10px);
    }

    .logo {
      font-family: 'Bebas Neue', cursive;
      font-size: 32px;
      color: var(--red);
      letter-spacing: 2px;
    }
    .logo span { color: white; }

    .menu { display: flex; gap: 30px; align-items: center; }
    .menu a {
      text-decoration: none;
      color: #ccc;
      font-size: 15px;
      font-weight: 500;
      transition: color 0.2s;
      position: relative;
    }
    .menu a::after {
      content: '';
      position: absolute;
      bottom: -4px; left: 0;
      width: 0; height: 2px;
      background: var(--red);
      transition: width 0.3s;
    }
    .menu a:hover { color: white; }
    .menu a:hover::after { width: 100%; }

    .nav-right { display: flex; gap: 15px; align-items: center; }

    .search-box {
      display: flex;
      align-items: center;
      background: #1c1c1c;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 8px 15px;
      gap: 8px;
    }
    .search-box input {
      background: none;
      border: none;
      outline: none;
      color: white;
      width: 200px;
      font-size: 14px;
      font-family: 'DM Sans', sans-serif;
    }
    .search-box input::placeholder { color: var(--muted); }
    .search-icon { color: var(--muted); font-size: 16px; }

    .login-btn {
      padding: 9px 22px;
      background: var(--red);
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
      font-family: 'DM Sans', sans-serif;
    }
    .login-btn:hover { background: var(--dark-red); transform: translateY(-1px); }

    /* HERO */
    .hero {
      height: 92vh;
      background: url('https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?q=80&w=1400') center/cover no-repeat;
      display: flex;
      align-items: center;
      padding-left: 80px;
      position: relative;
    }
    .hero::before {
      content: '';
      position: absolute; inset: 0;
      background: linear-gradient(90deg, rgba(0,0,0,0.92) 35%, rgba(0,0,0,0.3) 70%, transparent 100%);
    }
    .hero::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0; right: 0;
      height: 120px;
      background: linear-gradient(to top, var(--bg), transparent);
    }

    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 520px;
      animation: fadeUp 0.8s ease forwards;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .hero-badge {
      display: inline-block;
      background: var(--red);
      color: white;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 5px 12px;
      border-radius: 4px;
      margin-bottom: 20px;
    }

    .hero-content h1 {
      font-family: 'Bebas Neue', cursive;
      font-size: 80px;
      line-height: 1;
      margin-bottom: 20px;
      letter-spacing: 2px;
    }
    .hero-content h1 span { color: var(--red); }

    .hero-content p {
      font-size: 16px;
      line-height: 1.8;
      color: #ccc;
      margin-bottom: 35px;
    }

    .hero-meta {
      display: flex;
      gap: 20px;
      margin-bottom: 30px;
      font-size: 13px;
      color: var(--muted);
    }
    .hero-meta span { display: flex; align-items: center; gap: 5px; }

    .hero-buttons { display: flex; gap: 15px; }

    .btn-primary {
      padding: 14px 32px;
      background: var(--red);
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      font-family: 'DM Sans', sans-serif;
      display: flex; align-items: center; gap: 8px;
    }
    .btn-primary:hover { background: var(--dark-red); transform: translateY(-2px); box-shadow: 0 8px 25px rgba(229,9,20,0.4); }

    .btn-secondary {
      padding: 14px 32px;
      background: rgba(255,255,255,0.1);
      color: white;
      border: 1px solid rgba(255,255,255,0.2);
      border-radius: 8px;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      font-family: 'DM Sans', sans-serif;
      display: flex; align-items: center; gap: 8px;
      backdrop-filter: blur(5px);
    }
    .btn-secondary:hover { background: rgba(255,255,255,0.2); transform: translateY(-2px); }

    /* SECTIONS */
    .section { padding: 60px 60px 20px; }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 30px;
    }

    .section-title {
      font-family: 'Bebas Neue', cursive;
      font-size: 36px;
      letter-spacing: 1px;
    }
    .section-title span {
      display: inline-block;
      width: 4px; height: 30px;
      background: var(--red);
      margin-right: 12px;
      vertical-align: middle;
      border-radius: 2px;
    }

    .see-all {
      color: var(--red);
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
      text-decoration: none;
      transition: opacity 0.2s;
    }
    .see-all:hover { opacity: 0.7; }

    /* MOVIE GRID */
    .movie-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 20px;
    }

    .movie-card {
      background: var(--card-bg);
      border-radius: 12px;
      overflow: hidden;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
      border: 1px solid var(--border);
      position: relative;
    }
    .movie-card:hover {
      transform: translateY(-8px) scale(1.02);
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      border-color: var(--red);
    }

    .movie-card img {
      width: 100%;
      height: 290px;
      object-fit: cover;
      display: block;
      transition: filter 0.3s;
    }
    .movie-card:hover img { filter: brightness(0.7); }

    .movie-overlay {
      position: absolute;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.7);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      transition: opacity 0.3s;
    }
    .movie-card:hover .movie-overlay { opacity: 1; }

    .play-btn {
      width: 55px; height: 55px;
      background: var(--red);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 20px;
      transform: scale(0.8);
      transition: transform 0.3s;
    }
    .movie-card:hover .play-btn { transform: scale(1); }

    .movie-badge {
      position: absolute;
      top: 12px; left: 12px;
      background: var(--red);
      color: white;
      font-size: 10px;
      font-weight: 700;
      padding: 3px 8px;
      border-radius: 4px;
      letter-spacing: 1px;
      text-transform: uppercase;
    }

    .movie-info { padding: 15px; }
    .movie-info h3 {
      font-size: 15px;
      font-weight: 600;
      margin-bottom: 6px;
    }
    .movie-meta {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .movie-genre {
      color: var(--muted);
      font-size: 12px;
    }
    .movie-rating {
      color: #f5c518;
      font-size: 12px;
      font-weight: 600;
    }

    /* CATEGORIES */
    .categories { padding: 20px 60px 40px; }
    .category-list {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }
    .category-pill {
      padding: 8px 20px;
      border-radius: 50px;
      border: 1px solid var(--border);
      color: #ccc;
      font-size: 13px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s;
      background: var(--card-bg);
    }
    .category-pill:hover, .category-pill.active {
      background: var(--red);
      border-color: var(--red);
      color: white;
    }

    /* PROMO BANNER */
    .promo {
      margin: 20px 60px 60px;
      background: linear-gradient(135deg, #1a0000 0%, #2d0000 50%, #1a0000 100%);
      border: 1px solid #3d0000;
      border-radius: 16px;
      padding: 50px 60px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: relative;
      overflow: hidden;
    }
    .promo::before {
      content: '';
      position: absolute;
      top: -50%; right: -10%;
      width: 400px; height: 400px;
      background: radial-gradient(circle, rgba(229,9,20,0.15) 0%, transparent 70%);
    }
    .promo-text h2 {
      font-family: 'Bebas Neue', cursive;
      font-size: 48px;
      letter-spacing: 2px;
      margin-bottom: 10px;
    }
    .promo-text p { color: #ccc; font-size: 15px; max-width: 400px; }
    .promo-price {
      text-align: center;
      position: relative;
      z-index: 1;
    }
    .promo-price .amount {
      font-family: 'Bebas Neue', cursive;
      font-size: 64px;
      color: var(--red);
      line-height: 1;
    }
    .promo-price .period { color: var(--muted); font-size: 14px; margin-bottom: 20px; }

    /* FOOTER */
    footer {
      background: #0d0d0d;
      border-top: 1px solid var(--border);
      padding: 40px 60px 25px;
    }
    .footer-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 35px;
    }
    .footer-logo {
      font-family: 'Bebas Neue', cursive;
      font-size: 28px;
      color: var(--red);
      letter-spacing: 2px;
      margin-bottom: 10px;
    }
    .footer-desc { color: var(--muted); font-size: 13px; max-width: 220px; line-height: 1.7; }
    .footer-links h4 { font-size: 14px; font-weight: 700; margin-bottom: 15px; color: #ddd; }
    .footer-links a {
      display: block;
      color: var(--muted);
      text-decoration: none;
      font-size: 13px;
      margin-bottom: 8px;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--red); }
    .footer-bottom {
      border-top: 1px solid var(--border);
      padding-top: 20px;
      text-align: center;
      color: var(--muted);
      font-size: 13px;
    }

    /* MODAL */
    .modal-overlay {
      position: fixed; inset: 0;
      background: rgba(0,0,0,0.85);
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
      backdrop-filter: blur(5px);
    }
    .modal-overlay.active { opacity: 1; pointer-events: all; }

    .modal {
      background: #161616;
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 40px;
      width: 400px;
      transform: scale(0.9);
      transition: transform 0.3s;
    }
    .modal-overlay.active .modal { transform: scale(1); }

    .modal h2 {
      font-family: 'Bebas Neue', cursive;
      font-size: 32px;
      letter-spacing: 1px;
      margin-bottom: 6px;
    }
    .modal p { color: var(--muted); font-size: 14px; margin-bottom: 28px; }

    .modal-close {
      position: absolute;
      top: 15px; right: 20px;
      background: none;
      border: none;
      color: var(--muted);
      font-size: 24px;
      cursor: pointer;
      transition: color 0.2s;
    }
    .modal-close:hover { color: white; }

    .form-group { margin-bottom: 18px; }
    .form-group label { display: block; font-size: 13px; font-weight: 600; margin-bottom: 7px; color: #ccc; }
    .form-group input {
      width: 100%;
      padding: 12px 15px;
      background: #0f0f0f;
      border: 1px solid var(--border);
      border-radius: 8px;
      color: white;
      font-size: 14px;
      font-family: 'DM Sans', sans-serif;
      outline: none;
      transition: border-color 0.2s;
    }
    .form-group input:focus { border-color: var(--red); }

    .btn-full {
      width: 100%;
      padding: 13px;
      background: var(--red);
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 15px;
      font-weight: 700;
      cursor: pointer;
      font-family: 'DM Sans', sans-serif;
      transition: background 0.2s;
      margin-top: 5px;
    }
    .btn-full:hover { background: var(--dark-red); }

    .modal-switch { text-align: center; margin-top: 18px; color: var(--muted); font-size: 13px; }
    .modal-switch a { color: var(--red); cursor: pointer; font-weight: 600; text-decoration: none; }

    /* SEARCH RESULTS */
    .search-results {
      position: absolute;
      top: 75px; right: 60px;
      background: #1a1a1a;
      border: 1px solid var(--border);
      border-radius: 12px;
      width: 300px;
      z-index: 200;
      overflow: hidden;
      display: none;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
    }
    .search-results.visible { display: block; }
    .search-result-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 12px 16px;
      cursor: pointer;
      transition: background 0.2s;
    }
    .search-result-item:hover { background: #222; }
    .search-result-item img { width: 40px; height: 55px; object-fit: cover; border-radius: 6px; }
    .search-result-item .info { flex: 1; }
    .search-result-item .info h4 { font-size: 14px; margin-bottom: 3px; }
    .search-result-item .info p { font-size: 12px; color: var(--muted); }

    /* NO RESULTS */
    .no-results { padding: 20px; text-align: center; color: var(--muted); font-size: 14px; }

    /* TOAST */
    .toast {
      position: fixed;
      bottom: 30px; right: 30px;
      background: #1c1c1c;
      border: 1px solid var(--border);
      border-left: 4px solid var(--red);
      border-radius: 10px;
      padding: 16px 24px;
      color: white;
      font-size: 14px;
      z-index: 9999;
      transform: translateX(150%);
      transition: transform 0.4s cubic-bezier(0.34,1.56,0.64,1);
    }
    .toast.show { transform: translateX(0); }
  </style>
</head>
<body>

  <!-- NAVBAR -->
  <nav>
    <div class="logo">🎬 SHAFFY <span>MOVIES</span></div>
    <div class="menu">
      <a href="#">Home</a>
      <a href="#">Movies</a>
      <a href="#">Series</a>
      <a href="#">Trending</a>
    </div>
    <div class="nav-right">
      <div class="search-box">
        <span class="search-icon">🔍</span>
        <input type="text" id="searchInput" placeholder="Search movies..." oninput="handleSearch(this.value)">
      </div>
      <button class="login-btn" onclick="openModal('login')">Login</button>
    </div>
  </nav>

  <!-- SEARCH RESULTS DROPDOWN -->
  <div class="search-results" id="searchResults"></div>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-content">
      <div class="hero-badge">🔥 Now Trending</div>
      <h1>Unlimited<br><span>Movies</span></h1>
      <p>Watch the latest movies and series online anytime, anywhere on your phone or computer.</p>
      <div class="hero-meta">
        <span>⭐ 4.9 Rating</span>
        <span>🎬 1000+ Movies</span>
        <span>📺 HD Quality</span>
      </div>
      <div class="hero-buttons">
        <button class="btn-primary" onclick="showToast('▶ Starting playback...')">▶ Watch Now</button>
        <button class="btn-secondary" onclick="showToast('ℹ More info coming soon!')">ℹ More Info</button>
      </div>
    </div>
  </section>

  <!-- CATEGORIES -->
  <div class="categories">
    <div class="category-list" id="categoryList">
      <div class="category-pill active" onclick="filterCategory(this, 'all')">All</div>
      <div class="category-pill" onclick="filterCategory(this, 'action')">Action</div>
      <div class="category-pill" onclick="filterCategory(this, 'adventure')">Adventure</div>
      <div class="category-pill" onclick="filterCategory(this, 'romance')">Romance</div>
      <div class="category-pill" onclick="filterCategory(this, 'comedy')">Comedy</div>
      <div class="category-pill" onclick="filterCategory(this, 'horror')">Horror</div>
      <div class="category-pill" onclick="filterCategory(this, 'sci-fi')">Sci-Fi</div>
    </div>
  </div>

  <!-- MOVIES SECTION -->
  <section class="section">
    <div class="section-header">
      <div class="section-title"><span></span>Trending Movies</div>
      <a class="see-all">See All →</a>
    </div>
    <div class="movie-grid" id="movieGrid"></div>
  </section>

  <!-- PROMO BANNER -->
  <div class="promo">
    <div class="promo-text">
      <h2>Go Premium Today 🎬</h2>
      <p>Unlock unlimited movies, series, and exclusive content in Full HD. No ads. Cancel anytime.</p>
    </div>
    <div class="promo-price">
      <div class="amount">$4.99</div>
      <div class="period">per month</div>
      <button class="btn-primary" onclick="openModal('register')">Get Started</button>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <div class="footer-top">
      <div>
        <div class="footer-logo">🎬 Shaffy Movies</div>
        <div class="footer-desc">Your ultimate destination for movies and series. Watch anywhere, anytime.</div>
      </div>
      <div class="footer-links">
        <h4>Movies</h4>
        <a href="#">Action</a>
        <a href="#">Comedy</a>
        <a href="#">Romance</a>
        <a href="#">Horror</a>
      </div>
      <div class="footer-links">
        <h4>Company</h4>
        <a href="#">About Us</a>
        <a href="#">Contact</a>
        <a href="#">Blog</a>
        <a href="#">Careers</a>
      </div>
      <div class="footer-links">
        <h4>Support</h4>
        <a href="#">Help Center</a>
        <a href="#">Privacy Policy</a>
        <a href="#">Terms of Service</a>
      </div>
    </div>
    <div class="footer-bottom">© 2026 Shaffy Movies | All Rights Reserved</div>
  </footer>

  <!-- LOGIN MODAL -->
  <div class="modal-overlay" id="modalOverlay" onclick="closeModalOutside(event)">
    <div class="modal" style="position:relative">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div id="modalContent"></div>
    </div>
  </div>

  <!-- TOAST -->
  <div class="toast" id="toast"></div>

  <script>
    const movies = [
      { id:1, title:"Thunder Strike", genre:"action", rating:"8.2", img:"https://picsum.photos/300/400?11", badge:"NEW" },
      { id:2, title:"Lost Horizon", genre:"adventure", rating:"7.8", img:"https://picsum.photos/300/400?22", badge:"" },
      { id:3, title:"Forever Yours", genre:"romance", rating:"8.5", img:"https://picsum.photos/300/400?33", badge:"HOT" },
      { id:4, title:"Laugh Out Loud", genre:"comedy", rating:"7.4", img:"https://picsum.photos/300/400?44", badge:"" },
      { id:5, title:"Dark Shadows", genre:"horror", rating:"8.0", img:"https://picsum.photos/300/400?55", badge:"TOP" },
      { id:6, title:"Galaxy Quest", genre:"sci-fi", rating:"9.1", img:"https://picsum.photos/300/400?66", badge:"HOT" },
      { id:7, title:"Iron Fist", genre:"action", rating:"7.9", img:"https://picsum.photos/300/400?77", badge:"" },
      { id:8, title:"Midnight Run", genre:"adventure", rating:"8.3", img:"https://picsum.photos/300/400?88", badge:"NEW" },
    ];

    function renderMovies(list) {
      const grid = document.getElementById('movieGrid');
      if(list.length === 0) {
        grid.innerHTML = '<p style="color:var(--muted);grid-column:1/-1;text-align:center;padding:40px 0">No movies found.</p>';
        return;
      }
      grid.innerHTML = list.map(m => `
        <div class="movie-card" onclick="showToast('▶ Playing: ${m.title}')">
          ${m.badge ? `<div class="movie-badge">${m.badge}</div>` : ''}
          <img src="${m.img}" alt="${m.title}" loading="lazy">
          <div class="movie-overlay"><div class="play-btn">▶</div></div>
          <div class="movie-info">
            <h3>${m.title}</h3>
            <div class="movie-meta">
              <span class="movie-genre">${m.genre.charAt(0).toUpperCase()+m.genre.slice(1)}</span>
              <span class="movie-rating">⭐ ${m.rating}</span>
            </div>
          </div>
        </div>
      `).join('');
    }

    function filterCategory(el, genre) {
      document.querySelectorAll('.category-pill').forEach(p => p.classList.remove('active'));
      el.classList.add('active');
      const filtered = genre === 'all' ? movies : movies.filter(m => m.genre === genre);
      renderMovies(filtered);
    }

    function handleSearch(val) {
      const resultsDiv = document.getElementById('searchResults');
      if(!val.trim()) { resultsDiv.classList.remove('visible'); return; }
      const matches = movies.filter(m => m.title.toLowerCase().includes(val.toLowerCase()));
      if(matches.length === 0) {
        resultsDiv.innerHTML = '<div class="no-results">No movies found</div>';
      } else {
        resultsDiv.innerHTML = matches.map(m => `
          <div class="search-result-item" onclick="showToast('▶ Playing: ${m.title}')">
            <img src="${m.img}" alt="${m.title}">
            <div class="info"><h4>${m.title}</h4><p>${m.genre} • ⭐ ${m.rating}</p></div>
          </div>
        `).join('');
      }
      resultsDiv.classList.add('visible');
    }

    document.addEventListener('click', (e) => {
      if(!e.target.closest('.search-box') && !e.target.closest('#searchResults')) {
        document.getElementById('searchResults').classList.remove('visible');
      }
    });

    function openModal(type) {
      const overlay = document.getElementById('modalOverlay');
      const content = document.getElementById('modalContent');
      if(type === 'login') {
        content.innerHTML = `
          <h2>Welcome Back</h2>
          <p>Login to your Shaffy Movies account</p>
          <div class="form-group"><label>Email</label><input type="email" placeholder="your@email.com"></div>
          <div class="form-group"><label>Password</label><input type="password" placeholder="••••••••"></div>
          <button class="btn-full" onclick="handleLogin()">Login</button>
          <div class="modal-switch">Don't have an account? <a onclick="openModal('register')">Sign Up</a></div>
        `;
      } else {
        content.innerHTML = `
          <h2>Create Account</h2>
          <p>Join Shaffy Movies today — it's free!</p>
          <div class="form-group"><label>Full Name</label><input type="text" placeholder="Your name"></div>
          <div class="form-group"><label>Email</label><input type="email" placeholder="your@email.com"></div>
          <div class="form-group"><label>Password</label><input type="password" placeholder="••••••••"></div>
          <button class="btn-full" onclick="handleRegister()">Create Account</button>
          <div class="modal-switch">Already have an account? <a onclick="openModal('login')">Login</a></div>
        `;
      }
      overlay.classList.add('active');
    }

    function closeModal() { document.getElementById('modalOverlay').classList.remove('active'); }
    function closeModalOutside(e) { if(e.target.id === 'modalOverlay') closeModal(); }

    function handleLogin() { closeModal(); showToast('✅ Logged in successfully!'); }
    function handleRegister() { closeModal(); showToast('🎉 Account created! Welcome!'); }

    let toastTimer;
    function showToast(msg) {
      const t = document.getElementById('toast');
      t.textContent = msg;
      t.classList.add('show');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => t.classList.remove('show'), 3000);
    }

    renderMovies(movies);
  </script>
</body>
</html>
