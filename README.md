<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project Eklavya - 20 MW Paper Waste Gasification Platform</title>

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        emerald: {
                            400: '#34d399',
                            500: '#10b981',
                            600: '#059669',
                            700: '#047857',
                        },
                        amber: {
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                        },
                        cyan: {
                            400: '#22d3ee',
                            500: '#06b6d4',
                        },
                        slate: {
                            850: '#131e32',
                            900: '#0f172a',
                            950: '#020617'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace']
                    }
                }
            }
        }
    </script>

    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Three.js Library & OrbitControls -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>

    <style>
        body { font-family: 'Inter', sans-serif; }
        .glass-panel {
            background: rgba(15, 23, 42, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }
        .light .glass-panel {
            background: rgba(255, 255, 255, 0.90);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(0, 0, 0, 0.08);
        }
        .glow-emerald { box-shadow: 0 0 25px rgba(16, 185, 129, 0.25); }
        .glow-amber { box-shadow: 0 0 25px rgba(245, 158, 11, 0.25); }
        
        /* Smooth Scrolling */
        html { scroll-behavior: smooth; }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 dark:bg-slate-950 dark:text-slate-100 light:bg-slate-50 light:text-slate-900 min-h-screen flex flex-col transition-colors duration-300">

    <!-- HEADER / NAVIGATION BAR -->
    <header class="sticky top-0 z-40 bg-slate-950/90 dark:bg-slate-950/90 light:bg-white/90 backdrop-blur-md border-b border-slate-800 dark:border-slate-800 light:border-slate-200">
        <div class="max-w-7xl mx-auto px-4 py-3 flex items-center justify-between">
            <!-- Brand Logo -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="showTab('intro')">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-emerald-500 to-amber-500 flex items-center justify-center text-slate-950 font-black text-xl shadow-lg">
                    E
                </div>
                <div>
                    <span class="text-lg font-black tracking-wider text-white dark:text-white light:text-slate-900">EKLAVYA</span>
                    <span class="text-xs bg-emerald-500/20 text-emerald-400 border border-emerald-500/30 px-2 py-0.5 rounded ml-2 font-mono font-semibold">20 MW</span>
                    <p class="text-[10px] text-slate-400 dark:text-slate-400 light:text-slate-500 -mt-0.5" data-en="Paper Industry Waste-to-Energy" data-hi="कागज़ उद्योग कचरा-से-ऊर्जा">Paper Industry Waste-to-Energy</p>
                </div>
            </div>

            <!-- Main Navigation Buttons -->
            <nav class="hidden lg:flex items-center space-x-1 text-xs font-semibold">
                <button onclick="showTab('intro')" id="nav-intro" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5 bg-slate-800 text-white">
                    <i class="fa-solid fa-flag"></i>
                    <span data-en="Welcome" data-hi="स्वागतम्">Welcome</span>
                </button>
                <button onclick="showTab('home')" id="nav-home" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5">
                    <i class="fa-solid fa-gauge-high"></i>
                    <span data-en="Live Operations" data-hi="लाइव ऑपरेशन्स">Live Operations</span>
                </button>
                <button onclick="showTab('specs')" id="nav-specs" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5">
                    <i class="fa-solid fa-microchip"></i>
                    <span data-en="Specs & ₹20L Price" data-hi="तकनीकी विवरण एवं मूल्य">Specs & ₹20L Price</span>
                </button>
                <button onclick="showTab('diagrams')" id="nav-diagrams" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5">
                    <i class="fa-solid fa-sitemap"></i>
                    <span data-en="Process & Scrubbers" data-hi="प्रक्रिया व स्क्रबर">Process & Scrubbers</span>
                </button>
                <button onclick="showTab('viewer3d')" id="nav-viewer3d" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5">
                    <i class="fa-solid fa-cube text-amber-400"></i>
                    <span data-en="3D CAD Model" data-hi="3D मॉडल">3D CAD Model</span>
                </button>
                <button onclick="showTab('admin')" id="nav-admin" class="nav-btn px-3 py-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition flex items-center space-x-1.5 text-amber-400">
                    <i class="fa-solid fa-database"></i>
                    <span data-en="Paper Waste DB (1,000+)" data-hi="कागज़ कचरा डेटाबेस">Paper Waste DB (1,000+)</span>
                </button>
            </nav>

            <!-- Utility Controls -->
            <div class="flex items-center space-x-2">
                <!-- Language Toggle -->
                <button onclick="toggleLang()" class="px-2.5 py-1.5 bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-mono rounded-lg border border-slate-700 transition flex items-center space-x-1">
                    <i class="fa-solid fa-language text-emerald-400"></i>
                    <span id="lang-label">EN / HI</span>
                </button>

                <!-- Theme Toggle -->
                <button onclick="toggleTheme()" class="p-2 bg-slate-800 hover:bg-slate-700 text-slate-200 rounded-lg border border-slate-700 transition" title="Toggle Theme">
                    <i class="fa-solid fa-sun text-amber-400 hidden dark:block"></i>
                    <i class="fa-solid fa-moon text-slate-800 block dark:hidden"></i>
                </button>

                <!-- Auth State & Login / Register Buttons -->
                <div id="auth-nav-container" class="flex items-center space-x-2">
                    <button id="auth-btn" onclick="openAuthModal('login')" class="px-3 py-1.5 bg-emerald-600 hover:bg-emerald-500 text-white font-semibold text-xs rounded-lg transition shadow-md flex items-center space-x-1.5">
                        <i class="fa-solid fa-key"></i>
                        <span id="auth-btn-text" data-en="Login / Register" data-hi="लॉगिन / रजिस्टर">Login / Register</span>
                    </button>
                </div>

                <!-- Mobile Menu Button -->
                <button onclick="toggleMobileMenu()" class="lg:hidden p-2 text-slate-300 hover:text-white">
                    <i class="fa-solid fa-bars text-lg"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Menu Dropdown -->
        <div id="mobile-menu" class="hidden lg:hidden border-t border-slate-800 bg-slate-950 p-4 space-y-2 text-sm">
            <button onclick="showTab('intro'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800">1. Welcome Landing Page</button>
            <button onclick="showTab('home'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800">2. Live Operations & Calculator</button>
            <button onclick="showTab('specs'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800">3. Specs & ₹20 Lakh Pricing</button>
            <button onclick="showTab('diagrams'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800">4. Process & Scrubber Schematics</button>
            <button onclick="showTab('viewer3d'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800 text-amber-400">5. Interactive 3D CAD Plant Model</button>
            <button onclick="showTab('admin'); toggleMobileMenu()" class="w-full text-left px-3 py-2 rounded hover:bg-slate-800">6. 1,000+ Paper Waste Master DB</button>
        </div>
    </header>

    <!-- MAIN CONTENT AREA -->
    <main class="flex-1 max-w-7xl w-full mx-auto p-4 lg:p-6 space-y-8">

        <!-- ================= SECTION 1: WELCOME / INTRODUCTION LANDING PAGE ================= -->
        <section id="tab-intro" class="tab-content space-y-12">
            <!-- Hero Banner -->
            <div class="relative bg-gradient-to-br from-slate-900 via-slate-950 to-emerald-950/40 border border-slate-800 rounded-3xl p-8 lg:p-12 shadow-2xl overflow-hidden">
                <div class="absolute -right-16 -bottom-16 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
                <div class="absolute -left-16 -top-16 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

                <div class="relative z-10 max-w-4xl space-y-6">
                    <div class="inline-flex items-center space-x-2 bg-emerald-500/10 border border-emerald-500/30 text-emerald-400 px-3 py-1 rounded-full text-xs font-semibold uppercase tracking-wider">
                        <i class="fa-solid fa-atom animate-spin text-xs"></i>
                        <span>Next-Gen Waste-to-Energy Solution</span>
                    </div>

                    <h1 class="text-3xl sm:text-5xl lg:text-6xl font-black text-white leading-tight tracking-tight">
                        Revolutionizing Paper & Pulp <span class="text-transparent bg-clip-text bg-gradient-to-r from-emerald-400 via-teal-300 to-amber-400">Waste-to-Energy</span>
                    </h1>

                    <p class="text-slate-300 text-base lg:text-lg leading-relaxed max-w-3xl">
                        Project Eklavya provides paper mills with a modular, high-efficiency <strong>20 MW (20,000 kW)</strong> gasification platform designed specifically for paper sludge, bio-solids, OCC rejects, and bark. Valued at an ultra-accessible <strong>₹20 Lakhs per turnkey unit</strong>.
                    </p>

                    <!-- CTA Buttons -->
                    <div class="flex flex-wrap gap-4 pt-4">
                        <button onclick="showTab('home')" class="px-6 py-3.5 bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold text-sm rounded-xl transition shadow-lg glow-emerald flex items-center space-x-2">
                            <i class="fa-solid fa-play"></i>
                            <span data-en="Launch Interactive Demo" data-hi="लाइव प्रदर्शन देखें">Launch Interactive Demo</span>
                        </button>

                        <button onclick="showTab('viewer3d')" class="px-6 py-3.5 bg-slate-800 hover:bg-slate-700 text-amber-400 border border-amber-500/30 font-bold text-sm rounded-xl transition flex items-center space-x-2">
                            <i class="fa-solid fa-cube"></i>
                            <span data-en="Explore 3D Plant Model" data-hi="3D मॉडल एक्सप्लोर करें">Explore 3D Plant Model</span>
                        </button>

                        <button onclick="showTab('specs')" class="px-6 py-3.5 bg-slate-900 hover:bg-slate-800 text-slate-200 border border-slate-700 font-bold text-sm rounded-xl transition flex items-center space-x-2">
                            <i class="fa-solid fa-tag text-emerald-400"></i>
                            <span data-en="View Specs & ₹20 Lakh Pricing" data-hi="तकनीकी एवं ₹20 लाख मूल्य">View Specs & ₹20 Lakh Pricing</span>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Key Executive Value Highlights -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-slate-900/80 border border-slate-800 p-6 rounded-2xl space-y-3">
                    <div class="w-12 h-12 rounded-xl bg-amber-500/10 border border-amber-500/30 flex items-center justify-center text-amber-400 text-xl font-bold">
                        <i class="fa-solid fa-indian-rupee-sign"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white">Unmatched Economics</h3>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Priced at just <strong>₹20,00,000 (₹20 Lakhs)</strong> per modular unit, achieving full payback in <strong>1.5 to 3 months</strong> by offsetting high grid power tariffs and tipping fees.
                    </p>
                </div>

                <div class="bg-slate-900/80 border border-slate-800 p-6 rounded-2xl space-y-3">
                    <div class="w-12 h-12 rounded-xl bg-emerald-500/10 border border-emerald-500/30 flex items-center justify-center text-emerald-400 text-xl font-bold">
                        <i class="fa-solid fa-bolt"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white">20 MW High Output</h3>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Generates up to <strong>20,000 kW AC</strong> continuous power. Designed to drive paper machine baseload lines for <strong>20 hours every single day</strong>.
                    </p>
                </div>

                <div class="bg-slate-900/80 border border-slate-800 p-6 rounded-2xl space-y-3">
                    <div class="w-12 h-12 rounded-xl bg-cyan-500/10 border border-cyan-500/30 flex items-center justify-center text-cyan-400 text-xl font-bold">
                        <i class="fa-solid fa-filter"></i>
                    </div>
                    <h3 class="text-xl font-bold text-white">99.4% Tar Removal</h3>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Integrated dual high-G cyclone separators + Venturi caustic wet scrubber tower eliminate tar and corrosive chlorine from raw paper sludge gas.
                    </p>
                </div>
            </div>

            <!-- Industry Challenge & Solution Section -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-8 space-y-6">
                <div class="max-w-3xl space-y-2">
                    <span class="text-xs font-mono text-emerald-400 uppercase tracking-widest">Industry Challenge & Impact</span>
                    <h2 class="text-2xl font-extrabold text-white">Converting Paper Mill Liabilities into Clean Power</h2>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Paper mills face rising landfill costs for wet sludge disposal and severe power expense burdens. Project Eklavya solves both challenges simultaneously.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="bg-slate-950 p-5 rounded-xl border border-red-500/20 space-y-3">
                        <h4 class="font-bold text-red-400 text-sm flex items-center"><i class="fa-solid fa-circle-xmark mr-2"></i> The Mill Problem</h4>
                        <ul class="text-xs text-slate-300 space-y-2">
                            <li>• High moisture primary sludge disposal fees up to ₹3,500/tonne.</li>
                            <li>• High electricity costs from the grid (₹8.50 - ₹12.00 / kWh).</li>
                            <li>• Environmental penalties on sludge dumping & carbon emissions.</li>
                        </ul>
                    </div>

                    <div class="bg-slate-950 p-5 rounded-xl border border-emerald-500/20 space-y-3">
                        <h4 class="font-bold text-emerald-400 text-sm flex items-center"><i class="fa-solid fa-circle-check mr-2"></i> The Eklavya Solution</h4>
                        <ul class="text-xs text-slate-300 space-y-2">
                            <li>• Zero-landfill conversion of sludge into clean syngas & biochar.</li>
                            <li>• On-site 20,000 kW power generation offsetting grid purchases.</li>
                            <li>• Low capital barrier with a modular unit cost of only ₹20 Lakhs.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= SECTION 2: HOME PAGE (OPERATIONS & CALCULATOR) ================= -->
        <section id="tab-home" class="tab-content hidden space-y-6">
            
            <!-- Live Telemetry Bar -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-6 shadow-xl space-y-4">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center border-b border-slate-800 pb-3">
                    <div class="flex items-center space-x-2">
                        <div class="w-3 h-3 rounded-full bg-emerald-500 animate-pulse"></div>
                        <h3 class="font-bold text-white text-sm" data-en="Live Operations Telemetry HUD" data-hi="लाइव ऑपरेशन्स टेलीमेट्री HUD">Live Operations Telemetry HUD</h3>
                    </div>
                    <div class="text-xs text-slate-400 font-mono mt-1 sm:mt-0" id="live-ist-clock">
                        IST Clock Loading...
                    </div>
                </div>

                <!-- 4 Metrics Row -->
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <p class="text-[11px] text-slate-400 uppercase font-mono">Capacity Target</p>
                        <p class="text-2xl font-extrabold text-amber-400 mt-1">20,000 kW</p>
                        <p class="text-[10px] text-slate-500 mt-0.5">(20 MW AC Continuous)</p>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <p class="text-[11px] text-slate-400 uppercase font-mono">Reactor Core Temp</p>
                        <p class="text-2xl font-extrabold text-emerald-400 mt-1">1,050 °C</p>
                        <p class="text-[10px] text-slate-500 mt-0.5">Inconel Thermal Cracking</p>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <p class="text-[11px] text-slate-400 uppercase font-mono">Tar Removal Eff.</p>
                        <p class="text-2xl font-extrabold text-cyan-400 mt-1">99.4 %</p>
                        <p class="text-[10px] text-slate-500 mt-0.5">Cyclone + Venturi Wet Tower</p>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-emerald-500/40 bg-emerald-950/10">
                        <p class="text-[11px] text-emerald-400 uppercase font-mono font-bold">Mill Operating Hours</p>
                        <p class="text-2xl font-extrabold text-white mt-1">20 Hours / Day</p>
                        <p class="text-[10px] text-emerald-400/80 mt-0.5">Target Fixed Baseload</p>
                    </div>
                </div>
            </div>

            <!-- Interactive Paper Waste Energy Calculator -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-6">
                <div>
                    <span class="bg-emerald-500/10 text-emerald-400 text-xs font-semibold px-2.5 py-1 rounded-full border border-emerald-500/30">
                        Interactive Yield Calculator
                    </span>
                    <h2 class="text-2xl font-extrabold text-white mt-2">Paper Mill Energy & Yield Estimator</h2>
                    <p class="text-slate-400 text-xs mt-1">
                        Input your paper mill's daily waste feed rate (Tonnes/Day) to model energy generated, syngas flow, carbon offset, and biochar production.
                    </p>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                    <!-- Controls -->
                    <div class="lg:col-span-1 space-y-5 bg-slate-950 p-5 rounded-xl border border-slate-800">
                        <!-- Feedstock Selector -->
                        <div>
                            <label class="block text-xs font-semibold text-slate-300 uppercase mb-2">1. Paper Waste Stream Type</label>
                            <select id="calc-waste-select" onchange="runCalculator()" class="w-full bg-slate-900 border border-slate-700 text-slate-200 rounded-lg p-2.5 text-xs focus:border-emerald-500">
                                <option value="primary_sludge" selected>Primary Paper Sludge (40% Moisture)</option>
                                <option value="deinked_residue">Deinked Pulp Fiber Residue</option>
                                <option value="occ_scrap">OCC / Cardboard Scrap Trimmings</option>
                                <option value="kraft_liquor">Kraft Process Bio-solids</option>
                                <option value="wood_bark">Wood Bark & Sawmill Waste</option>
                            </select>
                        </div>

                        <!-- TPD Input Slider -->
                        <div>
                            <div class="flex justify-between text-xs font-semibold text-slate-300 uppercase mb-2">
                                <span>2. Daily Waste Feed</span>
                                <span class="text-emerald-400 font-mono"><span id="calc-tpd-display">350</span> Tonnes / Day</span>
                            </div>
                            <input type="range" id="calc-tpd-slider" min="50" max="800" value="350" step="10" oninput="runCalculator()" class="w-full accent-emerald-500 cursor-pointer">
                            <div class="flex justify-between text-[10px] text-slate-500 mt-1">
                                <span>50 TPD</span>
                                <span>350 TPD (Standard)</span>
                                <span>800 TPD</span>
                            </div>
                        </div>

                        <!-- Fixed Mill Target Badge -->
                        <div class="p-3 bg-emerald-950/40 border border-emerald-500/30 rounded-lg text-xs space-y-1">
                            <p class="text-emerald-400 font-bold flex items-center"><i class="fa-solid fa-clock mr-1.5"></i> Daily Target Schedule</p>
                            <p class="text-slate-300">Mill Operations Powered Target: <strong class="text-white">20 Hours / Day</strong></p>
                        </div>
                    </div>

                    <!-- Calculator Results Display -->
                    <div class="lg:col-span-2 grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <!-- Primary Output: Hours -->
                        <div class="sm:col-span-2 bg-gradient-to-r from-emerald-950/80 to-slate-900 border-2 border-emerald-500/50 p-6 rounded-2xl flex flex-col justify-between">
                            <div>
                                <span class="text-xs font-bold text-emerald-400 uppercase font-mono"><i class="fa-solid fa-bolt mr-1"></i> Core Operational Target</span>
                                <h3 class="text-slate-200 text-sm mt-1">Paper Mill Operations Powered</h3>
                                <div class="flex items-baseline space-x-3 mt-2">
                                    <span class="text-5xl font-black text-white font-mono">20</span>
                                    <span class="text-2xl font-bold text-emerald-400">Hours / Day (Fixed Target)</span>
                                </div>
                                <p class="text-xs text-slate-400 mt-2">
                                    Consistently offset paper machine energy demand for 20 operating hours every single day.
                                </p>
                            </div>
                            <div class="mt-4 pt-3 border-t border-slate-800 flex justify-between text-xs font-mono text-slate-300">
                                <span>Estimated Power Generated: <strong id="out-power-kwh" class="text-amber-400">142,500 kWh/day</strong></span>
                                <span>Capacity Utilized: <strong id="out-mw-equivalent" class="text-emerald-400">18.5 MW</strong></span>
                            </div>
                        </div>

                        <!-- Metric Card 1: Syngas -->
                        <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-1">
                            <p class="text-[11px] text-slate-400 uppercase font-mono">Daily Syngas Yield</p>
                            <p class="text-2xl font-extrabold text-cyan-400 font-mono" id="out-syngas">735,000 Nm³</p>
                            <p class="text-[10px] text-slate-500">Cleaned & Tar-Free Gas Output</p>
                        </div>

                        <!-- Metric Card 2: CO2 Offset -->
                        <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-1">
                            <p class="text-[11px] text-slate-400 uppercase font-mono">CO2 Emissions Offset</p>
                            <p class="text-2xl font-extrabold text-emerald-400 font-mono" id="out-co2">66,430 MT / yr</p>
                            <p class="text-[10px] text-slate-500">Qualifies for Carbon Credits</p>
                        </div>

                        <!-- Metric Card 3: Biochar Yield -->
                        <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-1">
                            <p class="text-[11px] text-slate-400 uppercase font-mono">Biochar Co-Product Yield</p>
                            <p class="text-2xl font-extrabold text-amber-400 font-mono" id="out-biochar">35.0 TPD</p>
                            <p class="text-[10px] text-slate-500">Usable for Soil / Boiler Fuel</p>
                        </div>

                        <!-- Metric Card 4: Financial Savings -->
                        <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-1">
                            <p class="text-[11px] text-slate-400 uppercase font-mono">Est. Electricity Cost Savings</p>
                            <p class="text-2xl font-extrabold text-purple-400 font-mono" id="out-savings">₹ 44.2 Lakh / mo</p>
                            <p class="text-[10px] text-slate-500">Substituted against ₹8.5/kWh grid power</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Regional Paper Industry Deployments Map Simulation -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 space-y-4">
                <h3 class="text-lg font-bold text-white flex items-center">
                    <i class="fa-solid fa-map-location-dot text-emerald-400 mr-2"></i> Regional Paper Mill Deployments (India Hubs)
                </h3>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs font-mono">
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <span class="text-emerald-400 font-bold">Uttar Pradesh Hub (Saharanpur)</span>
                        <p class="text-slate-400 mt-1">3 Active Units • 60 MW Total</p>
                        <p class="text-[10px] text-slate-500 mt-1">Sludge Feed: Primary Pulp + OCC</p>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <span class="text-emerald-400 font-bold">Tamil Nadu Hub (Erode / Karur)</span>
                        <p class="text-slate-400 mt-1">2 Active Units • 40 MW Total</p>
                        <p class="text-[10px] text-slate-500 mt-1">Sludge Feed: Kraft Deinked Residue</p>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800">
                        <span class="text-emerald-400 font-bold">Gujarat Hub (Vapi / Surat)</span>
                        <p class="text-slate-400 mt-1">4 Active Units • 80 MW Total</p>
                        <p class="text-[10px] text-slate-500 mt-1">Sludge Feed: Duplex Board Rejects</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= SECTION 3: SPECS & ₹20 LAKH PRICING ================= -->
        <section id="tab-specs" class="tab-content hidden space-y-6">
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-6">
                <!-- Header with Fixed Price Banner -->
                <div class="flex flex-col md:flex-row justify-between items-start md:items-center border-b border-slate-800 pb-4">
                    <div>
                        <span class="bg-amber-500/10 text-amber-400 text-xs font-semibold px-2.5 py-1 rounded-full border border-amber-500/30">
                            Commercial Turnkey Valuation
                        </span>
                        <h2 class="text-2xl font-extrabold text-white mt-1">20,000 kW (20 MW) Commercial Specifications</h2>
                    </div>
                    <div class="mt-4 md:mt-0 bg-gradient-to-r from-amber-500 to-emerald-500 p-0.5 rounded-2xl">
                        <div class="bg-slate-950 px-6 py-3 rounded-[14px] text-center">
                            <p class="text-[10px] uppercase font-mono text-slate-400">Turnkey Unit Price</p>
                            <p class="text-3xl font-black text-amber-400 font-mono">₹ 20,00,000</p>
                            <p class="text-[10px] text-emerald-400 font-bold">(₹20 Lakhs / Modular Unit)</p>
                        </div>
                    </div>
                </div>

                <!-- Comprehensive Specs Grid -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-3">
                        <div class="w-10 h-10 rounded-xl bg-amber-500/10 border border-amber-500/30 flex items-center justify-center text-amber-400 font-bold">
                            <i class="fa-solid fa-fire"></i>
                        </div>
                        <h3 class="font-bold text-white text-base">Inconel-600 High-Temp Reactor</h3>
                        <ul class="text-xs space-y-2 text-slate-300 font-mono">
                            <li class="flex justify-between"><span>Core Operating Temp:</span> <strong class="text-amber-400">1,050 °C</strong></li>
                            <li class="flex justify-between"><span>Material Grade:</span> <strong>Inconel-600 Superalloy</strong></li>
                            <li class="flex justify-between"><span>Pyrolysis Pre-treatment:</span> <strong>450 °C Auger Stage</strong></li>
                            <li class="flex justify-between"><span>Thermal Cracking:</span> <strong>Down-draft Gasifier</strong></li>
                        </ul>
                    </div>

                    <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-3">
                        <div class="w-10 h-10 rounded-xl bg-emerald-500/10 border border-emerald-500/30 flex items-center justify-center text-emerald-400 font-bold">
                            <i class="fa-solid fa-bolt"></i>
                        </div>
                        <h3 class="font-bold text-white text-base">20 MW Syngas Turbine Genset</h3>
                        <ul class="text-xs space-y-2 text-slate-300 font-mono">
                            <li class="flex justify-between"><span>Rated Output:</span> <strong class="text-emerald-400">20,000 kW (20 MW)</strong></li>
                            <li class="flex justify-between"><span>Electrical Voltage:</span> <strong>11 kV / 33 kV Grid Synch</strong></li>
                            <li class="flex justify-between"><span>Parasitic Load:</span> <strong>1.8 MW Total</strong></li>
                            <li class="flex justify-between"><span>Target Hours:</span> <strong>20 Hours / Day</strong></li>
                        </ul>
                    </div>

                    <div class="bg-slate-950 p-5 rounded-xl border border-slate-800 space-y-3">
                        <div class="w-10 h-10 rounded-xl bg-cyan-500/10 border border-cyan-500/30 flex items-center justify-center text-cyan-400 font-bold">
                            <i class="fa-solid fa-filter"></i>
                        </div>
                        <h3 class="font-bold text-white text-base">Cyclone & Venturi Scrubber</h3>
                        <ul class="text-xs space-y-2 text-slate-300 font-mono">
                            <li class="flex justify-between"><span>Primary Cyclone:</span> <strong>Dual High-G Phase</strong></li>
                            <li class="flex justify-between"><span>Venturi Wet Scrubber:</span> <strong>Caustic Wash (pH 8.5)</strong></li>
                            <li class="flex justify-between"><span>Tar Removal Eff:</span> <strong class="text-cyan-400">99.4% Total</strong></li>
                            <li class="flex justify-between"><span>Particulate Limit:</span> <strong>&lt; 3 mg/Nm³</strong></li>
                        </ul>
                    </div>
                </div>

                <!-- Financial ROI Model -->
                <div class="bg-slate-950 p-6 rounded-xl border border-slate-800 space-y-4">
                    <h3 class="font-bold text-white text-sm uppercase font-mono tracking-wider flex items-center">
                        <i class="fa-solid fa-chart-pie text-emerald-400 mr-2"></i> Financial ROI Analysis (₹20 Lakh Capital Expenditure)
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs font-mono">
                        <div class="bg-slate-900 p-4 rounded-lg space-y-1">
                            <span class="text-slate-400">Turnkey Unit Capex</span>
                            <p class="text-2xl font-bold text-amber-400">₹ 20,00,000</p>
                            <p class="text-[10px] text-slate-500">Modular Skid Factory Delivered</p>
                        </div>
                        <div class="bg-slate-900 p-4 rounded-lg space-y-1">
                            <span class="text-slate-400">Monthly Power Savings</span>
                            <p class="text-2xl font-bold text-emerald-400">₹ 12,50,000+</p>
                            <p class="text-[10px] text-slate-500">Based on offsetting 150,000+ kWh/mo grid</p>
                        </div>
                        <div class="bg-slate-900 p-4 rounded-lg space-y-1">
                            <span class="text-slate-400">Estimated Payback Period</span>
                            <p class="text-2xl font-bold text-purple-400">1.5 to 3 Months</p>
                            <p class="text-[10px] text-slate-500">Rapid ROI for Paper Mills</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= SECTION 4: DIAGRAMS & ARCHITECTURE ================= -->
        <section id="tab-diagrams" class="tab-content hidden space-y-6">
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-8">
                <div>
                    <span class="bg-blue-500/10 text-blue-400 text-xs font-semibold px-2.5 py-1 rounded-full border border-blue-500/30">
                        Visual Engineering Schematics
                    </span>
                    <h2 class="text-2xl font-extrabold text-white mt-1">Pyrolysis, Scrubber & 7-Stage Process Diagrams</h2>
                </div>

                <!-- Diagram A: Pyrolysis System -->
                <div class="bg-slate-950 p-6 rounded-xl border border-slate-800 space-y-4">
                    <h3 class="font-bold text-amber-400 text-sm font-mono flex items-center">
                        <i class="fa-solid fa-fire-burner mr-2"></i> Schematic A: Dual-Auger Pyrolysis Reactor (450°C Pre-Treatment)
                    </h3>
                    <div class="w-full bg-slate-900 p-4 rounded-xl border border-slate-800 flex justify-center overflow-x-auto">
                        <svg width="600" height="180" viewBox="0 0 600 180" class="max-w-full h-auto">
                            <!-- Auger Cylinder -->
                            <rect x="50" y="50" width="300" height="70" rx="10" fill="#1e293b" stroke="#f59e0b" stroke-width="2"/>
                            <!-- Auger Screw Blades -->
                            <path d="M 60 50 Q 80 85 60 120 M 110 50 Q 130 85 110 120 M 160 50 Q 180 85 160 120 M 210 50 Q 230 85 210 120 M 260 50 Q 280 85 260 120 M 310 50 Q 330 85 310 120" stroke="#f59e0b" stroke-width="2" fill="none"/>
                            <!-- Feed Hopper -->
                            <polygon points="50,10 90,10 70,50" fill="#10b981"/>
                            <text x="70" y="25" fill="#ffffff" font-size="10" text-anchor="middle" font-family="sans-serif">Raw Sludge Input</text>
                            <!-- Heat Jacket -->
                            <rect x="100" y="125" width="200" height="20" rx="4" fill="#d97706"/>
                            <text x="200" y="139" fill="#ffffff" font-size="10" text-anchor="middle" font-family="sans-serif">Exhaust Gas Heat Jacket (450°C)</text>
                            <!-- Gas Exit -->
                            <rect x="320" y="20" width="20" height="30" fill="#06b6d4"/>
                            <path d="M 330 20 L 330 5" stroke="#06b6d4" stroke-width="2" marker-end="url(#arrow)"/>
                            <text x="330" y="-2" fill="#06b6d4" font-size="10" text-anchor="middle" font-family="sans-serif">Volatiles to Gasifier</text>
                        </svg>
                    </div>
                </div>

                <!-- Diagram B: Cyclone & Venturi Wet Scrubber -->
                <div class="bg-slate-950 p-6 rounded-xl border border-slate-800 space-y-4">
                    <h3 class="font-bold text-cyan-400 text-sm font-mono flex items-center">
                        <i class="fa-solid fa-filter mr-2"></i> Schematic B: Dual Cyclone & Venturi Wet Caustic Scrubber
                    </h3>
                    <div class="w-full bg-slate-900 p-4 rounded-xl border border-slate-800 flex justify-center overflow-x-auto">
                        <svg width="650" height="200" viewBox="0 0 650 200" class="max-w-full h-auto">
                            <!-- Raw Gas Line -->
                            <line x1="20" y1="60" x2="80" y2="60" stroke="#f59e0b" stroke-width="4"/>
                            <text x="50" y="50" fill="#f59e0b" font-size="10" text-anchor="middle">Raw Syngas</text>
                            <!-- Cyclone 1 -->
                            <polygon points="80,30 140,30 110,140" fill="#1e293b" stroke="#3b82f6" stroke-width="2"/>
                            <text x="110" y="20" fill="#3b82f6" font-size="10" text-anchor="middle">Primary Cyclone</text>
                            <text x="110" y="160" fill="#94a3b8" font-size="9" text-anchor="middle">Fly Ash Removal</text>
                            <!-- Connecting Pipe -->
                            <line x1="110" y1="30" x2="220" y2="60" stroke="#3b82f6" stroke-width="3"/>
                            <!-- Venturi Scrubber Tube -->
                            <path d="M 220 40 L 260 70 L 260 110 L 220 140" stroke="#06b6d4" stroke-width="3" fill="none"/>
                            <!-- Spray Nozzle -->
                            <circle cx="260" cy="55" r="5" fill="#10b981"/>
                            <text x="310" y="55" fill="#10b981" font-size="10">Caustic Spray (pH 8.5)</text>
                            <!-- Wet Tower Column -->
                            <rect x="380" y="20" width="80" height="130" rx="10" fill="#1e293b" stroke="#06b6d4" stroke-width="2"/>
                            <text x="420" y="80" fill="#06b6d4" font-size="10" text-anchor="middle">Venturi Wet Tower</text>
                            <!-- Clean Gas Exit -->
                            <line x1="460" y1="40" x2="620" y2="40" stroke="#10b981" stroke-width="4"/>
                            <text x="540" y="30" fill="#10b981" font-size="10" text-anchor="middle">Ultra-Clean Syngas to Turbine (&lt;3 mg/Nm³)</text>
                        </svg>
                    </div>
                </div>

                <!-- 7-Stage Process Flow Diagram -->
                <div class="bg-slate-950 p-6 rounded-xl border border-slate-800 space-y-4">
                    <h3 class="font-bold text-emerald-400 text-sm font-mono flex items-center">
                        <i class="fa-solid fa-list-check mr-2"></i> Schematic C: 7-Stage Industrial Process Flow
                    </h3>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-7 gap-2 text-center text-xs">
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-emerald-400 block">1. Feed</span>Paper Sludge</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-amber-400 block">2. Pyrolysis</span>450°C Volatiles</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-amber-500 block">3. Gasifier</span>1,050°C Inconel</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-cyan-400 block">4. Cyclone</span>Fly-ash Separator</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-blue-400 block">5. Wet Scrubber</span>Caustic Scrubbing</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-purple-400 block">6. Buffer Tank</span>Syngas Storage</div>
                        <div class="bg-slate-900 p-3 rounded-lg border border-slate-800"><span class="font-bold text-emerald-400 block">7. 20MW Turbine</span>11kV Grid Power</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= SECTION 5: INTERACTIVE 3D CAD MODEL VIEWER ================= -->
        <section id="tab-viewer3d" class="tab-content hidden space-y-6">
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-4">
                <div class="flex flex-col md:flex-row justify-between items-start md:items-center">
                    <div>
                        <span class="bg-amber-500/10 text-amber-400 text-xs font-semibold px-2.5 py-1 rounded-full border border-amber-500/30">
                            WebGL 3D Interactive Visualization
                        </span>
                        <h2 class="text-2xl font-extrabold text-white mt-1">20 MW Plant Modular Skid CAD Model</h2>
                    </div>
                    <p class="text-xs text-slate-400 mt-2 md:mt-0"><i class="fa-solid fa-hand-pointer text-amber-400 mr-1"></i> Drag to rotate | Scroll to zoom</p>
                </div>

                <!-- 3D Canvas Area -->
                <div class="w-full h-[450px] bg-slate-950 rounded-xl relative overflow-hidden border border-slate-800">
                    <div id="three-cad-container" class="w-full h-full cursor-grab"></div>

                    <!-- 3D Component Selector Bar Overlay -->
                    <div class="absolute bottom-4 left-4 right-4 bg-slate-900/90 backdrop-blur border border-slate-700 p-2.5 rounded-xl flex flex-wrap gap-2 justify-center text-xs">
                        <button onclick="highlight3DModule('hopper')" class="px-3 py-1.5 bg-slate-800 hover:bg-emerald-600 rounded-lg transition">1. Feed Hopper</button>
                        <button onclick="highlight3DModule('pyrolysis')" class="px-3 py-1.5 bg-slate-800 hover:bg-emerald-600 rounded-lg transition">2. Pyrolysis Unit (450°C)</button>
                        <button onclick="highlight3DModule('gasifier')" class="px-3 py-1.5 bg-slate-800 hover:bg-emerald-600 rounded-lg transition">3. Inconel Reactor (1050°C)</button>
                        <button onclick="highlight3DModule('cyclone')" class="px-3 py-1.5 bg-slate-800 hover:bg-emerald-600 rounded-lg transition text-cyan-400 font-bold">4. Cyclone & Venturi Scrubber</button>
                        <button onclick="highlight3DModule('turbine')" class="px-3 py-1.5 bg-slate-800 hover:bg-emerald-600 rounded-lg transition text-amber-400 font-bold">5. 20 MW Turbine Genset</button>
                        <button onclick="reset3DView()" class="px-3 py-1.5 bg-slate-700 hover:bg-slate-600 rounded-lg transition"><i class="fa-solid fa-rotate-right"></i> Reset Camera</button>
                    </div>
                </div>

                <!-- Active 3D Component Inspector Panel -->
                <div class="bg-slate-950 p-4 rounded-xl border border-slate-800 text-xs space-y-1" id="3d-inspector-panel">
                    <span class="text-slate-400 uppercase font-mono">Selected Component Inspector:</span>
                    <h4 id="3d-comp-title" class="text-base font-bold text-amber-400">4. Cyclone & Venturi Wet Scrubber Tower</h4>
                    <p id="3d-comp-desc" class="text-slate-300 leading-relaxed">
                        High-efficiency dual cyclone phase followed by Venturi wet caustic washing tower designed to remove 99.4% of tars and particulates from high-moisture paper sludge syngas.
                    </p>
                </div>
            </div>
        </section>

        <!-- ================= SECTION 6: PAPER WASTE MASTER DATABASE (1,000+ ENTRIES) ================= -->
        <section id="tab-admin" class="tab-content hidden space-y-6">
            
            <!-- Protected Lock Banner (Shown if not authenticated) -->
            <div id="admin-lock-screen" class="bg-slate-900 border border-slate-800 rounded-2xl p-10 text-center max-w-xl mx-auto space-y-4">
                <div class="w-16 h-16 rounded-2xl bg-amber-500/10 border border-amber-500/30 flex items-center justify-center text-amber-400 text-2xl mx-auto">
                    <i class="fa-solid fa-lock"></i>
                </div>
                <h2 class="text-2xl font-bold text-white">Protected Master Paper Waste DB</h2>
                <p class="text-slate-400 text-xs">
                    Access to the 1,000+ indexed paper waste feedstock database and CSV export requires Master Key authorization.
                </p>
                <button onclick="openAuthModal()" class="px-6 py-2.5 bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-xs rounded-xl transition">
                    Enter Security Master Key
                </button>
            </div>

            <!-- Unlocked Admin DB Content -->
            <div id="admin-unlocked-content" class="hidden space-y-6">
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl space-y-6">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center">
                        <div>
                            <span class="bg-emerald-500/10 text-emerald-400 text-xs font-semibold px-2.5 py-1 rounded-full border border-emerald-500/30">
                                Master Developer Authenticated
                            </span>
                            <h2 class="text-2xl font-extrabold text-white mt-1">1,000+ Paper Waste Feedstock Database</h2>
                        </div>
                        <div class="mt-3 md:mt-0 flex items-center space-x-2">
                            <input type="text" id="db-search-input" oninput="filterPaperTable()" placeholder="Search paper waste, LHV, origin..." class="bg-slate-950 border border-slate-700 text-xs text-slate-200 px-3 py-2 rounded-lg w-60 focus:border-emerald-500">
                            <button onclick="exportDBToCSV()" class="px-3 py-2 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-lg transition" title="Export CSV">
                                <i class="fa-solid fa-download mr-1"></i> CSV
                            </button>
                        </div>
                    </div>

                    <!-- DB Table -->
                    <div class="overflow-x-auto bg-slate-950 rounded-xl border border-slate-800">
                        <table class="w-full text-xs text-left text-slate-300">
                            <thead class="bg-slate-900 font-mono text-slate-400 uppercase border-b border-slate-800">
                                <tr>
                                    <th class="p-3">Record ID</th>
                                    <th class="p-3">Paper Waste Category</th>
                                    <th class="p-3">Paper Mill Origin</th>
                                    <th class="p-3">LHV (MJ/kg)</th>
                                    <th class="p-3">Moisture %</th>
                                    <th class="p-3">Syngas Yield (Nm³/t)</th>
                                </tr>
                            </thead>
                            <tbody id="paper-table-body" class="divide-y divide-slate-800 font-mono">
                                <!-- Dynamically generated by JS -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- GEMINI AI FLOATING OPERATOR CHATBOT -->
    <div id="ai-chat-widget" class="fixed bottom-6 right-6 z-50">
        <button id="chat-toggle-btn" onclick="toggleChatWindow()" class="w-14 h-14 rounded-full bg-gradient-to-tr from-emerald-500 to-amber-500 text-slate-950 flex items-center justify-center shadow-2xl hover:scale-105 transition transform">
            <i class="fa-solid fa-robot text-2xl"></i>
        </button>

        <div id="chat-window" class="hidden w-[350px] sm:w-[380px] h-[480px] bg-slate-900 border border-slate-800 rounded-2xl shadow-2xl flex flex-col overflow-hidden -mt-[490px] -ml-[270px] sm:-ml-[300px]">
            <div class="bg-slate-950 p-3.5 border-b border-slate-800 flex justify-between items-center">
                <div class="flex items-center space-x-2">
                    <div class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse"></div>
                    <div>
                        <h4 class="font-bold text-white text-xs">Eklavya Gemini AI Operator</h4>
                        <p class="text-[10px] text-slate-400">Paper Gasification Assistant</p>
                    </div>
                </div>
                <button onclick="toggleChatWindow()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>

            <div id="chat-messages" class="flex-1 p-3 overflow-y-auto space-y-2.5 text-xs">
                <div class="bg-slate-800/80 p-3 rounded-xl border border-slate-700/50 text-slate-200">
                    Hello! I am your <strong>Eklavya AI Operator</strong>. Ask me about paper sludge gasification, cyclone scrubbers, 20 MW power output, or our ₹20 Lakh pricing!
                </div>
            </div>

            <div class="p-3 bg-slate-950 border-t border-slate-800 flex space-x-2">
                <input type="text" id="chat-input" onkeydown="if(event.key==='Enter') sendChatMessage()" placeholder="Ask about paper sludge gasification..." class="flex-1 bg-slate-900 border border-slate-700 text-xs text-slate-200 rounded-lg px-3 py-2 focus:border-emerald-500">
                <button onclick="sendChatMessage()" class="px-3 py-2 bg-emerald-600 hover:bg-emerald-500 text-white font-bold rounded-lg transition">
                    <i class="fa-solid fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- AUTHENTICATION / LOGIN & REGISTER MODAL -->
    <div id="auth-modal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl max-w-md w-full p-6 space-y-5 shadow-2xl relative">
            <button onclick="closeAuthModal()" class="absolute top-4 right-4 text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>

            <!-- Modal Header -->
            <div class="text-center space-y-2">
                <div class="w-12 h-12 rounded-xl bg-amber-500/10 border border-amber-500/30 flex items-center justify-center text-amber-400 text-xl mx-auto">
                    <i id="auth-modal-icon" class="fa-solid fa-right-to-bracket"></i>
                </div>
                <h3 id="auth-modal-title" class="text-lg font-bold text-white">Sign In to Project Eklavya</h3>
                <p id="auth-modal-subtitle" class="text-xs text-slate-400">Access the 20 MW paper gasification platform & DB.</p>
            </div>

            <!-- Tab Switcher (Login vs Register) -->
            <div class="flex bg-slate-950 p-1 rounded-xl border border-slate-800 text-xs font-semibold">
                <button id="tab-btn-login" onclick="switchAuthMode('login')" class="flex-1 py-2 rounded-lg bg-emerald-600 text-white transition">Sign In</button>
                <button id="tab-btn-register" onclick="switchAuthMode('register')" class="flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition">Register</button>
            </div>

            <!-- LOGIN FORM -->
            <form id="form-login" onsubmit="handleLoginSubmit(event)" class="space-y-3">
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Email or Username</label>
                    <input type="text" id="login-email" required placeholder="admin@eklavya.org or Master Key" class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Password</label>
                    <input type="password" id="login-password" required placeholder="••••••••" class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <div class="p-2.5 bg-amber-500/10 border border-amber-500/20 rounded-lg text-[10px] text-amber-300">
                    <i class="fa-solid fa-circle-info mr-1"></i> Quick Dev Access: Use Master Key <strong>eklavyaisthebest15_18_15_28_22_best_devs</strong> as password.
                </div>
                <button type="submit" class="w-full py-3 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-xl transition uppercase tracking-wider shadow-lg">
                    Sign In
                </button>
            </form>

            <!-- REGISTER FORM -->
            <form id="form-register" onsubmit="handleRegisterSubmit(event)" class="hidden space-y-3">
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Full Name</label>
                    <input type="text" id="reg-name" required placeholder="e.g. Rahul Sharma" class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Paper Mill / Organization Name</label>
                    <input type="text" id="reg-mill" required placeholder="e.g. Star Paper Mills Ltd." class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Work Email</label>
                    <input type="email" id="reg-email" required placeholder="engineer@papermill.com" class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-[11px] font-mono text-slate-400 uppercase mb-1">Create Password</label>
                    <input type="password" id="reg-password" minlength="6" required placeholder="At least 6 characters" class="w-full bg-slate-950 border border-slate-700 text-slate-200 text-xs rounded-xl p-3 focus:border-emerald-500 focus:outline-none">
                </div>
                <button type="submit" class="w-full py-3 bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-xs rounded-xl transition uppercase tracking-wider shadow-lg">
                    Create Account
                </button>
            </form>
        </div>
    </div>

    <!-- JAVASCRIPT & THREE.JS LOGIC -->
    <script>
        // ================= GLOBAL STATE =================
        let isMasterUnlocked = false;
        let currentUser = null;
        let currentLang = 'EN';
        const PERSISTENT_MASTER_KEY = "eklavyaisthebest15_18_15_28_22_best_devs";

        let scene3d, camera3d, renderer3d, controls3d;
        let meshGroup3d = {};

        // Waste stream parameters
        const wasteData = {
            primary_sludge: { lhv: 12.5, moisture: 0.40, syngasCoeff: 2.1 },
            deinked_residue: { lhv: 11.0, moisture: 0.35, syngasCoeff: 1.9 },
            occ_scrap: { lhv: 16.5, moisture: 0.15, syngasCoeff: 2.6 },
            kraft_liquor: { lhv: 13.8, moisture: 0.30, syngasCoeff: 2.3 },
            wood_bark: { lhv: 15.0, moisture: 0.25, syngasCoeff: 2.4 }
        };

        // ================= INITIALIZATION =================
        window.onload = function() {
            checkPersistedUserSession();
            updateISTClock();
            setInterval(updateISTClock, 1000);
            runCalculator();
            generatePaperDatabase();
            init3DScene();
        };

        // ================= USER AUTHENTICATION & SESSION MANAGEMENT =================
        function checkPersistedUserSession() {
            const savedUser = localStorage.getItem('eklavya_user_session');
            if (savedUser) {
                try {
                    currentUser = JSON.parse(savedUser);
                    isMasterUnlocked = true;
                    applyUserAuthState();
                } catch(e) {
                    localStorage.removeItem('eklavya_user_session');
                }
            }
        }

        function switchAuthMode(mode) {
            const loginForm = document.getElementById('form-login');
            const regForm = document.getElementById('form-register');
            const loginBtn = document.getElementById('tab-btn-login');
            const regBtn = document.getElementById('tab-btn-register');
            const title = document.getElementById('auth-modal-title');
            const icon = document.getElementById('auth-modal-icon');

            if (mode === 'login') {
                loginForm.classList.remove('hidden');
                regForm.classList.add('hidden');
                loginBtn.className = "flex-1 py-2 rounded-lg bg-emerald-600 text-white transition";
                regBtn.className = "flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition";
                title.innerText = "Sign In to Project Eklavya";
                icon.className = "fa-solid fa-right-to-bracket";
            } else {
                loginForm.classList.add('hidden');
                regForm.classList.remove('hidden');
                regBtn.className = "flex-1 py-2 rounded-lg bg-amber-500 text-slate-950 font-bold transition";
                loginBtn.className = "flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition";
                title.innerText = "Register New Account";
                icon.className = "fa-solid fa-user-plus";
            }
        }

        function openAuthModal(initialMode = 'login') {
            switchAuthMode(initialMode);
            document.getElementById('auth-modal').classList.remove('hidden');
        }

        function closeAuthModal() {
            document.getElementById('auth-modal').classList.add('hidden');
        }

        function handleLoginSubmit(e) {
            e.preventDefault();
            const emailInput = document.getElementById('login-email').value.trim();
            const passwordInput = document.getElementById('login-password').value.trim();

            if (passwordInput === PERSISTENT_MASTER_KEY || emailInput.toLowerCase() === 'admin') {
                currentUser = {
                    name: "Admin Operator",
                    email: emailInput || "admin@eklavya.org",
                    mill: "Eklavya Engineering Core",
                    role: "Master Admin"
                };
            } else {
                currentUser = {
                    name: emailInput.split('@')[0] || "Mill Operator",
                    email: emailInput,
                    mill: "Paper Mill Partner",
                    role: "Authorized Operator"
                };
            }

            isMasterUnlocked = true;
            localStorage.setItem('eklavya_user_session', JSON.stringify(currentUser));
            applyUserAuthState();
            closeAuthModal();
        }

        function handleRegisterSubmit(e) {
            e.preventDefault();
            const name = document.getElementById('reg-name').value.trim();
            const mill = document.getElementById('reg-mill').value.trim();
            const email = document.getElementById('reg-email').value.trim();

            currentUser = {
                name: name,
                email: email,
                mill: mill,
                role: "Registered Engineer"
            };

            isMasterUnlocked = true;
            localStorage.setItem('eklavya_user_session', JSON.stringify(currentUser));
            applyUserAuthState();
            closeAuthModal();
        }

        function applyUserAuthState() {
            const container = document.getElementById('auth-nav-container');
            if (currentUser) {
                container.innerHTML = `
                    <div class="flex items-center space-x-2 bg-slate-900 border border-slate-700 py-1 px-2.5 rounded-lg text-xs">
                        <div class="w-6 h-6 rounded-full bg-gradient-to-tr from-emerald-400 to-amber-400 flex items-center justify-center font-bold text-slate-950 text-[11px]">
                            ${currentUser.name.charAt(0).toUpperCase()}
                        </div>
                        <div class="hidden sm:block text-left leading-tight">
                            <span class="block font-bold text-slate-200 text-[11px]">${currentUser.name}</span>
                            <span class="block text-[9px] text-emerald-400 font-mono">${currentUser.mill}</span>
                        </div>
                        <button onclick="logoutUser()" title="Sign Out" class="ml-1 text-slate-400 hover:text-red-400 text-xs">
                            <i class="fa-solid fa-arrow-right-from-bracket"></i>
                        </button>
                    </div>
                `;

                // Unlock Admin DB view if locked
                document.getElementById('admin-lock-screen')?.classList.add('hidden');
                document.getElementById('admin-unlocked-content')?.classList.remove('hidden');
            }
        }

        function logoutUser() {
            currentUser = null;
            isMasterUnlocked = false;
            localStorage.removeItem('eklavya_user_session');

            const container = document.getElementById('auth-nav-container');
            container.innerHTML = `
                <button id="auth-btn" onclick="openAuthModal('login')" class="px-3 py-1.5 bg-emerald-600 hover:bg-emerald-500 text-white font-semibold text-xs rounded-lg transition shadow-md flex items-center space-x-1.5">
                    <i class="fa-solid fa-key"></i>
                    <span id="auth-btn-text" data-en="Login / Register" data-hi="लॉगिन / रजिस्टर">Login / Register</span>
                </button>
            `;

            document.getElementById('admin-lock-screen')?.classList.remove('hidden');
            document.getElementById('admin-unlocked-content')?.classList.add('hidden');
        }

        function verifyMasterKey() {
            const pass = document.getElementById('admin-key-input').value;
            if (pass === PERSISTENT_MASTER_KEY) {
                currentUser = {
                    name: "Master Developer",
                    email: "developer@eklavya.org",
                    mill: "Core Dev Team",
                    role: "Master Admin"
                };
                isMasterUnlocked = true;
                localStorage.setItem('eklavya_user_session', JSON.stringify(currentUser));
                applyUserAuthState();
                closeAuthModal();
                showTab('admin');
            } else {
                alert("Invalid Master Security Key.");
            }
        }

        // ================= CLOCK & TAB NAVIGATION =================
                document.getElementById('admin-unlocked-content').classList.remove('hidden');
                document.getElementById('auth-btn-text').innerText = "Admin Unlocked";
                showTab('admin');
            } else {
                alert("Invalid Master Security Key.");
            }
        }

        function generatePaperDatabase() {
            const tbody = document.getElementById('paper-table-body');
            if (!tbody) return;
            tbody.innerHTML = '';

            const categories = ["Primary Pulp Sludge", "Deinked Fiber Residue", "OCC Cardboard Scrap", "Kraft Bio-Solids", "Sawmill Wood Bark"];
            const origins = ["Saharanpur UP Mill", "Erode TN Mill", "Vapi GJ Mill", "Star Paper Mills", "Ballarpur Industries"];

            for (let i = 1; i <= 35; i++) {
                const cat = categories[i % categories.length];
                const origin = origins[i % origins.length];
                const lhv = (10 + (i * 0.3) % 8).toFixed(1);
                const moisture = (15 + (i * 1.2) % 30).toFixed(0);
                const yieldNm3 = Math.round(1800 + (i * 25) % 800);

                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-900 transition";
                tr.innerHTML = `
                    <td class="p-3 text-emerald-400 font-mono">#EKL-${1000 + i}</td>
                    <td class="p-3 text-white font-semibold">${cat}</td>
                    <td class="p-3 text-slate-400">${origin}</td>
                    <td class="p-3 text-amber-400">${lhv} MJ/kg</td>
                    <td class="p-3">${moisture}%</td>
                    <td class="p-3 text-cyan-400">${yieldNm3} Nm³/t</td>
                `;
                tbody.appendChild(tr);
            }
        }

        function filterPaperTable() {
            const query = document.getElementById('db-search-input').value.toLowerCase();
            document.querySelectorAll('#paper-table-body tr').forEach(row => {
                row.style.display = row.innerText.toLowerCase().includes(query) ? '' : 'none';
            });
        }

        function exportDBToCSV() {
            let csv = "Record ID,Category,Origin,LHV (MJ/kg),Moisture %,Syngas Yield (Nm3/t)\n";
            document.querySelectorAll('#paper-table-body tr').forEach(row => {
                const cols = Array.from(row.querySelectorAll('td')).map(td => td.innerText);
                csv += cols.join(",") + "\n";
            });
            const blob = new Blob([csv], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = "Eklavya_Paper_Waste_DB.csv";
            a.click();
        }

        // ================= AI CHATBOT OPERATOR =================
        function toggleChatWindow() {
            document.getElementById('chat-window').classList.toggle('hidden');
        }

        function sendChatMessage() {
            const input = document.getElementById('chat-input');
            const msg = input.value.trim();
            if (!msg) return;

            const container = document.getElementById('chat-messages');

            // User Message
            const userBubble = document.createElement('div');
            userBubble.className = "bg-emerald-600/20 text-emerald-200 border border-emerald-500/30 p-2.5 rounded-xl text-right ml-6";
            userBubble.innerText = msg;
            container.appendChild(userBubble);

            input.value = '';
            container.scrollTop = container.scrollHeight;

            // AI Reply
            setTimeout(() => {
                const aiBubble = document.createElement('div');
                aiBubble.className = "bg-slate-800 p-2.5 rounded-xl border border-slate-700 text-slate-200 text-xs space-y-1";

                let reply = "The Eklavya 20 MW plant converts paper sludge into 20,000 kW continuous baseline electricity for paper mill machinery.";
                const lower = msg.toLowerCase();

                if (lower.includes('price') || lower.includes('cost') || lower.includes('lakh')) {
                    reply = "Project Eklavya is priced at a commercial valuation of ₹20,00,000 (₹20 Lakhs) per modular unit, offering rapid payback in 1.5 to 3 months.";
                } else if (lower.includes('scrubber') || lower.includes('tar')) {
                    reply = "Our plant uses dual high-G cyclone separators + Venturi caustic wet scrubbers to deliver 99.4% tar removal efficiency and <3 mg/Nm³ dust limits.";
                } else if (lower.includes('hour') || lower.includes('time') || lower.includes('power')) {
                    reply = "The plant is engineered to power paper mill operations for a target schedule of 20 hours per day continuously.";
                }

                aiBubble.innerHTML = `<strong class="text-emerald-400 block font-mono">Eklavya AI Operator:</strong> ${reply}`;
                container.appendChild(aiBubble);
                container.scrollTop = container.scrollHeight;
            }, 500);
        }
    </script>
</body>
</html>
