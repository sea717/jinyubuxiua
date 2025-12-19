<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>金缕玉衣 · 三维动画毕业设计</title>
  <meta name="description" content="金缕玉衣三维动画毕业设计展示，以黄粱一梦视角探索汉代不朽之梦">
  <meta name="keywords" content="金缕玉衣,三维动画,毕业设计,汉代文化,文化遗产">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --gold: #d4af37;
      --dark-gold: #b8941f;
      --jade: #00a86b;
      --dark-jade: #007a4d;
      --black: #0f0f0f;
      --dark-gray: #1a1a1a;
      --medium-gray: #333;
      --light-gray: #f5f5f5;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    html {
      scroll-behavior: smooth;
      font-size: 16px;
    }
    
    body {
      font-family: 'Noto Serif SC', serif, 'Microsoft YaHei', sans-serif;
      background: var(--black);
      color: var(--light-gray);
      line-height: 1.6;
      overflow-x: hidden;
      -webkit-tap-highlight-color: transparent;
    }
    
    /* 移动端优化 */
    @media (max-width: 768px) {
      html {
        font-size: 14px;
      }
    }
    
    /* 导航栏 */
    nav {
      position: fixed;
      top: 0;
      width: 100%;
      background: rgba(15, 15, 15, 0.98);
      backdrop-filter: blur(10px);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.8rem 1.5rem;
      z-index: 1000;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
      border-bottom: 1px solid rgba(212, 175, 55, 0.2);
    }
    
    .logo {
      font-size: 1.2rem;
      color: var(--gold);
      font-weight: bold;
      letter-spacing: 2px;
      text-decoration: none;
    }
    
    .nav-links {
      display: flex;
      gap: 1.5rem;
    }
    
    .nav-links a {
      color: var(--gold);
      text-decoration: none;
      font-size: 0.9rem;
      position: relative;
      padding: 0.5rem 0;
      transition: all 0.3s;
      white-space: nowrap;
    }
    
    .nav-links a:hover {
      color: white;
    }
    
    .nav-links a::after {
      content: '';
      position: absolute;
      width: 0;
      height: 2px;
      bottom: 0;
      left: 0;
      background: linear-gradient(to right, var(--gold), var(--jade));
      transition: width 0.3s;
    }
    
    .nav-links a:hover::after {
      width: 100%;
    }
    
    /* 汉堡菜单 */
    .hamburger {
      display: none;
      flex-direction: column;
      cursor: pointer;
      width: 30px;
      height: 25px;
      justify-content: space-between;
    }
    
    .hamburger span {
      display: block;
      height: 3px;
      width: 100%;
      background: var(--gold);
      border-radius: 3px;
      transition: all 0.3s;
    }
    
    .hamburger.active span:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }
    
    .hamburger.active span:nth-child(2) {
      opacity: 0;
    }
    
    .hamburger.active span:nth-child(3) {
      transform: rotate(-45deg) translate(7px, -6px);
    }
    
    @media (max-width: 768px) {
      .nav-links {
        position: fixed;
        top: 60px;
        left: 0;
        width: 100%;
        background: rgba(15, 15, 15, 0.98);
        backdrop-filter: blur(15px);
        flex-direction: column;
        align-items: center;
        padding: 1rem 0;
        gap: 0;
        transform: translateY(-100%);
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
        z-index: 999;
      }
      
      .nav-links.active {
        transform: translateY(0);
        opacity: 1;
        visibility: visible;
      }
      
      .nav-links a {
        width: 100%;
        text-align: center;
        padding: 1rem;
        border-bottom: 1px solid rgba(212, 175, 55, 0.1);
      }
      
      .nav-links a:last-child {
        border-bottom: none;
      }
      
      .hamburger {
        display: flex;
      }
    }
    
    /* 标题区域 */
    header {
      height: 100vh;
      min-height: 600px;
      background: 
        linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.9)),
        url('hebei-bg.jpg') center/cover no-repeat;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      position: relative;
      overflow: hidden;
      padding: 0 1rem;
    }
    
    .header-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: 
        radial-gradient(circle at 30% 50%, rgba(212, 175, 55, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 70% 20%, rgba(0, 168, 107, 0.05) 0%, transparent 50%);
      z-index: 1;
      animation: pulseOverlay 8s ease-in-out infinite alternate;
    }
    
    @keyframes pulseOverlay {
      0% { opacity: 0.5; }
      100% { opacity: 0.8; }
    }
    
    .header-content {
      position: relative;
      z-index: 2;
      max-width: 900px;
      padding: 1rem;
      animation: fadeInUp 1.5s ease-out;
    }
    
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    header h1 {
      font-size: clamp(2rem, 8vw, 4rem);
      letter-spacing: 0.2em;
      margin-bottom: 1rem;
      text-shadow: 0 5px 15px rgba(0, 0, 0, 0.7);
      position: relative;
      display: inline-block;
      background: linear-gradient(135deg, var(--gold), #fff, var(--gold));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      animation: textGlow 3s ease-in-out infinite alternate;
      background-size: 200% 100%;
      line-height: 1.2;
    }
    
    @keyframes textGlow {
      0% {
        text-shadow: 0 0 10px rgba(212, 175, 55, 0.3);
      }
      100% {
        text-shadow: 0 0 20px rgba(212, 175, 55, 0.7), 0 0 30px rgba(212, 175, 55, 0.5);
      }
    }
    
    .title-decoration {
      position: relative;
      width: 150px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), transparent);
      margin: 1rem auto;
      animation: widthPulse 4s ease-in-out infinite;
    }
    
    @keyframes widthPulse {
      0%, 100% { width: 150px; }
      50% { width: 200px; }
    }
    
    header .subtitle {
      font-size: clamp(0.9rem, 3vw, 1.3rem);
      opacity: 0.9;
      margin-bottom: 1.5rem;
      font-weight: 300;
      letter-spacing: 1px;
      padding: 0.5rem;
    }
    
    .scroll-indicator {
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      color: var(--gold);
      font-size: 1.5rem;
      animation: bounce 2s infinite;
      cursor: pointer;
      background: rgba(0, 0, 0, 0.3);
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 1px solid rgba(212, 175, 55, 0.3);
      transition: all 0.3s;
      z-index: 10;
    }
    
    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% {
        transform: translateY(0) translateX(-50%);
      }
      40% {
        transform: translateY(-10px) translateX(-50%);
      }
      60% {
        transform: translateY(-5px) translateX(-50%);
      }
    }
    
    /* 主体内容区域 */
    section {
      max-width: 1200px;
      margin: 0 auto;
      padding: 4rem 1rem;
      position: relative;
    }
    
    @media (min-width: 768px) {
      section {
        padding: 6rem 2rem;
      }
    }
    
    section h2 {
      font-size: clamp(1.5rem, 5vw, 2.5rem);
      padding-left: 1rem;
      margin-bottom: 2rem;
      position: relative;
      display: inline-block;
      color: var(--gold);
    }
    
    section h2::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      width: 4px;
      height: 100%;
      background: linear-gradient(to bottom, var(--gold), var(--jade));
      border-radius: 2px;
    }
    
    .section-content {
      font-size: 1rem;
      line-height: 1.7;
      margin-bottom: 2rem;
      text-align: justify;
    }
    
    @media (min-width: 768px) {
      .section-content {
        font-size: 1.1rem;
        line-height: 1.9;
      }
    }
    
    .highlight {
      color: var(--gold);
      font-weight: bold;
    }
    
    .emphasize {
      color: var(--jade);
      font-style: italic;
    }
    
    /* 图片区块 */
    .image-block {
      margin: 2rem 0;
      text-align: center;
      position: relative;
    }
    
    .image-frame {
      position: relative;
      display: inline-block;
      max-width: 100%;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
      border: 1px solid rgba(212, 175, 55, 0.2);
      transition: all 0.3s;
      background: var(--dark-gray);
    }
    
    .image-frame:hover {
      transform: translateY(-5px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.7);
    }
    
    .image-block img {
      width: 100%;
      height: auto;
      display: block;
      transition: transform 0.5s;
    }
    
    .image-frame:hover img {
      transform: scale(1.02);
    }
    
    .image-caption {
      margin-top: 0.8rem;
      font-size: 0.8rem;
      opacity: 0.7;
      font-style: italic;
      padding: 0.5rem;
    }
    
    /* 视频区域 */
    .video-container {
      margin: 2rem 0;
      background: var(--dark-gray);
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
      border: 1px solid var(--medium-gray);
      position: relative;
    }
    
    .video-header {
      background: linear-gradient(to right, var(--dark-gray), #2a2a2a);
      padding: 1rem;
      border-bottom: 1px solid var(--medium-gray);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    
    .video-title {
      font-size: 1rem;
      color: var(--gold);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    
    .video-controls {
      display: flex;
      gap: 0.5rem;
    }
    
    .video-controls i {
      color: var(--light-gray);
      cursor: pointer;
      transition: all 0.3s;
      width: 35px;
      height: 35px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      background: rgba(0, 0, 0, 0.3);
      font-size: 0.9rem;
    }
    
    .video-controls i:hover {
      color: var(--gold);
      background: rgba(212, 175, 55, 0.1);
    }
    
    .video-box {
      padding: 1rem;
    }
    
    .video-player {
      width: 100%;
      max-height: 70vh;
      border-radius: 6px;
      overflow: hidden;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    }
    
    .video-structure {
      margin-top: 1rem;
      background: rgba(0, 0, 0, 0.3);
      padding: 1rem;
      border-radius: 6px;
      border-left: 3px solid var(--jade);
      font-size: 0.9rem;
    }
    
    /* 网格卡片 */
    .grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 1.5rem;
      margin-top: 2rem;
    }
    
    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 2rem;
        margin-top: 3rem;
      }
    }
    
    .card {
      background: linear-gradient(145deg, var(--dark-gray), #222);
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }
    
    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background: linear-gradient(to right, var(--gold), var(--jade));
    }
    
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 25px rgba(0, 0, 0, 0.6);
    }
    
    .card h3 {
      font-size: 1.2rem;
      margin-bottom: 1rem;
      color: var(--gold);
      position: relative;
      padding-bottom: 0.5rem;
    }
    
    .card h3::after {
      content: '';
      position: absolute;
      width: 40px;
      height: 2px;
      background: var(--jade);
      bottom: 0;
      left: 0;
    }
    
    /* 返回顶部按钮 */
    .back-to-top {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 45px;
      height: 45px;
      background: rgba(212, 175, 55, 0.2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--gold);
      font-size: 1rem;
      cursor: pointer;
      z-index: 999;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s;
      border: 1px solid rgba(212, 175, 55, 0.3);
    }
    
    .back-to-top.show {
      opacity: 0.8;
      visibility: visible;
    }
    
    /* 页脚 */
    footer {
      text-align: center;
      padding: 3rem 1rem;
      background: linear-gradient(to top, #000, #111);
      font-size: 0.8rem;
      position: relative;
      border-top: 1px solid rgba(212, 175, 55, 0.2);
    }
    
    .footer-content {
      max-width: 800px;
      margin: 0 auto;
    }
    
    .footer-logo {
      font-size: 1.5rem;
      color: var(--gold);
      margin-bottom: 1rem;
      letter-spacing: 0.1em;
    }
    
    .footer-info {
      opacity: 0.8;
      margin-bottom: 1.5rem;
      line-height: 1.5;
    }
    
    .copyright {
      opacity: 0.5;
      font-size: 0.75rem;
      margin-top: 1.5rem;
      padding-top: 1rem;
      border-top: 1px solid rgba(255, 255, 255, 0.1);
    }
    
    /* 加载动画 */
    .loading {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: var(--black);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      transition: opacity 0.5s ease-out;
    }
    
    .loading.hidden {
      opacity: 0;
      pointer-events: none;
    }
    
    .loading-spinner {
      width: 50px;
      height: 50px;
      border: 3px solid rgba(212, 175, 55, 0.3);
      border-top-color: var(--gold);
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }
    
    @keyframes spin {
      to { transform: rotate(360deg); }
    }
  </style>
</head>
<body>
  <!-- 加载动画 -->
  <div class="loading" id="loading">
    <div class="loading-spinner"></div>
  </div>

  <!-- 导航栏 -->
  <nav>
    <a href="#" class="logo">金缕玉衣</a>
    <div class="nav-links" id="navLinks">
      <a href="#intro"><i class="fas fa-home"></i> 项目概述</a>
      <a href="#animation"><i class="fas fa-play-circle"></i> 动画展示</a>
      <a href="#history"><i class="fas fa-landmark"></i> 历史背景</a>
      <a href="#excavation"><i class="fas fa-shovel"></i> 考古发掘</a>
      <a href="#meaning"><i class="fas fa-brain"></i> 核心寓意</a>
      <a href="#method"><i class="fas fa-tools"></i> 创作方法</a>
    </div>
    <div class="hamburger" id="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </nav>

  <!-- 标题区域 -->
  <header>
    <div class="header-overlay"></div>
    <div class="header-content">
      <h1>金缕玉衣</h1>
      <div class="title-decoration"></div>
      <p class="subtitle">——"黄粱一梦"视角下的三维动画毕业设计展示</p>
      <p>以三维动画重现汉代不朽之梦，探索金玉背后的永恒哲思</p>
    </div>
    <div class="scroll-indicator" onclick="scrollToSection('intro')">
      <i class="fas fa-chevron-down"></i>
    </div>
  </header>

  <!-- 项目概述 -->
  <section id="intro">
    <h2>项目概述 · 金玉不朽</h2>
    <div class="section-content">
      <p>本毕业设计以<strong class="highlight">"金玉不朽，美学古风"</strong>为总体创作理念，围绕西汉中山靖王刘胜的金缕玉衣展开，通过三维动画的形式，将历史文物、考古发现与文学哲思相结合，构建一场跨越两千年的精神对话。</p>
      
      <div class="image-block">
        <div class="image-frame">
          <img src="金缕玉衣_概念图.jpg" alt="金缕玉衣动画概念设定" loading="lazy">
        </div>
        <p class="image-caption">三维动画概念视觉设定</p>
      </div>
      
      <p>动画以<strong class="highlight">"黄粱一梦"</strong>为最高叙事隐喻，回应古人对肉身不朽的执念，并在当代视角下重新追问：<em class="emphasize">真正不朽的究竟是生命本身，还是被文明记住的精神价值？</em></p>
    </div>
  </section>

  <!-- 动画展示 -->
  <section id="animation">
    <h2>三维动画作品展示</h2>
    
    <div class="video-container">
      <div class="video-header">
        <div class="video-title">
          <i class="fas fa-film"></i>
          《金玉不朽》完整动画
        </div>
        <div class="video-controls">
          <i class="fas fa-expand" title="全屏" onclick="toggleFullscreen()"></i>
          <i class="fas fa-volume-up" title="音量" onclick="toggleMute()"></i>
          <i class="fas fa-play" title="播放/暂停" onclick="togglePlay()"></i>
        </div>
      </div>
      
      <div class="video-box">
        <video id="goldJadeVideo" class="video-player" controls playsinline webkit-playsinline poster="cover.jpg" preload="metadata">
          <source src="金玉不朽.mp4" type="video/mp4">
          您的浏览器不支持视频播放，请升级浏览器或使用其他浏览器访问。
        </video>
        
        <div class="video-structure">
          <p><strong>叙事结构：</strong>考古现场发现 → 汉代历史闪回 → 黄粱一梦哲学隐喻 → 博物馆当代反思</p>
          <p><strong>技术特点：</strong>三维扫描数据重建 · PBR材质渲染 · 动态光影模拟 · 历史场景复原</p>
        </div>
      </div>
    </div>
  </section>

  <!-- 历史背景 -->
  <section id="history">
    <h2>历史背景 · 刘胜与金缕玉衣</h2>
    <div class="section-content">
      <p>刘胜，西汉中山靖王，汉武帝之兄，在位四十二年。他是考古发现中<strong class="highlight">金缕玉衣最著名、等级最高的拥有者</strong>。</p>
      
      <div class="image-block">
        <div class="image-frame">
          <img src="金缕玉衣_实物博物馆.jpg" alt="金缕玉衣博物馆展陈" loading="lazy">
        </div>
        <p class="image-caption">博物馆展陈中的金缕玉衣</p>
      </div>
      
      <p>金缕玉衣由<strong class="highlight">2498片</strong>优质和田玉片与<strong class="highlight">1.1公斤</strong>金丝编缀而成，是汉代"玉能通神、金可镇魂"生死观的极致物质呈现。</p>
    </div>
  </section>

  <!-- 考古发掘 -->
  <section id="excavation">
    <h2>考古发掘 · 现实的起点</h2>
    <div class="section-content">
      <p>1968 年，河北满城汉墓的考古发掘，使这场古人的"长生之梦"重新进入当代视野。</p>
      
      <div class="image-block">
        <div class="image-frame">
          <img src="金缕玉衣_出土局部.jpg" alt="金缕玉衣出土局部" loading="lazy">
        </div>
        <p class="image-caption">金缕玉衣出土局部细节</p>
      </div>
      
      <p>动画在叙事中并置了考古清理、研究分析与博物馆展陈，使历史与当下形成对话。</p>
    </div>
  </section>

  <!-- 核心寓意 -->
  <section id="meaning">
    <h2>核心寓意 · 黄粱一梦与真正的不朽</h2>
    <div class="section-content">
      <p>本动画的核心哲学命题源于唐代传奇《枕中记》的"黄粱一梦"典故，深刻揭示了功名利禄与肉身不朽追求的虚幻本质。</p>
      
      <div class="grid">
        <div class="card">
          <h3>黄粱一梦</h3>
          <p>功名、欲望与肉身永存的虚幻本质。刘胜的金缕玉衣是"黄粱梦"的极致物质化体现。</p>
        </div>
        
        <div class="card">
          <h3>物质不朽的极限</h3>
          <p>金缕玉衣作为不朽执念的巅峰实践。玉能防腐，金代表永恒，但这种物质层面的不朽追求最终被时间证明是徒劳的。</p>
        </div>
        
        <div class="card">
          <h3>精神的不灭</h3>
          <p>文明通过记忆与再创造获得永生。刘胜的肉身早已腐朽，但他的金缕玉衣作为文化遗产，却在两千年后继续"活"在当代人的认知中。</p>
        </div>
      </div>
    </div>
  </section>

  <!-- 创作方法 -->
  <section id="method">
    <h2>创作方法与技术路线</h2>
    <div class="section-content">
      <p>本三维动画创作采用多学科交叉的研究方法，结合历史学、考古学与数字媒体艺术，形成完整的技术与艺术路径。</p>
      
      <ul style="list-style-type: none; margin: 1.5rem 0;">
        <li style="padding: 0.8rem 0; border-bottom: 1px solid rgba(255,255,255,0.1); position: relative; padding-left: 1.8rem;">
          <strong class="highlight">史实基石：</strong>基于河北省博物院提供的考古资料、测量数据与高清图像，确保文物复原的准确性。
        </li>
        <li style="padding: 0.8rem 0; border-bottom: 1px solid rgba(255,255,255,0.1); position: relative; padding-left: 1.8rem;">
          <strong class="highlight">文学结构：</strong>以"黄粱一梦"作为哲学母题，构建多层叙事框架，使动画超越单纯的历史再现。
        </li>
        <li style="padding: 0.8rem 0; position: relative; padding-left: 1.8rem;">
          <strong class="highlight">动画表达：</strong>三维建模、灯光、材质、动画
        </li>
      </ul>
    </div>
  </section>

  <!-- 返回顶部按钮 -->
  <div class="back-to-top" id="backToTop">
    <i class="fas fa-chevron-up"></i>
  </div>

  <!-- 页脚 -->
  <footer>
    <div class="footer-content">
      <div class="footer-logo">金缕玉衣</div>
      <div class="footer-info">
        <p>毕业设计展示网站 · 金缕玉衣三维动画创作</p>
        <p>资料参考：河北省博物院 · 满城汉墓考古报告 · 《西汉金缕玉衣研究》</p>
        <p>指导老师：李勇 | 动画制作：22级动画2班 刘海鑫</p>
      </div>
      <div class="copyright">
        <p>© 2026 美术与设计学院 毕业设计展</p>
        <p>本网站托管于 <a href="https://pages.github.com" style="color: var(--gold);">GitHub Pages</a></p>
      </div>
    </div>
  </footer>

  <script>
    // 页面加载
    window.addEventListener('load', function() {
      const loading = document.getElementById('loading');
      setTimeout(() => {
        loading.classList.add('hidden');
        setTimeout(() => {
          loading.style.display = 'none';
        }, 500);
      }, 800);
    });

    // 移动端菜单功能
    const hamburger = document.getElementById('hamburger');
    const navLinks = document.getElementById('navLinks');
    
    hamburger.addEventListener('click', function() {
      this.classList.toggle('active');
      navLinks.classList.toggle('active');
    });
    
    // 点击导航链接后关闭菜单
    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', function() {
        hamburger.classList.remove('active');
        navLinks.classList.remove('active');
      });
    });
    
    // 点击外部关闭菜单
    document.addEventListener('click', function(e) {
      if (!e.target.closest('nav') && navLinks.classList.contains('active')) {
        hamburger.classList.remove('active');
        navLinks.classList.remove('active');
      }
    });
    
    // 导航栏滚动效果
    window.addEventListener('scroll', function() {
      const nav = document.querySelector('nav');
      const backToTop = document.getElementById('backToTop');
      
      if (window.scrollY > 50) {
        nav.style.boxShadow = '0 5px 15px rgba(0, 0, 0, 0.5)';
      } else {
        nav.style.boxShadow = '0 2px 10px rgba(0, 0, 0, 0.5)';
      }
      
      // 显示/隐藏返回顶部按钮
      if (window.scrollY > 500) {
        backToTop.classList.add('show');
      } else {
        backToTop.classList.remove('show');
      }
    });
    
    // 平滑滚动到指定区域
    function scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        window.scrollTo({
          top: section.offsetTop - 70,
          behavior: 'smooth'
        });
      }
    }
    
    // 为所有导航链接添加点击事件
    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', function(e) {
        e.preventDefault();
        const href = this.getAttribute('href');
        if (href.startsWith('#')) {
          scrollToSection(href.substring(1));
        }
      });
    });
    
    // 返回顶部功能
    document.getElementById('backToTop').addEventListener('click', function() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    });
    
    // 视频控制功能
    const video = document.getElementById('goldJadeVideo');
    
    function toggleFullscreen() {
      if (video.requestFullscreen) {
        video.requestFullscreen();
      } else if (video.mozRequestFullScreen) {
        video.mozRequestFullScreen();
      } else if (video.webkitRequestFullscreen) {
        video.webkitRequestFullscreen();
      } else if (video.msRequestFullscreen) {
        video.msRequestFullscreen();
      }
    }
    
    function toggleMute() {
      video.muted = !video.muted;
      const volumeIcon = document.querySelector('.fa-volume-up');
      if (video.muted) {
        volumeIcon.classList.remove('fa-volume-up');
        volumeIcon.classList.add('fa-volume-mute');
        showToast('已静音');
      } else {
        volumeIcon.classList.remove('fa-volume-mute');
        volumeIcon.classList.add('fa-volume-up');
        showToast('已取消静音');
      }
    }
    
    function togglePlay() {
      if (video.paused) {
        video.play();
        document.querySelector('.fa-play').classList.remove('fa-play');
        document.querySelector('.fa-play').classList.add('fa-pause');
        showToast('开始播放');
      } else {
        video.pause();
        document.querySelector('.fa-pause').classList.remove('fa-pause');
        document.querySelector('.fa-pause').classList.add('fa-play');
        showToast('已暂停');
      }
    }
    
    // 视频事件监听
    video.addEventListener('play', function() {
      document.querySelector('.fa-play').classList.remove('fa-play');
      document.querySelector('.fa-play').classList.add('fa-pause');
    });
    
    video.addEventListener('pause', function() {
      document.querySelector('.fa-pause').classList.remove('fa-pause');
      document.querySelector('.fa-pause').classList.add('fa-play');
    });
    
    // 显示提示
    function showToast(message) {
      const toast = document.createElement('div');
      toast.textContent = message;
      toast.style.cssText = `
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: rgba(0,0,0,0.8);
        color: #d4af37;
        padding: 12px 20px;
        border-radius: 8px;
        z-index: 10000;
        border: 1px solid #d4af37;
        font-size: 14px;
        animation: fadeInOut 2s;
      `;
      
      document.body.appendChild(toast);
      
      setTimeout(() => {
        if (toast.parentNode) {
          document.body.removeChild(toast);
        }
      }, 2000);
    }
    
    // 添加CSS动画
    const style = document.createElement('style');
    style.textContent = `
      @keyframes fadeInOut {
        0% { opacity: 0; transform: translate(-50%, -50%) scale(0.8); }
        20% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        80% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        100% { opacity: 0; transform: translate(-50%, -50%) scale(0.8); }
      }
    `;
    document.head.appendChild(style);
    
    // 图片懒加载
    if ('IntersectionObserver' in window) {
      const imageObserver = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const img = entry.target;
            img.src = img.dataset.src;
            imageObserver.unobserve(img);
          }
        });
      });
      
      document.querySelectorAll('img[data-src]').forEach(img => {
        imageObserver.observe(img);
      });
    }
    
    // 处理横屏
    function handleOrientation() {
      if (window.orientation === 90 || window.orientation === -90) {
        document.body.classList.add('landscape');
      } else {
        document.body.classList.remove('landscape');
      }
    }
    
    window.addEventListener('orientationchange', handleOrientation);
    
    // 防止iOS Safari弹性滚动
    document.addEventListener('touchmove', function(e) {
      if (e.scale !== 1) {
        e.preventDefault();
      }
    }, { passive: false });
  </script>
</body>
</html>
