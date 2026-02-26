<html lang="en"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Glint Browser - A custom web proxy I built to bypass restrictions">
  <meta property="og:title" content="Glint Browser">
  <meta property="og:description" content="A custom web proxy to bypass restrictions">
  <meta property="og:type" content="website">
  <meta property="og:image" content="https://glintapp.org/images/page.png">
  <meta property="og:image:alt" content="Glint Browser">
  <meta property="og:url" content="https://glintapp.org">
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="Glint Browser">
  <meta name="twitter:description" content="A custom web proxy to bypass restrictions">
  <meta name="twitter:image" content="https://glintapp.org/images/page.png">
  <title>Glint Browser</title>

  <link rel="preload" href="images/logo.png" as="image">
  <link rel="preload" href="js/main.js" as="script">

  <link rel="dns-prefetch" href="https://fonts.googleapis.com">
  <link rel="dns-prefetch" href="https://fonts.gstatic.com">
  <link rel="dns-prefetch" href="https://cdnjs.cloudflare.com">

  <link rel="icon" type="image/png" href="images/favicon.png">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="">

  <style>
    :root {
      --bg-primary: #0f0f0f;
      --bg-secondary: #1a1a1a;
      --text-primary: #ffffff;
      --text-secondary: #d0d0d0
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box
    }

    body {
      background: #0f0f0f;
      min-height: 100vh
    }

    .browser {
      width: 100%;
      min-height: 100vh;
      display: flex;
      flex-direction: column
    }

    .top-bar {
      background: var(--bg-secondary);
      height: 44px
    }

    .toolbar {
      background: var(--bg-primary);
      height: 48px
    }
  </style>

  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet" media="all" onload="this.media='all'">
  <noscript>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap"
      rel="stylesheet">
  </noscript>

  <style>:root {
  --bg-primary: #0f0f0f;
  --bg-secondary: #1a1a1a;
  --bg-tab-bar: #1e1e1e;
  --bg-tertiary: #222222;
  --bg-content: #0f0f0f;
  --bg-header: #1e1e1e;
  --bg-active: #0f0f0f;
  --bg-hover: #282828;
  --bg-card: #1a1a1a;
  --bg-card-hover: #222222;
  --bg-input: #1a1a1a;
  --bg-dropdown: #0f0f0f;
  --text-primary: #ffffff;
  --text-secondary: #d0d0d0;
  --text-tertiary: #d0d0d0;
  --text-muted: rgba(255, 255, 255, 0.6);
  --border-color: rgba(255, 255, 255, 0.08);
  --border-hover: rgba(255, 255, 255, 0.14);
  --shadow: rgba(0, 0, 0, 0.6);
  --accent: #d0d0d0;
  --accent-hover: #e8e8e8;
  --success: #5a8a5a;
  --logo-filter: brightness(0) invert(1);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 105%;
}

body {
  background: #0f0f0f;
  width: 100%;
  min-height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
}

body.dragging {
  overflow-y: hidden;
  overflow-x: hidden;
}


.browser {
  width: 100%;
  min-height: 100vh;
  background: #0f0f0f;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  position: relative;
  z-index: 1;
  border: none;
}


/* Animations */
@keyframes tabAppear {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes tabClose {
  from {
    opacity: 1;
    transform: scale(1);
  }

  to {
    opacity: 0;
    transform: scale(0.8);
  }
}



/* Header and tabs */
.top-bar {
  display: flex;
  align-items: center;
  background: var(--bg-header);
  padding: 0 0 0 12px;
  height: 44px;
  position: relative;
  border: none;
  overflow-x: hidden;
  overflow-y: hidden;
}


.tabs {
  display: flex;
  align-items: flex-end;
  height: 100%;
  flex: 1;
  margin-left: 0;
  gap: 0;
  overflow-x: hidden;
  overflow-y: hidden;
  padding-left: 12px;
  margin-left: -12px;
  position: relative;
}


.tab {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  flex: 1 1 0;
  min-width: 120px;
  max-width: 220px;
  padding: 0 36px 0 16px;
  background: var(--bg-tab-bar);
  border-radius: 8px 8px 0 0;
  height: 36px;
  font-size: 13px;
  color: var(--text-secondary);
  cursor: grab;
  user-select: none;
  position: relative;
  border: none;
  border-bottom: none;
  transition: background 0.2s ease, color 0.2s ease, transform 0.2s ease;
  overflow: visible;
}

.tab::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: -8px;
  width: 8px;
  height: 8px;
  background: transparent;
  border-bottom-right-radius: 8px;
  box-shadow: 4px 4px 0 4px var(--bg-tab-bar);
  z-index: 0;
  pointer-events: none;
  transition: box-shadow 0.2s ease 0s;
}

.tab:first-child::before {
  left: -8px;
  box-shadow: 4px 4px 0 4px var(--bg-tab-bar);
}

.tab::after {
  content: '';
  position: absolute;
  bottom: 0;
  right: -8px;
  width: 8px;
  height: 8px;
  background: transparent;
  border-bottom-left-radius: 8px;
  box-shadow: -4px 4px 0 4px var(--bg-tab-bar);
  z-index: 0;
  pointer-events: none;
  transition: box-shadow 0.2s ease 0s;
}

.tab:active {
  cursor: grabbing;
}

.tab:not(.active):hover {
  background: var(--bg-hover);
  transition: background 0.2s ease, color 0.2s ease, transform 0.2s ease;
}

.tab:not(.active):hover::before {
  box-shadow: 4px 4px 0 4px var(--bg-hover);
  transition: box-shadow 0.2s ease 0s;
}

.tab:first-child:not(.active):hover::before {
  left: -8px;
  box-shadow: 4px 4px 0 4px var(--bg-hover);
  transition: box-shadow 0.2s ease 0s;
}

.tab:not(.active):hover::after {
  box-shadow: -4px 4px 0 4px var(--bg-hover);
  transition: box-shadow 0.2s ease 0s;
}

.tab-fav,
.tab-title,
.tab-favicon,
.tab-close {
  position: relative;
  z-index: 2;
}

.tab.closing {
  animation: tabClose 0.2s ease forwards;
}


.tab.active {
  background: var(--bg-active);
  color: var(--text-primary);
  z-index: 2;
  transition: background 0.2s ease, color 0.2s ease;
}

.tab.active::before {
  box-shadow: 4px 4px 0 4px var(--bg-active);
  transition: box-shadow 0.2s ease 0s;
}

.tab:first-child.active::before {
  left: -8px;
  box-shadow: 4px 4px 0 4px var(--bg-active);
  transition: box-shadow 0.2s ease 0s;
}

.tab.active::after {
  box-shadow: -4px 4px 0 4px var(--bg-active);
  transition: box-shadow 0.2s ease 0s;
}

.tab.dragging {
  opacity: 1;
  z-index: 1000;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
  transition: none !important;
  cursor: grabbing !important;
}

.tab:not(.dragging) {
  transition: background 0.2s ease, color 0.2s ease, transform 0.2s ease;
}

.tab:not(.dragging)::before,
.tab:not(.dragging)::after {
  transition: box-shadow 0.2s ease 0s;
}


.tab-title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-right: 10px;
}


.tab-close {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  opacity: 0.6;
  cursor: pointer;
  padding: 0;
  width: 22px;
  height: 22px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  transition: background 0.15s;
  z-index: 2;
}

.tab-close:hover {
  opacity: 1;
  background: var(--bg-hover);
  border-radius: 50%;
}

/* Divider between tabs */
.tab-divider {
  width: 1px;
  height: 15px;
  background: #444444;
  align-self: center;
  border-radius: 1px;
  opacity: 1;
  margin: 15px 10px 5px 10px;
  display: block;
}

.tab-favicon {
  width: 16px;
  height: 16px;
  margin-right: 8px;
  object-fit: contain;
}

.tab-fav {
  width: 20px;
  height: 20px;
  margin-right: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  color: var(--text-secondary);
  background-color: transparent;
  border-radius: 0;
  opacity: 0.7;
}

.tab-logo {
  width: 20px;
  height: 20px;
  object-fit: contain;
  filter: var(--logo-filter);
}

/* New tab button */
.add-tab {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  color: var(--text-secondary);
  cursor: pointer;
  margin-left: 5px;
  margin-bottom: 0;
  background: none;
  border: none;
  transition: all 0.2s ease;
  position: relative;
  top: -2px;
  padding: 0;
  font-size: 15px;
}

.add-tab:hover {
  background: var(--bg-hover);
  transform: rotate(90deg);
}

.add-tab i {
  transition: transform 0.2s ease;
}

.add-tab:hover i {
  transform: scale(1.1);
}

/* Toolbar stuff */
.toolbar {
  display: flex;
  align-items: center;
  padding: 0 18px;
  background: var(--bg-primary);
  height: 48px;
  position: relative;
}


.nav-btns {
  display: flex;
  align-items: center;
  gap: 2px;
}

.nav-btn {
  background: none;
  border: none;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-secondary);
  cursor: pointer;
  font-size: 15px;
  transition: background 0.15s;
}

.nav-btn:hover {
  background: var(--bg-hover);
}

/* Address bar stuff */
.url-bar {
  flex: 1;
  display: flex;
  align-items: center;
  background: var(--bg-input);
  border-radius: 20px;
  height: 32px;
  margin: 0 12px;
  padding: 0 14px;
  box-shadow: none;
}

.url-bar-lock {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 16px;
  height: 16px;
  margin-right: 8px;
  color: var(--success);
  font-size: 12px;
}

.url-bar-lock i {
  font-size: 12px;
}

.url-input {
  flex: 1;
  border: none;
  outline: none;
  background: transparent;
  font-size: 15px;
  color: var(--text-primary);
  height: 100%;
}

.url-input::placeholder {
  color: var(--text-tertiary);
}

/* Action buttons */
.toolbar-actions {
  display: flex;
  align-items: center;
  gap: 2px;
}

.action-btn {
  background: none;
  border: none;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-secondary);
  cursor: pointer;
  font-size: 17px;
  transition: background 0.15s;
}

.action-btn:hover {
  background: var(--bg-hover);
}

/* Main content area */
.view {
  flex: 1;
  background-color: #0c0c0c;
  background-image: linear-gradient(135deg, rgba(20, 20, 20, 0.4) 0%, rgba(8, 8, 8, 0.6) 100%);
  background-attachment: fixed;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 40px;
  position: relative;
  width: 100%;
  min-height: calc(100vh - 92px);
  isolation: isolate;
}

.view:not(.frame-active) {
  padding-top: 0;
}

.view.frame-active {
  overflow: hidden !important;
  overflow-y: hidden !important;
  overflow-x: hidden !important;
}

.view.frame-active .start-page {
  display: none !important;
  pointer-events: none !important;
  z-index: -1 !important;
}

.view.frame-active #frames {
  pointer-events: auto !important;
  z-index: 100 !important;
}


#frames {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  pointer-events: none;
  overflow: visible;
}

#frames.active {
  pointer-events: auto !important;
  z-index: 100 !important;
}

.frame {
  width: 100% !important;
  height: calc(100vh - 92px) !important;
  border: none !important;
  display: none;
  background-color: white;
  pointer-events: auto !important;
  overflow: auto !important;
  position: relative;
  z-index: 10;
}

.frame.visible {
  display: block !important;
}



.start-page {
  width: 100%;
  max-width: 100%;
  position: relative;
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 5;
  pointer-events: auto;
}

.start-page[style*="display: none"] {
  pointer-events: none !important;
  z-index: -1 !important;
}

.start-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 30px 20px;
}

/* Hero section */
.welcome {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding: 40px 0;
  margin-bottom: 40px;
}

.logo-wrap {
  margin-bottom: 40px;
  text-align: center;
}

.main-logo {
  width: 180px;
  height: auto;
  max-width: 100%;
  filter: var(--logo-filter) drop-shadow(0 8px 24px var(--shadow));
  transition: transform 0.3s ease;
}

.main-logo:hover {
  transform: scale(1.05);
}

/* Search box styling */
.search-wrap {
  width: 100%;
  max-width: 650px;
  margin: 0 auto;
}

.search-bar {
  display: flex;
  align-items: center;
  background: #1a1a1a;
  border-radius: 14px;
  padding: 6px 8px 6px 25px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.search-bar:hover {
  background: #222222;
  border-color: rgba(255, 255, 255, 0.12);
  transform: translateY(-2px);
}

.search-bar:focus-within {
  background: #222222;
  border-color: rgba(255, 255, 255, 0.14);
  transform: translateY(-2px);
}

.search-icon {
  color: var(--text-secondary);
  font-size: 18px;
  margin-right: 15px;
  flex-shrink: 0;
  opacity: 0.7;
}

.search-input {
  background: transparent;
  border: none;
  color: var(--text-primary);
  font-size: 16px;
  padding: 16px 0;
  width: 100%;
  outline: none;
}

.search-input::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.quick-links {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 16px;
  margin-top: 32px;
}

.qlink {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 6px;
  width: 84px;
  height: 76px;
  padding: 0;
  background: var(--bg-card);
  border-radius: 10px;
  border: 1px solid var(--border-color);
  color: var(--text-primary);
  text-decoration: none;
  font-size: 12px;
  transition: border-color 0.2s, transform 0.15s;
  box-sizing: border-box;
}

.qlink:hover {
  border-color: var(--border-hover);
  transform: translateY(-1px);
  color: var(--text-primary);
}

.qlink-icon {
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

.qlink-icon img { width: 32px; height: 32px; object-fit: contain; }
.qlink-games .qlink-icon { color: var(--text-secondary); }

.qlink-label {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 76px;
  text-align: center;
}


/* Footer */
.footer {
  margin-top: 48px;
  text-align: center;
  padding: 20px 0;
  color: var(--text-tertiary);
  font-size: 14px;
}

.footer p {
  font-size: 14px;
  letter-spacing: 0.5px;
}

.footer .network {
  color: var(--accent);
  font-weight: 500;
  transition: all 0.3s ease;
  text-decoration: none;
  position: relative;
  padding-bottom: 2px;
}

.footer .network:hover {
  color: var(--accent-hover);
  text-decoration: none;
}

.footer .network::after {
  content: '';
  position: absolute;
  width: 0;
  height: 1px;
  bottom: 0;
  left: 0;
  background-color: var(--accent-hover);
  transition: width 0.3s ease;
}

.footer .network:hover::after {
  width: 100%;
}

@media (max-width: 1200px) {
  .start-inner {
    padding: 30px 15px;
  }
}

@media (max-width: 900px) {
  .welcome {
    padding: 30px 0;
    margin-bottom: 30px;
  }

  .start-inner {
    padding: 25px 15px;
  }
}

@media (max-width: 768px) {
  .tab {
    min-width: 80px;
    padding: 0 24px 0 8px;
  }

  .url-bar {
    width: 100%;
  }

  .toolbar-actions {
    display: none;
  }

  .start-inner {
    padding: 20px 15px;
  }

  .welcome {
    padding: 20px 0;
    margin-bottom: 25px;
  }

  .logo-wrap {
    margin-bottom: 30px;
  }

  .main-logo {
    width: 140px;
  }

  .search-wrap {
    max-width: 100%;
  }

  .search-bar {
    padding: 5px 5px 5px 20px;
  }

  .search-input {
    font-size: 15px;
    padding: 14px 0;
  }
}

@media (max-width: 600px) {
  .logo-wrap {
    margin-bottom: 25px;
  }

  .main-logo {
    width: 120px;
  }

  .search-bar {
    padding: 4px 4px 4px 18px;
    border-radius: 12px;
  }

  .search-input {
    font-size: 14px;
    padding: 12px 0;
  }

  .start-inner {
    padding: 15px 10px;
  }

  .welcome {
    padding: 15px 0;
    margin-bottom: 20px;
  }
}

@media (max-width: 480px) {
  .top-bar {
    height: 40px;
  }

  .toolbar {
    height: 44px;
    padding: 0 12px;
  }

  .tab {
    min-width: 70px;
    padding: 0 20px 0 6px;
    font-size: 12px;
  }

  .tab-title {
    font-size: 12px;
  }

  .main-logo {
    width: 100px;
  }

  .search-bar {
    padding: 3px 3px 3px 15px;
  }

  .search-icon {
    font-size: 16px;
    margin-right: 12px;
  }

  .search-input {
    font-size: 13px;
    padding: 10px 0;
  }

  .footer {
    padding: 15px 0;
  }

  .footer p {
    font-size: 12px;
  }
}

.options-dropdown {
  position: fixed;
  top: 100px;
  right: 15px;
  background: #141414;
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  z-index: 1000;
  min-width: 180px;
  display: none;
  padding: 6px 0;
}

.menu-item {
  padding: 8px 14px;
  color: #ccc;
  font-size: 13px;
  cursor: pointer;
}

.menu-item:hover {
  background: rgba(255, 255, 255, 0.08);
  color: #fff;
}

.menu-divider {
  height: 1px;
  background: rgba(255, 255, 255, 0.1);
  margin: 6px 0;
}

.menu-label {
  padding: 6px 14px 4px;
  color: #666;
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.search-option {
  display: flex;
  align-items: center;
  gap: 10px;
}

.search-option input[type="radio"] {
  appearance: none;
  -webkit-appearance: none;
  width: 14px;
  height: 14px;
  border: 2px solid #444;
  border-radius: 50%;
  cursor: pointer;
  position: relative;
  flex-shrink: 0;
}

.search-option input[type="radio"]:checked {
  border-color: #666;
}

.search-option input[type="radio"]:checked::after {
  content: '';
  position: absolute;
  top: 2px;
  left: 2px;
  width: 6px;
  height: 6px;
  background: #666;
  border-radius: 50%;
}

.search-option label {
  cursor: pointer;
  font-size: 13px;
  color: #ccc;
}

.search-option:hover label {
  color: #fff;
}

@media (max-width: 768px) {
  .options-dropdown {
    right: 10px;
    top: 90px;
    min-width: 160px;
  }
}

@media (max-width: 480px) {
  .options-dropdown {
    right: 8px;
    top: 85px;
    min-width: 150px;
  }
}

</style>

  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" media="all" onload="this.media='all'">
  <noscript>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
  </noscript>

  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag() { dataLayer.push(arguments); }
    gtag("js", new Date());
    gtag("config", "G-YCZFXTQFN3");
    window.addEventListener('load', function () {
      var s = document.createElement('script');
      s.src = 'https://www.googletagmanager.com/gtag/js?id=G-YCZFXTQFN3';
      s.async = true;
      document.head.appendChild(s);
    });
  </script>

  <script src="baremux/index.js" defer=""></script>
  <script src="epoxy/index.js" defer=""></script>

  <script src="js/utils/url-utils.js" defer=""></script>
  <script src="js/utils/favicon.js" defer=""></script>
  <script src="js/utils/proxy-frames.js" defer=""></script>

  <script src="js/tabs/tab-history.js" defer=""></script>
  <script src="js/tabs/tab-storage.js" defer=""></script>
  <script src="js/tabs/tab-dragging.js" defer=""></script>
  <script src="js/tabs/tab-management.js" defer=""></script>

  <script src="js/navigation/navigation.js" defer=""></script>
  <script src="js/search.js" defer=""></script>
  <script src="js/proxy-config.js" defer=""></script>
  <script src="js/options.js" defer=""></script>
  <script src="js/main.js" defer=""></script>

  <script src="js/register-sw.js" defer=""></script>
<script src="https://www.googletagmanager.com/gtag/js?id=G-YCZFXTQFN3" async=""></script></head>

<body>
  <div class="browser">
    <div class="top-bar">
      <div class="tabs">
        <div class="tab active" data-tab-id="newtab" style="transform: translateY(1px);">
          <div class="tab-fav">
            <img src="images/logo.png" alt="Glint Logo" class="tab-logo">
          </div>
          <span class="tab-title">New Tab</span>
          <span class="tab-close"><i class="fas fa-times"></i></span>
        </div>
        <div class="add-tab">
          <i class="fas fa-plus"></i>
        </div>
      </div>
    </div>
    <div class="toolbar">
      <div class="nav-btns">
        <button class="nav-btn back-btn" aria-label="Go back">
          <i class="fas fa-arrow-left"></i>
        </button>
        <button class="nav-btn forward-btn" aria-label="Go forward">
          <i class="fas fa-arrow-right"></i>
        </button>
        <button class="nav-btn reload-btn" aria-label="Reload page">
          <i class="fas fa-redo"></i>
        </button>
      </div>
      <div class="url-bar">
        <span class="url-bar-lock"><i class="fas fa-lock"></i></span>
        <input type="text" class="url-input" placeholder="Search or enter a URL">
      </div>
      <div class="toolbar-actions">
        <button class="action-btn menu-btn" aria-label="More options">
          <i class="fas fa-ellipsis-v"></i>
        </button>
      </div>
    </div>
    <div class="view">
      <div class="start-page" style="display: flex;">
        <div class="start-inner" style="margin-top: 29px;">
          <div class="welcome">
            <div class="logo-wrap">
              <img src="images/logo.png" alt="Glint Logo" class="main-logo">
            </div>

            <div class="search-wrap">
              <div class="search-bar">
                <div class="search-icon">
                  <i class="fas fa-search"></i>
                </div>
                <input type="text" class="search-input" placeholder="Search or enter a site URL">
              </div>
            </div>

            <div class="quick-links">
              <a href="#" class="qlink qlink-yt" data-url="https://www.youtube.com" title="YouTube">
                <span class="qlink-icon"><img src="images/youtube.png" alt="" width="32" height="32"></span>
                <span class="qlink-label">YouTube</span>
              </a>
              <a href="#" class="qlink qlink-reddit" data-url="https://www.reddit.com" title="Reddit">
                <span class="qlink-icon"><img src="images/reddit.png" alt="" width="32" height="32"></span>
                <span class="qlink-label">Reddit</span>
              </a>
              <a href="#" class="qlink qlink-discord" data-url="https://discord.com" title="Discord">
                <span class="qlink-icon"><img src="images/discord.png" alt="" width="32" height="32"></span>
                <span class="qlink-label">Discord</span>
              </a>
              <a href="#" class="qlink qlink-x" data-url="https://x.com" title="X">
                <span class="qlink-icon"><img src="images/X.png" alt="" width="32" height="32"></span>
                <span class="qlink-label">X</span>
              </a>
              <a href="#" class="qlink qlink-games" data-url="/games.html" title="Games">
                <span class="qlink-icon"><i class="fas fa-dice"></i></span>
                <span class="qlink-label">Games</span>
              </a>
            </div>
          </div>

          <div class="footer">
            <p>
              Developed by
              <a href="https://discord.gg/UFTf5rE5fE" class="network" target="_blank">Hydra Network</a>
            </p>
          </div>
        </div>
      </div>

      <div id="frames" style="width: 100%; height: 100%; position: absolute; top: 0px; left: 0px; pointer-events: none; z-index: 1;"><iframe id="frame-newtab" class="frame loading" loading="eager" scrolling="yes" allowtransparency="true" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; fullscreen" style="display: none; border: none; width: 100%; height: calc(-92px + 100vh); pointer-events: auto; position: relative; z-index: 10; overflow: auto;"></iframe></div>
    </div>
  </div>

  <div class="options-dropdown" id="options-dropdown">
    <div class="menu-item" id="tab-cloak-btn">
      Tab Cloak
    </div>

    <div class="menu-divider"></div>

    <div class="menu-label">Search</div>
    <div class="menu-item search-option" data-engine="google">
      <input type="radio" id="dropdown-google" name="dropdown-search-engine" value="google">
      <label for="dropdown-google">Google</label>
    </div>
    <div class="menu-item search-option" data-engine="bing">
      <input type="radio" id="dropdown-bing" name="dropdown-search-engine" value="bing">
      <label for="dropdown-bing">Bing</label>
    </div>
    <div class="menu-item search-option" data-engine="duckduckgo">
      <input type="radio" id="dropdown-duckduckgo" name="dropdown-search-engine" value="duckduckgo">
      <label for="dropdown-duckduckgo">DuckDuckGo</label>
    </div>
    <div class="menu-item search-option" data-engine="yahoo">
      <input type="radio" id="dropdown-yahoo" name="dropdown-search-engine" value="yahoo">
      <label for="dropdown-yahoo">Yahoo</label>
    </div>

  </div>

  <script>
    (function () {
      function centerStartPage() {
        var page = document.querySelector('.start-page');
        var inner = document.querySelector('.start-inner');
        if (!page || !inner) return;
        var pageH = page.offsetHeight;
        var innerH = inner.offsetHeight;
        var offset = Math.max(0, (pageH - innerH) / 2 - 50);
        inner.style.marginTop = offset + 'px';
      }

      function run() { centerStartPage(); }
      if (document.readyState === 'loading') {
        document.addEventListener('DOMContentLoaded', run);
      } else {
        run();
      }
      window.addEventListener('resize', centerStartPage);
    })();
  </script>


</body></html>
