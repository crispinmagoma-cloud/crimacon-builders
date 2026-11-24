<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crimacon Builders | NCA Category 6 Construction In Kenya</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        heading: ['Plus Jakarta Sans', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace'],
                    },
                    colors: {
                        slate: {
                            850: '#172033',
                            950: '#0b1120',
                        },
                        amber: {
                            450: '#f59e0b',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        /* Architectural background grid */
        .bg-grid-pattern {
            background-size: 40px 40px;
            background-image:
                linear-gradient(to right, rgba(255, 255, 255, 0.03) 1px, transparent 1px),
                linear-gradient(to bottom, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
        }

        /* Formal print styling for Admin-generated Company Profile */
        @media print {
            body {
                background: #ffffff !important;
                color: #0f172a !important;
            }
            .no-print {
                display: none !important;
            }
            .print-only-container {
                box-shadow: none !important;
                border: none !important;
                margin: 0 !important;
                padding: 0 !important;
                max-width: 100% !important;
                width: 100% !important;
            }
            .page-break-inside-avoid {
                break-inside: avoid;
            }
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 antialiased selection:bg-amber-500 selection:text-slate-950 flex flex-col min-h-screen">

    <!-- ===================================================================== -->
    <!-- TOP HEADER BAR (CLIENT PORTAL TABS + ADMIN PORTAL LOGIN / CONTROLS)   -->
    <!-- ===================================================================== -->
    <header class="sticky top-0 z-40 bg-slate-950/95 backdrop-blur-md border-b border-slate-800 text-white no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 sm:h-20 gap-3">
                <!-- Left: Role Badge & Navigation Tabs -->
                <div class="flex items-center space-x-2 lg:space-x-4 min-w-0">
                    <span id="role-badge" class="hidden sm:inline-flex items-center px-2.5 py-1 rounded-full text-[11px] font-mono font-bold uppercase tracking-wider bg-amber-500/15 text-amber-400 border border-amber-500/30 shrink-0">
                        Client Portal • NCA 6
                    </span>

                    <!-- Client Navigation Tabs (Company Profile is intentionally hidden from clients) -->
                    <nav id="client-nav" class="hidden lg:flex items-center space-x-1" aria-label="Client Navigation">
                        <button type="button" data-tab="home" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-amber-400 bg-slate-800/90 transition-colors">Home</button>
                        <button type="button" data-tab="about" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors">About Us</button>
                        <button type="button" data-tab="services" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors">Services</button>
                        <button type="button" data-tab="projects" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors">Projects</button>
                        <button type="button" data-tab="careers" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors">Careers</button>
                        <button type="button" data-tab="contact" class="portal-tab px-3 py-2 rounded-lg text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors">Contact &amp; Quote</button>
                    </nav>

                    <!-- Admin Navigation Tabs (Visible only when logged in as Admin) -->
                    <nav id="admin-nav" class="hidden items-center space-x-1 overflow-x-auto" aria-label="Admin Navigation">
                        <button type="button" data-tab="admin-dashboard" class="portal-tab px-3 py-2 rounded-lg text-xs sm:text-sm font-semibold text-amber-400 bg-slate-800 transition-colors whitespace-nowrap">Admin CMS</button>
                        <button type="button" data-tab="admin-profile" class="portal-tab px-3 py-2 rounded-lg text-xs sm:text-sm font-semibold text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors whitespace-nowrap">Company Profile (Admin)</button>
                        <button type="button" data-tab="home" class="portal-tab px-3 py-2 rounded-lg text-xs sm:text-sm font-medium text-slate-300 hover:text-white hover:bg-slate-800/60 transition-colors whitespace-nowrap">Preview Client Site</button>
                    </nav>
                </div>

                <!-- Right: Admin Auth Controls + Official Crimacon Builders Monogram & Letterhead -->
                <div class="flex items-center space-x-3 shrink-0">
                    <div id="admin-auth-logged-out" class="flex items-center space-x-2">
                        <button type="button" id="open-admin-login-btn" class="px-3 py-2 rounded-lg text-xs sm:text-sm font-semibold text-slate-200 hover:text-white bg-slate-800 hover:bg-slate-700 border border-slate-700 transition-colors">
                            Admin Login
                        </button>
                        <button type="button" id="header-quote-btn" class="hidden sm:inline-flex items-center px-3.5 py-2 rounded-lg text-xs sm:text-sm font-semibold text-slate-950 bg-amber-500 hover:bg-amber-400 transition-colors shadow-lg shadow-amber-500/20">
                            Get Quote
                        </button>
                    </div>

                    <div id="admin-auth-logged-in" class="hidden items-center space-x-2">
                        <span class="hidden xl:inline-block text-xs font-mono text-emerald-400">Admin Active</span>
                        <button type="button" id="admin-logout-btn" class="px-3 py-2 rounded-lg text-xs sm:text-sm font-semibold text-rose-300 hover:text-white bg-rose-950/60 hover:bg-rose-900 border border-rose-800/70 transition-colors">
                            Sign Out
                        </button>
                    </div>

                    <!-- Right-Aligned Crimacon Builders Brand Mark -->
                    <button type="button" id="brand-home-btn" class="flex items-center space-x-2.5 text-right group focus:outline-none">
                        <div class="leading-tight">
                            <span class="block font-heading font-extrabold text-sm sm:text-base tracking-tight text-white group-hover:text-amber-400 transition-colors">
                                CRIMACON<span class="text-amber-500">.</span>
                            </span>
                            <span class="block font-mono text-[10px] text-amber-400/90 uppercase tracking-wider">
                                NCA 6 • Across th country
                            </span>
                        </div>
                        <div class="w-9 h-9 sm:w-10 sm:h-10 rounded-lg bg-amber-500/10 border border-amber-500/40 flex items-center justify-center shrink-0">
                            <svg class="w-5 h-5 sm:w-6 sm:h-6 text-amber-400" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M6 12L18 5L30 12V25L18 32L6 25V12Z" stroke="currentColor" stroke-width="2.2" stroke-linejoin="round"/>
                                <path d="M22 14.5C20.8 13.3 19.2 12.8 17.5 13C14.8 13.3 13 15.5 13 18.5C13 21.5 14.8 23.7 17.5 24C19.2 24.2 20.8 23.7 22 22.5" stroke="currentColor" stroke-width="2.4" stroke-linecap="round"/>
                                <path d="M18 8V11M18 26V29" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
                            </svg>
                        </div>
                    </button>

                    <!-- Mobile Menu Toggle -->
                    <button type="button" id="mobile-menu-btn" class="lg:hidden p-2 rounded-lg text-slate-300 hover:text-white hover:bg-slate-800 transition-colors" aria-label="Toggle Menu">
                        <svg id="menu-icon-open" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
                        </svg>
                        <svg id="menu-icon-close" class="w-6 h-6 hidden" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                        </svg>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Navigation Drawer -->
        <div id="mobile-menu" class="hidden lg:hidden bg-slate-900 border-b border-slate-800 px-4 pt-2 pb-5 space-y-1">
            <div id="mobile-client-links" class="space-y-1">
                <button type="button" data-tab="home" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-amber-400 bg-slate-800">Home</button>
                <button type="button" data-tab="about" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-slate-300 hover:text-white hover:bg-slate-800">About Us</button>
                <button type="button" data-tab="services" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-slate-300 hover:text-white hover:bg-slate-800">Services</button>
                <button type="button" data-tab="projects" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-slate-300 hover:text-white hover:bg-slate-800">Projects</button>
                <button type="button" data-tab="careers" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-slate-300 hover:text-white hover:bg-slate-800">Careers</button>
                <button type="button" data-tab="contact" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-medium text-slate-300 hover:text-white hover:bg-slate-800">Contact &amp; Quote</button>
            </div>
            <div id="mobile-admin-links" class="hidden space-y-1 pt-2 border-t border-slate-800">
                <button type="button" data-tab="admin-dashboard" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-semibold text-amber-400 bg-slate-800">Admin CMS Dashboard</button>
                <button type="button" data-tab="admin-profile" class="mobile-nav-link block w-full text-left px-3 py-2.5 rounded-lg text-base font-semibold text-slate-200 hover:bg-slate-800">Auto-Generate Company Profile (Admin)</button>
            </div>
        </div>
    </header>

    <!-- ===================================================================== -->
    <!-- MAIN APPLICATION CONTAINER                                            -->
    <!-- ===================================================================== -->
    <main class="flex-grow">

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 1: HOME (CLIENT LANDING VIEW)                                 -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-home" class="tab-view">
            <div class="relative bg-slate-950 text-white overflow-hidden bg-grid-pattern">
                <div class="absolute -top-24 -right-24 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16 sm:py-24 relative z-10">
                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                        <div class="lg:col-span-7 space-y-6">
                            <div class="inline-flex items-center space-x-2 px-3 py-1.5 rounded-full bg-amber-500/10 border border-amber-500/30 text-amber-300 text-xs font-mono uppercase tracking-wider">
                                <span class="w-2 h-2 rounded-full bg-amber-400 animate-pulse"></span>
                                <span>NCA Category 6 • Countrywide</span>
                            </div>

                            <h1 class="font-heading font-extrabold text-3xl sm:text-5xl lg:text-[3.35rem] tracking-tight leading-[1.12] text-white">
                                Offering Construction Services Across  <span class="text-amber-400">the Country</span> With Precision &amp; Integrity.
                            </h1>

                            <p class="text-base sm:text-lg text-slate-300 leading-relaxed max-w-2xl">
                                <strong class="text-white">Crimacon Builders</strong> is an <strong class="text-amber-300">NCA Category 6</strong> registered building construction, civil engineering, Water works, Electrical works, and Project management contractor delivering turnkey,Design and Build Residential, commercial, and infrastructure projects nationwide. Direct line &amp; WhatsApp: <strong class="text-white font-mono">0797521481</strong>.
                            </p>

                            <div class="flex flex-col sm:flex-row gap-3.5 pt-2">
                                <button type="button" data-jump-tab="contact" class="inline-flex items-center justify-center px-6 py-3.5 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm sm:text-base transition-all shadow-lg shadow-amber-500/25">
                                    Request Quote
                                    <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
                                    </svg>
                                </button>
                                <button type="button" data-jump-tab="projects" class="inline-flex items-center justify-center px-6 py-3.5 rounded-lg bg-slate-800/90 hover:bg-slate-800 text-white font-heading font-semibold text-sm sm:text-base border border-slate-700 transition-colors">
                                    Explore Live Projects
                                </button>
                            </div>

                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3.5 pt-6 border-t border-slate-800">
                                <div class="flex items-start space-x-3 bg-slate-900/70 p-3.5 rounded-xl border border-slate-800">
                                    <div class="w-10 h-10 rounded-lg bg-amber-500/15 text-amber-400 flex items-center justify-center shrink-0 font-mono font-bold text-xs">
                                        NCA 6
                                    </div>
                                    <div>
                                        <p class="font-heading font-bold text-white text-sm">NCA Category 6 Registered</p>
                                        <p class="text-xs text-slate-400">Compliant building &amp; civil engineering contractor</p>
                                    </div>
                                </div>
                                <div class="flex items-start space-x-3 bg-slate-900/70 p-3.5 rounded-xl border border-slate-800">
                                    <div class="w-10 h-10 rounded-lg bg-amber-500/15 text-amber-400 flex items-center justify-center shrink-0 font-mono font-bold text-xs">
                                        47
                                    </div>
                                    <div>
                                        <p class="font-heading font-bold text-white text-sm">All 47 Counties Mobilization</p>
                                        <p class="text-xs text-slate-400">Nairobi, Coast, Rift, Central, Nyanza &amp; Western</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Right Summary Card -->
                        <div class="lg:col-span-5">
                            <div class="bg-slate-900/95 border border-slate-800 rounded-2xl p-6 sm:p-7 shadow-2xl space-y-5">
                                <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                                    <div class="text-left">
                                        <span class="text-[11px] font-mono uppercase tracking-wider text-amber-400">Direct Client Desk</span>
                                        <p class="font-mono text-lg font-bold text-white">0797521481</p>
                                        <p class="text-xs text-slate-400">+254797521481 • Call &amp; WhatsApp</p>
                                    </div>
                                    <div class="text-right">
                                        <p class="font-heading font-extrabold text-white text-base">CRIMACON BUILDERS</p>
                                        <p class="font-mono text-[11px] text-amber-400">NCA CATEGORY 6</p>
                                    </div>
                                </div>

                                <div class="space-y-3 text-sm text-slate-300">
                                    <div class="flex items-center justify-between py-1.5 border-b border-slate-800/70">
                                        <span class="text-slate-400">Core Disciplines</span>
                                        <span class="font-semibold text-white">Building, Civil, Steel &amp; QS</span>
                                    </div>
                                    <div class="flex items-center justify-between py-1.5 border-b border-slate-800/70">
                                        <span class="text-slate-400">Material Standard</span>
                                        <span class="font-semibold text-amber-300">KEBS-Certified Spec</span>
                                    </div>
                                    <div class="flex items-center justify-between py-1.5">
                                        <span class="text-slate-400">Geographic Footprint</span>
                                        <span class="font-semibold text-white">Nationwide (47 Counties)</span>
                                    </div>
                                </div>

                                <div class="bg-amber-500/10 border border-amber-500/25 rounded-xl p-4 text-xs text-slate-200 leading-relaxed">
                                    Need a preliminary cost estimate in KES or site mobilization anywhere in Kenya? Use our instant estimator or toggle the bottom-right WhatsApp chat (<strong class="text-amber-300 font-mono">0797521481</strong>).
                                </div>

                                <div class="grid grid-cols-2 gap-3">
                                    <button type="button" data-jump-tab="services" class="py-2.5 px-3 rounded-lg bg-slate-800 hover:bg-slate-700 text-white text-xs font-semibold transition-colors">
                                        View Services
                                    </button>
                                    <button type="button" data-jump-tab="careers" class="py-2.5 px-3 rounded-lg bg-amber-500/20 hover:bg-amber-500/30 text-amber-300 border border-amber-500/40 text-xs font-semibold transition-colors">
                                        Open Careers
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Featured Projects Strip on Home -->
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-14 space-y-10">
                <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-4">
                    <div>
                        <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Featured Portfolio</span>
                        <h2 class="font-heading font-extrabold text-2xl sm:text-3xl text-slate-900 mt-1">Recent &amp; Ongoing Projects Across Kenya</h2>
                    </div>
                    <button type="button" data-jump-tab="projects" class="text-sm font-semibold text-amber-700 hover:text-amber-800 inline-flex items-center">
                        See all projects &amp; filter <span class="ml-1">&rarr;</span>
                    </button>
                </div>
                <div id="home-featured-projects" class="grid grid-cols-1 md:grid-cols-3 gap-6"></div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 2: ABOUT US (VISION, MISSION, VALUES, SUMMARY & LEADERSHIP)   -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-about" class="tab-view hidden py-14 sm:py-20">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-14">
                <div class="bg-white rounded-2xl border border-slate-200 p-6 sm:p-10 shadow-sm">
                    <div class="flex flex-col md:flex-row md:items-start justify-between gap-6 border-b border-slate-200 pb-6">
                        <div class="max-w-2xl">
                            <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">About Crimacon Builders</span>
                            <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-slate-900 mt-1">Engineering Excellence Across All 47 Counties</h2>
                            <p class="text-slate-600 mt-3 leading-relaxed">
                                Registered under <strong class="text-slate-900">NCA Category 6</strong>, Crimacon Builders delivers turnkey residential housing, commercial structures, civil &amp;   Design and Build projects, and project management across Kenya. Direct desk: <strong class="font-mono text-slate-900">0797521481</strong>.
                            </p>
                        </div>
                        <div class="md:text-right shrink-0">
                            <p class="font-heading font-extrabold text-xl text-slate-900">CRIMACON BUILDERS<span class="text-amber-600">.</span></p>
                            <p class="font-mono text-xs text-amber-700 font-bold">NCA CATEGORY 6 CONTRACTOR</p>
                            <p class="text-xs text-slate-500 mt-0.5">Tel / WhatsApp: 0797521481</p>
                        </div>
                    </div>

                    <!-- Executive Summary -->
                    <div class="mt-6">
                        <h3 class="font-heading font-bold text-lg text-slate-900 mb-2">Executive Summary</h3>
                        <p class="text-sm sm:text-base text-slate-600 leading-relaxed">
                            Crimacon Builders is an NCA Category 6 registered building construction and civil engineering firm serving private homeowners, corporate developers, institutions, and county/public stakeholders across  Kenya. We combine structured site engineering, transparent Bills of Quantities (BOQs), nationwide supply chain logistics, and KEBS-compliant materials to deliver resilient assets on schedule.
                        </p>
                    </div>

                    <!-- Vision & Mission -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-8">
                        <div class="p-6 rounded-xl bg-slate-900 text-white">
                            <span class="font-mono text-xs uppercase tracking-wider text-amber-400">Our Vision</span>
                            <h4 class="font-heading font-bold text-xl mt-1 mb-2">Kenya’s Trusted Nationwide Builder</h4>
                            <p class="text-sm text-slate-300 leading-relaxed">
                                To be Kenya’s most trusted, innovative, and dependable NCA Category 6 building and civil engineering contractor across all 47 counties—setting benchmarks in structural durability, cost transparency, and client satisfaction.
                            </p>
                        </div>
                        <div class="p-6 rounded-xl bg-amber-50 border border-amber-200 text-slate-900">
                            <span class="font-mono text-xs uppercase tracking-wider text-amber-700 font-bold">Our Mission</span>
                            <h4 class="font-heading font-bold text-xl mt-1 mb-2">Safe, Quality-Assured Delivery</h4>
                            <p class="text-sm text-slate-700 leading-relaxed">
                                To execute residential, civil, structural steel, and infrastructure projects on time and within budget using KEBS-certified materials, skilled engineering teams, rigorous site supervision, and ethical business practices.
                            </p>
                        </div>
                    </div>

                    <!-- Core Values -->
                    <div class="mt-8">
                        <h3 class="font-heading font-bold text-lg text-slate-900 mb-4">Core Values</h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">1. Structural Integrity &amp; Quality</p>
                                <p class="text-xs text-slate-600 mt-1">Uncompromising adherence to NCA 6 engineering standards, structural mixes, and KEBS-tested inputs.</p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">2. Cost Transparency &amp; Accountability</p>
                                <p class="text-xs text-slate-600 mt-1">Clear BOQs, milestone reporting, and honest procurement with zero hidden markups.</p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">3. Safety First (OSHA &amp; NCA)</p>
                                <p class="text-xs text-slate-600 mt-1">PPE compliance, safe scaffolding/excavation practices, and environmental care on every site.</p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">4. Nationwide Agility</p>
                                <p class="text-xs text-slate-600 mt-1">Rapid mobilization and material haulage across urban and rural counties throughout Kenya.</p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">5. Timely Handover</p>
                                <p class="text-xs text-slate-600 mt-1">Disciplined project scheduling and proactive site supervision to hit agreed completion dates.</p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-900 text-sm">6. Client-Centered Partnership</p>
                                <p class="text-xs text-slate-600 mt-1">Responsive communication from initial BOQ and site visit through post-handover support.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Executive & Management Team -->
                <div class="space-y-6">
                    <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-2">
                        <div>
                            <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Leadership &amp; Governance</span>
                            <h3 class="font-heading font-extrabold text-2xl sm:text-3xl text-slate-900 mt-1">Executive &amp; Management Team</h3>
                        </div>
                        <p class="text-xs font-mono text-slate-500">Live roster synced with Admin Portal</p>
                    </div>
                    <div id="client-team-grid" class="grid grid-cols-1 md:grid-cols-3 gap-6"></div>
                </div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 3: SERVICES & KEBS MATERIAL STANDARDS                          -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-services" class="tab-view hidden py-14 sm:py-20 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-14">
                <div class="max-w-3xl">
                    <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Engineering Capabilities</span>
                    <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-slate-900 mt-1">Comprehensive Construction Across Kenya</h2>
                    <p class="text-slate-600 mt-2">
                        Every discipline is executed under NCA Category 6 supervision and Kenyan KEBS-approved material specifications.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="p-6 sm:p-8 rounded-2xl bg-slate-50 border border-slate-200 space-y-3">
                        <span class="font-mono text-xs font-bold text-amber-700 uppercase">01 • Building Works</span>
                        <h3 class="font-heading font-bold text-xl text-slate-900">Residential Housing, Estates &amp; Villas</h3>
                        <p class="text-sm text-slate-600 leading-relaxed">
                            Turnkey construction of modern homes, bungalows, maisonettes, multi-unit housing estates, coastal villas, and commercial buildings across all 47 counties.
                        </p>
                        <ul class="text-xs text-slate-700 space-y-1.5 pt-2 border-t border-slate-200">
                            <li>• Reinforced concrete frames, slabs, columns &amp; masonry</li>
                            <li>• Comply & timsales / high-gloss MDF kitchens, wardrobes &amp; finishes</li>
                            <li>• Twyford / Micasso porcelain tiles, Mazeras stone &amp; black granite</li>
                        </ul>
                    </div>

                    <div class="p-6 sm:p-8 rounded-2xl bg-slate-50 border border-slate-200 space-y-3">
                        <span class="font-mono text-xs font-bold text-amber-700 uppercase">02 • Civil Engineering</span>
                        <h3 class="font-heading font-bold text-xl text-slate-900">Cabro Paving, Earthworks &amp; Drainage</h3>
                        <p class="text-sm text-slate-600 leading-relaxed">
                            Heavy-duty interlocking concrete cabro paving, site grading, access roads, perimeter walls, and reinforced stormwater drainage systems.
                        </p>
                        <ul class="text-xs text-slate-700 space-y-1.5 pt-2 border-t border-slate-200">
                            <li>• 60mm &amp; 80mm cabro blocks on compacted murram/hardcore</li>
                            <li>• Reinforced concrete invert block drains, culverts &amp; kerbs</li>
                            <li>• Commercial yard, petrol station &amp; estate road works</li>
                        </ul>
                    </div>

                    <div class="p-6 sm:p-8 rounded-2xl bg-slate-50 border border-slate-200 space-y-3">
                        <span class="font-mono text-xs font-bold text-amber-700 uppercase">03 • Structural &amp; MEP</span>
                        <h3 class="font-heading font-bold text-xl text-slate-900">Structural Steel, Water Towers &amp; Plumbing</h3>
                        <p class="text-sm text-slate-600 leading-relaxed">
                            Elevated steel water tank towers, steel portal structures, water reticulation, and certified electrical/plumbing installations.
                        </p>
                        <ul class="text-xs text-slate-700 space-y-1.5 pt-2 border-t border-slate-200">
                            <li>• Elevated steel tank towers (1,000L to 50,000L+)</li>
                            <li>• Danco PPR piping &amp; Pegler Class 2 brass gate valves</li>
                            <li>• Havells MCBs/MCCBs &amp; East African / ASL cables</li>
                        </ul>
                    </div>

                    <div class="p-6 sm:p-8 rounded-2xl bg-slate-50 border border-slate-200 space-y-3">
                        <span class="font-mono text-xs font-bold text-amber-700 uppercase">04 • Commercial &amp; QS</span>
                        <h3 class="font-heading font-bold text-xl text-slate-900">Quantity Surveying, BOQs &amp; Project Control</h3>
                        <p class="text-sm text-slate-600 leading-relaxed">
                            Accurate cost engineering, measured Bills of Quantities (BOQs), tender pricing, stage valuations, and site schedule management.
                        </p>
                        <ul class="text-xs text-slate-700 space-y-1.5 pt-2 border-t border-slate-200">
                            <li>• Elemental &amp; trade BOQ preparation and verification</li>
                            <li>• Nationwide haulage &amp; material rate benchmarking</li>
                            <li>• Weekly progress reporting &amp; quality sign-offs</li>
                        </ul>
                    </div>
                </div>

                <!-- Kenyan KEBS Material Standards -->
                <div class="rounded-2xl bg-slate-950 text-white p-6 sm:p-10 border border-slate-800">
                    <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b border-slate-800 pb-6 mb-6">
                        <div>
                            <span class="font-mono text-xs uppercase tracking-widest text-amber-400">Quality Assurance</span>
                            <h3 class="font-heading font-bold text-2xl mt-1">Approved Kenyan KEBS Material Specifications</h3>
                        </div>
                        <span class="font-mono text-xs text-slate-400">Enforced Across All 47 Counties</span>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 text-xs">
                        <div class="p-4 rounded-xl bg-slate-900 border border-slate-800">
                            <p class="font-mono font-bold text-amber-400">Plumbing &amp; Valves</p>
                            <p class="text-slate-200 font-semibold mt-1">Danco PPR Pipes &amp; Pegler Class 2 Gate Valves</p>
                            <p class="text-slate-400 mt-1">Pressure-rated hot/cold water lines and durable brass isolation valves.</p>
                        </div>
                        <div class="p-4 rounded-xl bg-slate-900 border border-slate-800">
                            <p class="font-mono font-bold text-amber-400">Electrical &amp; Switchgear</p>
                            <p class="text-slate-200 font-semibold mt-1">Havells MCBs/MCCBs &amp; East African / ASL Cables</p>
                            <p class="text-slate-400 mt-1">KEBS-certified conductors and safe circuit protection assemblies.</p>
                        </div>
                        <div class="p-4 rounded-xl bg-slate-900 border border-slate-800">
                            <p class="font-mono font-bold text-amber-400">Tiles &amp; Joinery</p>
                            <p class="text-slate-200 font-semibold mt-1">Twyford / Micasso Porcelain &amp; Comply / High-Gloss MDF</p>
                            <p class="text-slate-400 mt-1">High-wear floor/wall tiling and precision-fitted cabinetry.</p>
                        </div>
                        <div class="p-4 rounded-xl bg-slate-900 border border-slate-800">
                            <p class="font-mono font-bold text-amber-400">Stone &amp; Countertops</p>
                            <p class="text-slate-200 font-semibold mt-1">Mazeras Stonework &amp; Black Granite</p>
                            <p class="text-slate-400 mt-1">Weather-resistant natural stone accents and durable kitchen tops.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 4: PROJECTS & PHOTO GALLERY (CLIENT VIEW)                     -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-projects" class="tab-view hidden py-14 sm:py-20">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-12">
                <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6">
                    <div>
                        <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Live Project Portfolio</span>
                        <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-slate-900 mt-1">Completed &amp; Ongoing Works</h2>
                        <p class="text-slate-600 mt-1.5">Updated live from Crimacon Builders project records across Kenya.</p>
                    </div>

                    <div class="flex flex-wrap gap-2" id="project-filter-bar">
                        <button type="button" data-filter="All" class="project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-slate-900 text-white transition-colors">All Projects</button>
                        <button type="button" data-filter="Residential" class="project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200 transition-colors">Residential</button>
                        <button type="button" data-filter="Civil & Paving" class="project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200 transition-colors">Civil &amp; Paving</button>
                        <button type="button" data-filter="Infrastructure" class="project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200 transition-colors">Infrastructure</button>
                    </div>
                </div>

                <div id="client-projects-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"></div>

                <div class="pt-6 border-t border-slate-200 space-y-6">
                    <div>
                        <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Visual Archive</span>
                        <h3 class="font-heading font-extrabold text-2xl text-slate-900 mt-1">Site &amp; Engineering Photo Gallery</h3>
                    </div>
                    <div id="client-gallery-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5"></div>
                </div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 5: CAREERS PORTAL (CLIENT VIEW)                                -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-careers" class="tab-view hidden py-14 sm:py-20">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-10">
                <div class="max-w-3xl">
                    <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Join Our Team</span>
                    <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-slate-900 mt-1">Current Job Opportunities</h2>
                    <p class="text-slate-600 mt-2">
                        We recruit competent engineers, quantity surveyors, site foremen, and procurement specialists for projects across Kenya’s 47 counties.
                    </p>
                </div>

                <div id="client-jobs-grid" class="grid grid-cols-1 md:grid-cols-2 gap-6"></div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 6: CONTACT, KES COST ESTIMATOR & QUOTE REQUEST (CLIENT VIEW)   -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-contact" class="tab-view hidden py-14 sm:py-20">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-12">
                <div>
                    <span class="font-mono text-xs font-bold uppercase tracking-widest text-amber-600">Nationwide Mobilization &amp; Estimates</span>
                    <h2 class="font-heading font-extrabold text-3xl sm:text-4xl text-slate-900 mt-1">KES Cost Estimator &amp; Quote Desk</h2>
                    <p class="text-slate-600 mt-1.5">
                        Calculate a preliminary Kenyan Shilling estimate across regions and submit your project scope directly to our team or call/WhatsApp <strong class="font-mono text-slate-900">0797521481</strong>.
                    </p>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
                    <!-- KES Preliminary Cost Estimator -->
                    <div class="lg:col-span-6 bg-slate-950 text-white rounded-2xl p-6 sm:p-8 border border-slate-800 space-y-5">
                        <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                            <div>
                                <span class="font-mono text-xs uppercase tracking-wider text-amber-400">Interactive Tool</span>
                                <h3 class="font-heading font-bold text-xl mt-0.5">Preliminary KES Estimator</h3>
                            </div>
                            <span class="font-mono text-xs px-2.5 py-1 rounded bg-slate-800 text-amber-300">NCA 6 Guide</span>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="est-scope" class="block text-xs font-semibold text-slate-300 mb-1.5">Project Scope</label>
                                <select id="est-scope" class="w-full px-3.5 py-2.5 rounded-lg bg-slate-900 border border-slate-700 text-sm text-white focus:outline-none focus:border-amber-400">
                                    <option value="residential" data-rate="46000">Residential / Mansionette (per m²)</option>
                                    <option value="cabro" data-rate="2850">Cabro Paving &amp; Drainage (per m²)</option>
                                    <option value="steel" data-rate="32000">Structural Steel / Tower (per unit/m²)</option>
                                </select>
                            </div>
                            <div>
                                <label for="est-region" class="block text-xs font-semibold text-slate-300 mb-1.5">County / Region Zone</label>
                                <select id="est-region" class="w-full px-3.5 py-2.5 rounded-lg bg-slate-900 border border-slate-700 text-sm text-white focus:outline-none focus:border-amber-400">
                                    <option value="1.00">Nairobi &amp; Central Corridor (1.00x)</option>
                                    <option value="1.06">Rift Valley &amp; Eastern (1.06x)</option>
                                    <option value="1.09">Coast Region (1.09x)</option>
                                    <option value="1.11">Western, Nyanza &amp; Northern (1.11x)</option>
                                </select>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label for="est-area" class="block text-xs font-semibold text-slate-300 mb-1.5">Estimated Area / Scale (m²)</label>
                                <input id="est-area" type="number" min="10" max="50000" value="180" class="w-full px-3.5 py-2.5 rounded-lg bg-slate-900 border border-slate-700 text-sm text-white font-mono focus:outline-none focus:border-amber-400">
                            </div>
                            <div>
                                <label for="est-tier" class="block text-xs font-semibold text-slate-300 mb-1.5">Finish &amp; Spec Tier</label>
                                <select id="est-tier" class="w-full px-3.5 py-2.5 rounded-lg bg-slate-900 border border-slate-700 text-sm text-white focus:outline-none focus:border-amber-400">
                                    <option value="0.90">Standard KEBS Spec (0.90x)</option>
                                    <option value="1.00" selected>Executive / Recommended (1.00x)</option>
                                    <option value="1.22">Premium Finishes &amp; Stone (1.22x)</option>
                                </select>
                            </div>
                        </div>

                        <div class="p-5 rounded-xl bg-slate-900 border border-amber-500/30">
                            <p class="text-xs font-mono uppercase tracking-wider text-slate-400">Indicative Estimate Range (KES)</p>
                            <p id="est-result-range" class="font-heading font-extrabold text-2xl sm:text-3xl text-amber-400 mt-1">KES 7,452,000 – KES 9,108,000</p>
                            <p class="text-xs text-slate-400 mt-1.5">Includes indicative regional haulage; final figures depend on site soil tests, architectural drawings, and priced BOQ.</p>
                        </div>

                        <button type="button" id="apply-estimate-btn" class="w-full py-3 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors">
                            Attach Estimate to Quote Form &rarr;
                        </button>
                    </div>

                    <!-- Quote Request & Direct Contact Form -->
                    <div class="lg:col-span-6 bg-white rounded-2xl p-6 sm:p-8 border border-slate-200 shadow-sm space-y-5">
                        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-slate-200 pb-4">
                            <div>
                                <h3 class="font-heading font-bold text-xl text-slate-900">Submit Project Inquiry / Quote</h3>
                                <p class="text-xs text-slate-500">Direct line &amp; WhatsApp: <strong class="font-mono text-slate-800">0797521481</strong> (+254797521481)</p>
                            </div>
                            <span class="text-xs font-mono font-bold text-amber-700 bg-amber-50 px-2.5 py-1 rounded border border-amber-200">47 Counties</span>
                        </div>

                        <form id="client-quote-form" class="space-y-4">
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                                <div>
                                    <label for="quote-name" class="block text-xs font-semibold text-slate-700 mb-1">Full Name / Organization *</label>
                                    <input id="quote-name" type="text" required placeholder="e.g. Eng. Samuel Kamau" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                                </div>
                                <div>
                                    <label for="quote-phone" class="block text-xs font-semibold text-slate-700 mb-1">Phone / WhatsApp *</label>
                                    <input id="quote-phone" type="tel" required placeholder="e.g. 0712345678" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                                </div>
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                                <div>
                                    <label for="quote-county" class="block text-xs font-semibold text-slate-700 mb-1">Project County / Location *</label>
                                    <input id="quote-county" type="text" required placeholder="e.g. Kiambu, Nakuru, Mombasa" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                                </div>
                                <div>
                                    <label for="quote-email" class="block text-xs font-semibold text-slate-700 mb-1">Email Address</label>
                                    <input id="quote-email" type="email" placeholder="client@example.com" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                                </div>
                            </div>
                            <div>
                                <label for="quote-details" class="block text-xs font-semibold text-slate-700 mb-1">Scope, Timeline &amp; Notes *</label>
                                <textarea id="quote-details" rows="3" required placeholder="Describe your building, cabro paving, structural steel, or BOQ requirement..." class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500"></textarea>
                            </div>
                            <button type="submit" class="w-full py-3 px-4 rounded-lg bg-slate-900 hover:bg-slate-800 text-white font-heading font-bold text-sm transition-colors">
                                Send Quote Request
                            </button>
                        </form>

                        <div id="quote-confirmation" class="hidden p-4 rounded-xl bg-emerald-50 border border-emerald-200 text-emerald-900 text-xs sm:text-sm"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 7: ADMIN PORTAL CMS DASHBOARD (LOGIN-GATED)                    -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-admin-dashboard" class="tab-view hidden py-12 sm:py-16">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-10">
                <div class="bg-slate-950 text-white rounded-2xl p-6 sm:p-8 border border-slate-800 flex flex-col lg:flex-row lg:items-center justify-between gap-6">
                    <div>
                        <div class="inline-flex items-center space-x-2 px-2.5 py-1 rounded-full bg-emerald-500/15 border border-emerald-500/30 text-emerald-300 text-xs font-mono">
                            <span>Authenticated Administrator • Crimacon Builders (NCA 6)</span>
                        </div>
                        <h2 class="font-heading font-extrabold text-2xl sm:text-3xl mt-2">Admin Content &amp; Operations Portal</h2>
                        <p class="text-sm text-slate-300 mt-1">
                            Add or edit projects, publish job vacancies, upload photos, update executive/management leaders, or open the exclusive <strong class="text-amber-400">Company Profile Generator</strong>.
                        </p>
                    </div>
                    <div class="flex flex-wrap gap-3">
                        <button type="button" data-jump-tab="admin-profile" class="px-4 py-2.5 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-xs sm:text-sm transition-colors">
                            Auto-Generate Company Profile &rarr;
                        </button>
                        <button type="button" id="reset-demo-data-btn" class="px-4 py-2.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-200 border border-slate-700 font-semibold text-xs sm:text-sm transition-colors">
                            Reset Default Data
                        </button>
                    </div>
                </div>

                <!-- Admin Sub-Tabs -->
                <div class="flex flex-wrap gap-2 border-b border-slate-200 pb-3" id="admin-cms-subtabs">
                    <button type="button" data-cms-tab="projects" class="cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-slate-900 text-white">Projects Manager</button>
                    <button type="button" data-cms-tab="jobs" class="cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200">Job Opportunities</button>
                    <button type="button" data-cms-tab="photos" class="cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200">Photo Gallery</button>
                    <button type="button" data-cms-tab="team" class="cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200">Executive &amp; Management</button>
                </div>

                <!-- CMS PANEL A: PROJECTS MANAGER -->
                <div id="cms-panel-projects" class="cms-panel grid grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-5 bg-white rounded-2xl p-6 border border-slate-200 shadow-sm h-fit">
                        <h3 id="project-form-heading" class="font-heading font-bold text-lg text-slate-900 mb-4">Add New Project</h3>
                        <form id="admin-project-form" class="space-y-3.5">
                            <input type="hidden" id="proj-edit-id">
                            <div>
                                <label for="proj-title" class="block text-xs font-semibold text-slate-700 mb-1">Project Title *</label>
                                <input id="proj-title" type="text" required placeholder="e.g. Kisumu Commercial & Cabro Yard" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                <div>
                                    <label for="proj-location" class="block text-xs font-semibold text-slate-700 mb-1">County / Location *</label>
                                    <input id="proj-location" type="text" required placeholder="e.g. Kisumu County" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                                </div>
                                <div>
                                    <label for="proj-category" class="block text-xs font-semibold text-slate-700 mb-1">Category *</label>
                                    <select id="proj-category" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm bg-white">
                                        <option value="Residential">Residential</option>
                                        <option value="Civil & Paving">Civil &amp; Paving</option>
                                        <option value="Infrastructure">Infrastructure</option>
                                    </select>
                                </div>
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                <div>
                                    <label for="proj-status" class="block text-xs font-semibold text-slate-700 mb-1">Status *</label>
                                    <select id="proj-status" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm bg-white">
                                        <option value="Completed">Completed</option>
                                        <option value="Ongoing">Ongoing</option>
                                    </select>
                                </div>
                                <div>
                                    <label for="proj-budget" class="block text-xs font-semibold text-slate-700 mb-1">Indicative Value / Scale</label>
                                    <input id="proj-budget" type="text" placeholder="e.g. KES 18.5M • 2,400m²" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                                </div>
                            </div>
                            <div>
                                <label for="proj-photo-select" class="block text-xs font-semibold text-slate-700 mb-1">Select from Photo Gallery or Custom URL</label>
                                <select id="proj-photo-select" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm bg-white mb-2"></select>
                                <input id="proj-photo-url" type="text" placeholder="Or paste image URL (https://...)" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="proj-scope" class="block text-xs font-semibold text-slate-700 mb-1">Engineering Scope &amp; Specs *</label>
                                <textarea id="proj-scope" rows="3" required placeholder="Describe structural works, finishes, or civil engineering deliverables..." class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm"></textarea>
                            </div>
                            <div class="flex gap-2 pt-1">
                                <button type="submit" id="proj-submit-btn" class="flex-1 py-2.5 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors">
                                    Save Project
                                </button>
                                <button type="button" id="proj-cancel-edit-btn" class="hidden py-2.5 px-3 rounded-lg bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-semibold">
                                    Cancel
                                </button>
                            </div>
                        </form>
                    </div>

                    <div class="lg:col-span-7 space-y-4">
                        <h3 class="font-heading font-bold text-lg text-slate-900">Published Projects (<span id="admin-proj-count">0</span>)</h3>
                        <div id="admin-projects-list" class="space-y-3"></div>
                    </div>
                </div>

                <!-- CMS PANEL B: JOB OPPORTUNITIES MANAGER -->
                <div id="cms-panel-jobs" class="cms-panel hidden grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-5 bg-white rounded-2xl p-6 border border-slate-200 shadow-sm h-fit">
                        <h3 id="job-form-heading" class="font-heading font-bold text-lg text-slate-900 mb-4">Post Job Opportunity</h3>
                        <form id="admin-job-form" class="space-y-3.5">
                            <input type="hidden" id="job-edit-id">
                            <div>
                                <label for="job-title" class="block text-xs font-semibold text-slate-700 mb-1">Job Title *</label>
                                <input id="job-title" type="text" required placeholder="e.g. Senior Site Civil Engineer" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                                <div>
                                    <label for="job-dept" class="block text-xs font-semibold text-slate-700 mb-1">Department *</label>
                                    <input id="job-dept" type="text" required placeholder="e.g. Civil & Structural" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                                </div>
                                <div>
                                    <label for="job-location" class="block text-xs font-semibold text-slate-700 mb-1">Location / County *</label>
                                    <input id="job-location" type="text" required placeholder="e.g. Nationwide / Nakuru" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                                </div>
                            </div>
                            <div>
                                <label for="job-type" class="block text-xs font-semibold text-slate-700 mb-1">Employment Type *</label>
                                <select id="job-type" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm bg-white">
                                    <option value="Full-Time">Full-Time</option>
                                    <option value="Contract / Project-Based">Contract / Project-Based</option>
                                    <option value="Consultant">Consultant</option>
                                </select>
                            </div>
                            <div>
                                <label for="job-summary" class="block text-xs font-semibold text-slate-700 mb-1">Role Summary &amp; Qualifications *</label>
                                <textarea id="job-summary" rows="3" required placeholder="Specify qualifications, NCA/EBK/IQSK experience, and key duties..." class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm"></textarea>
                            </div>
                            <div class="flex gap-2 pt-1">
                                <button type="submit" class="flex-1 py-2.5 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors">
                                    Save Job Opening
                                </button>
                                <button type="button" id="job-cancel-edit-btn" class="hidden py-2.5 px-3 rounded-lg bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-semibold">
                                    Cancel
                                </button>
                            </div>
                        </form>
                    </div>

                    <div class="lg:col-span-7 space-y-4">
                        <h3 class="font-heading font-bold text-lg text-slate-900">Active Job Listings (<span id="admin-job-count">0</span>)</h3>
                        <div id="admin-jobs-list" class="space-y-3"></div>
                    </div>
                </div>

                <!-- CMS PANEL C: PHOTO GALLERY MANAGER -->
                <div id="cms-panel-photos" class="cms-panel hidden grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-5 bg-white rounded-2xl p-6 border border-slate-200 shadow-sm h-fit">
                        <h3 id="photo-form-heading" class="font-heading font-bold text-lg text-slate-900 mb-4">Add Project / Site Photo</h3>
                        <form id="admin-photo-form" class="space-y-3.5">
                            <input type="hidden" id="photo-edit-id">
                            <div>
                                <label for="photo-caption" class="block text-xs font-semibold text-slate-700 mb-1">Photo Caption / Title *</label>
                                <input id="photo-caption" type="text" required placeholder="e.g. Heavy-Duty Cabro Court — Eldoret" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="photo-tag" class="block text-xs font-semibold text-slate-700 mb-1">Category Tag *</label>
                                <input id="photo-tag" type="text" required placeholder="e.g. Civil & Paving / Residential" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="photo-file" class="block text-xs font-semibold text-slate-700 mb-1">Upload Photo File (PNG / JPG / WebP)</label>
                                <input id="photo-file" type="file" accept="image/*" class="w-full text-xs text-slate-600 file:mr-3 file:py-2 file:px-3 file:rounded-lg file:border-0 file:text-xs file:font-semibold file:bg-amber-50 file:text-amber-700 hover:file:bg-amber-100">
                            </div>
                            <div>
                                <label for="photo-url" class="block text-xs font-semibold text-slate-700 mb-1">Or Image URL</label>
                                <input id="photo-url" type="text" placeholder="https://images.unsplash.com/..." class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div class="flex gap-2 pt-1">
                                <button type="submit" class="flex-1 py-2.5 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors">
                                    Save Photo
                                </button>
                                <button type="button" id="photo-cancel-edit-btn" class="hidden py-2.5 px-3 rounded-lg bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-semibold">
                                    Cancel
                                </button>
                            </div>
                        </form>
                    </div>

                    <div class="lg:col-span-7 space-y-4">
                        <h3 class="font-heading font-bold text-lg text-slate-900">Media Gallery (<span id="admin-photo-count">0</span>)</h3>
                        <div id="admin-photos-list" class="grid grid-cols-1 sm:grid-cols-2 gap-4"></div>
                    </div>
                </div>

                <!-- CMS PANEL D: EXECUTIVE & MANAGEMENT TEAM MANAGER -->
                <div id="cms-panel-team" class="cms-panel hidden grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-5 bg-white rounded-2xl p-6 border border-slate-200 shadow-sm h-fit">
                        <h3 id="team-form-heading" class="font-heading font-bold text-lg text-slate-900 mb-4">Add Executive / Management Leader</h3>
                        <form id="admin-team-form" class="space-y-3.5">
                            <input type="hidden" id="team-edit-id">
                            <div>
                                <label for="team-name" class="block text-xs font-semibold text-slate-700 mb-1">Full Name *</label>
                                <input id="team-name" type="text" required placeholder="e.g. Eng. Peter Mwangi" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="team-role" class="block text-xs font-semibold text-slate-700 mb-1">Title / Role *</label>
                                <input id="team-role" type="text" required placeholder="e.g. Managing Director • NCA 6 Lead" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="team-photo" class="block text-xs font-semibold text-slate-700 mb-1">Portrait URL (Optional)</label>
                                <input id="team-photo" type="text" placeholder="https://..." class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm">
                            </div>
                            <div>
                                <label for="team-bio" class="block text-xs font-semibold text-slate-700 mb-1">Bio &amp; Credentials *</label>
                                <textarea id="team-bio" rows="3" required placeholder="Summarize engineering background, project leadership, and NCA 6 governance..." class="w-full px-3 py-2 rounded-lg border border-slate-300 text-sm"></textarea>
                            </div>
                            <div class="flex gap-2 pt-1">
                                <button type="submit" class="flex-1 py-2.5 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors">
                                    Save Leader
                                </button>
                                <button type="button" id="team-cancel-edit-btn" class="hidden py-2.5 px-3 rounded-lg bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-semibold">
                                    Cancel
                                </button>
                            </div>
                        </form>
                    </div>

                    <div class="lg:col-span-7 space-y-4">
                        <h3 class="font-heading font-bold text-lg text-slate-900">Executive &amp; Management Roster (<span id="admin-team-count">0</span>)</h3>
                        <div id="admin-team-list" class="space-y-3"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ----------------------------------------------------------------- -->
        <!-- TAB 8: AUTO-GENERATED FORMAL COMPANY PROFILE (ADMIN-ONLY)          -->
        <!-- ----------------------------------------------------------------- -->
        <section id="view-admin-profile" class="tab-view hidden py-10 sm:py-14">
            <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 space-y-6">
                <div class="bg-slate-900 text-white rounded-2xl p-5 sm:p-6 border border-slate-800 no-print space-y-4">
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b border-slate-800 pb-4">
                        <div>
                            <span class="font-mono text-xs uppercase tracking-wider text-amber-400">Admin-Exclusive Document Generator</span>
                            <h2 class="font-heading font-extrabold text-2xl mt-0.5">Auto-Generated Formal Company Profile</h2>
                            <p class="text-xs text-slate-300 mt-0.5">Restricted exclusively to authenticated Crimacon Builders administrators; hidden from clients.</p>
                        </div>
                        <button type="button" id="print-company-profile-btn" class="inline-flex items-center justify-center px-5 py-2.5 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm transition-colors shrink-0">
                            Print / Save Formal PDF
                        </button>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3.5">
                        <div>
                            <label for="prof-recipient" class="block text-xs font-semibold text-slate-300 mb-1">Prepared For / Procuring Entity</label>
                            <input id="prof-recipient" type="text" value="Prospective Client / Tender Committee" class="w-full px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 text-xs sm:text-sm text-white">
                        </div>
                        <div>
                            <label for="prof-ref" class="block text-xs font-semibold text-slate-300 mb-1">Document / Tender Reference</label>
                            <input id="prof-ref" type="text" value="CB/NCA6/PROF-47C" class="w-full px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 text-xs sm:text-sm text-white font-mono">
                        </div>
                        <div>
                            <label for="prof-region" class="block text-xs font-semibold text-slate-300 mb-1">Target County / Region</label>
                            <input id="prof-region" type="text" value="All 47 Counties (Republic of Kenya)" class="w-full px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 text-xs sm:text-sm text-white">
                        </div>
                        <div>
                            <label for="prof-focus" class="block text-xs font-semibold text-slate-300 mb-1">Primary Focus Area</label>
                            <select id="prof-focus" class="w-full px-3 py-2 rounded-lg bg-slate-800 border border-slate-700 text-xs sm:text-sm text-white">
                                <option value="full">Turnkey Building, Civil &amp; Structural</option>
                                <option value="building">Residential, Estates &amp; Villas</option>
                                <option value="civil">Cabro Paving &amp; Civil Works</option>
                                <option value="steel">Structural Steel &amp; Water Works</option>
                            </select>
                        </div>
                    </div>
                </div>

                <!-- Formal Corporate Document Sheet (Letterhead on Right) -->
                <article class="bg-white text-slate-900 rounded-2xl border border-slate-300 shadow-lg p-6 sm:p-10 lg:p-12 print-only-container space-y-8">
                    <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-6 border-b-2 border-slate-900 pb-6">
                        <div class="text-xs font-mono text-slate-600 space-y-1">
                            <p><strong class="text-slate-900">PREPARED FOR:</strong> <span id="doc-recipient">Prospective Client / Tender Committee</span></p>
                            <p><strong class="text-slate-900">REF NO:</strong> <span id="doc-ref">CB/NCA6/PROF-47C</span></p>
                            <p><strong class="text-slate-900">COVERAGE:</strong> <span id="doc-region">All 47 Counties (Republic of Kenya)</span></p>
                            <p><strong class="text-slate-900">DIRECT LINE / WHATSAPP:</strong> 0797521481 (+254797521481)</p>
                        </div>

                        <div class="sm:text-right flex items-center sm:justify-end space-x-3">
                            <div>
                                <h1 class="font-heading font-extrabold text-2xl sm:text-3xl tracking-tight text-slate-950">
                                    CRIMACON BUILDERS<span class="text-amber-600">.</span>
                                </h1>
                                <p class="font-mono text-xs font-bold uppercase tracking-wider text-amber-700">
                                    Building Contractors &amp; Civil Engineers • NCA Category 6
                                </p>
                                <p class="text-xs text-slate-600 mt-0.5">
                                    Nationwide Operations Across All 47 Counties of Kenya
                                </p>
                            </div>
                            <div class="w-12 h-12 rounded-lg bg-slate-950 text-amber-400 flex items-center justify-center font-mono font-bold text-xs shrink-0">
                                NCA 6
                            </div>
                        </div>
                    </div>

                    <div class="space-y-2 page-break-inside-avoid">
                        <h2 class="font-heading font-bold text-base uppercase tracking-wider text-slate-950 border-b border-slate-200 pb-1">
                            1. Executive Summary
                        </h2>
                        <p id="doc-exec-summary" class="text-sm text-slate-700 leading-relaxed"></p>
                    </div>

                    <div class="space-y-4 page-break-inside-avoid">
                        <h2 class="font-heading font-bold text-base uppercase tracking-wider text-slate-950 border-b border-slate-200 pb-1">
                            2. Vision, Mission &amp; Core Values
                        </h2>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-xs sm:text-sm">
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-950">Vision</p>
                                <p class="text-slate-700 mt-1 leading-relaxed">
                                    To be Kenya’s trusted NCA Category 6 building and civil engineering contractor across all 47 counties, delivering durable infrastructure and transparent project execution.
                                </p>
                            </div>
                            <div class="p-4 rounded-xl bg-slate-50 border border-slate-200">
                                <p class="font-heading font-bold text-slate-950">Mission</p>
                                <p class="text-slate-700 mt-1 leading-relaxed">
                                    To deliver residential, commercial, cabro paving, structural steel, and infrastructure works on time and within budget using KEBS-certified materials and disciplined site engineering.
                                </p>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 sm:grid-cols-3 gap-2.5 text-xs">
                            <div class="p-3 rounded-lg border border-slate-200"><strong>Integrity &amp; Quality:</strong> NCA 6 &amp; KEBS compliance</div>
                            <div class="p-3 rounded-lg border border-slate-200"><strong>Cost Clarity:</strong> Transparent BOQs &amp; milestones</div>
                            <div class="p-3 rounded-lg border border-slate-200"><strong>Safety First:</strong> OSHA &amp; site risk control</div>
                            <div class="p-3 rounded-lg border border-slate-200"><strong>47-County Reach:</strong> Nationwide mobilization</div>
                            <div class="p-3 rounded-lg border border-slate-200"><strong>Timeliness:</strong> Disciplined schedule control</div>
                            <div class="p-3 rounded-lg border border-slate-200"><strong>Reliability:</strong> Responsive client partnership</div>
                        </div>
                    </div>

                    <div class="space-y-3 page-break-inside-avoid">
                        <h2 class="font-heading font-bold text-base uppercase tracking-wider text-slate-950 border-b border-slate-200 pb-1">
                            3. Executive &amp; Management Team
                        </h2>
                        <div id="doc-team-list" class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs"></div>
                    </div>

                    <div class="space-y-3 page-break-inside-avoid">
                        <h2 class="font-heading font-bold text-base uppercase tracking-wider text-slate-950 border-b border-slate-200 pb-1">
                            4. Approved KEBS Specifications &amp; Representative Projects
                        </h2>
                        <p class="text-xs text-slate-700 leading-relaxed">
                            <strong>Approved Material Standards:</strong> Danco PPR pipes, Pegler Class 2 gate valves, Havells MCBs/MCCBs, East African / ASL cables, Twyford / Micasso porcelain tiles, Comply / high-gloss MDF cabinetry, Mazeras stonework, and black granite.
                        </p>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse text-xs">
                                <thead>
                                    <tr class="bg-slate-100 border-b border-slate-300">
                                        <th class="p-2.5 font-bold">Project</th>
                                        <th class="p-2.5 font-bold">Location</th>
                                        <th class="p-2.5 font-bold">Category</th>
                                        <th class="p-2.5 font-bold">Status</th>
                                    </tr>
                                </thead>
                                <tbody id="doc-projects-tbody" class="divide-y divide-slate-200"></tbody>
                            </table>
                        </div>
                    </div>

                    <div class="pt-4 border-t-2 border-slate-900 flex flex-col sm:flex-row sm:items-end justify-between gap-4 text-xs page-break-inside-avoid">
                        <div class="font-mono text-slate-600 space-y-1">
                            <p>Registration: NCA Category 6 (NCA 6)</p>
                            <p>Contact &amp; WhatsApp: 0797521481 (+254797521481)</p>
                        </div>
                        <div class="sm:text-right">
                            <p class="font-heading font-bold text-slate-950">For: Crimacon Builders</p>
                            <p class="text-slate-500 font-mono mt-1">Authorized Management Signatory</p>
                        </div>
                    </div>
                </article>
            </div>
        </section>

    </main>

    <!-- ===================================================================== -->
    <!-- FOOTER                                                                -->
    <!-- ===================================================================== -->
    <footer class="bg-slate-950 text-slate-400 border-t border-slate-800 py-10 mt-auto no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs">
            <div>
                <p class="font-heading font-bold text-white text-sm">CRIMACON BUILDERS<span class="text-amber-500">.</span></p>
                <p class="font-mono text-slate-500 mt-0.5">NCA Category 6 • All 47 Counties of Kenya • Tel/WhatsApp: 0797521481</p>
            </div>
            <div class="flex items-center space-x-4 font-mono">
                <button type="button" id="footer-admin-trigger" class="text-amber-400 hover:text-amber-300 underline underline-offset-4">
                    Admin Portal Login
                </button>
                <span>&copy; <span id="footer-year"></span> Crimacon Builders</span>
            </div>
        </div>
    </footer>

    <!-- ===================================================================== -->
    <!-- ADMIN LOGIN MODAL                                                     -->
    <!-- ===================================================================== -->
    <div id="admin-login-modal" class="fixed inset-0 z-50 hidden items-center justify-center bg-slate-950/80 backdrop-blur-sm p-4 no-print">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 sm:p-7 shadow-2xl border border-slate-200 space-y-4">
            <div class="flex items-start justify-between">
                <div>
                    <span class="font-mono text-xs font-bold uppercase text-amber-600">Restricted Access</span>
                    <h3 class="font-heading font-bold text-xl text-slate-900">Crimacon Admin Portal</h3>
                </div>
                <button type="button" id="close-admin-login-btn" class="text-slate-400 hover:text-slate-700 text-lg font-bold px-2">&times;</button>
            </div>

            <div class="p-3 rounded-lg bg-amber-50 border border-amber-200 text-xs text-amber-950 font-mono">
                <p class="font-bold">Admin Sign-In Credentials:</p>
                <p>Email: <strong>admin@crimaconbuilders.co.ke</strong></p>
                <p>Password: <strong>CrimaconNCA6</strong></p>
            </div>

            <form id="admin-login-form" class="space-y-3.5">
                <div>
                    <label for="admin-email-input" class="block text-xs font-semibold text-slate-700 mb-1">Admin Email</label>
                    <input id="admin-email-input" type="email" required value="admin@crimaconbuilders.co.ke" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                </div>
                <div>
                    <label for="admin-password-input" class="block text-xs font-semibold text-slate-700 mb-1">Password</label>
                    <input id="admin-password-input" type="password" required value="CrimaconNCA6" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm focus:outline-none focus:border-amber-500">
                </div>
                <p id="admin-login-error" class="hidden text-xs font-semibold text-rose-600">Invalid admin credentials. Please check email and password.</p>
                <button type="submit" class="w-full py-2.5 px-4 rounded-lg bg-slate-900 hover:bg-slate-800 text-white font-heading font-bold text-sm transition-colors">
                    Sign In to Admin Portal
                </button>
            </form>
        </div>
    </div>

    <!-- ===================================================================== -->
    <!-- JOB APPLICATION MODAL                                                 -->
    <!-- ===================================================================== -->
    <div id="job-apply-modal" class="fixed inset-0 z-50 hidden items-center justify-center bg-slate-950/80 backdrop-blur-sm p-4 no-print">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 shadow-2xl border border-slate-200 space-y-4">
            <div class="flex items-start justify-between">
                <div>
                    <span class="font-mono text-xs font-bold uppercase text-amber-600">Careers Application</span>
                    <h3 id="apply-modal-role" class="font-heading font-bold text-lg text-slate-900">Apply for Role</h3>
                </div>
                <button type="button" id="close-job-apply-btn" class="text-slate-400 hover:text-slate-700 text-lg font-bold px-2">&times;</button>
            </div>
            <form id="job-apply-form" class="space-y-3">
                <input id="apply-name" type="text" required placeholder="Your Full Name *" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm">
                <input id="apply-phone" type="tel" required placeholder="Phone / WhatsApp (e.g. 0797521481) *" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm">
                <textarea id="apply-notes" rows="3" required placeholder="Brief summary of qualifications & experience *" class="w-full px-3.5 py-2.5 rounded-lg border border-slate-300 text-sm"></textarea>
                <button type="submit" class="w-full py-2.5 px-4 rounded-lg bg-amber-500 hover:bg-amber-400 text-slate-950 font-heading font-bold text-sm">
                    Submit Application
                </button>
            </form>
            <div id="job-apply-success" class="hidden p-3 rounded-lg bg-emerald-50 border border-emerald-200 text-xs text-emerald-900 font-medium"></div>
        </div>
    </div>

    <!-- ===================================================================== -->
    <!-- PROMINENT BOTTOM-RIGHT WHATSAPP TOGGLE & LIVE CHAT DRAWER             -->
    <!-- ===================================================================== -->
    <div class="fixed bottom-5 right-5 z-50 no-print flex flex-col items-end">
        <!-- Expandable Quick-Chat Box -->
        <div id="wa-chat-panel" class="hidden mb-3 w-80 sm:w-96 bg-white rounded-2xl shadow-2xl border border-slate-200 overflow-hidden">
            <div class="bg-[#075E54] text-white px-4 py-3.5 flex items-center justify-between">
                <div class="flex items-center space-x-2.5">
                    <span class="w-2.5 h-2.5 rounded-full bg-[#25D366] ring-2 ring-white/40"></span>
                    <div>
                        <p class="font-heading font-bold text-sm leading-tight">Crimacon Builders WhatsApp</p>
                        <p class="text-[11px] text-emerald-100 font-mono">+254797521481 (0797521481) • NCA 6</p>
                    </div>
                </div>
                <button type="button" id="wa-close-btn" aria-label="Close WhatsApp Drawer" class="text-white/80 hover:text-white text-xl font-bold px-1.5 leading-none">&times;</button>
            </div>

            <div class="p-4 bg-[#efeae2] space-y-3">
                <div class="bg-white p-3 rounded-xl rounded-tl-none shadow-sm text-xs text-slate-700 leading-relaxed">
                    Karibu! Reach <strong>Crimacon Builders</strong> on WhatsApp for nationwide construction across all 47 counties, BOQs, cabro paving, structural steel, or site visits.
                </div>

                <!-- Quick Topic Chips -->
                <div class="flex flex-wrap gap-1.5">
                    <button type="button" data-wa-msg="Hello Crimacon Builders (NCA 6), I need a project quote across Kenya." class="wa-preset-btn text-[11px] bg-white hover:bg-emerald-50 text-slate-800 px-2.5 py-1 rounded-full border border-slate-200 font-medium transition-colors">
                        Project Quote
                    </button>
                    <button type="button" data-wa-msg="Hello Crimacon Builders, I would like to inquire about cabro paving & civil works." class="wa-preset-btn text-[11px] bg-white hover:bg-emerald-50 text-slate-800 px-2.5 py-1 rounded-full border border-slate-200 font-medium transition-colors">
                        Cabro &amp; Civil
                    </button>
                    <button type="button" data-wa-msg="Hello Crimacon Builders, I am inquiring about structural steel / water tower works." class="wa-preset-btn text-[11px] bg-white hover:bg-emerald-50 text-slate-800 px-2.5 py-1 rounded-full border border-slate-200 font-medium transition-colors">
                        Steel &amp; Water
                    </button>
                    <button type="button" data-wa-msg="Hello Crimacon Builders, I am inquiring about current job opportunities." class="wa-preset-btn text-[11px] bg-white hover:bg-emerald-50 text-slate-800 px-2.5 py-1 rounded-full border border-slate-200 font-medium transition-colors">
                        Careers
                    </button>
                </div>

                <textarea id="wa-message-input" rows="2" aria-label="WhatsApp Message" class="w-full px-3 py-2 rounded-lg border border-slate-300 text-xs text-slate-800 bg-white focus:outline-none focus:border-[#25D366]">Hello Crimacon Builders, I would like to inquire about a construction project.</textarea>

                <a id="wa-send-link" href="https://wa.me/254797521481?text=Hello%20Crimacon%20Builders%2C%20I%20would%20like%20to%20inquire%20about%20a%20construction%20project." target="_blank" rel="noopener noreferrer" class="w-full py-2.5 px-4 rounded-lg bg-[#25D366] hover:bg-[#20bd5a] text-slate-950 font-heading font-bold text-xs sm:text-sm flex items-center justify-center shadow transition-colors">
                    Open WhatsApp (+254797521481) &rarr;
                </a>
            </div>
        </div>

        <!-- High-Visibility Bottom-Right WhatsApp Toggle Button -->
        <button type="button" id="wa-toggle-btn" aria-expanded="false" aria-controls="wa-chat-panel" class="flex items-center space-x-2.5 px-4 py-3 rounded-full bg-[#25D366] hover:bg-[#20bd5a] text-slate-950 font-heading font-bold text-xs sm:text-sm shadow-2xl ring-2 ring-white/80 transition-all hover:scale-105">
            <svg class="w-5 h-5 fill-current shrink-0" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M12.031 2c-5.516 0-9.969 4.453-9.969 9.969 0 1.766.469 3.484 1.344 5l-1.406 5.141 5.266-1.375c1.469.797 3.109 1.219 4.766 1.219 5.516 0 9.969-4.453 9.969-9.969s-4.453-9.985-9.969-9.985zm5.813 14.156c-.25.703-1.438 1.344-1.984 1.422-.516.078-1.172.109-1.891-.125-.438-.141-1-.328-1.766-.656-3.109-1.344-5.141-4.484-5.297-4.688-.156-.203-1.266-1.688-1.266-3.219 0-1.531.797-2.281 1.078-2.594.281-.313.625-.391.828-.391.203 0 .406 0 .594.016.188.016.438-.078.688.516.25.609.859 2.094.938 2.25.078.156.125.344.016.547-.109.203-.156.328-.313.516-.156.188-.328.406-.469.547-.156.156-.328.328-.141.641.188.313.828 1.359 1.781 2.203 1.219 1.094 2.25 1.438 2.563 1.594.313.156.5.125.688-.078.188-.203.797-.938 1.016-1.25.219-.313.422-.266.719-.156.297.109 1.891.891 2.219 1.047.328.156.547.234.625.375.078.141.078.813-.172 1.516z"/>
            </svg>
            <span id="wa-toggle-label">WhatsApp • 0797521481</span>
        </button>
    </div>

    <!-- ===================================================================== -->
    <!-- APPLICATION STATE, ACCESS CONTROL & RENDERING ENGINE                  -->
    <!-- ===================================================================== -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const STORAGE_KEY = 'crimacon_dual_portal_v1';
            const AUTH_KEY = 'crimacon_admin_auth_v1';
            const WHATSAPP_NUMBER = '254797521481';
            const ADMIN_EMAIL = 'admin@crimaconbuilders.co.ke';
            const ADMIN_PASS = 'CrimaconNCA6';

            const DEFAULT_STATE = {
                projects: [
                    {
                        id: 'p1',
                        title: 'Modern 4-Bedroom Suburban Mansionette',
                        location: 'Kiambu County',
                        category: 'Residential',
                        status: 'Completed',
                        budget: 'KES 14.8M • 240m²',
                        photo: 'https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=900&q=80',
                        scope: 'Turnkey residence featuring Twyford / Micasso porcelain tiling, Comply high-gloss MDF cabinetry, black granite kitchen countertops, and Danco PPR plumbing.'
                    },
                    {
                        id: 'p2',
                        title: 'Heavy-Duty Cabro Paving & Stormwater Drainage',
                        location: 'Murang’a County',
                        category: 'Civil & Paving',
                        status: 'Completed',
                        budget: 'KES 9.6M • 3,100m²',
                        photo: 'https://images.unsplash.com/photo-1581094794329-c8112a89af12?auto=format&fit=crop&w=900&q=80',
                        scope: 'Compacted murram sub-base, 80mm heavy-duty interlocking cabro blocks, precast kerbs, and reinforced concrete drainage channels.'
                    },
                    {
                        id: 'p3',
                        title: 'Elevated Structural Steel Water Tower & Reticulation',
                        location: 'Nakuru County',
                        category: 'Infrastructure',
                        status: 'Ongoing',
                        budget: 'KES 6.2M • 20,000L',
                        photo: 'https://images.unsplash.com/photo-1504307651254-35680f356dfd?auto=format&fit=crop&w=900&q=80',
                        scope: 'Reinforced concrete footing, structural steel tower fabrication, Pegler Class 2 gate valves, and Havells switchgear integration.'
                    },
                    {
                        id: 'p4',
                        title: 'Coastal Villa with Mazeras Stonework',
                        location: 'Mombasa County',
                        category: 'Residential',
                        status: 'Ongoing',
                        budget: 'KES 22.0M • 360m²',
                        photo: 'https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?auto=format&fit=crop&w=900&q=80',
                        scope: 'Marine-resilient coastal residence combining natural Mazeras stone cladding, East African / ASL cable wiring, and custom timber joinery.'
                    }
                ],
                jobs: [
                    {
                        id: 'j1',
                        title: 'Site Civil & Structural Engineer',
                        department: 'Engineering & Site Operations',
                        location: 'Nationwide (47 Counties)',
                        type: 'Full-Time',
                        summary: 'BSc/BEng in Civil or Structural Engineering with experience in reinforced concrete, cabro paving, and NCA 6 site quality control.'
                    },
                    {
                        id: 'j2',
                        title: 'Project Quantity Surveyor (QS)',
                        department: 'Commercial & BOQs',
                        location: 'Nairobi & Regional Sites',
                        type: 'Full-Time',
                        summary: 'Degree/Diploma in Quantity Surveying experienced in BOQ preparation, valuation certificates, and nationwide material cost tracking.'
                    },
                    {
                        id: 'j3',
                        title: 'General Building & Finishes Foreman',
                        department: 'Site Supervision',
                        location: 'Central, Rift & Coast',
                        type: 'Contract / Project-Based',
                        summary: 'Hands-on site foreman skilled in masonry, roofing, cabro laying, and supervising KEBS-certified finishing trades.'
                    }
                ],
                photos: [
                    {
                        id: 'ph1',
                        caption: 'Contemporary Residential Villa Elevation',
                        tag: 'Residential',
                        url: 'https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=900&q=80'
                    },
                    {
                        id: 'ph2',
                        caption: 'Civil Engineering & Site Works',
                        tag: 'Civil & Paving',
                        url: 'https://images.unsplash.com/photo-1581094794329-c8112a89af12?auto=format&fit=crop&w=900&q=80'
                    },
                    {
                        id: 'ph3',
                        caption: 'Structural Steel & Site Supervision',
                        tag: 'Infrastructure',
                        url: 'https://images.unsplash.com/photo-1504307651254-35680f356dfd?auto=format&fit=crop&w=900&q=80'
                    },
                    {
                        id: 'ph4',
                        caption: 'Architectural Courtyard & Exterior Finishes',
                        tag: 'Residential',
                        url: 'https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?auto=format&fit=crop&w=900&q=80'
                    }
                ],
                team: [
                    {
                        id: 't1',
                        name: 'Eng. Samuel Kariuki',
                        role: 'Managing Director • NCA 6 Lead',
                        photo: 'https://images.unsplash.com/photo-1560250097-0b93528c311a?auto=format&fit=crop&w=500&q=80',
                        bio: 'Leads corporate strategy, nationwide mobilization across all 47 counties, and NCA Category 6 regulatory compliance.'
                    },
                    {
                        id: 't2',
                        name: 'QS. Faith Wanjiku',
                        role: 'Head of Quantity Surveying & Contracts',
                        photo: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?auto=format&fit=crop&w=500&q=80',
                        bio: 'Oversees BOQ engineering, tender submissions, procurement audits, and milestone cost control.'
                    },
                    {
                        id: 't3',
                        name: 'David Otieno',
                        role: 'Operations & Logistics Manager',
                        photo: 'https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?auto=format&fit=crop&w=500&q=80',
                        bio: 'Coordinates site superintendents, equipment dispatch, and KEBS-certified material deliveries nationwide.'
                    }
                ]
            };

            function loadState() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEY);
                    if (!raw) return JSON.parse(JSON.stringify(DEFAULT_STATE));
                    const parsed = JSON.parse(raw);
                    return {
                        projects: Array.isArray(parsed.projects) ? parsed.projects : DEFAULT_STATE.projects,
                        jobs: Array.isArray(parsed.jobs) ? parsed.jobs : DEFAULT_STATE.jobs,
                        photos: Array.isArray(parsed.photos) ? parsed.photos : DEFAULT_STATE.photos,
                        team: Array.isArray(parsed.team) ? parsed.team : DEFAULT_STATE.team
                    };
                } catch (err) {
                    return JSON.parse(JSON.stringify(DEFAULT_STATE));
                }
            }

            function saveState() {
                try {
                    localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));
                } catch (err) {
                    // Ignore storage write errors
                }
            }

            let appState = loadState();
            let isAdminAuthenticated = sessionStorage.getItem(AUTH_KEY) === 'true';
            let activeTab = 'home';
            let activeProjectFilter = 'All';

            const yearEl = document.getElementById('footer-year');
            if (yearEl) yearEl.textContent = new Date().getFullYear();

            // -----------------------------------------------------------------
            // ACCESS CONTROL & TAB NAVIGATION
            // -----------------------------------------------------------------
            function isAdminOnlyTab(tabName) {
                return tabName === 'admin-dashboard' || tabName === 'admin-profile';
            }

            function setActiveTab(tabName) {
                if (isAdminOnlyTab(tabName) && !isAdminAuthenticated) {
                    openAdminLoginModal();
                    return;
                }

                activeTab = tabName;

                document.querySelectorAll('.tab-view').forEach((section) => {
                    const id = section.id.replace('view-', '');
                    section.classList.toggle('hidden', id !== tabName);
                });

                document.querySelectorAll('.portal-tab').forEach((btn) => {
                    const isCurrent = btn.dataset.tab === tabName;
                    btn.classList.toggle('text-amber-400', isCurrent);
                    btn.classList.toggle('bg-slate-800/90', isCurrent);
                    btn.classList.toggle('text-slate-300', !isCurrent);
                });

                const mobileMenu = document.getElementById('mobile-menu');
                mobileMenu.classList.add('hidden');
                document.getElementById('menu-icon-open').classList.remove('hidden');
                document.getElementById('menu-icon-close').classList.add('hidden');

                if (tabName === 'admin-profile') {
                    renderAdminCompanyProfile();
                }

                window.scrollTo({ top: 0, behavior: 'smooth' });
            }

            function syncAuthUI() {
                const badge = document.getElementById('role-badge');
                const clientNav = document.getElementById('client-nav');
                const adminNav = document.getElementById('admin-nav');
                const loggedOutBox = document.getElementById('admin-auth-logged-out');
                const loggedInBox = document.getElementById('admin-auth-logged-in');
                const mobileClientLinks = document.getElementById('mobile-client-links');
                const mobileAdminLinks = document.getElementById('mobile-admin-links');

                if (isAdminAuthenticated) {
                    badge.textContent = 'Admin Portal • Authenticated';
                    badge.className = 'hidden sm:inline-flex items-center px-2.5 py-1 rounded-full text-[11px] font-mono font-bold uppercase tracking-wider bg-emerald-500/15 text-emerald-300 border border-emerald-500/30 shrink-0';
                    clientNav.classList.add('hidden');
                    clientNav.classList.remove('lg:flex');
                    adminNav.classList.remove('hidden');
                    adminNav.classList.add('flex');
                    loggedOutBox.classList.add('hidden');
                    loggedInBox.classList.remove('hidden');
                    loggedInBox.classList.add('flex');
                    mobileClientLinks.classList.add('hidden');
                    mobileAdminLinks.classList.remove('hidden');
                } else {
                    badge.textContent = 'Client Portal • NCA 6';
                    badge.className = 'hidden sm:inline-flex items-center px-2.5 py-1 rounded-full text-[11px] font-mono font-bold uppercase tracking-wider bg-amber-500/15 text-amber-400 border border-amber-500/30 shrink-0';
                    clientNav.classList.remove('hidden');
                    clientNav.classList.add('lg:flex');
                    adminNav.classList.add('hidden');
                    adminNav.classList.remove('flex');
                    loggedOutBox.classList.remove('hidden');
                    loggedInBox.classList.add('hidden');
                    loggedInBox.classList.remove('flex');
                    mobileClientLinks.classList.remove('hidden');
                    mobileAdminLinks.classList.add('hidden');

                    if (isAdminOnlyTab(activeTab)) {
                        setActiveTab('home');
                    }
                }
            }

            document.querySelectorAll('.portal-tab, .mobile-nav-link, [data-jump-tab]').forEach((el) => {
                el.addEventListener('click', () => {
                    const targetTab = el.dataset.tab || el.dataset.jumpTab;
                    if (targetTab) setActiveTab(targetTab);
                });
            });

            document.getElementById('brand-home-btn').addEventListener('click', () => setActiveTab('home'));
            document.getElementById('header-quote-btn').addEventListener('click', () => setActiveTab('contact'));

            const mobileMenuBtn = document.getElementById('mobile-menu-btn');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuBtn.addEventListener('click', () => {
                const willOpen = mobileMenu.classList.contains('hidden');
                mobileMenu.classList.toggle('hidden', !willOpen);
                document.getElementById('menu-icon-open').classList.toggle('hidden', willOpen);
                document.getElementById('menu-icon-close').classList.toggle('hidden', !willOpen);
            });

            // -----------------------------------------------------------------
            // ADMIN LOGIN & LOGOUT
            // -----------------------------------------------------------------
            const loginModal = document.getElementById('admin-login-modal');
            const loginError = document.getElementById('admin-login-error');

            function openAdminLoginModal() {
                loginError.classList.add('hidden');
                loginModal.classList.remove('hidden');
                loginModal.classList.add('flex');
            }

            function closeAdminLoginModal() {
                loginModal.classList.add('hidden');
                loginModal.classList.remove('flex');
            }

            document.getElementById('open-admin-login-btn').addEventListener('click', openAdminLoginModal);
            document.getElementById('footer-admin-trigger').addEventListener('click', () => {
                if (isAdminAuthenticated) {
                    setActiveTab('admin-dashboard');
                } else {
                    openAdminLoginModal();
                }
            });
            document.getElementById('close-admin-login-btn').addEventListener('click', closeAdminLoginModal);

            document.getElementById('admin-login-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const email = document.getElementById('admin-email-input').value.trim().toLowerCase();
                const pass = document.getElementById('admin-password-input').value;

                if (email === ADMIN_EMAIL.toLowerCase() && pass === ADMIN_PASS) {
                    isAdminAuthenticated = true;
                    sessionStorage.setItem(AUTH_KEY, 'true');
                    closeAdminLoginModal();
                    syncAuthUI();
                    renderAll();
                    setActiveTab('admin-dashboard');
                } else {
                    loginError.classList.remove('hidden');
                }
            });

            document.getElementById('admin-logout-btn').addEventListener('click', () => {
                isAdminAuthenticated = false;
                sessionStorage.removeItem(AUTH_KEY);
                syncAuthUI();
                setActiveTab('home');
            });

            // -----------------------------------------------------------------
            // CLIENT RENDERERS
            // -----------------------------------------------------------------
            const FALLBACK_IMG = 'https://placehold.co/800x500/0f172a/f59e0b?text=Crimacon+Builders+(NCA+6)';

            function renderClientProjects() {
                const filtered = activeProjectFilter === 'All'
                    ? appState.projects
                    : appState.projects.filter((p) => p.category === activeProjectFilter);

                const grid = document.getElementById('client-projects-grid');
                if (!filtered.length) {
                    grid.innerHTML = '<div class="col-span-full p-8 rounded-xl bg-white border border-slate-200 text-center text-sm text-slate-500">No projects in this category yet.</div>';
                } else {
                    grid.innerHTML = filtered.map((p) => `
                        <article class="bg-white rounded-2xl border border-slate-200 overflow-hidden shadow-sm flex flex-col">
                            <div class="h-48 bg-slate-900 overflow-hidden relative">
                                <img src="${escapeHtml(p.photo || FALLBACK_IMG)}" alt="${escapeHtml(p.title)}" onerror="this.src='${FALLBACK_IMG}'" class="w-full h-full object-cover">
                                <span class="absolute top-3 left-3 px-2.5 py-1 rounded-md text-[11px] font-mono font-bold bg-slate-950/85 text-amber-400">${escapeHtml(p.category)}</span>
                                <span class="absolute top-3 right-3 px-2.5 py-1 rounded-md text-[11px] font-mono font-bold ${p.status === 'Completed' ? 'bg-emerald-600 text-white' : 'bg-amber-500 text-slate-950'}">${escapeHtml(p.status)}</span>
                            </div>
                            <div class="p-5 flex-grow flex flex-col justify-between space-y-3">
                                <div>
                                    <p class="text-xs font-mono text-slate-500">${escapeHtml(p.location)} ${p.budget ? '• ' + escapeHtml(p.budget) : ''}</p>
                                    <h3 class="font-heading font-bold text-lg text-slate-900 mt-1">${escapeHtml(p.title)}</h3>
                                    <p class="text-xs sm:text-sm text-slate-600 mt-2 leading-relaxed">${escapeHtml(p.scope)}</p>
                                </div>
                            </div>
                        </article>
                    `).join('');
                }

                const homeStrip = document.getElementById('home-featured-projects');
                homeStrip.innerHTML = appState.projects.slice(0, 3).map((p) => `
                    <article class="bg-white rounded-2xl border border-slate-200 overflow-hidden shadow-sm">
                        <div class="h-44 bg-slate-900 overflow-hidden">
                            <img src="${escapeHtml(p.photo || FALLBACK_IMG)}" alt="${escapeHtml(p.title)}" onerror="this.src='${FALLBACK_IMG}'" class="w-full h-full object-cover">
                        </div>
                        <div class="p-5">
                            <p class="text-[11px] font-mono uppercase text-amber-700 font-bold">${escapeHtml(p.category)} • ${escapeHtml(p.location)}</p>
                            <h3 class="font-heading font-bold text-base text-slate-900 mt-1">${escapeHtml(p.title)}</h3>
                            <p class="text-xs text-slate-600 mt-1.5 line-clamp-2">${escapeHtml(p.scope)}</p>
                        </div>
                    </article>
                `).join('');
            }

            document.querySelectorAll('.project-filter-btn').forEach((btn) => {
                btn.addEventListener('click', () => {
                    activeProjectFilter = btn.dataset.filter;
                    document.querySelectorAll('.project-filter-btn').forEach((b) => {
                        const active = b.dataset.filter === activeProjectFilter;
                        b.className = active
                            ? 'project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-slate-900 text-white transition-colors'
                            : 'project-filter-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200 transition-colors';
                    });
                    renderClientProjects();
                });
            });

            function renderClientGallery() {
                const grid = document.getElementById('client-gallery-grid');
                if (!appState.photos.length) {
                    grid.innerHTML = '<p class="text-sm text-slate-500 col-span-full">No photos uploaded yet.</p>';
                    return;
                }
                grid.innerHTML = appState.photos.map((ph) => `
                    <figure class="bg-white rounded-xl border border-slate-200 overflow-hidden shadow-sm">
                        <div class="h-40 bg-slate-900 overflow-hidden">
                            <img src="${escapeHtml(ph.url || FALLBACK_IMG)}" alt="${escapeHtml(ph.caption)}" onerror="this.src='${FALLBACK_IMG}'" class="w-full h-full object-cover">
                        </div>
                        <figcaption class="p-3">
                            <span class="text-[10px] font-mono uppercase text-amber-700 font-bold">${escapeHtml(ph.tag)}</span>
                            <p class="text-xs font-semibold text-slate-900 mt-0.5">${escapeHtml(ph.caption)}</p>
                        </figcaption>
                    </figure>
                `).join('');
            }

            function renderClientJobs() {
                const grid = document.getElementById('client-jobs-grid');
                if (!appState.jobs.length) {
                    grid.innerHTML = '<div class="col-span-full p-8 rounded-xl bg-white border border-slate-200 text-center text-sm text-slate-500">No open positions at the moment.</div>';
                    return;
                }
                grid.innerHTML = appState.jobs.map((j) => `
                    <article class="bg-white rounded-2xl border border-slate-200 p-6 shadow-sm flex flex-col justify-between space-y-4">
                        <div>
                            <div class="flex flex-wrap items-center gap-2 text-xs font-mono">
                                <span class="px-2.5 py-0.5 rounded bg-amber-100 text-amber-800 font-bold">${escapeHtml(j.type)}</span>
                                <span class="text-slate-500">${escapeHtml(j.department)} • ${escapeHtml(j.location)}</span>
                            </div>
                            <h3 class="font-heading font-bold text-lg text-slate-900 mt-2">${escapeHtml(j.title)}</h3>
                            <p class="text-sm text-slate-600 mt-2 leading-relaxed">${escapeHtml(j.summary)}</p>
                        </div>
                        <div>
                            <button type="button" data-apply-role="${escapeHtml(j.title)}" class="open-apply-btn px-4 py-2 rounded-lg bg-slate-900 hover:bg-slate-800 text-white text-xs font-semibold transition-colors">
                                Apply for Position
                            </button>
                        </div>
                    </article>
                `).join('');

                document.querySelectorAll('.open-apply-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        document.getElementById('apply-modal-role').textContent = 'Apply: ' + btn.dataset.applyRole;
                        document.getElementById('job-apply-form').reset();
                        document.getElementById('job-apply-success').classList.add('hidden');
                        const modal = document.getElementById('job-apply-modal');
                        modal.classList.remove('hidden');
                        modal.classList.add('flex');
                    });
                });
            }

            document.getElementById('close-job-apply-btn').addEventListener('click', () => {
                const modal = document.getElementById('job-apply-modal');
                modal.classList.add('hidden');
                modal.classList.remove('flex');
            });

            document.getElementById('job-apply-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const name = document.getElementById('apply-name').value.trim();
                const box = document.getElementById('job-apply-success');
                box.textContent = `Thank you, ${name}. Your application has been recorded for Crimacon Builders HR review (0797521481).`;
                box.classList.remove('hidden');
                e.target.reset();
            });

            function renderClientTeam() {
                const grid = document.getElementById('client-team-grid');
                if (!appState.team.length) {
                    grid.innerHTML = '<p class="text-sm text-slate-500 col-span-full">Executive team details are being updated.</p>';
                    return;
                }
                grid.innerHTML = appState.team.map((m) => `
                    <article class="bg-white rounded-2xl border border-slate-200 overflow-hidden shadow-sm">
                        <div class="h-48 bg-slate-900 overflow-hidden">
                            <img src="${escapeHtml(m.photo || FALLBACK_IMG)}" alt="${escapeHtml(m.name)}" onerror="this.src='${FALLBACK_IMG}'" class="w-full h-full object-cover object-top">
                        </div>
                        <div class="p-5">
                            <h4 class="font-heading font-bold text-base text-slate-900">${escapeHtml(m.name)}</h4>
                            <p class="text-xs font-mono text-amber-700 font-bold mt-0.5">${escapeHtml(m.role)}</p>
                            <p class="text-xs sm:text-sm text-slate-600 mt-2.5 leading-relaxed">${escapeHtml(m.bio)}</p>
                        </div>
                    </article>
                `).join('');
            }

            // -----------------------------------------------------------------
            // ADMIN CMS SUB-TABS & CRUD HANDLERS
            // -----------------------------------------------------------------
            document.querySelectorAll('.cms-subtab-btn').forEach((btn) => {
                btn.addEventListener('click', () => {
                    const panelKey = btn.dataset.cmsTab;
                    document.querySelectorAll('.cms-subtab-btn').forEach((b) => {
                        const active = b.dataset.cmsTab === panelKey;
                        b.className = active
                            ? 'cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-slate-900 text-white'
                            : 'cms-subtab-btn px-4 py-2 rounded-lg text-xs sm:text-sm font-semibold bg-white text-slate-700 hover:bg-slate-100 border border-slate-200';
                    });
                    document.querySelectorAll('.cms-panel').forEach((panel) => {
                        const isTarget = panel.id === 'cms-panel-' + panelKey;
                        panel.classList.toggle('hidden', !isTarget);
                        panel.classList.toggle('grid', isTarget);
                    });
                });
            });

            function refreshPhotoSelectDropdown() {
                const select = document.getElementById('proj-photo-select');
                if (!select) return;
                select.innerHTML = '<option value="">-- Choose from Media Gallery --</option>' +
                    appState.photos.map((ph) => `<option value="${escapeHtml(ph.url)}">${escapeHtml(ph.caption)}</option>`).join('');
            }

            document.getElementById('proj-photo-select').addEventListener('change', (e) => {
                if (e.target.value) {
                    document.getElementById('proj-photo-url').value = e.target.value;
                }
            });

            const projForm = document.getElementById('admin-project-form');
            projForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const editId = document.getElementById('proj-edit-id').value;
                const photoUrl = document.getElementById('proj-photo-url').value.trim() ||
                    document.getElementById('proj-photo-select').value ||
                    (appState.photos[0] && appState.photos[0].url) ||
                    FALLBACK_IMG;

                const entry = {
                    id: editId || ('p_' + Date.now()),
                    title: document.getElementById('proj-title').value.trim(),
                    location: document.getElementById('proj-location').value.trim(),
                    category: document.getElementById('proj-category').value,
                    status: document.getElementById('proj-status').value,
                    budget: document.getElementById('proj-budget').value.trim(),
                    photo: photoUrl,
                    scope: document.getElementById('proj-scope').value.trim()
                };

                if (editId) {
                    appState.projects = appState.projects.map((item) => item.id === editId ? entry : item);
                } else {
                    appState.projects.unshift(entry);
                }

                saveState();
                resetProjectForm();
                renderAll();
            });

            function resetProjectForm() {
                projForm.reset();
                document.getElementById('proj-edit-id').value = '';
                document.getElementById('project-form-heading').textContent = 'Add New Project';
                document.getElementById('proj-cancel-edit-btn').classList.add('hidden');
            }
            document.getElementById('proj-cancel-edit-btn').addEventListener('click', resetProjectForm);

            function renderAdminProjects() {
                document.getElementById('admin-proj-count').textContent = appState.projects.length;
                const list = document.getElementById('admin-projects-list');
                list.innerHTML = appState.projects.map((p) => `
                    <div class="bg-white rounded-xl border border-slate-200 p-4 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                        <div>
                            <span class="text-[11px] font-mono font-bold text-amber-700">${escapeHtml(p.category)} • ${escapeHtml(p.status)} • ${escapeHtml(p.location)}</span>
                            <h4 class="font-heading font-bold text-slate-900">${escapeHtml(p.title)}</h4>
                            <p class="text-xs text-slate-600 mt-0.5">${escapeHtml(p.scope)}</p>
                        </div>
                        <div class="flex items-center gap-2 shrink-0">
                            <button type="button" data-edit-proj="${p.id}" class="edit-proj-btn px-3 py-1.5 rounded-lg bg-slate-100 hover:bg-slate-200 text-slate-800 text-xs font-semibold">Edit</button>
                            <button type="button" data-del-proj="${p.id}" class="del-proj-btn px-3 py-1.5 rounded-lg bg-rose-50 hover:bg-rose-100 text-rose-700 text-xs font-semibold">Delete</button>
                        </div>
                    </div>
                `).join('');

                list.querySelectorAll('.edit-proj-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        const p = appState.projects.find((item) => item.id === btn.dataset.editProj);
                        if (!p) return;
                        document.getElementById('proj-edit-id').value = p.id;
                        document.getElementById('proj-title').value = p.title;
                        document.getElementById('proj-location').value = p.location;
                        document.getElementById('proj-category').value = p.category;
                        document.getElementById('proj-status').value = p.status;
                        document.getElementById('proj-budget').value = p.budget || '';
                        document.getElementById('proj-photo-url').value = p.photo || '';
                        document.getElementById('proj-scope').value = p.scope;
                        document.getElementById('project-form-heading').textContent = 'Edit Project';
                        document.getElementById('proj-cancel-edit-btn').classList.remove('hidden');
                    });
                });

                list.querySelectorAll('.del-proj-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        appState.projects = appState.projects.filter((item) => item.id !== btn.dataset.delProj);
                        saveState();
                        renderAll();
                    });
                });
            }

            const jobForm = document.getElementById('admin-job-form');
            jobForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const editId = document.getElementById('job-edit-id').value;
                const entry = {
                    id: editId || ('j_' + Date.now()),
                    title: document.getElementById('job-title').value.trim(),
                    department: document.getElementById('job-dept').value.trim(),
                    location: document.getElementById('job-location').value.trim(),
                    type: document.getElementById('job-type').value,
                    summary: document.getElementById('job-summary').value.trim()
                };
                if (editId) {
                    appState.jobs = appState.jobs.map((item) => item.id === editId ? entry : item);
                } else {
                    appState.jobs.unshift(entry);
                }
                saveState();
                resetJobForm();
                renderAll();
            });

            function resetJobForm() {
                jobForm.reset();
                document.getElementById('job-edit-id').value = '';
                document.getElementById('job-form-heading').textContent = 'Post Job Opportunity';
                document.getElementById('job-cancel-edit-btn').classList.add('hidden');
            }
            document.getElementById('job-cancel-edit-btn').addEventListener('click', resetJobForm);

            function renderAdminJobs() {
                document.getElementById('admin-job-count').textContent = appState.jobs.length;
                const list = document.getElementById('admin-jobs-list');
                list.innerHTML = appState.jobs.map((j) => `
                    <div class="bg-white rounded-xl border border-slate-200 p-4 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                        <div>
                            <span class="text-[11px] font-mono font-bold text-amber-700">${escapeHtml(j.type)} • ${escapeHtml(j.location)}</span>
                            <h4 class="font-heading font-bold text-slate-900">${escapeHtml(j.title)}</h4>
                            <p class="text-xs text-slate-600 mt-0.5">${escapeHtml(j.summary)}</p>
                        </div>
                        <div class="flex items-center gap-2 shrink-0">
                            <button type="button" data-edit-job="${j.id}" class="edit-job-btn px-3 py-1.5 rounded-lg bg-slate-100 hover:bg-slate-200 text-slate-800 text-xs font-semibold">Edit</button>
                            <button type="button" data-del-job="${j.id}" class="del-job-btn px-3 py-1.5 rounded-lg bg-rose-50 hover:bg-rose-100 text-rose-700 text-xs font-semibold">Delete</button>
                        </div>
                    </div>
                `).join('');

                list.querySelectorAll('.edit-job-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        const j = appState.jobs.find((item) => item.id === btn.dataset.editJob);
                        if (!j) return;
                        document.getElementById('job-edit-id').value = j.id;
                        document.getElementById('job-title').value = j.title;
                        document.getElementById('job-dept').value = j.department;
                        document.getElementById('job-location').value = j.location;
                        document.getElementById('job-type').value = j.type;
                        document.getElementById('job-summary').value = j.summary;
                        document.getElementById('job-form-heading').textContent = 'Edit Job Opportunity';
                        document.getElementById('job-cancel-edit-btn').classList.remove('hidden');
                    });
                });

                list.querySelectorAll('.del-job-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        appState.jobs = appState.jobs.filter((item) => item.id !== btn.dataset.delJob);
                        saveState();
                        renderAll();
                    });
                });
            }

            const photoForm = document.getElementById('admin-photo-form');
            let pendingUploadedDataUrl = '';

            document.getElementById('photo-file').addEventListener('change', (e) => {
                const file = e.target.files && e.target.files[0];
                if (!file) {
                    pendingUploadedDataUrl = '';
                    return;
                }
                const reader = new FileReader();
                reader.onload = () => {
                    pendingUploadedDataUrl = typeof reader.result === 'string' ? reader.result : '';
                    if (pendingUploadedDataUrl) {
                        document.getElementById('photo-url').value = pendingUploadedDataUrl;
                    }
                };
                reader.readAsDataURL(file);
            });

            photoForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const editId = document.getElementById('photo-edit-id').value;
                const urlVal = pendingUploadedDataUrl || document.getElementById('photo-url').value.trim() || FALLBACK_IMG;
                const entry = {
                    id: editId || ('ph_' + Date.now()),
                    caption: document.getElementById('photo-caption').value.trim(),
                    tag: document.getElementById('photo-tag').value.trim(),
                    url: urlVal
                };
                if (editId) {
                    appState.photos = appState.photos.map((item) => item.id === editId ? entry : item);
                } else {
                    appState.photos.unshift(entry);
                }
                saveState();
                resetPhotoForm();
                renderAll();
            });

            function resetPhotoForm() {
                photoForm.reset();
                pendingUploadedDataUrl = '';
                document.getElementById('photo-edit-id').value = '';
                document.getElementById('photo-form-heading').textContent = 'Add Project / Site Photo';
                document.getElementById('photo-cancel-edit-btn').classList.add('hidden');
            }
            document.getElementById('photo-cancel-edit-btn').addEventListener('click', resetPhotoForm);

            function renderAdminPhotos() {
                document.getElementById('admin-photo-count').textContent = appState.photos.length;
                const list = document.getElementById('admin-photos-list');
                list.innerHTML = appState.photos.map((ph) => `
                    <div class="bg-white rounded-xl border border-slate-200 overflow-hidden shadow-sm">
                        <img src="${escapeHtml(ph.url || FALLBACK_IMG)}" alt="${escapeHtml(ph.caption)}" onerror="this.src='${FALLBACK_IMG}'" class="w-full h-32 object-cover bg-slate-900">
                        <div class="p-3 space-y-2">
                            <p class="text-xs font-bold text-slate-900">${escapeHtml(ph.caption)}</p>
                            <p class="text-[11px] font-mono text-amber-700">${escapeHtml(ph.tag)}</p>
                            <div class="flex gap-2 pt-1">
                                <button type="button" data-edit-photo="${ph.id}" class="edit-photo-btn px-2.5 py-1 rounded bg-slate-100 hover:bg-slate-200 text-xs font-semibold">Edit</button>
                                <button type="button" data-del-photo="${ph.id}" class="del-photo-btn px-2.5 py-1 rounded bg-rose-50 hover:bg-rose-100 text-rose-700 text-xs font-semibold">Delete</button>
                            </div>
                        </div>
                    </div>
                `).join('');

                list.querySelectorAll('.edit-photo-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        const ph = appState.photos.find((item) => item.id === btn.dataset.editPhoto);
                        if (!ph) return;
                        document.getElementById('photo-edit-id').value = ph.id;
                        document.getElementById('photo-caption').value = ph.caption;
                        document.getElementById('photo-tag').value = ph.tag;
                        document.getElementById('photo-url').value = ph.url;
                        document.getElementById('photo-form-heading').textContent = 'Edit Photo';
                        document.getElementById('photo-cancel-edit-btn').classList.remove('hidden');
                    });
                });

                list.querySelectorAll('.del-photo-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        appState.photos = appState.photos.filter((item) => item.id !== btn.dataset.delPhoto);
                        saveState();
                        renderAll();
                    });
                });
            }

            const teamForm = document.getElementById('admin-team-form');
            teamForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const editId = document.getElementById('team-edit-id').value;
                const entry = {
                    id: editId || ('t_' + Date.now()),
                    name: document.getElementById('team-name').value.trim(),
                    role: document.getElementById('team-role').value.trim(),
                    photo: document.getElementById('team-photo').value.trim() || 'https://images.unsplash.com/photo-1560250097-0b93528c311a?auto=format&fit=crop&w=500&q=80',
                    bio: document.getElementById('team-bio').value.trim()
                };
                if (editId) {
                    appState.team = appState.team.map((item) => item.id === editId ? entry : item);
                } else {
                    appState.team.push(entry);
                }
                saveState();
                resetTeamForm();
                renderAll();
            });

            function resetTeamForm() {
                teamForm.reset();
                document.getElementById('team-edit-id').value = '';
                document.getElementById('team-form-heading').textContent = 'Add Executive / Management Leader';
                document.getElementById('team-cancel-edit-btn').classList.add('hidden');
            }
            document.getElementById('team-cancel-edit-btn').addEventListener('click', resetTeamForm);

            function renderAdminTeam() {
                document.getElementById('admin-team-count').textContent = appState.team.length;
                const list = document.getElementById('admin-team-list');
                list.innerHTML = appState.team.map((m) => `
                    <div class="bg-white rounded-xl border border-slate-200 p-4 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                        <div>
                            <h4 class="font-heading font-bold text-slate-900">${escapeHtml(m.name)}</h4>
                            <p class="text-xs font-mono text-amber-700 font-bold">${escapeHtml(m.role)}</p>
                            <p class="text-xs text-slate-600 mt-1">${escapeHtml(m.bio)}</p>
                        </div>
                        <div class="flex items-center gap-2 shrink-0">
                            <button type="button" data-edit-team="${m.id}" class="edit-team-btn px-3 py-1.5 rounded-lg bg-slate-100 hover:bg-slate-200 text-slate-800 text-xs font-semibold">Edit</button>
                            <button type="button" data-del-team="${m.id}" class="del-team-btn px-3 py-1.5 rounded-lg bg-rose-50 hover:bg-rose-100 text-rose-700 text-xs font-semibold">Delete</button>
                        </div>
                    </div>
                `).join('');

                list.querySelectorAll('.edit-team-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        const m = appState.team.find((item) => item.id === btn.dataset.editTeam);
                        if (!m) return;
                        document.getElementById('team-edit-id').value = m.id;
                        document.getElementById('team-name').value = m.name;
                        document.getElementById('team-role').value = m.role;
                        document.getElementById('team-photo').value = m.photo || '';
                        document.getElementById('team-bio').value = m.bio;
                        document.getElementById('team-form-heading').textContent = 'Edit Executive / Management Leader';
                        document.getElementById('team-cancel-edit-btn').classList.remove('hidden');
                    });
                });

                list.querySelectorAll('.del-team-btn').forEach((btn) => {
                    btn.addEventListener('click', () => {
                        appState.team = appState.team.filter((item) => item.id !== btn.dataset.delTeam);
                        saveState();
                        renderAll();
                    });
                });
            }

            document.getElementById('reset-demo-data-btn').addEventListener('click', () => {
                appState = JSON.parse(JSON.stringify(DEFAULT_STATE));
                saveState();
                renderAll();
            });

            // -----------------------------------------------------------------
            // ADMIN-ONLY AUTO-GENERATED FORMAL COMPANY PROFILE
            // -----------------------------------------------------------------
            const FOCUS_SUMMARIES = {
                full: 'Crimacon Builders is an NCA Category 6 registered Kenyan building construction and civil engineering contractor operating across all 47 counties of Kenya. We execute residential estates, villas, commercial buildings, cabro paving, stormwater drainage, structural steel water towers, and quantity surveying with KEBS-certified materials and direct client accountability (0797521481).',
                building: 'Crimacon Builders (NCA Category 6) specializes in residential housing, mansionettes, estates, and coastal villas across all 47 counties of Kenya, delivering durable structural frames, Twyford / Micasso porcelain tiles, Comply / high-gloss MDF joinery, Mazeras stonework, and black granite finishes.',
                civil: 'Crimacon Builders (NCA Category 6) delivers heavy-duty cabro paving, site grading, access works, and reinforced concrete drainage across all 47 counties of Kenya using compacted sub-bases and KEBS-compliant materials.',
                steel: 'Crimacon Builders (NCA Category 6) constructs elevated structural steel water towers, steel structures, and water reticulation systems nationwide with Pegler Class 2 gate valves, Danco PPR piping, and Havells switchgear.'
            };

            function renderAdminCompanyProfile() {
                if (!isAdminAuthenticated) return;
                const recipient = document.getElementById('prof-recipient').value.trim() || 'Prospective Client / Tender Committee';
                const refCode = document.getElementById('prof-ref').value.trim() || 'CB/NCA6/PROF-47C';
                const region = document.getElementById('prof-region').value.trim() || 'All 47 Counties (Republic of Kenya)';
                const focus = document.getElementById('prof-focus').value;

                document.getElementById('doc-recipient').textContent = recipient;
                document.getElementById('doc-ref').textContent = refCode;
                document.getElementById('doc-region').textContent = region;
                document.getElementById('doc-exec-summary').textContent = FOCUS_SUMMARIES[focus] || FOCUS_SUMMARIES.full;

                document.getElementById('doc-team-list').innerHTML = appState.team.map((m) => `
                    <div class="p-3 rounded-lg bg-slate-50 border border-slate-200">
                        <p class="font-bold text-slate-950">${escapeHtml(m.name)}</p>
                        <p class="font-mono text-[11px] text-amber-700">${escapeHtml(m.role)}</p>
                        <p class="text-slate-600 mt-1">${escapeHtml(m.bio)}</p>
                    </div>
                `).join('');

                document.getElementById('doc-projects-tbody').innerHTML = appState.projects.map((p) => `
                    <tr>
                        <td class="p-2.5 font-semibold text-slate-900">${escapeHtml(p.title)}</td>
                        <td class="p-2.5 text-slate-700">${escapeHtml(p.location)}</td>
                        <td class="p-2.5 text-slate-700">${escapeHtml(p.category)}</td>
                        <td class="p-2.5 font-mono text-slate-800">${escapeHtml(p.status)}</td>
                    </tr>
                `).join('');
            }

            ['prof-recipient', 'prof-ref', 'prof-region', 'prof-focus'].forEach((id) => {
                document.getElementById(id).addEventListener('input', renderAdminCompanyProfile);
                document.getElementById(id).addEventListener('change', renderAdminCompanyProfile);
            });

            document.getElementById('print-company-profile-btn').addEventListener('click', () => {
                if (!isAdminAuthenticated) {
                    openAdminLoginModal();
                    return;
                }
                renderAdminCompanyProfile();
                window.print();
            });

            // -----------------------------------------------------------------
            // KES ESTIMATOR, QUOTE FORM & BOTTOM-RIGHT WHATSAPP TOGGLE
            // -----------------------------------------------------------------
            function calculateKesEstimate() {
                const scopeEl = document.getElementById('est-scope');
                const baseRate = parseFloat(scopeEl.options[scopeEl.selectedIndex].dataset.rate || '46000');
                const regionMult = parseFloat(document.getElementById('est-region').value || '1');
                const tierMult = parseFloat(document.getElementById('est-tier').value || '1');
                const area = Math.max(10, parseFloat(document.getElementById('est-area').value || '180'));

                const mid = baseRate * regionMult * tierMult * area;
                const low = Math.round((mid * 0.9) / 1000) * 1000;
                const high = Math.round((mid * 1.1) / 1000) * 1000;

                const fmt = (n) => 'KES ' + n.toLocaleString('en-KE');
                const text = `${fmt(low)} – ${fmt(high)}`;
                document.getElementById('est-result-range').textContent = text;
                return text;
            }

            ['est-scope', 'est-region', 'est-tier', 'est-area'].forEach((id) => {
                document.getElementById(id).addEventListener('input', calculateKesEstimate);
                document.getElementById(id).addEventListener('change', calculateKesEstimate);
            });

            document.getElementById('apply-estimate-btn').addEventListener('click', () => {
                const rangeText = calculateKesEstimate();
                const scopeText = document.getElementById('est-scope').options[document.getElementById('est-scope').selectedIndex].text;
                const regionText = document.getElementById('est-region').options[document.getElementById('est-region').selectedIndex].text;
                const areaVal = document.getElementById('est-area').value;

                if (!document.getElementById('quote-county').value) {
                    document.getElementById('quote-county').value = regionText;
                }
                const detailsEl = document.getElementById('quote-details');
                detailsEl.value = `Preliminary Estimate (${scopeText}, ${areaVal} m², ${regionText}): ${rangeText}.`;
                detailsEl.focus();
            });

            document.getElementById('client-quote-form').addEventListener('submit', (e) => {
                e.preventDefault();
                const name = document.getElementById('quote-name').value.trim();
                const county = document.getElementById('quote-county').value.trim();
                const box = document.getElementById('quote-confirmation');
                box.innerHTML = `<strong>Quote Request Received:</strong> Thank you, <strong>${escapeHtml(name)}</strong>. Our NCA 6 team has logged your inquiry for <strong>${escapeHtml(county)}</strong>. You can also reach us directly on <strong>0797521481</strong> (+254797521481).`;
                box.classList.remove('hidden');
                e.target.reset();
            });

            // Bottom-Right WhatsApp Toggle Logic
            const waToggleBtn = document.getElementById('wa-toggle-btn');
            const waToggleLabel = document.getElementById('wa-toggle-label');
            const waPanel = document.getElementById('wa-chat-panel');
            const waInput = document.getElementById('wa-message-input');
            const waLink = document.getElementById('wa-send-link');

            function syncWaLink() {
                const encoded = encodeURIComponent(waInput.value.trim() || 'Hello Crimacon Builders, I need construction assistance.');
                waLink.href = `https://wa.me/${WHATSAPP_NUMBER}?text=${encoded}`;
            }

            function setWaDrawerOpen(open) {
                waPanel.classList.toggle('hidden', !open);
                waToggleBtn.setAttribute('aria-expanded', String(open));
                waToggleLabel.textContent = open ? 'Close WhatsApp' : 'WhatsApp • 0797521481';
                if (open) syncWaLink();
            }

            waToggleBtn.addEventListener('click', () => {
                const isCurrentlyOpen = !waPanel.classList.contains('hidden');
                setWaDrawerOpen(!isCurrentlyOpen);
            });

            document.getElementById('wa-close-btn').addEventListener('click', () => setWaDrawerOpen(false));
            waInput.addEventListener('input', syncWaLink);

            document.querySelectorAll('.wa-preset-btn').forEach((btn) => {
                btn.addEventListener('click', () => {
                    waInput.value = btn.dataset.waMsg;
                    syncWaLink();
                });
            });

            function escapeHtml(str) {
                return String(str || '')
                    .replace(/&/g, '&amp;')
                    .replace(/</g, '&lt;')
                    .replace(/>/g, '&gt;')
                    .replace(/"/g, '&quot;')
                    .replace(/'/g, '&#39;');
            }

            function renderAll() {
                refreshPhotoSelectDropdown();
                renderClientProjects();
                renderClientGallery();
                renderClientJobs();
                renderClientTeam();
                renderAdminProjects();
                renderAdminJobs();
                renderAdminPhotos();
                renderAdminTeam();
                if (isAdminAuthenticated) {
                    renderAdminCompanyProfile();
                }
            }

            syncAuthUI();
            calculateKesEstimate();
            syncWaLink();
            renderAll();
            setActiveTab('home');
        });
    </script>
</body>
</html>
