<!doctype html>
<html lang="es" class="h-full">
<head>
  <meta name="google-site-verification" content="sZTPhoeZnbLxTnGGWw7t9iEMYBD8BIFEIoOHjvc1JLw" />
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GAME_ZYRO</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    * { font-family: 'Rajdhani', sans-serif; }
    .font-gaming { font-family: 'Orbitron', sans-serif; }
    
    @keyframes glow {
      0%, 100% { box-shadow: 0 0 5px #00ff88, 0 0 10px #00ff88, 0 0 15px #00ff88; }
      50% { box-shadow: 0 0 10px #00ff88, 0 0 20px #00ff88, 0 0 30px #00ff88; }
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes pulse-border {
      0%, 100% { border-color: #00ff88; }
      50% { border-color: #00ccff; }
    }
    
    .glow-effect { animation: glow 2s ease-in-out infinite; }
    .float-animation { animation: float 3s ease-in-out infinite; }
    .pulse-border { animation: pulse-border 2s ease-in-out infinite; }
    
    .product-card {
      background: linear-gradient(145deg, #1a1a2e 0%, #16213e 100%);
      transition: all 0.3s ease;
    }
    .product-card:hover {
      transform: translateY(-5px) scale(1.02);
      box-shadow: 0 10px 40px rgba(0, 255, 136, 0.3);
    }
    
    .btn-gaming {
      background: linear-gradient(135deg, #00ff88 0%, #00ccff 100%);
      transition: all 0.3s ease;
    }
    .btn-gaming:hover {
      transform: scale(1.05);
      box-shadow: 0 5px 20px rgba(0, 255, 136, 0.5);
    }
    
    .glass-effect {
      background: rgba(26, 26, 46, 0.9);
      backdrop-filter: blur(10px);
    }
    
    ::-webkit-scrollbar { width: 8px; }
    ::-webkit-scrollbar-track { background: #0f0f1a; }
    ::-webkit-scrollbar-thumb { background: linear-gradient(#00ff88, #00ccff); border-radius: 4px; }
    
    .category-btn {
      transition: all 0.3s ease;
    }
    .category-btn.active, .category-btn:hover {
      background: linear-gradient(135deg, #00ff88 0%, #00ccff 100%);
      color: #0f0f1a;
    }
    
    .cart-badge {
      animation: pulse 1s ease infinite;
    }
    
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    
    .input-gaming {
      background: rgba(255,255,255,0.05);
      border: 2px solid rgba(0, 255, 136, 0.3);
      transition: all 0.3s ease;
    }
    .input-gaming:focus {
      border-color: #00ff88;
      box-shadow: 0 0 15px rgba(0, 255, 136, 0.3);
      outline: none;
    }
    
    .toast {
      animation: slideIn 0.3s ease, slideOut 0.3s ease 2.7s;
    }
    @keyframes slideIn {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    @keyframes slideOut {
      from { transform: translateX(0); opacity: 1; }
      to { transform: translateX(100%); opacity: 0; }
    }

    body { box-sizing: border-box; }
  </style>
</head>
<body class="h-full text-white overflow-auto" style="background: linear-gradient(135deg, #2a0a1a 0%, #0f0f1a 25%, #0a1a3a 50%, #2a0a1a 75%, #0a051a 100%);">
  <div id="app" class="min-h-full w-full">
    <div id="toast-container" class="fixed top-4 right-4 z-50 flex flex-col gap-2"></div>

    <header class="glass-effect sticky top-0 z-40 border-b border-[#00ff88]/30">
      <div class="max-w-7xl mx-auto px-4 py-4">
        <div class="flex items-center justify-between">
          <h1 id="store-name" class="font-gaming text-2xl md:text-3xl font-bold bg-gradient-to-r from-[#00ff88] to-[#00ccff] bg-clip-text text-transparent">GAME_ZYRO</h1>
          <nav class="flex items-center gap-4">
            <button onclick="showSection('products')" class="hidden md:block text-gray-300 hover:text-[#00ff88] transition-colors font-semibold">Productos</button>
            <button onclick="showSection('support')" class="hidden md:block text-gray-300 hover:text-[#00ff88] transition-colors font-semibold">Contáctanos</button>
            <button onclick="showSection('cart')" class="relative p-2 rounded-lg bg-[#1a1a2e] hover:bg-[#00ff88]/20 transition-all" aria-label="Ver carrito">
              <svg class="w-6 h-6 text-[#00ff88]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z" />
              </svg>
              <span id="cart-count" class="absolute -top-1 -right-1 bg-gradient-to-r from-[#ff0066] to-[#ff6600] text-white text-xs font-bold rounded-full w-5 h-5 flex items-center justify-center cart-badge hidden">0</span>
            </button>
          </nav>
        </div>
      </div>
    </header>

    <section id="hero-section" class="relative py-16 md:py-24 overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-[#00ff88]/10 via-transparent to-[#00ccff]/10"></div>
      <div class="absolute top-10 left-10 w-32 h-32 bg-[#00ff88]/20 rounded-full blur-3xl"></div>
      <div class="absolute bottom-10 right-10 w-40 h-40 bg-[#00ccff]/20 rounded-full blur-3xl"></div>
      <div class="max-w-7xl mx-auto px-4 text-center relative z-10">
        <h2 id="hero-title" class="font-gaming text-4xl md:text-6xl font-black mb-4 bg-gradient-to-r from-[#00ff88] via-[#00ccff] to-[#00ff88] bg-clip-text text-transparent float-animation">TU DESTINO GAMING DEFINITIVO</h2>
        <p id="hero-subtitle" class="text-xl md:text-2xl text-gray-400 mb-8 font-medium">Los mejores productos para gamers exigentes</p>
        <div class="flex flex-wrap justify-center gap-4">
          <button onclick="showSection('products')" class="btn-gaming px-8 py-3 rounded-full font-gaming font-bold text-[#0f0f1a]">
            VER PRODUCTOS
          </button>
        </div>
      </div>
    </section>

    <section id="products-section" class="py-12">
      <div class="max-w-7xl mx-auto px-4">
        <div class="flex flex-wrap justify-center gap-3 mb-10">
          <button onclick="filterByCategory('all')" class="category-btn active px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold" data-category="all">🎮 Todos</button>

          <button onclick="filterByCategory('teclados')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="teclados">
            <svg viewBox="0 0 60 40" class="w-5 h-5">
              <defs>
                <filter id="catKeyboardLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <rect x="3" y="8" width="54" height="30" rx="3" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="12" cy="12" r="1.5" fill="#00ff88" filter="url(#catKeyboardLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" />
              </circle>
              <circle cx="22" cy="12" r="1.5" fill="#00ccff" filter="url(#catKeyboardLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="0.5s" />
              </circle>
              <circle cx="32" cy="12" r="1.5" fill="#00ff88" filter="url(#catKeyboardLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="1s" />
              </circle>
            </svg>
            Teclados
          </button>

          <button onclick="filterByCategory('ratones')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="ratones">
            <svg viewBox="0 0 40 50" class="w-5 h-5">
              <defs>
                <filter id="catMouseLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <ellipse cx="20" cy="20" rx="12" ry="15" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="15" cy="10" r="1.5" fill="#00ff88" filter="url(#catMouseLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" />
              </circle>
              <circle cx="25" cy="10" r="1.5" fill="#00ccff" filter="url(#catMouseLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" begin="0.6s" />
              </circle>
            </svg>
            Ratones
          </button>

          <button onclick="filterByCategory('sillas')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="sillas">
            <svg viewBox="0 0 40 50" class="w-5 h-5">
              <defs>
                <filter id="catChairLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <rect x="8" y="5" width="24" height="18" rx="2" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="12" cy="8" r="1.2" fill="#00ff88" filter="url(#catChairLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" />
              </circle>
              <circle cx="28" cy="8" r="1.2" fill="#00ccff" filter="url(#catChairLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="0.7s" />
              </circle>
              <line x1="15" y1="23" x2="15" y2="35" stroke="#00ff88" stroke-width="1.5" opacity="0.6" />
              <line x1="25" y1="23" x2="25" y2="35" stroke="#00ff88" stroke-width="1.5" opacity="0.6" />
            </svg>
            Sillas
          </button>

          <button onclick="filterByCategory('moviles')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="moviles">
            <svg viewBox="0 0 40 50" class="w-5 h-5">
              <defs>
                <filter id="catMobileLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <rect x="8" y="5" width="24" height="40" rx="2" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="15" cy="10" r="1.5" fill="#00ff88" filter="url(#catMobileLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" />
              </circle>
              <circle cx="25" cy="10" r="1.5" fill="#00ccff" filter="url(#catMobileLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="0.7s" />
              </circle>
            </svg>
            Móviles
          </button>

          <button onclick="filterByCategory('pc')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="pc">
            <svg viewBox="0 0 60 50" class="w-5 h-5">
              <defs>
                <filter id="catPcLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <rect x="8" y="5" width="44" height="32" rx="2" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="18" cy="10" r="1.2" fill="#00ff88" filter="url(#catPcLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" />
              </circle>
              <circle cx="32" cy="10" r="1.2" fill="#00ccff" filter="url(#catPcLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" begin="0.5s" />
              </circle>
              <circle cx="46" cy="10" r="1.2" fill="#00ff88" filter="url(#catPcLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" begin="1s" />
              </circle>
            </svg>
            PC
          </button>

          <button onclick="filterByCategory('accesorios')" class="category-btn px-5 py-2 rounded-full border-2 border-[#00ff88]/50 font-semibold text-gray-300 flex items-center gap-2" data-category="accesorios">
            <svg viewBox="0 0 50 50" class="w-5 h-5">
              <defs>
                <filter id="catAccessLed">
                  <feGaussianBlur stdDeviation="1.5" result="coloredBlur" />
                  <feMerge>
                    <feMergeNode in="coloredBlur" />
                    <feMergeNode in="SourceGraphic" />
                  </feMerge>
                </filter>
              </defs>
              <circle cx="15" cy="15" r="8" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="35" cy="15" r="8" fill="#1a1a2e" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <path d="M 20 25 Q 25 32 30 25" fill="none" stroke="#00ff88" stroke-width="1.2" opacity="0.8" />
              <circle cx="12" cy="12" r="1.2" fill="#00ff88" filter="url(#catAccessLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" />
              </circle>
              <circle cx="38" cy="12" r="1.2" fill="#00ccff" filter="url(#catAccessLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="0.6s" />
              </circle>
              <circle cx="25" cy="28" r="1.2" fill="#00ff88" filter="url(#catAccessLed)">
                <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="1.2s" />
              </circle>
            </svg>
            Accesorios
          </button>
        </div>

        <div id="products-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6"></div>
      </div>
    </section>

    <section id="cart-section" class="py-12 hidden">
      <div class="max-w-4xl mx-auto px-4">
        <h2 class="font-gaming text-3xl font-bold text-center mb-8 bg-gradient-to-r from-[#00ff88] to-[#00ccff] bg-clip-text text-transparent">🛒 TU CARRITO</h2>
        <div id="cart-items" class="space-y-4 mb-8"></div>
        <div id="cart-empty" class="text-center py-12 hidden">
          <div class="text-6xl mb-4">🛒</div>
          <p class="text-gray-400 text-xl">Tu carrito está vacío</p>
          <button onclick="showSection('products')" class="btn-gaming mt-6 px-8 py-3 rounded-full font-gaming font-bold text-[#0f0f1a]">IR A COMPRAR</button>
        </div>
        <div id="cart-summary" class="glass-effect rounded-2xl p-6 border border-[#00ff88]/30">
          <div class="flex justify-between items-center mb-6">
            <span class="text-xl font-semibold">Total:</span>
            <span id="cart-total" class="font-gaming text-3xl font-bold text-[#00ff88]">€0.00</span>
          </div>
          <button onclick="showCheckout()" class="w-full btn-gaming py-4 rounded-xl font-gaming font-bold text-[#0f0f1a] text-lg">PROCEDER AL PAGO</button>
        </div>
      </div>
    </section>

    <section id="checkout-section" class="py-12 hidden">
      <div class="max-w-2xl mx-auto px-4">
        <h2 class="font-gaming text-3xl font-bold text-center mb-8 bg-gradient-to-r from-[#00ff88] to-[#00ccff] bg-clip-text text-transparent">📦 FINALIZAR PEDIDO</h2>
        <form id="checkout-form" class="glass-effect rounded-2xl p-6 md:p-8 border border-[#00ff88]/30 space-y-6">
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <label for="checkout-name" class="block text-sm font-semibold text-[#00ff88] mb-2">Nombre Completo *</label>
              <input type="text" id="checkout-name" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="Tu nombre">
            </div>
            <div>
              <label for="checkout-email" class="block text-sm font-semibold text-[#00ff88] mb-2">Email *</label>
              <input type="email" id="checkout-email" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="tu@email.com">
            </div>
          </div>
          <div>
            <label for="checkout-phone" class="block text-sm font-semibold text-[#00ff88] mb-2">Teléfono *</label>
            <input type="tel" id="checkout-phone" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="+34 600 000 000">
          </div>
          <div>
            <label for="checkout-address" class="block text-sm font-semibold text-[#00ff88] mb-2">Dirección *</label>
            <input type="text" id="checkout-address" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="Calle, número, piso...">
          </div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div>
              <label for="checkout-city" class="block text-sm font-semibold text-[#00ff88] mb-2">Ciudad *</label>
              <input type="text" id="checkout-city" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="Tu ciudad">
            </div>
            <div>
              <label for="checkout-postal" class="block text-sm font-semibold text-[#00ff88] mb-2">Código Postal *</label>
              <input type="text" id="checkout-postal" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="00000">
            </div>
          </div>
          <div class="border-t border-[#00ff88]/30 pt-6">
            <h3 class="font-gaming text-lg font-bold text-[#00ff88] mb-4">Resumen del Pedido</h3>
            <div id="checkout-summary" class="space-y-2 text-gray-300"></div>
            <div class="flex justify-between items-center mt-4 pt-4 border-t border-[#00ff88]/30">
              <span class="text-xl font-semibold">Total a Pagar:</span>
              <span id="checkout-total" class="font-gaming text-2xl font-bold text-[#00ff88]">€0.00</span>
            </div>
          </div>
          <p class="text-xs text-gray-500 text-center">⚠️ DEMO: Este es un formulario de demostración. Los pedidos se guardan en tu hoja de datos de Canva.</p>
          <button type="submit" id="checkout-submit" class="w-full btn-gaming py-4 rounded-xl font-gaming font-bold text-[#0f0f1a] text-lg">CONFIRMAR PEDIDO</button>
        </form>
      </div>
    </section>

    <section id="support-section" class="py-12 hidden">
      <div class="max-w-2xl mx-auto px-4">
        <h2 class="font-gaming text-3xl font-bold text-center mb-8 bg-gradient-to-r from-[#00ff88] to-[#00ccff] bg-clip-text text-transparent">💬 CONTÁCTANOS</h2>
        <form id="support-form" class="glass-effect rounded-2xl p-6 md:p-8 border border-[#00ff88]/30 space-y-6">
          <div>
            <label for="support-name" class="block text-sm font-semibold text-[#00ff88] mb-2">Nombre *</label>
            <input type="text" id="support-name" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="Tu nombre">
          </div>
          <div>
            <label for="support-email" class="block text-sm font-semibold text-[#00ff88] mb-2">Email *</label>
            <input type="email" id="support-email" required class="input-gaming w-full px-4 py-3 rounded-lg text-white" placeholder="tu@email.com">
          </div>
          <div>
            <label for="support-message" class="block text-sm font-semibold text-[#00ff88] mb-2">Mensaje *</label>
            <textarea id="support-message" required rows="5" class="input-gaming w-full px-4 py-3 rounded-lg text-white resize-none" placeholder="¿En qué podemos ayudarte?"></textarea>
          </div>
          <p class="text-xs text-gray-500 text-center">📧 Nos pondremos en contacto contigo lo antes posible</p>
          <button type="submit" id="support-submit" class="w-full btn-gaming py-4 rounded-xl font-gaming font-bold text-[#0f0f1a] text-lg">ENVIAR MENSAJE</button>
        </form>
      </div>
    </section>

    <section id="success-section" class="py-12 hidden">
      <div class="max-w-lg mx-auto px-4 text-center">
        <div class="glass-effect rounded-2xl p-8 border border-[#00ff88]/30">
          <div class="text-8xl mb-6 float-animation">✅</div>
          <h2 class="font-gaming text-2xl font-bold text-[#00ff88] mb-4">¡PEDIDO CONFIRMADO!</h2>
          <p class="text-gray-300 mb-6">Gracias por tu compra. Hemos registrado tu pedido y te contactaremos pronto.</p>
          <button onclick="resetAndGoHome()" class="btn-gaming px-8 py-3 rounded-full font-gaming font-bold text-[#0f0f1a]">SEGUIR COMPRANDO</button>
        </div>
      </div>
    </section>

    <section class="py-16 bg-gradient-to-r from-[#00ff88]/5 via-transparent to-[#00ccff]/5">
      <div class="max-w-7xl mx-auto px-4">
        <h2 class="font-gaming text-4xl font-black text-center mb-12 bg-gradient-to-r from-[#00ff88] via-[#00ccff] to-[#00ff88] bg-clip-text text-transparent">✨ ¿POR QUÉ ELEGIR GAME_ZYRO? ✨</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div class="glass-effect rounded-2xl p-6 border border-[#00ff88]/30 hover:border-[#00ff88]/80 transition-all hover:shadow-lg hover:shadow-[#00ff88]/20">
            <div class="text-5xl mb-4">🚀</div>
            <h3 class="font-gaming text-xl font-bold text-[#00ff88] mb-3">Rendimiento Premium</h3>
            <p class="text-gray-300 leading-relaxed">Todos nuestros productos son seleccionados meticulosamente para garantizar el máximo rendimiento en tus sesiones gaming. Desde periféricos con respuesta ultra rápida hasta PCs gaming con especificaciones top.</p>
          </div>
          <div class="glass-effect rounded-2xl p-6 border border-[#00ccff]/30 hover:border-[#00ccff]/80 transition-all hover:shadow-lg hover:shadow-[#00ccff]/20">
            <div class="text-5xl mb-4">💰</div>
            <h3 class="font-gaming text-xl font-bold text-[#00ccff] mb-3">Precios Competitivos</h3>
            <p class="text-gray-300 leading-relaxed">Ofrecemos la mejor relación calidad-precio del mercado. Sin intermediarios, sin gastos innecesarios. Obtienes el máximo valor por cada euro invertido en tu setup gaming.</p>
          </div>
          <div class="glass-effect rounded-2xl p-6 border border-[#ff00ff]/30 hover:border-[#ff00ff]/80 transition-all hover:shadow-lg hover:shadow-[#ff00ff]/20">
            <div class="text-5xl mb-4">🎮</div>
            <h3 class="font-gaming text-xl font-bold text-[#ff00ff] mb-3">Expertos en Gaming</h3>
            <p class="text-gray-300 leading-relaxed">Nuestro equipo son gamers profesionales que entienden lo que necesitas. Cada producto ha sido probado en condiciones reales competitivas.</p>
          </div>
          <div class="glass-effect rounded-2xl p-6 border border-[#ff6600]/30 hover:border-[#ff6600]/80 transition-all hover:shadow-lg hover:shadow-[#ff6600]/20">
            <div class="text-5xl mb-4">📦</div>
            <h3 class="font-gaming text-xl font-bold text-[#ff6600] mb-3">Envíos Rápidos</h3>
            <p class="text-gray-300 leading-relaxed">Recibe tu pedido en el menor tiempo posible. Entrega express en 24-48 horas. Embalaje profesional que garantiza que tu equipo llega en perfecto estado.</p>
          </div>
          <div class="glass-effect rounded-2xl p-6 border border-[#00ff88]/30 hover:border-[#00ff88]/80 transition-all hover:shadow-lg hover:shadow-[#00ff88]/20">
            <div class="text-5xl mb-4">🛡️</div>
            <h3 class="font-gaming text-xl font-bold text-[#00ff88] mb-3">Garantía Total</h3>
            <p class="text-gray-300 leading-relaxed">Todos nuestros productos incluyen garantía del fabricante extendida. Soporte técnico dedicado disponible 24/7 para resolver cualquier duda o problema.</p>
          </div>
          <div class="glass-effect rounded-2xl p-6 border border-[#0099ff]/30 hover:border-[#0099ff]/80 transition-all hover:shadow-lg hover:shadow-[#0099ff]/20">
            <div class="text-5xl mb-4">🤝</div>
            <h3 class="font-gaming text-xl font-bold text-[#0099ff] mb-3">Comunidad ZYRO</h3>
            <p class="text-gray-300 leading-relaxed">Únete a miles de gamers que confían en GAME_ZYRO. Acceso a eventos exclusivos, torneos, descuentos especiales y comunidad de gamers apasionados como tú.</p>
          </div>
        </div>
      </div>
    </section>

    <section class="py-12 bg-gradient-to-r from-[#00ff88]/10 via-[#00ccff]/5 to-[#ff00ff]/10">
      <div class="max-w-4xl mx-auto px-4 text-center">
        <h2 class="font-gaming text-3xl md:text-4xl font-bold mb-6 text-white">🎯 ¿LISTO PARA MEJORAR TU SETUP?</h2>
        <p class="text-xl text-gray-300 mb-8">Explora nuestro catálogo completo de productos gaming premium y encuentra todo lo que necesitas para dominar tu juego.</p>
        <button onclick="showSection('products')" class="btn-gaming px-12 py-4 rounded-full font-gaming font-bold text-[#0f0f1a] text-lg hover:scale-110 transition-transform">🛍️ EXPLORAR PRODUCTOS AHORA</button>
      </div>
    </section>

    <footer class="glass-effect border-t border-[#00ff88]/30 py-8 mt-12">
      <div class="max-w-7xl mx-auto px-4 text-center">
        <p class="font-gaming text-[#00ff88] mb-2">GAME_ZYRO</p>
        <p class="text-gray-500 text-sm">© 2026 Todos los derechos reservados</p>
        <div class="flex justify-center gap-6 mt-4">
          <button onclick="showSection('products')" class="text-gray-400 hover:text-[#00ff88] transition-colors">Productos</button>
          <button onclick="showSection('support')" class="text-gray-400 hover:text-[#00ff88] transition-colors">Contacto</button>
        </div>
      </div>
    </footer>
  </div>

  <script>
    const defaultConfig = {
      store_name: 'GAME_ZYRO',
      hero_title: 'TU DESTINO GAMING DEFINITIVO',
      hero_subtitle: 'Los mejores productos para gamers exigentes',
      background_color: '#0f0f1a',
      surface_color: '#1a1a2e',
      text_color: '#ffffff',
      primary_action: '#00ff88',
      secondary_action: '#00ccff'
    };

    let config = { ...defaultConfig };

    const getKeyboardSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 200 140" class="w-32 h-24">
          <defs>
            <filter id="ledGlow${id}">
              <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="keyboardGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="10" y="20" width="180" height="100" rx="8" fill="url(#keyboardGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.9"/>
          <rect x="15" y="25" width="170" height="20" rx="4" fill="#1a1a2e" stroke="${color1}" stroke-width="1.5" opacity="0.6"/>
          <circle cx="30" cy="35" r="4" fill="${color1}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="60" cy="35" r="4" fill="${color2}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2.3s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2.3s" repeatCount="indefinite"/>
          </circle>
          <circle cx="90" cy="35" r="4" fill="${color3}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2.6s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2.6s" repeatCount="indefinite"/>
          </circle>
          <circle cx="120" cy="35" r="4" fill="${color1}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2s" repeatCount="indefinite" begin="0.5s"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <circle cx="150" cy="35" r="4" fill="${color2}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2.3s" repeatCount="indefinite" begin="1s"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2.3s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <circle cx="170" cy="35" r="4" fill="${color3}" filter="url(#ledGlow${id})">
            <animate attributeName="r" values="4;6;4" dur="2.6s" repeatCount="indefinite" begin="1.5s"/>
            <animate attributeName="opacity" values="0.4;1;0.4" dur="2.6s" repeatCount="indefinite" begin="1.5s"/>
          </circle>
          <g opacity="0.7">
            <rect x="20" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="40" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="60" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="80" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="100" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="120" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="140" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="160" y="55" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="20" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="40" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="60" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="80" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color3}" stroke-width="1" opacity="0.5"/>
            <rect x="100" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color3}" stroke-width="1" opacity="0.5"/>
            <rect x="120" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="140" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="160" y="75" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="20" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color3}" stroke-width="1" opacity="0.5"/>
            <rect x="40" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="60" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="80" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color3}" stroke-width="1" opacity="0.5"/>
            <rect x="100" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
            <rect x="120" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color2}" stroke-width="1" opacity="0.5"/>
            <rect x="140" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color3}" stroke-width="1" opacity="0.5"/>
            <rect x="160" y="95" width="12" height="12" rx="2" fill="#333" stroke="${color1}" stroke-width="1" opacity="0.5"/>
          </g>
          <text x="100" y="120" font-family="'Orbitron', sans-serif" font-size="10" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.8">ZYRO GAMING</text>
        </svg>
      `;
    };

    const getMobileSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 120 200" class="w-24 h-40">
          <defs>
            <filter id="phoneLedGlow${id}">
              <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="phoneGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="10" y="10" width="100" height="180" rx="12" fill="url(#phoneGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.95"/>
          <rect x="15" y="25" width="90" height="130" rx="8" fill="#0a0a15" stroke="${color2}" stroke-width="1.5" opacity="0.7"/>
          <circle cx="30" cy="18" r="2.5" fill="${color1}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="r" values="2.5;3.5;2.5" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="50" cy="18" r="2.5" fill="${color2}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="r" values="2.5;3.5;2.5" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="70" cy="18" r="2.5" fill="${color3}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="r" values="2.5;3.5;2.5" dur="2.2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="90" cy="18" r="2.5" fill="${color1}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="r" values="2.5;3.5;2.5" dur="1.8s" repeatCount="indefinite" begin="0.5s"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <rect x="17" y="27" width="86" height="126" rx="6" fill="none" stroke="${color1}" stroke-width="0.5" opacity="0.3"/>
          <circle cx="8" cy="80" r="2" fill="${color2}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="112" cy="80" r="2" fill="${color3}" filter="url(#phoneLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <rect x="6" y="85" width="3" height="15" rx="1.5" fill="${color1}" opacity="0.6"/>
          <rect x="50" y="194" width="20" height="2" rx="1" fill="${color1}" opacity="0.5"/>
          <text x="60" y="155" font-family="'Orbitron', sans-serif" font-size="8" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.7">ZYRO</text>
        </svg>
      `;
    };

    const getMouseSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 90 140" class="w-20 h-32">
          <defs>
            <filter id="mouseLedGlow${id}">
              <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="mouseGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <ellipse cx="45" cy="50" rx="35" ry="45" fill="url(#mouseGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.95"/>
          <circle cx="30" cy="25" r="3" fill="${color1}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="45" cy="18" r="3" fill="${color2}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="60" cy="25" r="3" fill="${color3}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="2.2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="12" cy="50" r="2.5" fill="${color2}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="12" cy="70" r="2.5" fill="${color3}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="0.8s"/>
          </circle>
          <circle cx="78" cy="50" r="2.5" fill="${color1}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="0.4s"/>
          </circle>
          <circle cx="78" cy="70" r="2.5" fill="${color2}" filter="url(#mouseLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="1.2s"/>
          </circle>
          <ellipse cx="35" cy="40" rx="8" ry="12" fill="none" stroke="${color1}" stroke-width="1.5" opacity="0.6"/>
          <ellipse cx="55" cy="40" rx="8" ry="12" fill="none" stroke="${color2}" stroke-width="1.5" opacity="0.6"/>
          <rect x="42" y="50" width="6" height="10" rx="1" fill="${color3}" opacity="0.7" stroke="${color1}" stroke-width="1"/>
          <line x1="45" y1="95" x2="45" y2="130" stroke="${color1}" stroke-width="4" opacity="0.7"/>
          <circle cx="45" cy="135" r="3" fill="${color1}" opacity="0.8"/>
          <text x="45" y="115" font-family="'Orbitron', sans-serif" font-size="6" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.6">ZYRO</text>
        </svg>
      `;
    };

    const getChairSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 100 140" class="w-24 h-32">
          <defs>
            <filter id="chairLedGlow${id}">
              <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="chairGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="20" y="10" width="60" height="50" rx="8" fill="url(#chairGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.95"/>
          <circle cx="35" cy="18" r="2.5" fill="${color1}" filter="url(#chairLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="50" cy="15" r="2.5" fill="${color2}" filter="url(#chairLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="65" cy="18" r="2.5" fill="${color3}" filter="url(#chairLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="2.2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <rect x="25" y="15" width="50" height="38" fill="none" stroke="${color2}" stroke-width="1.5" opacity="0.5" rx="6"/>
          <ellipse cx="50" cy="68" rx="35" ry="18" fill="url(#chairGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.95"/>
          <circle cx="18" cy="68" r="2" fill="${color2}" filter="url(#chairLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="82" cy="68" r="2" fill="${color3}" filter="url(#chairLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <rect x="45" y="82" width="10" height="20" rx="3" fill="${color1}" opacity="0.7" stroke="${color2}" stroke-width="1.5"/>
          <circle cx="30" cy="108" r="5" fill="url(#chairGrad${id})" stroke="${color1}" stroke-width="1.5" opacity="0.8"/>
          <circle cx="70" cy="108" r="5" fill="url(#chairGrad${id})" stroke="${color1}" stroke-width="1.5" opacity="0.8"/>
          <circle cx="50" cy="112" r="5" fill="url(#chairGrad${id})" stroke="${color3}" stroke-width="1.5" opacity="0.8"/>
          <circle cx="30" cy="108" r="1.5" fill="${color2}"/>
          <circle cx="70" cy="108" r="1.5" fill="${color3}"/>
          <circle cx="50" cy="112" r="1.5" fill="${color1}"/>
          <text x="50" y="50" font-family="'Orbitron', sans-serif" font-size="7" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.6">ZYRO</text>
        </svg>
      `;
    };

    const getPcSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 120 160" class="w-28 h-40">
          <defs>
            <filter id="pcLedGlow${id}">
              <feGaussianBlur stdDeviation="2.5" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="pcGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="15" y="10" width="90" height="120" rx="8" fill="url(#pcGrad${id})" stroke="${color1}" stroke-width="2.5" opacity="0.95"/>
          <rect x="20" y="15" width="80" height="40" rx="6" fill="#1a1a2e" stroke="${color2}" stroke-width="1.5" opacity="0.7"/>
          <circle cx="35" cy="25" r="3" fill="${color1}" filter="url(#pcLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="60" cy="22" r="3" fill="${color2}" filter="url(#pcLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="85" cy="25" r="3" fill="${color3}" filter="url(#pcLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="2.2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="60" cy="40" r="12" fill="none" stroke="${color1}" stroke-width="1.5" opacity="0.6"/>
          <circle cx="60" cy="40" r="8" fill="none" stroke="${color2}" stroke-width="1" opacity="0.4"/>
          <line x1="60" y1="32" x2="60" y2="48" stroke="${color3}" stroke-width="1" opacity="0.5"/>
          <line x1="52" y1="40" x2="68" y2="40" stroke="${color3}" stroke-width="1" opacity="0.5"/>
          <rect x="22" y="60" width="30" height="50" rx="3" fill="#0a0a15" stroke="${color2}" stroke-width="1.5" opacity="0.6"/>
          <rect x="58" y="60" width="30" height="50" rx="3" fill="#0a0a15" stroke="${color3}" stroke-width="1.5" opacity="0.6"/>
          <circle cx="12" cy="70" r="2.5" fill="${color2}" filter="url(#pcLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="108" cy="70" r="2.5" fill="${color1}" filter="url(#pcLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <circle cx="12" cy="100" r="2.5" fill="${color3}" filter="url(#pcLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <circle cx="108" cy="100" r="2.5" fill="${color2}" filter="url(#pcLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite" begin="1.5s"/>
          </circle>
          <rect x="28" y="115" width="4" height="8" rx="1" fill="${color1}" opacity="0.6"/>
          <rect x="38" y="115" width="4" height="8" rx="1" fill="${color2}" opacity="0.6"/>
          <rect x="48" y="115" width="4" height="8" rx="1" fill="${color3}" opacity="0.6"/>
          <line x1="30" y1="132" x2="30" y2="145" stroke="${color1}" stroke-width="3" opacity="0.7"/>
          <line x1="90" y1="132" x2="90" y2="145" stroke="${color1}" stroke-width="3" opacity="0.7"/>
          <rect x="25" y="143" width="70" height="3" rx="1.5" fill="${color2}" opacity="0.6"/>
          <text x="60" y="155" font-family="'Orbitron', sans-serif" font-size="7" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.6">ZYRO PC</text>
        </svg>
      `;
    };

    const getHeadsetSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 140 120" class="w-32 h-28">
          <defs>
            <filter id="headsetLedGlow${id}">
              <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="headsetGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#2a2a4e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <path d="M 30 30 Q 70 10 110 30" fill="none" stroke="${color1}" stroke-width="4" stroke-linecap="round" opacity="0.9"/>
          <circle cx="50" cy="22" r="2.5" fill="${color1}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="70" cy="12" r="2.5" fill="${color2}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="90" cy="22" r="2.5" fill="${color3}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="2.2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="30" cy="45" r="18" fill="url(#headsetGrad${id})" stroke="${color1}" stroke-width="2" opacity="0.95"/>
          <circle cx="30" cy="45" r="12" fill="#1a1a2e" stroke="${color2}" stroke-width="1.5" opacity="0.7"/>
          <circle cx="30" cy="45" r="3" fill="${color1}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="1.8s" repeatCount="indefinite" begin="0.3s"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="1.8s" repeatCount="indefinite" begin="0.3s"/>
          </circle>
          <circle cx="110" cy="45" r="18" fill="url(#headsetGrad${id})" stroke="${color1}" stroke-width="2" opacity="0.95"/>
          <circle cx="110" cy="45" r="12" fill="#1a1a2e" stroke="${color2}" stroke-width="1.5" opacity="0.7"/>
          <circle cx="110" cy="45" r="3" fill="${color2}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="r" values="3;5;3" dur="2s" repeatCount="indefinite" begin="0.5s"/>
            <animate attributeName="opacity" values="0.3;1;0.3" dur="2s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <path d="M 30 63 Q 20 75 15 85" fill="none" stroke="${color1}" stroke-width="2.5" stroke-linecap="round" opacity="0.8"/>
          <circle cx="15" cy="87" r="3" fill="${color3}" opacity="0.8" stroke="${color1}" stroke-width="1"/>
          <circle cx="15" cy="87" r="2" fill="${color3}" filter="url(#headsetLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <rect x="115" y="70" width="4" height="20" rx="2" fill="${color1}" opacity="0.6" stroke="${color2}" stroke-width="1"/>
          <rect x="117" y="75" width="6" height="2" fill="${color2}" opacity="0.8"/>
          <path d="M 70 63 Q 70 90 60 100" fill="none" stroke="${color1}" stroke-width="2.5" opacity="0.7"/>
          <circle cx="60" cy="102" r="2" fill="${color1}" opacity="0.8"/>
          <text x="70" y="110" font-family="'Orbitron', sans-serif" font-size="6" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.6">ZYRO AUDIO</text>
        </svg>
      `;
    };

    const getMousepadSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 160 100" class="w-40 h-24">
          <defs>
            <filter id="mousepadLedGlow${id}">
              <feGaussianBlur stdDeviation="1.5" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="mousepadGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#1a1a2e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="10" y="15" width="140" height="70" rx="8" fill="url(#mousepadGrad${id})" stroke="${color1}" stroke-width="2" opacity="0.95"/>
          <rect x="15" y="20" width="130" height="60" rx="6" fill="#0a0a15" stroke="${color2}" stroke-width="1" opacity="0.5"/>
          <circle cx="30" cy="12" r="2" fill="${color1}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="r" values="2;3.5;2" dur="1.6s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite"/>
          </circle>
          <circle cx="60" cy="10" r="2" fill="${color2}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="r" values="2;3.5;2" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="90" cy="10" r="2" fill="${color3}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="r" values="2;3.5;2" dur="2s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="120" cy="12" r="2" fill="${color1}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="r" values="2;3.5;2" dur="1.6s" repeatCount="indefinite" begin="0.4s"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite" begin="0.4s"/>
          </circle>
          <circle cx="30" cy="88" r="2" fill="${color2}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="80" cy="91" r="2" fill="${color3}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.2s" repeatCount="indefinite" begin="0.7s"/>
          </circle>
          <circle cx="130" cy="88" r="2" fill="${color1}" filter="url(#mousepadLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2.2s" repeatCount="indefinite" begin="1.4s"/>
          </circle>
          <line x1="25" y1="30" x2="135" y2="30" stroke="${color1}" stroke-width="0.5" opacity="0.2"/>
          <line x1="25" y1="40" x2="135" y2="40" stroke="${color2}" stroke-width="0.5" opacity="0.2"/>
          <line x1="25" y1="50" x2="135" y2="50" stroke="${color3}" stroke-width="0.5" opacity="0.2"/>
          <line x1="25" y1="60" x2="135" y2="60" stroke="${color1}" stroke-width="0.5" opacity="0.2"/>
          <line x1="25" y1="70" x2="135" y2="70" stroke="${color2}" stroke-width="0.5" opacity="0.2"/>
          <line x1="20" y1="85" x2="20" y2="98" stroke="${color1}" stroke-width="2" opacity="0.6"/>
          <circle cx="20" cy="100" r="1.5" fill="${color1}" opacity="0.8"/>
          <text x="80" y="50" font-family="'Orbitron', sans-serif" font-size="8" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.4">ZYRO PAD</text>
        </svg>
      `;
    };

    const getCableSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 100 140" class="w-20 h-32">
          <defs>
            <filter id="cableLedGlow${id}">
              <feGaussianBlur stdDeviation="1.5" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
          </defs>
          <path d="M 30 10 Q 40 30 35 50 Q 30 70 40 90 Q 35 110 50 130" fill="none" stroke="${color1}" stroke-width="5" stroke-linecap="round" opacity="0.85"/>
          <path d="M 50 15 Q 55 35 50 55 Q 48 75 55 95 Q 50 115 65 135" fill="none" stroke="${color2}" stroke-width="5" stroke-linecap="round" opacity="0.85"/>
          <path d="M 70 12 Q 75 32 70 52 Q 68 72 75 92 Q 70 112 80 132" fill="none" stroke="${color3}" stroke-width="5" stroke-linecap="round" opacity="0.85"/>
          <circle cx="35" cy="25" r="1.5" fill="${color1}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.4s" repeatCount="indefinite"/>
          </circle>
          <circle cx="32" cy="50" r="1.5" fill="${color1}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.4s" repeatCount="indefinite" begin="0.3s"/>
          </circle>
          <circle cx="37" cy="75" r="1.5" fill="${color1}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.4s" repeatCount="indefinite" begin="0.6s"/>
          </circle>
          <circle cx="50" cy="35" r="1.5" fill="${color2}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite"/>
          </circle>
          <circle cx="49" cy="60" r="1.5" fill="${color2}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite" begin="0.4s"/>
          </circle>
          <circle cx="53" cy="85" r="1.5" fill="${color2}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite" begin="0.8s"/>
          </circle>
          <circle cx="70" cy="30" r="1.5" fill="${color3}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="68" cy="55" r="1.5" fill="${color3}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.8s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <circle cx="73" cy="80" r="1.5" fill="${color3}" filter="url(#cableLedGlow${id})">
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.8s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <circle cx="30" cy="8" r="2.5" fill="${color1}" stroke="${color1}" stroke-width="1.5" opacity="0.9"/>
          <circle cx="50" cy="128" r="2.5" fill="${color1}" stroke="${color1}" stroke-width="1.5" opacity="0.9"/>
          <circle cx="65" cy="133" r="2.5" fill="${color3}" stroke="${color3}" stroke-width="1.5" opacity="0.9"/>
        </svg>
      `;
    };

    const getCoolingPadSVG = (color1, color2, color3) => {
      const id = Math.random().toString(36).substr(2, 9);
      return `
        <svg viewBox="0 0 140 100" class="w-32 h-24">
          <defs>
            <filter id="coolingLedGlow${id}">
              <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
              <feMerge>
                <feMergeNode in="coloredBlur"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <linearGradient id="coolingGrad${id}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" style="stop-color:#1a1a2e;stop-opacity:1" />
              <stop offset="100%" style="stop-color:#0f0f1a;stop-opacity:1" />
            </linearGradient>
          </defs>
          <rect x="10" y="15" width="120" height="70" rx="8" fill="url(#coolingGrad${id})" stroke="${color1}" stroke-width="2" opacity="0.95"/>
          <circle cx="35" cy="50" r="20" fill="none" stroke="${color1}" stroke-width="1.5" opacity="0.6"/>
          <circle cx="35" cy="50" r="16" fill="none" stroke="${color2}" stroke-width="1" opacity="0.4"/>
          <path d="M 35 34 L 40 50 L 35 66 M 35 34 L 30 50 L 35 66" stroke="${color1}" stroke-width="1" opacity="0.5"/>
          <circle cx="105" cy="50" r="20" fill="none" stroke="${color1}" stroke-width="1.5" opacity="0.6"/>
          <circle cx="105" cy="50" r="16" fill="none" stroke="${color3}" stroke-width="1" opacity="0.4"/>
          <path d="M 105 34 L 110 50 L 105 66 M 105 34 L 100 50 L 105 66" stroke="${color1}" stroke-width="1" opacity="0.5"/>
          <circle cx="35" cy="50" r="2.5" fill="${color2}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="1.6s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.6s" repeatCount="indefinite"/>
          </circle>
          <circle cx="105" cy="50" r="2.5" fill="${color3}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="r" values="2.5;4;2.5" dur="1.8s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="0.2;1;0.2" dur="1.8s" repeatCount="indefinite"/>
          </circle>
          <circle cx="15" cy="30" r="1.5" fill="${color1}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2s" repeatCount="indefinite"/>
          </circle>
          <circle cx="125" cy="30" r="1.5" fill="${color2}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2s" repeatCount="indefinite" begin="0.5s"/>
          </circle>
          <circle cx="15" cy="70" r="1.5" fill="${color3}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2s" repeatCount="indefinite" begin="1s"/>
          </circle>
          <circle cx="125" cy="70" r="1.5" fill="${color1}" filter="url(#coolingLedGlow${id})">
            <animate attributeName="opacity" values="0;1;0" dur="2s" repeatCount="indefinite" begin="1.5s"/>
          </circle>
          <rect x="70" y="35" width="30" height="4" rx="2" fill="#0a0a15" stroke="${color1}" stroke-width="1" opacity="0.7"/>
          <rect x="72" y="36" width="8" height="2" rx="1" fill="${color2}" opacity="0.8"/>
          <rect x="68" y="78" width="4" height="6" rx="1" fill="${color1}" opacity="0.6" stroke="${color2}" stroke-width="0.5"/>
          <text x="70" y="90" font-family="'Orbitron', sans-serif" font-size="6" font-weight="bold" text-anchor="middle" fill="${color1}" opacity="0.5">ZYRO COOL</text>
        </svg>
      `;
    };

    const products = [
      { id: 1, name: 'ZYRO Nexus Pro', category: 'teclados', svg: getKeyboardSVG('#00ff88', '#00ccff', '#00ff88'), price: 249.99, desc: 'RGB Focus 8000Hz, switches ópticos', fullDesc: 'Compuesto por switches ópticos lineales de última generación con activación de 1.5mm. Incluye iluminación RGB personalizable en cada tecla, estructura de aluminio reforzado y reposamuñecas ergonómico magnético desmontable. Muy cómodo para sesiones largas de gaming gracias a su diseño ergonómico y teclas silenciosas.' },
      { id: 2, name: 'ZYRO Inferno RGB', category: 'teclados', svg: getKeyboardSVG('#ff0066', '#ff6600', '#ff0066'), price: 229.99, desc: 'iCUE Backlighting, 8 zonas RGB', fullDesc: 'Teclado mecánico con 8 zonas de iluminación RGB independientes sincronizables. Cuenta con switches tácticos de respuesta rápida y estructura de ABS reforzado. Reposamuñecas integrado y software iCUE para personalizaciones avanzadas. Muy cómodo con sus teclas de baja altura y respuesta inmediata.' },
      { id: 3, name: 'ZYRO Plasma Elite', category: 'teclados', svg: getKeyboardSVG('#00ccff', '#0099ff', '#00ccff'), price: 199.99, desc: 'Per-Key RGB, 60 millones de colores', fullDesc: 'Teclado gaming con iluminación RGB por tecla permitiendo 60 millones de combinaciones de colores. Switches mecánicos hot-swap para cambiar rápidamente. Estructura de aluminio ligera, cable trenzado y software de programación personalizable. Excelente comodidad gracias a su layout compacto sin perder funcionalidad.' },
      { id: 4, name: 'ZYRO Vortex Mini', category: 'teclados', svg: getKeyboardSVG('#ff00ff', '#ff0099', '#ff00ff'), price: 179.99, desc: 'RGB Spectrum, sincronización inalámbrica', fullDesc: 'Teclado 60% compacto con RGB Spectrum en movimiento y conectividad inalámbrica 2.4GHz estable. Switches silenciosos de película/membrana de alta calidad. Batería de larga duración (30 días), reposamuñecas integrado. Muy cómodo para portabilidad manteniendo la velocidad de respuesta de un gaming teclado.' },
      { id: 5, name: 'ZYRO Nova Compact', category: 'teclados', svg: getKeyboardSVG('#00ff88', '#ff00ff', '#00ccff'), price: 159.99, desc: '60% Layout RGB, mecánico', fullDesc: 'Teclado mecánico 60% con RGB programable. Switches rojos lineales ultra rápidos (2mm de activación) y carcasa de plástico reforzado de calidad superior. Incluye estabilizadores estabilizados de fábrica y teclas ABS dobladas. Muy cómodo para jugadores competitivos que buscan compacto y respuesta rápida.' },
      { id: 6, name: 'ZYRO Storm Wireless', category: 'teclados', svg: getKeyboardSVG('#ff6600', '#ffaa00', '#ff0066'), price: 199.99, desc: 'Inalámbrico 2.4GHz, 40 horas batería', fullDesc: 'Teclado inalámbrico 2.4GHz con batería de 40 horas de autonomía. Switches mecánicos azules con retroalimentación táctil clara. Estructura de goma antideslizante en la base, teclas con acabado mate premium. Muy cómodo para jugar sin cables con conectividad ultra rápida sin latencia.' },

      { id: 7, name: 'ZYRO Swift Pro', category: 'ratones', svg: getMouseSVG('#00ff88', '#00ccff', '#00ff88'), price: 149.99, desc: 'LED Focus 16K, 63g ultraligero', fullDesc: 'Ratón gaming ultraligero de 63g con sensor Focus de 16,000 DPI. Botones laterales programables de titanio reforzado y revestimiento especial antideslizante texturizado. Iluminación LED RGB animada y cable paracord tejido. Muy cómodo en la mano gracias a su peso ultra reducido perfecto para FPS competitivos.' },
      { id: 8, name: 'ZYRO Viper X', category: 'ratones', svg: getMouseSVG('#ff0066', '#ff6600', '#ff0066'), price: 169.99, desc: 'Chroma RGB, 16.8M colores', fullDesc: 'Ratón con iluminación Chroma RGB capaz de mostrar 16.8 millones de colores diferentes. Sensor óptico 20,000 DPI, 8 botones programables con macros personalizables. Grip ergonómico con zonas texturizadas especiales. Muy cómodo con respuesta instantánea ideal para MOBAs y MMORPGs.' },
      { id: 9, name: 'ZYRO Phantom Lite', category: 'ratones', svg: getMouseSVG('#00ccff', '#0099ff', '#00ccff'), price: 189.99, desc: 'RGB Gaming, 65g ultraligero', fullDesc: 'Ratón gaming minimalista de 65g con RGB personalizable en el logo y rueda de scroll. Sensor avanzado de 18,000 DPI con aceleración inteligente. Botones laterales precisos con microswitches Omron. Muy cómodo en la palma con su diseño ergonómico amigable para uso extenso.' },
      { id: 10, name: 'ZYRO Storm', category: 'ratones', svg: getMouseSVG('#ff00ff', '#ff0099', '#ff00ff'), price: 129.99, desc: 'LED azul gaming, precision 3389', fullDesc: 'Ratón gaming clásico con sensor de precisión 3389 y LED azul animado. 6 botones programables con respuesta inmediata y cable reforzado de PVC. Peso optimizado (95g) y grip de goma antideslizante. Muy cómodo y versátil para todos los tipos de juegos con rendimiento estable.' },
      { id: 11, name: 'ZYRO Apex Wireless', category: 'ratones', svg: getMouseSVG('#00ff88', '#ff00ff', '#00ccff'), price: 139.99, desc: 'Gaming inalámbrico, 100 horas batería', fullDesc: 'Ratón inalámbrico 2.4GHz con batería de 100 horas de autonomía real. Sensor de 16,000 DPI con conexión ultra rápida sin lag. 7 botones programables con retroalimentación háptica suave. Muy cómodo gracias a su carcasa de goma suave y peso balanceado para gaming sin cables.' },
      { id: 12, name: 'ZYRO Falcon Pro', category: 'ratones', svg: getMouseSVG('#ff6600', '#ffaa00', '#ff0066'), price: 159.99, desc: '26K DPI, 8 botones programables', fullDesc: 'Ratón profesional gaming con sensor PMW3389 de 26,000 DPI máximo. 8 botones programables incluyendo botón de ajuste DPI rápido. Estructura de aluminio ligero (88g) con cable paracord tejido resistente. Muy cómodo con su ergonomía ambidiestra y respuesta precisa para esports competitivos.' },

      { id: 13, name: 'ZYRO Throne Pro', category: 'sillas', svg: getChairSVG('#00ff88', '#00ccff', '#00ff88'), price: 549.99, desc: 'Ergonómica con soporte lumbar', fullDesc: 'Silla gaming ergonómica compuesta de espuma de memoria de alta densidad, soporte lumbar ajustable en 4 direcciones y reposacabezas de cuello acolchado. Base de aluminio con ruedas de 75mm silenciosas. Recubrimiento de tela transpirable y asiento reclinable hasta 165 grados. Muy cómoda para sesiones largas de gaming sin fatiga lumbar.' },
      { id: 14, name: 'ZYRO Supreme Max', category: 'sillas', svg: getChairSVG('#ff00ff', '#ff0066', '#ff00ff'), price: 1395.00, desc: 'Premium con ajustes personalizados', fullDesc: 'Silla gaming premium de lujo compuesta por respaldo de cuero genuino, soporte lumbar 3D ajustable, reposacabezas de espuma viscoelástica. Brazos 4D completamente móviles y mecanismo de reclinación con bloqueo infinito. Base de 5 puntos con ruedas de titanio. Muy cómoda con múltiples ajustes para cada tipo de usuario garantizando máximo confort.' },
      { id: 15, name: 'ZYRO Commander', category: 'sillas', svg: getChairSVG('#ff6600', '#ffaa00', '#ff0066'), price: 449.99, desc: 'Diseño elegante y cómodo', fullDesc: 'Silla gaming con diseño moderno compuesta de tela deportiva de calidad, espuma ergonómica en el asiento y respaldo acolchado. Brazos ajustables en altura, mecanismo de balancín y base con ruedas resistentes. Altura regulable mediante pistón neumático de calidad industrial. Muy cómoda con un balance perfecto entre diseño y funcionalidad.' },
      { id: 16, name: 'ZYRO Champion', category: 'sillas', svg: getChairSVG('#0099ff', '#00ff88', '#00ccff'), price: 329.99, desc: 'Clásica y resistente', fullDesc: 'Silla gaming clásica compuesta de estructura reforzada de acero de 5mm, asiento acolchado en material resistente de poliéster. Base estable de 5 ruedas y altura regulable. Diseño compacto ideal para espacios reducidos. Soporte máximo de peso de 120kg. Muy cómoda y duradera para gaming casual y trabajo diario.' },
      { id: 17, name: 'ZYRO Vortex Elite', category: 'sillas', svg: getChairSVG('#ff0099', '#00ffff', '#00ff88'), price: 799.99, desc: 'Full reclinable, reposabrazos 3D', fullDesc: 'Silla gaming reclinable compuesta de respaldo totalmente reclinable hasta 180 grados, reposabrazos 3D móviles en todas direcciones. Asiento tipo cápsula ergonómica con espuma viscoelástica y soporte lumbar integral. Ruedas de nylon de calidad premium. Muy cómoda tanto para gaming intensivo como para relajación completa.' },
      { id: 18, name: 'ZYRO Legend', category: 'sillas', svg: getChairSVG('#ffaa00', '#ff6600', '#00ccff'), price: 649.99, desc: 'Respaldo alto, ruedas premium', fullDesc: 'Silla gaming profesional compuesta de respaldo alto acolchado de 80cm, ruedas de titanio de 80mm premium silenciosas. Brazos ajustables en 4 direcciones y soporte lumbar regulable. Estructura de acero reforzado de 2.5mm. Altura regulable y mecanismo de reclinación suave. Muy cómoda para largas jornadas de gaming profesional.' },

      { id: 19, name: 'ZYRO Pulse 8 Pro', category: 'moviles', svg: getMobileSVG('#00ff88', '#00ccff', '#00ff88'), price: 1199.99, desc: 'Snapdragon 8 Gen 3, 24GB RAM', fullDesc: 'Móvil gaming compuesto de procesador Snapdragon 8 Gen 3 y 24GB de RAM LPDDR5X. Pantalla AMOLED de 6.7" a 120Hz, sistema de refrigeración por cámara de vapor dual. Batería de 5400mAh con carga rápida de 120W. GPU Adreno premium. Muy cómodo de sostener con bordes curvados y peso optimizado de 188g ideal para gaming móvil.' },
      { id: 20, name: 'ZYRO Gaming Beast', category: 'moviles', svg: getMobileSVG('#ff0066', '#ff6600', '#ff0066'), price: 799.99, desc: 'Refrigeración activa gaming', fullDesc: 'Móvil gaming especializado compuesto de sistema de refrigeración activa por ventilador, procesador potente MediaTek Dimensity 9200. Pantalla LCD de 6.5" a 165Hz respuesta ultra rápida. Batería de 6000mAh y carga 80W. Diseño robusto con metal y vidrio templado Gorilla Glass 5. Muy cómodo con grips laterales especiales para gaming intensivo sin sobrecalentamiento.' },
      { id: 21, name: 'ZYRO Ultra Max', category: 'moviles', svg: getMobileSVG('#00ccff', '#0099ff', '#00ccff'), price: 1469.99, desc: 'A17 Pro, gaming AAA', fullDesc: 'Móvil premium compuesto de chip Apple A17 Pro de arquitectura de 6 núcleos ultra potente. Pantalla Super Retina XDR de 6.7" con ProMotion de 120Hz. GPU 6-núcleos para gráficos AAA sin compromisos. Batería de larga duración con carga MagSafe. Sistema de cámaras triple avanzado. Muy cómodo de sostener y jugar con marcos de acero inoxidable y trasera de vidrio mate.' },
      { id: 22, name: 'ZYRO Velocity', category: 'moviles', svg: getMobileSVG('#ff00ff', '#ff0099', '#ff00ff'), price: 1359.99, desc: 'Snapdragon 8 Gen 3', fullDesc: 'Móvil flagship compuesto de Snapdragon 8 Gen 3 con GPU Adreno 8 core última generación. 12GB LPDDR5X y almacenamiento UFS 4.0 ultrarrápido. Pantalla AMOLED de 6.8" a 144Hz para gaming suavísimo. Batería de 5000mAh y carga 65W. Diseño premium aluminio y vidrio. Muy cómodo con peso equilibrado y bordes delgados para sesiones de gaming extendidas.' },
      { id: 23, name: 'ZYRO Core Gaming', category: 'moviles', svg: getMobileSVG('#00ff88', '#ff00ff', '#00ccff'), price: 649.99, desc: 'Mediatek Helio G99, 120Hz', fullDesc: 'Móvil gaming económico compuesto de MediaTek Helio G99, 8GB RAM y 128GB almacenamiento expansible. Pantalla IPS LCD de 6.5" a 120Hz suave y responsive. Batería 5000mAh y carga 18W. Diseño plástico resistente y ligero de 180g. Sistema de refrigeración pasiva efectiva. Muy cómodo como entrada al gaming móvil sin sacrificar rendimiento.' },
      { id: 24, name: 'ZYRO Edge Pro', category: 'moviles', svg: getMobileSVG('#ff6600', '#ffaa00', '#ff0066'), price: 959.99, desc: 'Snapdragon 8 Gen 2, pantalla AMOLED', fullDesc: 'Móvil gaming compuesto de Snapdragon 8 Gen 2 con 8GB LPDDR5 y almacenamiento UFS 3.1. Pantalla AMOLED de 6.6" a 120Hz con colores vívidos. Sistema de cámaras dual profesional de 48MP+12MP. Batería 4500mAh y carga 45W. Diseño curvo ergonómico de titanio. Muy cómodo de sostener con marcos lisos y trasera mate anti-huellas.' },

      { id: 25, name: 'ZYRO Ultimate Rig', category: 'pc', svg: getPcSVG('#00ff88', '#00ccff', '#00ff88'), price: 3499.99, desc: 'i9-14900K, RTX 4090, 64GB DDR5', fullDesc: 'PC gaming ultrapoderoso compuesto de procesador Intel Core i9-14900K (24 núcleos), GPU RTX 4090 de 24GB GDDR6X. 64GB RAM DDR5 de 7200MHz, SSD NVMe de 2TB gen4. Sistema de refrigeración líquida 360mm RGB y fuente modular de 1200W Gold. Muy cómodo de usar con todas las especificaciones máximas para juegos 4K ultra sin limitaciones.' },
      { id: 26, name: 'ZYRO Beast Machine', category: 'pc', svg: getPcSVG('#ff00ff', '#ff0066', '#00ccff'), price: 2499.99, desc: 'i7-14700K, RTX 4080, 32GB DDR5', fullDesc: 'PC gaming premium compuesto de Intel Core i7-14700K (20 núcleos) y GPU RTX 4080 de 16GB. 32GB RAM DDR5 de 6400MHz, SSD NVMe de 1TB gen4. Refrigeración líquida 280mm RGB y fuente 850W Gold modular. Torre gaming con RGB integrado de 4 ventiladores. Muy cómodo para gaming 1440p máximo y streaming simultáneo sin problemas.' },
      { id: 27, name: 'ZYRO Pro Config', category: 'pc', svg: getPcSVG('#ff6600', '#ffaa00', '#ff0066'), price: 1799.99, desc: 'Ryzen 9 7950X, RTX 4070 Ti, 32GB', fullDesc: 'PC gaming profesional compuesto de AMD Ryzen 9 7950X (16 núcleos) y GPU RTX 4070 Ti de 12GB. 32GB RAM DDR5 de 6000MHz y SSD NVMe de 1TB gen4. Refrigeración aire AIO 240mm y fuente 800W Gold. Diseño compacto Mid-Tower. Muy cómodo para gaming 1440p ultra y trabajos de contenido creativo simultáneamente.' },
      { id: 28, name: 'ZYRO Gaming Starter', category: 'pc', svg: getPcSVG('#0099ff', '#00ff88', '#00ccff'), price: 1199.99, desc: 'Ryzen 7 7800X3D, RTX 4060, 16GB', fullDesc: 'PC gaming de entrada-media compuesto de AMD Ryzen 7 7800X3D (8 núcleos, caché 3D) y GPU RTX 4060 de 8GB. 16GB RAM DDR5 de 5600MHz y SSD NVMe de 512GB. Refrigeración aire torre y fuente 600W Bronze. Muy cómodo para gaming 1080p máximo con muy buena relación calidad-precio y consumo eficiente.' },
      { id: 29, name: 'ZYRO Compact Gaming', category: 'pc', svg: getPcSVG('#ff0099', '#00ffff', '#00ff88'), price: 899.99, desc: 'Ryzen 5 7600X, RTX 3060, 16GB', fullDesc: 'PC gaming compacto compuesto de AMD Ryzen 5 7600X (6 núcleos) y GPU RTX 3060 de 12GB. 16GB RAM DDR4 y SSD NVMe de 480GB. Refrigeración aire compacta y fuente 550W. Caja Mini-ITX tipo cubo. Muy cómodo para gaming casual 1080p y fácilmente transportable a LAN parties.' },
      { id: 30, name: 'ZYRO Esports Edition', category: 'pc', svg: getPcSVG('#ffaa00', '#ff6600', '#00ccff'), price: 2199.99, desc: 'i9-13900K, RTX 4070 Super, 32GB', fullDesc: 'PC esports profesional compuesto de Intel Core i9-13900K (24 núcleos) y GPU RTX 4070 Super de 12GB. 32GB RAM DDR5 de 5600MHz y SSD NVMe de 1TB. Refrigeración líquida 360mm RGB y fuente 850W Gold modular. RGB personalizable en todos los componentes. Muy cómodo para competiciones profesionales con máximo rendimiento en juegos esports.' },

      { id: 31, name: 'ZYRO Sonic Headset', category: 'accesorios', svg: getHeadsetSVG('#00ff88', '#00ccff', '#ff0066'), price: 179.99, desc: 'Sonido 7.1, micrófono cancelación ruido', fullDesc: 'Headset gaming compuesto de drivers de 50mm con sonido envolvente 7.1 virtual, micrófono con cancelación de ruido AI inteligente. Almohadillas de espuma viscoelástica acolchadas cómodamente. Control de volumen en la copa y silenciado rápido. Cable paracord tejido reforzado. Muy cómodo para largas sesiones con aislamiento de ruido completo.' },
      { id: 32, name: 'ZYRO Pro Mousepad', category: 'accesorios', svg: getMousepadSVG('#ff6600', '#00ff88', '#00ccff'), price: 49.99, desc: 'XL RGB, velocidad controlada', fullDesc: 'Mousepad gaming XL compuesto de goma base antideslizante de 4mm grosor y superficie de tela de microfibra. Iluminación RGB en los bordes sincronizable. Tamaño 900x400x4mm perfecta para teclado y ratón. Orillas cosidas reforzadas para durabilidad. Muy cómodo para movimientos amplios con deslizamiento controlado y rápido.' },
      { id: 33, name: 'ZYRO Cable Management', category: 'accesorios', svg: getCableSVG('#00ff88', '#ff0066', '#00ccff'), price: 29.99, desc: 'Organizador RGB con LED', fullDesc: 'Organizador de cables compuesto de tubo helicoidal flexible revestido de silicona suave. Iluminación RGB integrada con múltiples modos de animación. Capacidad de organización de hasta 6 cables simultáneamente. Adhesivos reutilizables en la base. Muy cómodo para mantener el escritorio limpio y gaming setup profesional.' },
      { id: 34, name: 'ZYRO Stand Monitor', category: 'accesorios', svg: getPcSVG('#0099ff', '#ff00ff', '#ffaa00'), price: 99.99, desc: 'Ajustable, almacenamiento integrado', fullDesc: 'Soporte de monitor gaming compuesto de estructura de acero reforzado, altura y ángulo ajustables. Compartimiento de almacenamiento integrado debajo para periféricos. Soporta hasta 30kg de peso monitor. Base antideslizante con patas de goma. Compatible con monitores de 17" a 32". Muy cómodo para ergonomía optimizada durante horas de gaming.' },
      { id: 35, name: 'ZYRO RGB Hub', category: 'accesorios', svg: getHeadsetSVG('#ff00ff', '#00ffff', '#00ff88'), price: 69.99, desc: 'Control centralizado de luces', fullDesc: 'Hub de control RGB compuesto de software sincronización universal con 30+ marcas gaming. Conexión USB 3.0 y compatible con hasta 20 dispositivos LED simultáneamente. Control remoto inalámbrico o app móvil dedicada. Programación de efectos personalizados avanzada. Muy cómodo para gestionar toda la iluminación del setup gaming desde un único punto de control.' },
      { id: 36, name: 'ZYRO Cooling Pad', category: 'accesorios', svg: getCoolingPadSVG('#00ff88', '#ff0099', '#00ccff'), price: 79.99, desc: 'Refrigeración activa para laptop gaming', fullDesc: 'Almohadilla de refrigeración compuesta de 2 ventiladores de 120mm silenciosos con control de velocidad independiente. Soporte de ángulo ajustable para laptop de 10" a 17" y peso máximo 3kg. Panel USB de control en tiempo real y puertos USB 2.0 adicionales. Muy cómodo para mantener la temperatura óptima en laptop gaming durante sesiones largas.' }
    ];

    let cart = [];
    let currentCategory = 'all';
    let recordCount = 0;

    function showToast(message, type = 'success') {
      const container = document.getElementById('toast-container');
      const toast = document.createElement('div');
      toast.className = `toast px-6 py-3 rounded-lg font-semibold shadow-lg ${
        type === 'success' ? 'bg-gradient-to-r from-[#00ff88] to-[#00ccff] text-[#0f0f1a]' :
        type === 'error' ? 'bg-gradient-to-r from-[#ff0066] to-[#ff6600] text-white' :
        'bg-[#1a1a2e] text-white border border-[#00ff88]/50'
      }`;
      toast.textContent = message;
      container.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    function showSection(section) {
      const sections = ['products', 'cart', 'checkout', 'support', 'success'];
      sections.forEach(s => {
        const el = document.getElementById(`${s}-section`);
        if (el) el.classList.add('hidden');
      });

      const heroSection = document.getElementById('hero-section');
      if (section === 'products') {
        heroSection.classList.remove('hidden');
      } else {
        heroSection.classList.add('hidden');
      }

      const targetSection = document.getElementById(`${section}-section`);
      if (targetSection) {
        targetSection.classList.remove('hidden');
      }

      if (section === 'cart') {
        renderCart();
      }

      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function filterByCategory(category) {
      currentCategory = category;

      document.querySelectorAll('.category-btn').forEach(btn => {
        btn.classList.remove('active');
        btn.classList.add('text-gray-300');
      });

      const activeBtn = document.querySelector(`[data-category="${category}"]`);
      if (activeBtn) {
        activeBtn.classList.add('active');
        activeBtn.classList.remove('text-gray-300');
      }

      renderProducts();
    }

    function renderProducts() {
      const grid = document.getElementById('products-grid');
      const filteredProducts = currentCategory === 'all'
        ? products
        : products.filter(p => p.category === currentCategory);

      grid.innerHTML = filteredProducts.map(product => `
        <div class="product-card rounded-2xl overflow-hidden border border-[#00ff88]/20">
          <div class="h-40 flex items-center justify-center bg-gradient-to-br from-[#00ff88]/10 to-[#00ccff]/10">
            ${product.svg ? product.svg : `<span class="text-7xl">${product.emoji}</span>`}
          </div>
          <div class="p-5">
            <h3 class="font-gaming text-lg font-bold text-white mb-2 line-clamp-1">${product.name}</h3>
            <p class="text-gray-300 text-xs leading-relaxed mb-3 line-clamp-3">${product.fullDesc}</p>
            <div class="flex items-center justify-between">
              <span class="font-gaming text-2xl font-bold text-[#00ff88]">€${product.price.toFixed(2)}</span>
              <button onclick="addToCart(${product.id})" class="btn-gaming px-4 py-2 rounded-lg font-bold text-[#0f0f1a] text-sm">
                + Añadir
              </button>
            </div>
          </div>
        </div>
      `).join('');
    }

    function addToCart(productId) {
      const product = products.find(p => p.id === productId);
      if (!product) return;

      const existingItem = cart.find(item => item.id === productId);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        cart.push({ ...product, quantity: 1 });
      }

      updateCartBadge();
      showToast(`${product.name} añadido al carrito 🛒`);
    }

    function removeFromCart(productId) {
      cart = cart.filter(item => item.id !== productId);
      updateCartBadge();
      renderCart();
      showToast('Producto eliminado del carrito');
    }

    function updateQuantity(productId, delta) {
      const item = cart.find(i => i.id === productId);
      if (item) {
        item.quantity += delta;
        if (item.quantity <= 0) {
          removeFromCart(productId);
        } else {
          renderCart();
        }
      }
      updateCartBadge();
    }

    function updateCartBadge() {
      const badge = document.getElementById('cart-count');
      const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);

      if (totalItems > 0) {
        badge.textContent = totalItems;
        badge.classList.remove('hidden');
      } else {
        badge.classList.add('hidden');
      }
    }

    function getCartTotal() {
      return cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    }

    function renderCart() {
      const cartItems = document.getElementById('cart-items');
      const cartEmpty = document.getElementById('cart-empty');
      const cartSummary = document.getElementById('cart-summary');
      const cartTotal = document.getElementById('cart-total');

      if (cart.length === 0) {
        cartItems.classList.add('hidden');
        cartSummary.classList.add('hidden');
        cartEmpty.classList.remove('hidden');
        return;
      }

      cartItems.classList.remove('hidden');
      cartSummary.classList.remove('hidden');
      cartEmpty.classList.add('hidden');

      cartItems.innerHTML = cart.map(item => `
        <div class="glass-effect rounded-xl p-4 border border-[#00ff88]/20 flex items-center gap-4">
          <div class="w-16 h-16 flex items-center justify-center bg-[#00ff88]/10 rounded-lg">
            ${item.svg ? item.svg : `<span class="text-3xl">${item.emoji}</span>`}
          </div>
          <div class="flex-1 min-w-0">
            <h4 class="font-gaming font-bold text-white truncate">${item.name}</h4>
            <p class="text-[#00ff88] font-bold">€${item.price.toFixed(2)}</p>
          </div>
          <div class="flex items-center gap-2">
            <button onclick="updateQuantity(${item.id}, -1)" class="w-8 h-8 rounded-full bg-[#1a1a2e] text-white hover:bg-[#00ff88] hover:text-[#0f0f1a] transition-colors font-bold">-</button>
            <span class="w-8 text-center font-bold">${item.quantity}</span>
            <button onclick="updateQuantity(${item.id}, 1)" class="w-8 h-8 rounded-full bg-[#1a1a2e] text-white hover:bg-[#00ff88] hover:text-[#0f0f1a] transition-colors font-bold">+</button>
          </div>
          <button onclick="removeFromCart(${item.id})" class="p-2 text-gray-400 hover:text-[#ff0066] transition-colors" aria-label="Eliminar producto">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path>
            </svg>
          </button>
        </div>
      `).join('');

      cartTotal.textContent = `€${getCartTotal().toFixed(2)}`;
    }

    function showCheckout() {
      if (cart.length === 0) {
        showToast('Tu carrito está vacío', 'error');
        return;
      }

      showSection('checkout');

      const checkoutSummary = document.getElementById('checkout-summary');
      checkoutSummary.innerHTML = cart.map(item => `
        <div class="flex justify-between">
          <span>${item.name} x${item.quantity}</span>
          <span class="text-[#00ff88]">€${(item.price * item.quantity).toFixed(2)}</span>
        </div>
      `).join('');

      document.getElementById('checkout-total').textContent = `€${getCartTotal().toFixed(2)}`;
    }

    function resetAndGoHome() {
      cart = [];
      updateCartBadge();
      showSection('products');
    }

    async function onConfigChange(cfg) {
      config = { ...defaultConfig, ...cfg };

      const storeNameEl = document.getElementById('store-name');
      if (storeNameEl) storeNameEl.textContent = config.store_name;

      const heroTitleEl = document.getElementById('hero-title');
      if (heroTitleEl) heroTitleEl.textContent = config.hero_title;

      const heroSubtitleEl = document.getElementById('hero-subtitle');
      if (heroSubtitleEl) heroSubtitleEl.textContent = config.hero_subtitle;

      document.body.style.backgroundColor = config.background_color;
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (cfg) => ({
          recolorables: [
            {
              get: () => cfg.background_color || defaultConfig.background_color,
              set: (v) => { cfg.background_color = v; window.elementSdk.setConfig({ background_color: v }); }
            },
            {
              get: () => cfg.surface_color || defaultConfig.surface_color,
              set: (v) => { cfg.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); }
            },
            {
              get: () => cfg.text_color || defaultConfig.text_color,
              set: (v) => { cfg.text_color = v; window.elementSdk.setConfig({ text_color: v }); }
            },
            {
              get: () => cfg.primary_action || defaultConfig.primary_action,
              set: (v) => { cfg.primary_action = v; window.elementSdk.setConfig({ primary_action: v }); }
            },
            {
              get: () => cfg.secondary_action || defaultConfig.secondary_action,
              set: (v) => { cfg.secondary_action = v; window.elementSdk.setConfig({ secondary_action: v }); }
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (cfg) => new Map([
          ['store_name', cfg.store_name || defaultConfig.store_name],
          ['hero_title', cfg.hero_title || defaultConfig.hero_title],
          ['hero_subtitle', cfg.hero_subtitle || defaultConfig.hero_subtitle]
        ])
      });
    }

    const dataHandler = {
      onDataChanged(data) {
        recordCount = data.length;
      }
    };

    async function initDataSdk() {
      if (window.dataSdk) {
        const result = await window.dataSdk.init(dataHandler);
        if (!result.isOk) {
          console.error('Failed to initialize data SDK');
        }
      }
    }

    document.getElementById('checkout-form').addEventListener('submit', async function(e) {
      e.preventDefault();

      if (recordCount >= 999) {
        showToast('Se ha alcanzado el límite de pedidos. Contacta con atención al cliente.', 'error');
        return;
      }

      const submitBtn = document.getElementById('checkout-submit');
      submitBtn.disabled = true;
      submitBtn.textContent = 'PROCESANDO...';

      const orderData = {
        type: 'pedido',
        name: document.getElementById('checkout-name').value,
        email: document.getElementById('checkout-email').value,
        phone: document.getElementById('checkout-phone').value,
        address: document.getElementById('checkout-address').value,
        city: document.getElementById('checkout-city').value,
        postal_code: document.getElementById('checkout-postal').value,
        message: '',
        items: cart.map(item => `${item.name} x${item.quantity}`).join(', '),
        total: `€${getCartTotal().toFixed(2)}`,
        created_at: new Date().toISOString()
      };

      if (window.dataSdk) {
        const result = await window.dataSdk.create(orderData);
        if (result.isOk) {
          cart = [];
          updateCartBadge();
          document.getElementById('checkout-form').reset();
          showSection('success');
          showToast('¡Pedido realizado con éxito!', 'success');
        } else {
          showToast('Error al procesar el pedido. Inténtalo de nuevo.', 'error');
        }
      } else {
        cart = [];
        updateCartBadge();
        document.getElementById('checkout-form').reset();
        showSection('success');
      }

      submitBtn.disabled = false;
      submitBtn.textContent = 'CONFIRMAR PEDIDO';
    });

    document.getElementById('support-form').addEventListener('submit', async function(e) {
      e.preventDefault();

      if (recordCount >= 999) {
        showToast('Se ha alcanzado el límite de mensajes. Envía un email directamente.', 'error');
        return;
      }

      const submitBtn = document.getElementById('support-submit');
      submitBtn.disabled = true;
      submitBtn.textContent = 'ENVIANDO...';

      const supportData = {
        type: 'soporte',
        name: document.getElementById('support-name').value,
        email: document.getElementById('support-email').value,
        phone: '',
        address: '',
        city: '',
        postal_code: '',
        message: document.getElementById('support-message').value,
        items: '',
        total: '',
        created_at: new Date().toISOString()
      };

      if (window.dataSdk) {
        const result = await window.dataSdk.create(supportData);
        if (result.isOk) {
          document.getElementById('support-form').reset();
          showToast('¡Mensaje enviado! Te responderemos pronto.', 'success');
        } else {
          showToast('Error al enviar el mensaje. Inténtalo de nuevo.', 'error');
        }
      } else {
        document.getElementById('support-form').reset();
        showToast('¡Mensaje enviado! (Demo)', 'info');
      }

      submitBtn.disabled = false;
      submitBtn.textContent = 'ENVIAR MENSAJE';
    });

    initDataSdk();
    renderProducts();
  </script>

  <script>
    (function () {
      function c() {
        var b = a.contentDocument || a.contentWindow.document;
        if (b) {
          var d = b.createElement('script');
          d.innerHTML = "window.__CF$cv$params={r:'9dac7e8614770863',t:'MTc3MzI1MjM5OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";
          b.getElementsByTagName('head')[0].appendChild(d);
        }
      }
      if (document.body) {
        var a = document.createElement('iframe');
        a.height = 1;
        a.width = 1;
        a.style.position = 'absolute';
        a.style.top = 0;
        a.style.left = 0;
        a.style.border = 'none';
        a.style.visibility = 'hidden';
        document.body.appendChild(a);
        if ('loading' !== document.readyState) c();
        else if (window.addEventListener) document.addEventListener('DOMContentLoaded', c);
        else {
          var e = document.onreadystatechange || function () {};
          document.onreadystatechange = function (b) {
            e(b);
            if ('loading' !== document.readyState) {
              document.onreadystatechange = e;
              c();
            }
          };
        }
      }
    })();
  </script>
</body>
</html>
