---
hide:
  - navigation
  - toc
  - path
---

<style>

  body {
    background-color: #000000 !important;
    background-image: 
      radial-gradient(circle at 30% 60%, rgba(255, 100, 50, 0.15) 0%, transparent 60%),
      radial-gradient(circle at 15% 35%, rgba(220, 20, 20, 0.25) 0%, transparent 50%),
      radial-gradient(circle at 85% 70%, rgba(144, 1, 1, 0.2) 0%, transparent 50%),
      linear-gradient(rgba(255, 255, 255, 0.045) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255, 255, 255, 0.045) 1px, transparent 1px) !important;
    background-size: 100% 100%, 100% 100%, 100% 100%, 40px 40px, 40px 40px !important;
    background-attachment: fixed !important;
    animation: backgroundShift 15s ease-in-out infinite alternate;
  }

  @keyframes backgroundShift {
    0% { background-position: 0% 0%, 0% 0%, 0% 0%, 0px 0px, 0px 0px; }
    100% { background-position: 5% 5%, -5% -5%, 3% 3%, 0px 0px, 0px 0px; }
  }

  .md-main, .md-content { background: transparent !important; }
  .md-grid { max-width: 100% !important; padding: 0 !important; margin: 0 !important; }
  .md-main__inner { margin: 0 !important; }
  .md-content__inner { margin: 0 !important; padding: 0 !important; max-width: 100% !important; }
  .md-typeset h1:first-child { display: none; }

  .astro-hero {
    display: flex;
    flex-direction: row; 
    flex-wrap: wrap; 
    align-items: center; 
    justify-content: center; 
    gap: 40px; 
    min-height: 80vh; 
    padding: 40px 5%; 
    max-width: 1400px; 
    margin: 0 auto; 
    animation: fadeIn 1s ease-out;
  }

  .hero-content {
    flex: 1 1 450px; 
    max-width: 700px;
  }

  .hero-visual {
    flex: 1 1 350px; 
    max-width: 450px;
    height: 400px;
    display: flex;
    position: relative;
  }

  .md-typeset h1.astro-title {
    display: flex !important;
    align-items: center;
    flex-wrap: wrap;
    gap: 15px;

    font-size: clamp(2.5rem, 4.5vw, 4rem) !important;
    font-weight: 800;
    margin: 0 0 5px 0 !important;
    padding: 0 !important;
    letter-spacing: -0.02em;
    color: #ffffff !important;
    line-height: 1.1;
  }

  .mars-logo { 
    height: clamp(40px, 5vw, 65px) !important;
    width: auto !important;
    object-fit: contain;
  }
  
  .astro-title-text { color: #ffffff; font-weight: 700; white-space: nowrap; }
  
  .astro-subtitle {
    font-size: 1.4rem; color: #e0e0e0; margin: 0 0 35px 0 !important;
    font-weight: 500; letter-spacing: 4px; text-transform: uppercase;
  }
  .astro-buttons { display: flex; gap: 15px; flex-wrap: wrap; align-items: center; }

  .astro-btn-primary {
    background-color: #cc0000; color: #ffffff !important; padding: 10px 24px;
    border-radius: 30px; font-size: 15px; font-weight: 600; text-decoration: none !important;
    transition: all 0.3s ease; display: flex; align-items: center; gap: 8px;
    border: 1px solid #ff1a1a; box-shadow: 0 4px 20px rgba(204, 0, 0, 0.4); 
  }
  .astro-btn-primary:hover {
    background-color: #ff1a1a; transform: translateY(-2px); box-shadow: 0 6px 25px rgba(255, 26, 26, 0.6);
  }
  .astro-btn-secondary {
    background-color: transparent; color: #ffffff !important; font-size: 15px; 
    font-weight: 500; text-decoration: none !important; transition: all 0.2s ease;
  }
  .astro-btn-secondary:hover { color: #ff4d4d !important; transform: translateX(5px); }

  .stz-footer {
    margin-top: 50px; display: flex; align-items: center; flex-wrap: wrap;
    gap: 8px; font-size: 14px; color: #a1a1aa; font-weight: 400; animation: fadeIn 1.5s ease-out;
  }
  .stz-logo { height: 22px !important; width: auto !important; opacity: 0.9; transition: opacity 0.3s ease; }
  .stz-footer:hover .stz-logo, .stz-footer:hover { opacity: 1; color: #ffffff; }

  .contributors-cluster {
    position: relative;
    width: 100%;
    height: 100%;
  }

  .avatar {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(255, 255, 255, 0.15);
    background-color: rgba(30, 30, 30, 0.6);
    object-fit: cover;
    box-shadow: 0 8px 20px rgba(0,0,0,0.4);
    transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275), border-color 0.3s ease;
  }

  .avatar:hover {
    transform: scale(1.15);
    border-color: #ff4d4d;
    z-index: 10;
  }

  .av-lg { width: 68px; height: 68px; }
  .av-md { width: 48px; height: 48px; }
  .av-sm { width: 32px; height: 32px; }
  .av-empty { border: 1px dashed rgba(255, 255, 255, 0.2); box-shadow: none; background: transparent; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>

<div class="astro-hero">
  
  <div class="hero-content">
    <h1 class="astro-title">
      <img src="assets/logo.png" alt="MARS Logo" class="mars-logo">
      <span class="astro-title-text">Documentation</span>
    </h1>
    <p class="astro-subtitle">The FRC Robotics Framework</p>
    
    <div class="astro-buttons">
      <a href="getting-started/overview/" class="astro-btn-primary">
        Install MARS 
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="7 10 12 15 17 10"></polyline><line x1="12" y1="15" x2="12" y2="3"></line></svg>
      </a>
      <a href="getting-started/overview/" class="astro-btn-secondary">
        Learn about MARS features &rarr;
      </a>
    </div>

    <div class="stz-footer">
      Powered by <img src="assets/stz.png" alt="STZ Logo" class="stz-logo">
    </div>
  </div>

  <div class="hero-visual">
    <div class="contributors-cluster">
      
      <img src="https://github.com/Imcab.png" alt="Imcab" class="avatar av-lg" style="top: 40%; left: 45%; z-index: 5;">
      
      <img src="https://github.com/wpilibsuite.png" alt="WPILib" class="avatar av-md" style="top: 15%; left: 30%;">
      
      <img src="https://github.com/esangarr.png" alt="esangarr" class="avatar av-md" style="top: 65%; left: 60%;">

      <img src="https://github.com/DarkarChong.png" alt="DarkarChong" class="avatar av-md" style="top: 50%; left: 15%;">

      <img src="https://github.com/Endermite123.png" alt="Endermite123" class="avatar av-sm" style="top: 25%; left: 70%;">

      <div class="avatar av-sm av-empty" style="top: 10%; left: 60%;"></div>
      <div class="avatar av-md av-empty" style="top: 80%; left: 35%;"></div>
      
    </div>
  </div>

</div>