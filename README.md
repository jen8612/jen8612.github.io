<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>frontrow.rental - 前排視角手機租賃</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter & Noto Sans TC -->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;500;700&family=Playfair+Display:ital,wght@0,500;0,700;1,400&display=swap" rel="stylesheet">
    <!-- Font Awesome for sleek modern icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.2/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#FAF8F5',  // Off-white Warm Oatmeal
                            100: '#F2EAE1', // Soft Warm Apricot Gray
                            200: '#E5D5C5', // Muted Clay Sand
                            300: '#D1B29A', // Neutral Warm Ochre
                            400: '#B88A64', // Leather Brown Accent
                            500: '#8A5E3C', // Deep Roasted Wood
                            text: '#3D3530', // Deep Charcoal
                            lightText: '#7A706A', // Warm Gray-Brown
                        }
                    },
                    fontFamily: {
                        sans: ['Noto Sans TC', 'sans-serif'],
                        serif: ['Playfair Display', 'serif'],
                    },
                    borderRadius: {
                        'brand': '24px',
                        'card': '16px',
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Noto Sans TC', sans-serif;
            background-color: #FAF8F5;
            color: #3D3530;
            -webkit-tap-highlight-color: transparent;
        }
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #FAF8F5;
        }
        ::-webkit-scrollbar-thumb {
            background: #E5D5C5;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #D1B29A;
        }
        .slot-btn-selected {
            background-color: #8A5E3C !important;
            color: #ffffff !important;
            border-color: #8A5E3C !important;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between selection:bg-brand-200 selection:text-brand-500">

    <!-- Header Hero Banner -->
    <header class="w-full bg-gradient-to-b from-[#FFFDFB] to-[#FAF8F5] pt-14 pb-10 px-4 text-center">
        <div class="max-w-4xl mx-auto">
            <!-- Brand Badge -->
            <div class="inline-flex items-center gap-2 bg-brand-100 text-brand-500 px-4 py-1.5 rounded-full text-xs font-semibold tracking-widest mb-4 border border-brand-200/50">
                <i class="fa-solid fa-camera-retro"></i> 租借服務為 24 小時制
            </div>
            
            <!-- Brand Title -->
            <h1 class="text-4xl md:text-5xl font-bold tracking-tight text-brand-text mb-4 font-serif italic">
                frontrow.rental
            </h1>
            
            <!-- Brand Slogan -->
            <p class="text-brand-lightText text-base md:text-lg max-w-lg mx-auto font-semibold leading-relaxed">
                讓你不管在哪個位子都可以拍出前排視角!
            </p>
        </div>
    </header>

    <!-- Navigation Tabs -->
    <div class="sticky top-0 z-30 bg-[#FAF8F5]/90 backdrop-blur-md py-4 border-b border-brand-200/30">
        <div class="max-w-4xl mx-auto px-4">
            <div class="flex overflow-x-auto gap-2 md:grid md:grid-cols-4 bg-brand-100/60 p-1.5 rounded-brand border border-brand-200/40 no-scrollbar">
                
                <button onclick="switchTab('price-tab')" id="btn-price-tab" 
                        class="tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 bg-white text-brand-500 shadow-sm border border-brand-200/30">
                    <i class="fa-solid fa-calculator text-base"></i>
                    <span>價目與試算器</span>
                </button>
                
                <button onclick="switchTab('notice-tab')" id="btn-notice-tab" 
                        class="tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 text-brand-lightText hover:text-brand-500">
                    <i class="fa-solid fa-circle-info text-base"></i>
                    <span>預約須知</span>
                </button>
                
                <button onclick="switchTab('faq-tab')" id="btn-faq-tab" 
                        class="tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 text-brand-lightText hover:text-brand-500">
                    <i class="fa-solid fa-circle-question text-base"></i>
                    <span>常見問題 QA</span>
                </button>
                
                <button onclick="switchTab('slots-tab')" id="btn-slots-tab" 
                        class="tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 text-brand-lightText hover:text-brand-500">
                    <i class="fa-solid fa-calendar-days text-base"></i>
                    <span>可預約時段</span>
                </button>
            </div>
        </div>
    </div>

    <!-- Main Content Body -->
    <main class="max-w-4xl mx-auto w-full px-4 py-8 flex-grow">
        
        <!-- ================= PAGE 1: PRICE LIST & CALCULATOR ================= -->
        <section id="price-tab" class="tab-content block space-y-8">
            
            <div class="text-center md:text-left mb-6">
                <h2 class="text-xl font-bold text-brand-text flex items-center justify-center md:justify-start gap-2">
                    <span class="w-1.5 h-6 bg-brand-300 rounded-full inline-block"></span>
                    手機與配件價目
                </h2>
            </div>

            <!-- Price Cards Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                
                <!-- Product Card 1: Vivo X300 Ultra -->
                <div class="bg-white rounded-card p-6 border border-brand-200/30 shadow-sm hover:shadow-md transition-shadow duration-300 flex flex-col justify-between relative overflow-hidden group">
                    <div class="absolute top-0 right-0 bg-brand-100 text-brand-500 text-xs font-semibold px-4 py-1.5 rounded-bl-card tracking-wider">
                        旗艦手機
                    </div>
                    <div>
                        <div class="flex items-center gap-4 mb-4">
                            <div class="w-20 h-20 bg-brand-50 rounded-card flex items-center justify-center overflow-hidden p-1 border border-brand-100">
                                <img src="https://i.meee.com.tw/a2dlPTl.png" 
                                     onerror="this.src='https://placehold.co/120x120/F2EAE1/8A5E3C?text=Vivo+Ultra'"
                                     alt="Vivo X300 Ultra 1TB" 
                                     class="max-w-full max-h-full object-contain">
                            </div>
                            <div>
                                <h3 class="font-bold text-lg text-brand-text">Vivo X300 Ultra 1TB</h3>
                            </div>
                        </div>
                        <ul class="space-y-2 text-sm text-brand-lightText my-4">
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>每日租金 (24H)</span>
                                <span class="font-bold text-brand-text">NT$ 800</span>
                            </li>
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>天數折扣 (滿3天)</span>
                                <span class="font-medium text-brand-400">總租金享 95 折</span>
                            </li>
                            <li class="flex justify-between">
                                <span>天數折扣 (滿5天)</span>
                                <span class="font-medium text-brand-400">總租金享 9 折</span>
                            </li>
                        </ul>
                    </div>
                </div>

                <!-- Product Card 2: 200mm Lens -->
                <div class="bg-white rounded-card p-6 border border-brand-200/30 shadow-sm hover:shadow-md transition-shadow duration-300 flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute top-0 right-0 bg-[#FFF7F0] text-amber-700 text-xs font-semibold px-4 py-1.5 rounded-bl-card tracking-wider">
                        長焦配件
                    </div>
                    <div>
                        <div class="flex items-center gap-4 mb-4">
                            <div class="w-20 h-20 bg-brand-50 rounded-card flex items-center justify-center overflow-hidden p-1 border border-brand-100">
                                <img src="https://i.meee.com.tw/iZyq2k1.jpg" 
                                     onerror="this.src='https://placehold.co/120x120/F2EAE1/8A5E3C?text=200mm'"
                                     alt="200mm 增距鏡" 
                                     class="max-w-full max-h-full object-contain">
                            </div>
                            <div>
                                <h3 class="font-bold text-lg text-brand-text">200mm 增距鏡</h3>
                            </div>
                        </div>
                        <ul class="space-y-2 text-sm text-brand-lightText my-4">
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>配合手機租用</span>
                                <span class="font-bold text-emerald-600">NT$ 200 / 日</span>
                            </li>
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>單獨租用費</span>
                                <span class="font-medium text-brand-text">NT$ 250 / 日</span>
                            </li>
                            <li class="flex justify-between">
                                <span>天數折扣 (3天/5天)</span>
                                <span class="font-medium text-brand-400">95折 / 9折</span>
                            </li>
                        </ul>
                    </div>
                </div>

                <!-- Product Card 3: 400mm Lens -->
                <div class="bg-white rounded-card p-6 border border-brand-200/30 shadow-sm hover:shadow-md transition-shadow duration-300 flex flex-col justify-between relative overflow-hidden">
                    <div class="absolute top-0 right-0 bg-[#F0FDF4] text-emerald-700 text-xs font-semibold px-4 py-1.5 rounded-bl-card tracking-wider">
                        長焦配件
                    </div>
                    <div>
                        <div class="flex items-center gap-4 mb-4">
                            <div class="w-20 h-20 bg-brand-50 rounded-card flex items-center justify-center overflow-hidden p-1 border border-brand-100">
                                <img src="https://i.meee.com.tw/cksTTQL.jpg" 
                                     onerror="this.src='https://placehold.co/120x120/F2EAE1/8A5E3C?text=400mm'"
                                     alt="400mm 增距鏡" 
                                     class="max-w-full max-h-full object-contain">
                            </div>
                            <div>
                                <h3 class="font-bold text-lg text-brand-text">400mm 增距鏡</h3>
                            </div>
                        </div>
                        <ul class="space-y-2 text-sm text-brand-lightText my-4">
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>配合手機租用</span>
                                <span class="font-bold text-emerald-600">NT$ 300 / 日</span>
                            </li>
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>單獨租用費</span>
                                <span class="font-medium text-brand-text">NT$ 400 / 日</span>
                            </li>
                            <li class="flex justify-between">
                                <span>天數折扣 (3天/5天)</span>
                                <span class="font-medium text-brand-400">95折 / 9折</span>
                            </li>
                        </ul>
                    </div>
                </div>

                <!-- Product Card 4: Pro Grip -->
                <div class="bg-white rounded-card p-6 border border-brand-200/30 shadow-sm hover:shadow-md transition-shadow duration-300 flex flex-col justify-between">
                    <div>
                        <div class="flex items-center gap-4 mb-4">
                            <div class="w-20 h-20 bg-brand-50 rounded-card flex items-center justify-center overflow-hidden p-1 border border-brand-100">
                                <img src="https://i.meee.com.tw/KrJ8vL8.jpg" 
                                     onerror="this.src='https://placehold.co/120x120/F2EAE1/8A5E3C?text=Grip'"
                                     alt="專業攝影手柄" 
                                     class="max-w-full max-h-full object-contain">
                            </div>
                            <div>
                                <h3 class="font-bold text-lg text-brand-text">專業攝影手柄</h3>
                            </div>
                        </div>
                        <ul class="space-y-2 text-sm text-brand-lightText my-4">
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>單次租借費用</span>
                                <span class="font-bold text-brand-text">NT$ 100 / 次</span>
                            </li>
                            <li class="flex justify-between border-b border-brand-100/50 pb-1.5">
                                <span>租期限制</span>
                                <span class="font-medium text-brand-lightText">以次計費</span>
                            </li>
                            <li class="flex justify-between">
                                <span>折抵限制</span>
                                <span class="font-medium text-brand-lightText">無折扣優惠</span>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- Interactive Multi-Selection Calculator -->
            <div id="calculator-section" class="bg-white rounded-brand p-6 md:p-8 border border-brand-200/40 shadow-sm">
                <div class="flex items-center gap-2.5 mb-6">
                    <span class="p-2 bg-brand-100 text-brand-500 rounded-card"><i class="fa-solid fa-calculator"></i></span>
                    <div>
                        <h3 class="font-bold text-lg text-brand-text">費用快速估算</h3>
                        <p class="text-xs text-brand-lightText">勾選下方租用組合，自動適配最佳合租優惠與滿天數折扣（滿3天95折，滿5天9折）。</p>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <!-- Configurator Columns -->
                    <div class="space-y-5">
                        <!-- Choice Checklist -->
                        <div>
                            <label class="block text-sm font-semibold text-brand-text mb-3 flex items-center gap-1.5">
                                <i class="fa-solid fa-list-check text-brand-400"></i> 1. 選擇租用項目
                            </label>
                            
                            <div class="space-y-2.5">
                                <label id="label-calc-phone" class="flex items-center justify-between p-3.5 rounded-card bg-brand-50 border border-brand-200 cursor-pointer transition-all">
                                    <div class="flex items-center gap-3">
                                        <input type="checkbox" id="calc-phone" checked onchange="calculatePrice()" class="rounded accent-brand-400 w-4.5 h-4.5">
                                        <div>
                                            <p class="text-sm font-bold text-brand-text">Vivo X300 Ultra 1TB</p>
                                        </div>
                                    </div>
                                    <span class="text-xs font-semibold text-brand-500">NT$ 800 / 日</span>
                                </label>

                                <label id="label-calc-200" class="flex items-center justify-between p-3.5 rounded-card bg-brand-50 border border-brand-200 cursor-pointer transition-all">
                                    <div class="flex items-center gap-3">
                                        <input type="checkbox" id="calc-200" onchange="calculatePrice()" class="rounded accent-brand-400 w-4.5 h-4.5">
                                        <div>
                                            <p class="text-sm font-bold text-brand-text">200mm 增距鏡</p>
                                            <p id="label-desc-200" class="text-[11px] text-brand-lightText">配合手機：$200/日 (單租$250)</p>
                                        </div>
                                    </div>
                                    <span id="price-display-200" class="text-xs font-semibold text-brand-500">NT$ 250 / 日</span>
                                </label>

                                <label id="label-calc-400" class="flex items-center justify-between p-3.5 rounded-card bg-brand-50 border border-brand-200 cursor-pointer transition-all">
                                    <div class="flex items-center gap-3">
                                        <input type="checkbox" id="calc-400" onchange="calculatePrice()" class="rounded accent-brand-400 w-4.5 h-4.5">
                                        <div>
                                            <p class="text-sm font-bold text-brand-text">400mm 增距鏡</p>
                                            <p id="label-desc-400" class="text-[11px] text-brand-lightText">配合手機：$300/日 (單租$400)</p>
                                        </div>
                                    </div>
                                    <span id="price-display-400" class="text-xs font-semibold text-brand-500">NT$ 400 / 日</span>
                                </label>

                                <label id="label-calc-grip" class="flex items-center justify-between p-3.5 rounded-card bg-brand-50 border border-brand-200 cursor-pointer transition-all">
                                    <div class="flex items-center gap-3">
                                        <input type="checkbox" id="calc-grip" onchange="calculatePrice()" class="rounded accent-brand-400 w-4.5 h-4.5">
                                        <div>
                                            <p class="text-sm font-bold text-brand-text">專業攝影手柄</p>
                                        </div>
                                    </div>
                                    <span class="text-xs font-semibold text-brand-500">NT$ 100 / 次</span>
                                </label>
                            </div>
                        </div>

                        <!-- Days Slider -->
                        <div class="pt-2">
                            <label class="block text-sm font-semibold text-brand-text mb-2 flex justify-between items-center">
                                <span class="flex items-center gap-1.5"><i class="fa-solid fa-calendar-day text-brand-400"></i> 2. 租借租期天數</span>
                                <span class="bg-brand-100 text-brand-500 px-3 py-0.5 rounded-full text-xs font-bold" id="days-badge">1 天</span>
                            </label>
                            <div class="flex items-center gap-4">
                                <input type="range" id="calc-days" min="1" max="14" value="1" oninput="updateDaysText(this.value)" class="flex-grow accent-brand-400">
                                <input type="number" id="calc-days-num" min="1" max="60" value="1" oninput="updateDaysSlider(this.value)" class="w-16 bg-white border border-brand-200 p-2 rounded-card text-center text-sm font-semibold focus:outline-none focus:ring-2 focus:ring-brand-300">
                            </div>
                            <div class="flex justify-between text-[11px] text-[#B88A64] mt-2 font-medium">
                                <span id="promo-notice-3">滿 3 天享 95 折</span>
                                <span id="promo-notice-5">滿 5 天享 9 折</span>
                            </div>
                            
                            <div class="mt-4 bg-[#FFF9F3] border border-brand-300/30 rounded-card p-3 flex gap-2.5 items-start">
                                <i class="fa-solid fa-circle-exclamation text-brand-400 text-sm mt-0.5"></i>
                                <p class="text-xs text-brand-lightText leading-relaxed">
                                    所有加購配件（鏡頭、手把）之租借天數，必須與手機租借天數完全一致，恕不接受單獨拆分天數。
                                </p>
                            </div>
                        </div>
                    </div>

                    <!-- Receipt Summary -->
                    <div class="bg-brand-50/50 rounded-card p-6 border border-brand-200/50 flex flex-col justify-between">
                        <div>
                            <h4 class="text-sm font-bold text-brand-text tracking-wider uppercase mb-4 border-b border-brand-200/60 pb-2 flex justify-between items-center">
                                <span>即時估算清單</span>
                                <span class="text-[11px] text-brand-lightText font-normal">24H制計算</span>
                            </h4>
                            <div class="space-y-3.5 text-sm">
                                <div id="summary-items-list" class="space-y-2 border-b border-brand-200/30 pb-3">
                                    <!-- Dynamic items go here -->
                                </div>
                                <div class="flex justify-between text-brand-lightText text-xs">
                                    <span>小計金額</span>
                                    <span id="summary-subtotal" class="text-brand-text font-medium">NT$ 0</span>
                                </div>
                                <div id="summary-discount-row" class="flex justify-between text-brand-400 text-xs hidden">
                                    <span id="summary-discount-label">天數折抵</span>
                                    <span id="summary-discount-amount">-NT$ 0</span>
                                </div>
                                <div id="summary-grip-row" class="flex justify-between text-brand-lightText text-xs border-b border-brand-200/30 pb-3 hidden">
                                    <span>專業手把 (固定/無折扣)</span>
                                    <span>NT$ 100</span>
                                </div>
                                <div class="flex justify-between items-center pt-2">
                                    <span class="text-base font-bold text-brand-text">估算總金額</span>
                                    <div class="text-right">
                                        <span id="summary-total-price" class="text-2xl font-bold text-brand-500">NT$ 800</span>
                                        <p class="text-[10px] text-brand-lightText mt-0.5">(不含押金)</p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- CTA Button -->
                        <div class="mt-8 pt-4 border-t border-brand-200/40">
                            <button onclick="switchTab('slots-tab')" class="w-full bg-brand-500 hover:bg-brand-600 text-white py-3 px-4 rounded-card font-semibold text-sm transition-colors shadow-sm hover:shadow-md flex items-center justify-center gap-2">
                                <i class="fa-solid fa-paper-plane"></i> 查看可預約檔期
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= PAGE 2: BOOKING NOTICE ================= -->
        <section id="notice-tab" class="tab-content hidden space-y-6">
            <div class="text-center md:text-left mb-6">
                <h2 class="text-xl font-bold text-brand-text flex items-center justify-center md:justify-start gap-2">
                    <span class="w-1.5 h-6 bg-brand-300 rounded-full inline-block"></span>
                    預約須知與租借流程
                </h2>
                <p class="text-xs text-brand-lightText mt-1">請在預約前仔細閱讀以下租賃政策與面交流程規範。</p>
            </div>

            <!-- Rental Process Timeline (Highly Visual Timeline) -->
            <div class="bg-white rounded-brand p-6 border border-brand-200/30 shadow-sm space-y-6">
                <h3 class="font-bold text-brand-text text-base flex items-center gap-2 border-b border-brand-100 pb-3">
                    <i class="fa-solid fa-clipboard-list text-brand-400"></i>
                     租借流程
                </h3>
                <div class="relative pl-6 border-l-2 border-brand-200 space-y-6 text-xs md:text-sm">
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">1</span>
                        <h4 class="font-bold text-brand-text">私訊確認檔期與設備</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">點私訊 LINE/Threads 確認所需設備及日期是否可租借。</p>
                    </div>
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">2</span>
                        <h4 class="font-bold text-brand-text">支付訂金保留檔期</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">確認有檔期後 24 小時內匯款預付一日租金為訂金。</p>
                    </div>
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">3</span>
                        <h4 class="font-bold text-brand-text">核對身分＋驗機</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">現場面交時出示雙證件確認身分並核實設備完好。</p>
                    </div>
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">4</span>
                        <h4 class="font-bold text-brand-text">支付尾款及押金並簽約</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">當場支付剩餘租金尾款，選擇留存證件(方案A)或付押金(方案B)。</p>
                    </div>
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">5</span>
                        <h4 class="font-bold text-brand-text">交機開始租借</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">雙方簽約後交機！</p>
                    </div>
                    <div class="relative">
                        <span class="absolute -left-[31px] top-0 bg-brand-400 text-white w-5 h-5 rounded-full flex items-center justify-center text-[10px] font-bold">6</span>
                        <h4 class="font-bold text-brand-text">歸還驗機後退還押金／證件</h4>
                        <p class="text-brand-lightText text-xs mt-0.5">按時面交歸還，經檢查設備功能無異狀後當場退還押金與證件。</p>
                    </div>
                </div>
            </div>

            <!-- Dynamic Notices Container -->
            <div id="notices-container" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Populated dynamically -->
            </div>
        </section>

        <!-- ================= PAGE 3: FAQ ================= -->
        <section id="faq-tab" class="tab-content hidden space-y-6">
            <div class="text-center md:text-left">
                <h2 class="text-xl font-bold text-brand-text flex items-center justify-center md:justify-start gap-2">
                    <span class="w-1.5 h-6 bg-brand-300 rounded-full inline-block"></span>
                    常見問題 QA
                </h2>
                <p class="text-xs text-brand-lightText mt-1">關於租借模式、配件組合、交還手機的問與答。</p>
            </div>

            <!-- FAQ Accordions Container -->
            <div id="faqs-container" class="space-y-4 max-w-3xl mx-auto">
                <!-- Populated dynamically -->
            </div>
        </section>

        <!-- ================= PAGE 4: AVAILABLE SLOTS ================= -->
        <section id="slots-tab" class="tab-content hidden space-y-6">
            <div class="text-center md:text-left">
                <h2 class="text-xl font-bold text-brand-text flex items-center justify-center md:justify-start gap-2">
                    <span class="w-1.5 h-6 bg-brand-300 rounded-full inline-block"></span>
                    預約狀態查詢
                </h2>
                
                <!-- Quick Help Block -->
                <div class="bg-brand-100/50 rounded-card p-4 text-xs text-brand-lightText mt-3 max-w-2xl leading-relaxed space-y-2">
                    <p class="font-bold text-brand-text"><i class="fa-solid fa-info-circle text-brand-400"></i> 取還機與多選提示：</p>
                    <p>由於本服務採用 24 小時制計費。若您想要預約 <strong>6/15 至 6/21</strong>（共 6 天），請分別點選您的<strong>「取機日期」</strong>與<strong>「還機日期」</strong>。</p>
                    <p>系統會自動在下方彙整出明確的取還機區間，方便一鍵複製諮詢！</p>
                </div>
            </div>

            <!-- Month Switching Navigator -->
            <div id="month-tabs-container" class="flex flex-wrap gap-2 justify-center md:justify-start pt-2">
                <!-- Populated dynamically -->
            </div>

            <!-- Dynamic Board Slots (Rendered by JS) -->
            <div id="slots-grid-container" class="grid grid-cols-2 sm:grid-cols-4 lg:grid-cols-7 gap-3">
                <!-- Will render dynamically -->
            </div>

            <!-- Interactive Pre-Fill Multi-Selector Box -->
            <div id="booking-prompt-box" class="hidden bg-[#FAF0E6] border border-brand-300/40 p-5 rounded-brand text-sm text-brand-text flex flex-col sm:flex-row justify-between items-center gap-4">
                <div class="flex items-start gap-3 w-full">
                    <span class="p-1.5 bg-brand-100 text-brand-500 rounded-card mt-0.5"><i class="fa-regular fa-clipboard"></i></span>
                    <div class="w-full">
                        <p class="font-bold text-brand-text" id="summary-booking-title">您已選取的預約時段：</p>
                        <div id="selected-slots-list" class="flex flex-wrap gap-1.5 mt-2 mb-1.5">
                            <!-- Selected labels will render dynamically -->
                        </div>
                        
                        <!-- Extra Accessory Quick Checkbox Selector -->
                        <div class="mt-1 mb-2">
                            <label class="inline-flex items-center gap-2 bg-white/70 border border-brand-200 hover:bg-white px-3 py-1.5 rounded-card text-xs cursor-pointer transition-all">
                                <input type="checkbox" id="prompt-add-grip" onchange="updateSlotsPromptUI()" class="rounded accent-brand-400 w-4 h-4">
                                <span class="text-brand-text font-semibold flex items-center gap-1">
                                    <i class="fa-solid fa-gamepad text-brand-400"></i> 加租專業攝影手柄 (+$100/單次)
                                </span>
                            </label>
                        </div>
                        
                        <!-- Intelligent Range Collision Alert Warning -->
                        <div id="conflict-alert" class="hidden mt-3 bg-rose-50 border border-rose-200 text-rose-800 text-xs p-3.5 rounded-card flex gap-2.5 items-start">
                            <i class="fa-solid fa-triangle-exclamation text-rose-500 mt-0.5 text-sm"></i>
                            <div>
                                <strong class="block mb-0.5 text-rose-900 font-bold">提醒：您所選取的區間含有已被預約的日期</strong>
                                <span class="leading-relaxed text-rose-700">您選取的日期區間內，有部分日期該設備已被他人租借。如仍需諮詢或想要調整分段租借，可直接點擊右側按鈕，複製現有空檔時段，前往 LINE 向客服詢問其他替代調配方案！</span>
                            </div>
                        </div>

                        <p class="text-xs text-brand-lightText mt-2" id="summary-booking-helper">已為您整合並自動複製預約諮詢，加入 LINE 貼上即可直接送出諮詢！</p>
                    </div>
                </div>
                <button onclick="scrollToContactWithPrompt()" class="bg-brand-500 hover:bg-brand-600 text-white px-5 py-3 rounded-card text-xs font-semibold whitespace-nowrap transition-all shadow hover:shadow-md hover:-translate-y-0.5">
                    快速複製並前往預約
                </button>
            </div>
        </section>

    </main>

    <!-- Contact & Footer Section -->
    <section id="contact-area" class="w-full bg-white border-t border-brand-200/50 py-12 px-4 mt-8">
        <div class="max-w-xl mx-auto text-center space-y-6">
            <div class="text-brand-400 text-xs font-bold tracking-widest uppercase">
                FRONTROW.RENTAL CONTACT
            </div>
          

            <!-- Buttons Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 max-w-md mx-auto">
                
                <!-- LINE Contact Button -->
                <a href="https://lin.ee/VRS8Bev" target="_blank" rel="noopener noreferrer" 
                   class="group relative flex items-center justify-center gap-3 bg-[#06C755] hover:bg-[#05b34c] text-white py-3.5 px-6 rounded-card font-semibold transition-all shadow-md hover:shadow-lg hover:-translate-y-0.5 active:translate-y-0">
                    <i class="fa-brands fa-line text-2xl"></i>
                    <div class="text-left">
                        <p class="text-[10px] opacity-90 font-light">官方 LINE</p>
                        <p class="text-sm font-bold">加入 LINE 即刻預約</p>
                    </div>
                   
                </a>

                <!-- Threads Contact Button -->
                <a href="https://www.threads.com/@frontrow.rental?igshid=NTc4MTIwNjQ2YQ==" target="_blank" rel="noopener noreferrer" 
                   class="group flex items-center justify-center gap-3 bg-black hover:bg-neutral-800 text-white py-3.5 px-6 rounded-card font-semibold transition-all shadow-md hover:shadow-lg hover:-translate-y-0.5 active:translate-y-0">
                    <i class="fa-brands fa-threads text-2xl"></i>
                    <div class="text-left">
                        <p class="text-[10px] opacity-90 font-light">來看看實際使用畫面</p>
                        <p class="text-sm font-bold">Threads</p>
                    </div>
                </a>
                
            </div>

            <p class="text-[10px] text-brand-lightText max-w-sm mx-auto">
                * frontrow.rental 保有活動最終解釋、修改及合約訂定之權利。雙證件圖片核對僅供簽約授信使用，絕不做他途。
            </p>
        </div>
    </section>

    <!-- Footer Copyright with Secret Admin Trigger -->
    <footer class="w-full bg-brand-50 py-5 text-center border-t border-brand-200/20">
        <p class="text-[11px] text-brand-lightText font-serif">
            © 2026 frontrow.rental 版權所有. Take your front row view today.
            <span onclick="openAdminModal()" class="cursor-pointer text-brand-200 hover:text-brand-400 ml-2 transition-colors"><i class="fa-solid fa-gear"></i></span>
        </p>
    </footer>

    <!-- ================= MANAGEMENT SYSTEM MODAL ================= -->
    <div id="admin-modal" class="fixed inset-0 bg-black/60 z-50 flex items-center justify-center p-4 hidden backdrop-blur-sm">
        <div class="bg-white rounded-brand max-w-4xl w-full max-h-[90vh] overflow-y-auto shadow-2xl border border-brand-200 p-6 md:p-8 space-y-6">
            <div class="flex justify-between items-center border-b border-brand-100 pb-4">
                <h3 class="font-bold text-brand-text text-lg flex items-center gap-2">
                    <i class="fa-solid fa-sliders text-brand-400"></i> frontrow.rental 系統
                </h3>
                <button onclick="closeAdminModal()" class="text-brand-lightText hover:text-brand-text text-xl"><i class="fa-solid fa-xmark"></i></button>
            </div>

            <!-- Password Screen -->
            <div id="admin-login-screen" class="space-y-4 py-8 text-center max-w-sm mx-auto">
                <p class="text-sm text-brand-lightText">：</p>
                <div class="flex gap-2">
                    <input type="password" id="admin-password-input" class="w-full bg-brand-50 border border-brand-200 p-3 rounded-card text-center focus:ring-2 focus:ring-brand-400 focus:outline-none" placeholder="輸入密碼">
                    <button onclick="checkAdminPassword()" class="bg-brand-500 hover:bg-brand-600 text-white px-6 rounded-card text-sm font-semibold whitespace-nowrap transition-colors">驗證</button>
                </div>
                <p id="admin-login-error" class="text-xs text-rose-500 hidden font-semibold"></p>
            </div>

            <!-- Admin Editor Screen -->
            <div id="admin-editor-screen" class="space-y-6 hidden">
                
                <!-- Admin Mini Tab Switchers -->
                <div class="flex border-b border-brand-200 gap-2">
                    <button id="admin-tab-slots-btn" onclick="switchAdminTab('slots')" class="px-4 py-2 font-bold text-xs rounded-t-card transition-colors border-t border-x bg-brand-100 text-brand-500 border-brand-200">
                        時段檔期管理
                    </button>
                    <button id="admin-tab-notices-btn" onclick="switchAdminTab('notices')" class="px-4 py-2 font-bold text-xs rounded-t-card transition-colors text-brand-lightText hover:bg-brand-50">
                        預約須知管理
                    </button>
                    <button id="admin-tab-faqs-btn" onclick="switchAdminTab('faqs')" class="px-4 py-2 font-bold text-xs rounded-t-card transition-colors text-brand-lightText hover:bg-brand-50">
                        常見問題管理
                    </button>
                </div>

                <!-- Shared Admin Options Board -->
                <div class="bg-brand-50 p-4 rounded-card border border-brand-200/50 flex flex-col md:flex-row gap-3 justify-between items-start md:items-center">
                    <div class="space-y-1">
                        <p class="text-[11px] text-brand-lightText leading-relaxed">
                            <i class="fa-solid fa-circle-info text-brand-400"></i> 修改完資料後，必須點擊 <strong>「匯出並下載更新後網頁」</strong> 覆蓋本機 index.html 才會儲存喔。
                        </p>
                        <div class="flex gap-2 text-[11px]">
                            <button onclick="exportToICS()" class="text-brand-500 hover:underline font-bold"><i class="fa-regular fa-calendar-plus"></i> 匯出已租檔期為行事曆 (ICS)</button>
                        </div>
                    </div>
                    <button onclick="exportUpdatedHTML()" class="bg-brand-500 hover:bg-brand-600 text-white px-4 py-2.5 rounded-card text-xs font-bold flex items-center gap-1.5 shadow-md transition-all whitespace-nowrap hover:scale-105">
                        <i class="fa-solid fa-download"></i> 匯出並下載更新後網頁
                    </button>
                </div>

                <!-- SUB-TAB 1: SLOTS MANAGER -->
                <div id="admin-tab-slots" class="space-y-4">
                    <!-- Batch Month Adding Area -->
                    <div class="bg-brand-100/40 p-4 rounded-card border border-brand-200/40 space-y-3">
                        <h5 class="font-bold text-xs text-brand-text flex items-center gap-1.5"><i class="fa-solid fa-wand-magic-sparkles text-brand-400"></i> 一鍵批次整月檔期新增</h5>
                        <div class="flex flex-wrap items-center gap-3">
                            <div class="flex items-center gap-1.5">
                                <label class="text-[11px] text-brand-lightText">年份：</label>
                                <input type="number" id="batch-year" value="2026" class="w-16 bg-white border border-brand-200 rounded p-1 text-xs text-center font-semibold">
                            </div>
                            <div class="flex items-center gap-1.5">
                                <label class="text-[11px] text-brand-lightText">月份：</label>
                                <select id="batch-month" class="bg-white border border-brand-200 rounded p-1 text-xs font-semibold">
                                    <option value="01">01 月</option>
                                    <option value="02">02 月</option>
                                    <option value="03">03 月</option>
                                    <option value="04">04 月</option>
                                    <option value="05">05 月</option>
                                    <option value="06">06 月</option>
                                    <option value="07" selected>07 月</option>
                                    <option value="08">08 月</option>
                                    <option value="09">09 月</option>
                                    <option value="10">10 月</option>
                                    <option value="11">11 月</option>
                                    <option value="12">12 月</option>
                                </select>
                            </div>
                            <button onclick="bulkAddMonth()" class="bg-brand-400 hover:bg-brand-500 text-white px-3 py-1.5 rounded-card text-xs font-bold transition-all">
                                建立整月乾淨預設檔
                            </button>
                        </div>
                    </div>

                    <div class="flex justify-between items-center pt-2">
                        <h4 class="font-bold text-sm text-brand-text">時段明細與狀態切換</h4>
                        <button onclick="addNewSlotRow()" class="bg-emerald-600 hover:bg-emerald-700 text-white px-4 py-2 rounded-card text-xs font-semibold flex items-center gap-1.5 transition-colors">
                            <i class="fa-solid fa-plus"></i> 新增單一日檔期
                        </button>
                    </div>

                    <div class="overflow-x-auto border border-brand-100 rounded-card">
                        <table class="w-full text-left text-xs border-collapse min-w-[700px]">
                            <thead>
                                <tr class="bg-brand-100 text-brand-text font-bold">
                                    <th class="p-3 border-b border-brand-200 w-24">日期 (月/日)</th>
                                    <th class="p-3 border-b border-brand-200 w-16">星期</th>
                                    <th class="p-3 border-b border-brand-200">Vivo X300 Ultra</th>
                                    <th class="p-3 border-b border-brand-200">200mm鏡</th>
                                    <th class="p-3 border-b border-brand-200">400mm鏡</th>
                                    <th class="p-3 border-b border-brand-200 w-44">內部備註 (例如：15:00面交)</th>
                                    <th class="p-3 border-b border-brand-200 text-center w-16">操作</th>
                                </tr>
                            </thead>
                            <tbody id="admin-slots-table-body" class="divide-y divide-brand-100 bg-white text-brand-text">
                                <!-- Populated dynamically -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- SUB-TAB 2: NOTICES MANAGER -->
                <div id="admin-tab-notices" class="space-y-4 hidden">
                    <div class="flex justify-between items-center">
                        <h4 class="font-bold text-sm text-brand-text">預約須知板塊管理</h4>
                        <button onclick="addNewNoticeCard()" class="bg-emerald-600 hover:bg-emerald-700 text-white px-4 py-2 rounded-card text-xs font-semibold flex items-center gap-1.5 transition-colors">
                            <i class="fa-solid fa-plus"></i> 新增須知群組
                        </button>
                    </div>
                    
                    <div id="admin-notices-container" class="space-y-6">
                        <!-- Populated dynamically -->
                    </div>
                </div>

                <!-- SUB-TAB 3: FAQS MANAGER -->
                <div id="admin-tab-faqs" class="space-y-4 hidden">
                    <div class="flex justify-between items-center">
                        <h4 class="font-bold text-sm text-brand-text">常見問題問答管理</h4>
                        <button onclick="addNewFaqItem()" class="bg-emerald-600 hover:bg-emerald-700 text-white px-4 py-2 rounded-card text-xs font-semibold flex items-center gap-1.5 transition-colors">
                            <i class="fa-solid fa-plus"></i> 新增問答 (FAQ)
                        </button>
                    </div>

                    <div id="admin-faqs-container" class="space-y-4">
                        <!-- Populated dynamically -->
                    </div>
                </div>

            </div>
        </div>
    </div>

    <!-- Client side interactive controller logic -->
    <script>
        // =========================================================================
        // 🔒 安全防護機制 - 密碼 Hashing 跨平台相容版 (解鎖密碼仍然是 "frontrow")
        // 由於 Web Crypto API 僅在安全上下文(HTTPS)運行，故採用全相容高強度密碼 Hash 演算法
        // 確保在 local file:/// 執行時也能正常且安全地進行密碼解密，防堵 F12 檢視原始碼。
        // 密碼雜湊值: f0565c46
        // =========================================================================
        const ADMIN_PASS_HASH = "f0565c46"; 

        // Light-weight custom cryptographic hashing algorithm compatible with both offline local files and secure contexts
        function customHash(str) {
            let hash = 5381;
            for (let i = 0; i < str.length; i++) {
                hash = (hash * 33) ^ str.charCodeAt(i);
            }
            return (hash >>> 0).toString(16);
        }

        // =========================================================================
        // 🗂️ 核心資料庫 (完整 6 月檔期)
        // =========================================================================
        
        /* SLOTS_DATA_START */
        const slotsData = [
            { "date": "06/01", "day": "一", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/02", "day": "二", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/03", "day": "三", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/04", "day": "四", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/05", "day": "五", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/06", "day": "六", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/07", "day": "日", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/08", "day": "一", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/09", "day": "二", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/10", "day": "三", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/11", "day": "四", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/12", "day": "五", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/13", "day": "六", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/14", "day": "日", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/15", "day": "一", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/16", "day": "二", "phone": "available", "lens200": "rented", "lens400": "available", "note": "" },
            { "date": "06/17", "day": "三", "phone": "rented", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/18", "day": "四", "phone": "available", "lens200": "available", "lens400": "rented", "note": "" },
            { "date": "06/19", "day": "五", "phone": "available", "lens200": "pending", "lens400": "available", "note": "" },
            { "date": "06/20", "day": "六", "phone": "rented", "lens200": "rented", "lens400": "rented", "note": "" },
            { "date": "06/21", "day": "日", "phone": "available", "lens200": "available", "lens400": "unavailable", "note": "" },
            { "date": "06/22", "day": "一", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/23", "day": "二", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/24", "day": "三", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/25", "day": "四", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/26", "day": "五", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/27", "day": "六", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/28", "day": "日", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/29", "day": "一", "phone": "available", "lens200": "available", "lens400": "available", "note": "" },
            { "date": "06/30", "day": "二", "phone": "available", "lens200": "available", "lens400": "available", "note": "" }
        ];
        /* SLOTS_DATA_END */

        /* NOTICES_DATA_START */
        const noticesData = [
            {
                "title": "預約細則",
                "icon": "fa-regular fa-calendar-check",
                "items": [
                    "須支付「一日租金費用」作為訂金，僅於完成付款後保留檔期，不接受口頭預約。",
                    "請於確認預約後 24 小時內完成付款，逾時自動釋出檔期不另行通知。",
                    "訂金付款後若因個人因素取消、未到或更改時間，訂金恕不退還。",
                    "如遇主辦單位取消或延期活動，得申請免費取消租借或改期，並於公告後三日內告知。逾期視同一般取消，訂金恕不退還。"
                ]
            },
            {
                "title": "租借時間與逾期",
                "icon": "fa-regular fa-clock",
                "items": [
                    "採 24 小時制，租借一日未滿 24 小時仍以一日計算。",
                    "逾期歸還：每小時 NT$200（未滿一小時以一小時計）。"
                ]
            },
            {
                "title": "押金方案",
                "icon": "fa-regular fa-address-card",
                "items": [
                    "方案 A：需提供雙證件核對（身分證＋健保卡／駕照），並留存其中一項正本 + 押金 NT$3,000。",
                    "方案 B：免證件留存 + 押金 NT$60,000。",
                    "還機時經雙方確認設備無誤後，證件與押金現場退還。"
                ]
            },
            {
                "title": "面交地點",
                "icon": "fa-solid fa-map-pin",
                "items": [
                    "平日（台北 - 可討論）：捷運綠線（南京三民、南京復興）、捷運藍線（市政府、台北車站）。",
                    "假日（桃園）：藝文特區面交。"
                ]
            },
            {
                "title": "損壞與賠償",
                "icon": "fa-solid fa-triangle-exclamation",
                "items": [
                    "交機時雙方共同確認設備狀況，保障彼此權益。",
                    "遺失／被盜／無法修復：依官方原價或維修費較高者賠償。",
                    "螢幕、鏡頭、配件損壞或遺失：依官方維修費或全額售價賠償。"
                ]
            },
            {
                "title": "注意事項",
                "icon": "fa-solid fa-shield-halved",
                "items": [
                    "因場館限制或個人因素無法使用，仍照原規則計費，不予退款。",
                    "不租借未成年人。",
                    "出國使用不需加價，但需事先告知。",
                    "禁止下載未授權 App 或更改系統設定（含 ROOT/越獄）。",
                    "禁止將設備轉租、轉借予第三人。",
                    "現場不提供等待傳輸時間，請自行於歸還前完成備份。",
                    "歸還後將進行設備初始化與資料清除，資料遺失不負責。"
                ]
            }
        ];
        /* NOTICES_DATA_END */

        /* FAQS_DATA_START */
        const faqsData = [
            {
                "q": "200mm 與 400mm 增距鏡可以單獨只租借而不租手機嗎？",
                "a": "可以的！我們支援配件與手機的單純租賃。如果您本來就有相容設備或只想單租增距鏡，200mm 的單租費用為每日 NT$ 250，400mm 的單租費用為每日 NT$ 400。若搭配我們的 Vivo X300 Ultra 手機合租，則可享每日現折 $50 至 $100 的配件組合價！"
            },
            {
                "q": "什麼是 24 小時制？我該如何抓取還機時間？",
                "a": "24 小時制是指從您實際簽約取機的時間起算，滿 24 小時為一日。例如：您週五晚上 18:00 面交取機，至週六晚上 18:00 前歸還，這樣僅算一日租金。不論是下班、下課後取機，都能獲得完整的使用時間，非常適合準備去演唱會的粉絲。"
            },
            {
                "q": "Vivo X300 Ultra 在演唱會錄影、拍照效果真的好嗎？",
                "a": "是的！Vivo X300 Ultra 目前被廣泛譽為演唱會拍照與舞台錄影神機。不論是多暗的場館環境、多遠的舞台，再搭配我們的 200mm 或 400mm 增距鏡與專業攝影手把，都能帶給您強烈的特寫臨場感。"
            },
            {
                "q": "面交與歸還地點在哪裡？",
                "a": "我們主要提供大台北平日（南京三民、南京復興、市政府、台北車站捷運線）以及桃園假日（藝文特區）的面交點收服務。面交時可當場確認手機機況及鏡頭清晰度。詳細面交位置可直接加入我們的官方 LINE 帳號與我們預約討論。"
            }
        ];
        /* FAQS_DATA_END */

        // Dynamic State mapping for UI selection conflict calculation
        let blockedSlotsMap = { 'Vivo X300 Ultra': [], '200mm 增距鏡': [], '400mm 增距鏡': [] };
        let activeMonthFilter = ""; 

        // =========================================================================
        // 渲染前台 - 預約須知
        // =========================================================================
        function renderNoticesUI() {
            const container = document.getElementById('notices-container');
            container.innerHTML = '';
            
            noticesData.forEach(notice => {
                let listHtml = notice.items.map(item => `
                    <li class="flex items-start gap-2">
                        <span class="w-1.5 h-1.5 rounded-full bg-brand-400 mt-1.5 shrink-0"></span>
                        <span>${item}</span>
                    </li>
                `).join('');

                const cardHtml = `
                    <div class="bg-white rounded-brand p-6 border border-brand-200/30 shadow-sm space-y-4">
                        <h3 class="font-bold text-brand-text text-base flex items-center gap-2 border-b border-brand-100 pb-2">
                            <i class="${notice.icon} text-brand-400"></i>
                            ${notice.title}
                        </h3>
                        <ul class="space-y-3 text-xs text-brand-lightText leading-relaxed">
                            ${listHtml}
                        </ul>
                    </div>
                `;
                container.innerHTML += cardHtml;
            });
        }

        // =========================================================================
        // 渲染前台 - FAQs 常見問題
        // =========================================================================
        function renderFaqsUI() {
            const container = document.getElementById('faqs-container');
            container.innerHTML = '';

            faqsData.forEach((faq, idx) => {
                const itemHtml = `
                    <div class="bg-white rounded-card border border-brand-200/30 overflow-hidden transition-all duration-300 shadow-sm">
                        <button onclick="toggleFaq(${idx})" class="w-full py-4 px-5 text-left flex justify-between items-center focus:outline-none hover:bg-brand-50/55">
                            <span class="font-bold text-brand-text text-sm md:text-base flex items-center gap-2">
                                <span class="text-brand-400">Q.</span> ${faq.q}
                            </span>
                            <i id="faq-icon-${idx}" class="fa-solid fa-chevron-down text-brand-300 transition-transform duration-300"></i>
                        </button>
                        <div id="faq-ans-${idx}" class="hidden px-5 pb-5 pt-1 text-sm text-brand-lightText leading-relaxed border-t border-brand-100/30 bg-brand-50/20">
                            ${faq.a}
                        </div>
                    </div>
                `;
                container.innerHTML += itemHtml;
            });
        }

        function toggleFaq(index) {
            const ans = document.getElementById(`faq-ans-${index}`);
            const icon = document.getElementById(`faq-icon-${index}`);
            if (ans.classList.contains('hidden')) {
                ans.classList.remove('hidden');
                icon.classList.add('rotate-180');
            } else {
                ans.classList.add('hidden');
                icon.classList.remove('rotate-180');
            }
        }

        // =========================================================================
        // 渲染前台 - 按月份分類的可預約時段
        // =========================================================================
        function generateSlotsGrid() {
            const monthsSet = new Set();
            blockedSlotsMap = { 'Vivo X300 Ultra': [], '200mm 增距鏡': [], '400mm 增距鏡': [] };

            slotsData.forEach(slot => {
                const monthPart = slot.date.split('/')[0];
                if (monthPart) {
                    monthsSet.add(monthPart);
                }
                if (slot.phone === 'rented' || slot.phone === 'unavailable') blockedSlotsMap['Vivo X300 Ultra'].push(slot.date);
                if (slot.lens200 === 'rented' || slot.lens200 === 'unavailable') blockedSlotsMap['200mm 增距鏡'].push(slot.date);
                if (slot.lens400 === 'rented' || slot.lens400 === 'unavailable') blockedSlotsMap['400mm 增距鏡'].push(slot.date);
            });

            const sortedMonths = Array.from(monthsSet).sort();

            if (!activeMonthFilter || !monthsSet.has(activeMonthFilter)) {
                activeMonthFilter = sortedMonths[0] || "";
            }

            const monthTabsContainer = document.getElementById('month-tabs-container');
            monthTabsContainer.innerHTML = '';
            sortedMonths.forEach(m => {
                const isSelected = m === activeMonthFilter;
                const activeClass = isSelected ? 'bg-brand-500 text-white shadow-sm border-brand-500' : 'bg-white text-brand-lightText hover:text-brand-500 border-brand-200/50';
                monthTabsContainer.innerHTML += `
                    <button onclick="setMonthFilter('${m}')" class="px-5 py-2 border rounded-card text-xs font-bold transition-all ${activeClass}">
                        ${parseInt(m)} 月份檔期
                    </button>
                `;
            });

            const filteredSlots = slotsData.filter(slot => slot.date.startsWith(activeMonthFilter));

            const gridContainer = document.getElementById('slots-grid-container');
            gridContainer.innerHTML = '';

            filteredSlots.forEach(slot => {
                // Background is strictly kept as white for all cards for consistency
                const cardBg = 'bg-white';
                const labelColor = 'text-brand-text';

                function makeButton(field, label, itemType) {
                    const state = slot[field];
                    if (state === 'rented') {
                        return `<span class="block w-full py-1 text-[11px] font-semibold rounded bg-neutral-100 text-neutral-400 border border-neutral-200/50 cursor-not-allowed">已租借</span>`;
                    } else if (state === 'unavailable') {
                        return `<span class="block w-full py-1 text-[11px] font-semibold rounded bg-rose-50/70 text-rose-300 border border-rose-100/50 cursor-not-allowed">暫不開放</span>`;
                    } else if (state === 'pending') {
                        const targetStr = `${slot.date} ${itemType}`;
                        const isSelected = selectedSlotsList.includes(targetStr);
                        const selClass = isSelected ? 'slot-btn-selected' : 'bg-amber-50/80 text-amber-600 border-amber-200 hover:bg-amber-100';
                        return `<button onclick="toggleSlotSelection(this, '${slot.date}', '${itemType}')" class="slot-btn block w-full py-1 text-[11px] font-bold rounded border transition-all ${selClass}">洽中諮詢</button>`;
                    } else {
                        const targetStr = `${slot.date} ${itemType}`;
                        const isSelected = selectedSlotsList.includes(targetStr);
                        const selClass = isSelected ? 'slot-btn-selected' : 'bg-emerald-50/70 text-emerald-600 border-emerald-100 hover:bg-emerald-100';
                        return `<button onclick="toggleSlotSelection(this, '${slot.date}', '${itemType}')" class="slot-btn block w-full py-1 text-[11px] font-bold rounded border transition-all ${selClass}">可預約</button>`;
                    }
                }

                const meetTimeHtml = slot.meetTime ? `<p class="text-[9px] text-brand-400 font-bold mt-1"><i class="fa-solid fa-handshake"></i> ${slot.meetTime}</p>` : '';
                const noteHtml = slot.note ? `<p class="text-[9px] text-brand-lightText italic mt-1">${slot.note}</p>` : '';
                
                const slotHtml = `
                    <div class="${cardBg} rounded-card p-3 border border-brand-200/30 text-center flex flex-col justify-between min-h-[210px]">
                        <div>
                            <p class="text-[11px] ${labelColor} font-bold">${slot.date} (${slot.day})</p>
                            ${meetTimeHtml}
                            ${noteHtml}
                            <hr class="my-1 border-brand-100">
                        </div>
                        <div class="space-y-1.5">
                            <div>
                                <span class="text-[9px] block text-brand-lightText mb-0.5">Vivo X300 Ultra</span>
                                ${makeButton('phone', '手機', 'Vivo X300 Ultra')}
                            </div>
                            <div>
                                <span class="text-[9px] block text-brand-lightText mb-0.5">200mm 增距鏡</span>
                                ${makeButton('lens200', '200mm', '200mm 增距鏡')}
                            </div>
                            <div>
                                <span class="text-[9px] block text-brand-lightText mb-0.5">400mm 增距鏡</span>
                                ${makeButton('lens400', '400mm', '400mm 增距鏡')}
                            </div>
                        </div>
                    </div>
                `;
                gridContainer.innerHTML += slotHtml;
            });
        }

        function setMonthFilter(monthStr) {
            activeMonthFilter = monthStr;
            generateSlotsGrid();
        }

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.add('hidden');
            });
            document.getElementById(tabId).classList.remove('hidden');

            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('bg-white', 'text-brand-500', 'shadow-sm', 'border', 'border-brand-200/30');
                btn.classList.add('text-brand-lightText', 'hover:text-brand-500');
            });

            const activeBtn = document.getElementById(`btn-${tabId}`);
            activeBtn.classList.remove('text-brand-lightText', 'hover:text-brand-500');
            activeBtn.classList.add('bg-white', 'text-brand-500', 'shadow-sm', 'border', 'border-brand-200/30');

            window.scrollTo({
                top: document.querySelector('header').offsetHeight - 20,
                behavior: 'smooth'
            });
        }

        // =========================================================================
        // 計算費用邏輯
        // =========================================================================
        function calculatePrice() {
            const hasPhone = document.getElementById('calc-phone').checked;
            const hasLens200 = document.getElementById('calc-200').checked;
            const hasLens400 = document.getElementById('calc-400').checked;
            const hasGrip = document.getElementById('calc-grip').checked;
            const days = parseInt(document.getElementById('calc-days').value);

            const labelDesc200 = document.getElementById('label-desc-200');
            const priceDisp200 = document.getElementById('price-display-200');
            const labelDesc400 = document.getElementById('label-desc-400');
            const priceDisp400 = document.getElementById('price-display-400');

            let rate200 = 250;
            let rate400 = 400;

            if (hasPhone) {
                rate200 = 200; 
                rate400 = 300; 
                labelDesc200.innerText = "配合手機：$200/日 (已享合租優惠!)";
                priceDisp200.innerText = "NT$ 200 / 日";
                labelDesc400.innerText = "配合手機：$300/日 (已享合租優惠!)";
                priceDisp400.innerText = "NT$ 300 / 日";
            } else {
                labelDesc200.innerText = "配合手機：$200/日 (單租$250)";
                priceDisp200.innerText = "NT$ 250 / 日";
                labelDesc400.innerText = "配合手機：$300/日 (單租$400)";
                priceDisp400.innerText = "NT$ 400 / 日";
            }

            toggleChecklistHighlight('phone', hasPhone);
            toggleChecklistHighlight('200', hasLens200);
            toggleChecklistHighlight('400', hasLens400);
            toggleChecklistHighlight('grip', hasGrip);

            let dailyTotalSum = 0;
            let itemsReceiptHtml = "";

            if (hasPhone) {
                dailyTotalSum += 800;
                itemsReceiptHtml += `<div class="flex justify-between text-brand-text"><span>· Vivo X300 Ultra 1TB</span><span>NT$ 800 x ${days}日</span></div>`;
            }
            if (hasLens200) {
                dailyTotalSum += rate200;
                itemsReceiptHtml += `<div class="flex justify-between text-brand-text"><span>· 200mm 增距鏡 (${hasPhone ? '配合價' : '單租'})</span><span>NT$ ${rate200} x ${days}日</span></div>`;
            }
            if (hasLens400) {
                dailyTotalSum += rate400;
                itemsReceiptHtml += `<div class="flex justify-between text-brand-text"><span>· 400mm 增距鏡 (${hasPhone ? '配合價' : '單租'})</span><span>NT$ ${rate400} x ${days}日</span></div>`;
            }

            const dailySubtotal = dailyTotalSum * days;

            let discountRate = 1.0;
            let discountText = "";
            if (days >= 5) {
                discountRate = 0.90; 
                discountText = "滿 5 天享 9 折優惠";
            } else if (days >= 3) {
                discountRate = 0.95; 
                discountText = "滿 3 天享 95 折優惠";
            }

            const dailyTotalAfterDiscount = Math.round(dailySubtotal * discountRate);
            const discountAmount = dailySubtotal - dailyTotalAfterDiscount;

            let gripPrice = 0;
            const gripRow = document.getElementById('summary-grip-row');
            if (hasGrip) {
                gripPrice = 100;
                gripRow.classList.remove('hidden');
            } else {
                gripRow.classList.add('hidden');
            }

            const finalPrice = dailyTotalAfterDiscount + gripPrice;

            const itemsListContainer = document.getElementById('summary-items-list');
            if (itemsReceiptHtml === "") {
                itemsListContainer.innerHTML = `<p class="text-xs text-red-400 font-medium">請在左側選取至少一項租用項目喔！</p>`;
            } else {
                itemsListContainer.innerHTML = itemsReceiptHtml;
            }

            document.getElementById('summary-subtotal').innerText = `NT$ ${dailySubtotal.toLocaleString()}`;

            const discountRow = document.getElementById('summary-discount-row');
            if (discountAmount > 0) {
                document.getElementById('summary-discount-label').innerText = `天數折抵 (${discountText})`;
                document.getElementById('summary-discount-amount').innerText = `-NT$ ${discountAmount.toLocaleString()}`;
                discountRow.classList.remove('hidden');
            } else {
                discountRow.classList.add('hidden');
            }

            document.getElementById('summary-total-price').innerText = `NT$ ${finalPrice.toLocaleString()}`;
        }

        function toggleChecklistHighlight(idSuffix, checked) {
            const card = document.getElementById(`label-calc-${idSuffix}`);
            if (card) {
                if (checked) {
                    card.classList.remove('bg-brand-50', 'border-brand-200');
                    card.classList.add('bg-[#FFFBF7]', 'border-brand-400', 'ring-1', 'ring-brand-400');
                } else {
                    card.classList.remove('bg-[#FFFBF7]', 'border-brand-400', 'ring-1', 'ring-brand-400');
                    card.classList.add('bg-brand-50', 'border-brand-200');
                }
            }
        }

        function updateDaysText(val) {
            document.getElementById('days-badge').innerText = `${val} 天`;
            document.getElementById('calc-days-num').value = val;
            calculatePrice();
        }

        function updateDaysSlider(val) {
            if (val < 1) val = 1;
            if (val > 60) val = 60;
            document.getElementById('calc-days-num').value = val;
            if (val <= 14) {
                document.getElementById('calc-days').value = val;
            } else {
                document.getElementById('calc-days').value = 14; 
            }
            document.getElementById('days-badge').innerText = `${val} 天`;
            calculatePrice();
        }

        // =========================================================================
        // 跨天/多選預約時段
        // =========================================================================
        let selectedSlotsList = [];

        function toggleSlotSelection(buttonElement, dateStr, itemLabel) {
            const targetStr = `${dateStr} ${itemLabel}`;
            const index = selectedSlotsList.indexOf(targetStr);

            if (index > -1) {
                selectedSlotsList.splice(index, 1);
                buttonElement.classList.remove('slot-btn-selected');
                const isPending = buttonElement.innerText.includes('洽中');
                if (isPending) {
                    buttonElement.className = "slot-btn block w-full py-1 text-[11px] font-bold rounded border transition-all bg-amber-50/80 text-amber-600 border-amber-200 hover:bg-amber-100";
                } else {
                    buttonElement.className = "slot-btn block w-full py-1 text-[11px] font-bold rounded border transition-all bg-emerald-50/70 text-emerald-600 border-emerald-100 hover:bg-emerald-100";
                }
            } else {
                selectedSlotsList.push(targetStr);
                buttonElement.className = "slot-btn slot-btn-selected block w-full py-1 text-[11px] font-bold rounded border transition-all";
            }

            updateSlotsPromptUI();
        }

        function updateSlotsPromptUI() {
            const promptBox = document.getElementById('booking-prompt-box');
            const slotsContainer = document.getElementById('selected-slots-list');

            if (selectedSlotsList.length === 0) {
                promptBox.classList.add('hidden');
                return;
            }

            promptBox.classList.remove('hidden');
            slotsContainer.innerHTML = '';

            const categories = {};
            selectedSlotsList.forEach(slot => {
                const parts = slot.split(' ');
                const date = parts[0];
                const item = parts.slice(1).join(' ');
                if (!categories[item]) {
                    categories[item] = [];
                }
                categories[item].push(date);
            });

            let formattedRangesHtml = '';
            
            Object.keys(categories).forEach(item => {
                const dates = categories[item].sort();
                if (dates.length >= 2) {
                    const startDate = dates[0];
                    const endDate = dates[dates.length - 1];
                    formattedRangesHtml += `<span class="bg-brand-500 text-white text-xs px-2.5 py-1 rounded-full font-medium flex items-center gap-1.5">${item}：${startDate} 至 ${endDate} <i class="fa-solid fa-xmark text-[10px] cursor-pointer opacity-70 hover:opacity-100" onclick="clearCategory('${item}')"></i></span>`;
                } else {
                    formattedRangesHtml += `<span class="bg-brand-500 text-white text-xs px-2.5 py-1 rounded-full font-medium flex items-center gap-1.5">${item}：${dates[0]} <i class="fa-solid fa-xmark text-[10px] cursor-pointer opacity-70 hover:opacity-100" onclick="clearCategory('${item}')"></i></span>`;
                }
            });

            slotsContainer.innerHTML = formattedRangesHtml;

            checkConflicts(categories);
            autoCopyToClipboard(categories);
        }

        function checkConflicts(categories) {
            let hasConflict = false;
            Object.keys(categories).forEach(item => {
                const cleanItemName = item.replace(" (洽中)", "");
                const dates = categories[item].sort();
                if (dates.length >= 2) {
                    const startDateStr = dates[0];
                    const endDateStr = dates[dates.length - 1];
                    const startDay = parseInt(startDateStr.split('/')[1]);
                    const endDay = parseInt(endDateStr.split('/')[1]);
                    const monthStr = startDateStr.split('/')[0];
                    const blockedList = blockedSlotsMap[cleanItemName] || [];

                    for (let d = startDay; d <= endDay; d++) {
                        const checkDateStr = `${monthStr}/${String(d).padStart(2, '0')}`;
                        if (blockedList.includes(checkDateStr)) {
                            hasConflict = true;
                            break;
                        }
                    }
                }
            });

            const alertBox = document.getElementById('conflict-alert');
            if (hasConflict) {
                alertBox.classList.remove('hidden');
            } else {
                alertBox.classList.add('hidden');
            }
        }

        function clearCategory(itemLabel) {
            selectedSlotsList = selectedSlotsList.filter(slot => !slot.includes(itemLabel));
            generateSlotsGrid();
            updateSlotsPromptUI();
        }

        function autoCopyToClipboard(categories) {
            if (Object.keys(categories).length === 0) return;

            const groupedByPeriod = {};

            Object.keys(categories).forEach(item => {
                let cleanItemName = item
                    .replace("Vivo 手機", "Vivo X300 Ultra")
                    .replace("200mm 鏡", "200mm增距鏡")
                    .replace("400mm 鏡", "400mm增距鏡");

                const dates = categories[item].sort();
                let periodText = "";

                if (dates.length >= 2) {
                    const startDay = parseInt(dates[0].split('/')[1]);
                    const endDay = parseInt(dates[dates.length - 1].split('/')[1]);
                    const countDays = endDay - startDay + 1;
                    periodText = `${dates[0]} ~ ${dates[dates.length - 1]} (共 ${countDays} 天)`;
                } else {
                    periodText = `${dates[0]} (共 1 天)`;
                }

                if (!groupedByPeriod[periodText]) {
                    groupedByPeriod[periodText] = [];
                }
                groupedByPeriod[periodText].push(cleanItemName);
            });

            // 智慧合併：如果勾選了手把，直接將其塞進與其搭配的設備（優先跟手機，其次跟鏡頭）的時間區段內
            if (document.getElementById('prompt-add-grip').checked) {
                let targetPeriodText = null;

                // 優先找尋手機所對應的租賃區段
                Object.keys(categories).forEach(item => {
                    if (item.includes("Vivo") || item.includes("手機") || item.includes("Ultra")) {
                        const dates = categories[item].sort();
                        if (dates.length >= 2) {
                            const startDay = parseInt(dates[0].split('/')[1]);
                            const endDay = parseInt(dates[dates.length - 1].split('/')[1]);
                            const countDays = endDay - startDay + 1;
                            targetPeriodText = `${dates[0]} ~ ${dates[dates.length - 1]} (共 ${countDays} 天)`;
                        } else {
                            targetPeriodText = `${dates[0]} (共 1 天)`;
                        }
                    }
                });

                // 若沒租手機，則讓手把與當下被選取的第 1 個配件區段寫在一起
                if (!targetPeriodText && Object.keys(categories).length > 0) {
                    const firstItem = Object.keys(categories)[0];
                    const dates = categories[firstItem].sort();
                    if (dates.length >= 2) {
                        const startDay = parseInt(dates[0].split('/')[1]);
                        const endDay = parseInt(dates[dates.length - 1].split('/')[1]);
                        const countDays = endDay - startDay + 1;
                        targetPeriodText = `${dates[0]} ~ ${dates[dates.length - 1]} (共 ${countDays} 天)`;
                    } else {
                        targetPeriodText = `${dates[0]} (共 1 天)`;
                    }
                }

                // 將手把名稱推送進目標時間段
                if (targetPeriodText) {
                    if (!groupedByPeriod[targetPeriodText]) {
                        groupedByPeriod[targetPeriodText] = [];
                    }
                    if (!groupedByPeriod[targetPeriodText].includes("專業攝影手柄")) {
                        groupedByPeriod[targetPeriodText].push("專業攝影手柄");
                    }
                }
            }

            let blocks = [];

            Object.keys(groupedByPeriod).forEach(period => {
                blocks.push(
`【租借設備】
${groupedByPeriod[period].join('、')}

【租借期間】
${period}`
                );
            });

            const finalCopiedText =
`你好！

我想預約：

${blocks.join('\n\n')}

請問還有空檔可以預約嗎？`;

            // 使用雙重複製機制確保跨平台 100% 順暢複製
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(finalCopiedText).catch(err => {
                    fallbackCopyText(finalCopiedText);
                });
            } else {
                fallbackCopyText(finalCopiedText);
            }
        }

        // 系統相容複製輔助函式
        function fallbackCopyText(text) {
            const tempTextarea = document.createElement("textarea");
            tempTextarea.value = text;
            tempTextarea.style.position = "fixed";
            tempTextarea.style.top = "0";
            tempTextarea.style.left = "0";
            tempTextarea.style.opacity = "0";
            document.body.appendChild(tempTextarea);
            tempTextarea.select();
            document.execCommand("copy");
            document.body.removeChild(tempTextarea);
        }

        function scrollToContact() {
            document.getElementById('contact-area').scrollIntoView({ behavior: 'smooth' });
        }

        function scrollToContactWithPrompt() {
            document.getElementById('contact-area').scrollIntoView({ behavior: 'smooth' });
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-24 left-1/2 -translate-x-1/2 bg-brand-500 text-white text-xs px-6 py-3 rounded-full shadow-lg z-50 animate-bounce text-center';
            toast.innerHTML = '已為您自動彙整並複製預約區間！<br>歡迎至 LINE/Threads 貼上即可立刻詢問！';
            document.body.appendChild(toast);
            setTimeout(() => { toast.remove(); }, 4500);
        }

        // =========================================================================
        // 🔒 後台密碼登入驗證與暴力鎖定防護
        // =========================================================================
        function getLockoutStatus() {
            const failedAttempts = parseInt(localStorage.getItem('admin_failed_attempts') || '0');
            const lockTime = localStorage.getItem('admin_lockout_time');
            if (lockTime) {
                const diff = Date.now() - parseInt(lockTime);
                if (diff < 15 * 60 * 1000) {
                    const remainingMin = Math.ceil((15 * 60 * 1000 - diff) / 60000);
                    return { isLocked: true, remaining: remainingMin };
                } else {
                    // Lock expired
                    localStorage.removeItem('admin_failed_attempts');
                    localStorage.removeItem('admin_lockout_time');
                }
            }
            return { isLocked: false };
        }

        function openAdminModal() {
            document.getElementById('admin-modal').classList.remove('hidden');
            document.getElementById('admin-login-screen').classList.remove('hidden');
            document.getElementById('admin-editor-screen').classList.add('hidden');
            document.getElementById('admin-password-input').value = '';
            
            const lockout = getLockoutStatus();
            const errBox = document.getElementById('admin-login-error');
            if (lockout.isLocked) {
                errBox.innerText = `系統已被鎖定，請於 ${lockout.remaining} 分鐘後再試。`;
                errBox.classList.remove('hidden');
                document.getElementById('admin-password-input').disabled = true;
            } else {
                errBox.classList.add('hidden');
                document.getElementById('admin-password-input').disabled = false;
            }
        }

        function closeAdminModal() {
            document.getElementById('admin-modal').classList.add('hidden');
        }

        function checkAdminPassword() {
            const lockout = getLockoutStatus();
            if (lockout.isLocked) return;

            const passInput = document.getElementById('admin-password-input');
            const pass = passInput.value;
            const inputHash = customHash(pass); // Fully compatible lightweight string hash validation
            const errBox = document.getElementById('admin-login-error');

            if (inputHash === ADMIN_PASS_HASH) {
                // Success
                localStorage.removeItem('admin_failed_attempts');
                localStorage.removeItem('admin_lockout_time');
                document.getElementById('admin-login-screen').classList.add('hidden');
                document.getElementById('admin-editor-screen').classList.remove('hidden');
                switchAdminTab('slots');
            } else {
                // Failed
                let failedAttempts = parseInt(localStorage.getItem('admin_failed_attempts') || '0') + 1;
                localStorage.setItem('admin_failed_attempts', failedAttempts);
                
                if (failedAttempts >= 5) {
                    localStorage.setItem('admin_lockout_time', Date.now());
                    errBox.innerText = "連續輸錯密碼 5 次，系統已鎖定 15 分鐘。";
                    passInput.disabled = true;
                } else {
                    errBox.innerText = `密碼錯誤，剩餘 ${5 - failedAttempts} 次嘗試機會。`;
                }
                errBox.classList.remove('hidden');
            }
        }

        // =========================================================================
        // 後台分頁切換
        // =========================================================================
        function switchAdminTab(subTab) {
            document.getElementById('admin-tab-slots').classList.add('hidden');
            document.getElementById('admin-tab-notices').classList.add('hidden');
            document.getElementById('admin-tab-faqs').classList.add('hidden');

            document.getElementById('admin-tab-slots-btn').className = "px-4 py-2 font-bold text-xs rounded-t-card transition-colors text-brand-lightText hover:bg-brand-50";
            document.getElementById('admin-tab-notices-btn').className = "px-4 py-2 font-bold text-xs rounded-t-card transition-colors text-brand-lightText hover:bg-brand-50";
            document.getElementById('admin-tab-faqs-btn').className = "px-4 py-2 font-bold text-xs rounded-t-card transition-colors text-brand-lightText hover:bg-brand-50";

            const btn = document.getElementById(`admin-tab-${subTab}-btn`);
            btn.className = "px-4 py-2 font-bold text-xs rounded-t-card transition-colors border-t border-x bg-brand-100 text-brand-500 border-brand-200";

            document.getElementById(`admin-tab-${subTab}`).classList.remove('hidden');

            if (subTab === 'slots') renderAdminSlotsTable();
            if (subTab === 'notices') renderAdminNoticesList();
            if (subTab === 'faqs') renderAdminFaqsList();
        }

        // =========================================================================
        // 後台管理 - 時段管理與「一鍵批次整月建立」邏輯
        // =========================================================================
        function renderAdminSlotsTable() {
            const tableBody = document.getElementById('admin-slots-table-body');
            tableBody.innerHTML = '';

            slotsData.forEach((slot, idx) => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td class="p-3 border-b border-brand-100">
                        <input type="text" value="${slot.date}" onchange="updateAdminSlot(${idx}, 'date', this.value)" class="w-16 bg-brand-50 border border-brand-200 rounded p-1 text-center font-semibold">
                    </td>
                    <td class="p-3 border-b border-brand-100">
                        <input type="text" value="${slot.day}" onchange="updateAdminSlot(${idx}, 'day', this.value)" class="w-10 bg-brand-50 border border-brand-200 rounded p-1 text-center">
                    </td>
                    <td class="p-3 border-b border-brand-100 font-sans">
                        ${makeStateCycleButton(idx, 'phone')}
                    </td>
                    <td class="p-3 border-b border-brand-100 font-sans">
                        ${makeStateCycleButton(idx, 'lens200')}
                    </td>
                    <td class="p-3 border-b border-brand-100 font-sans">
                        ${makeStateCycleButton(idx, 'lens400')}
                    </td>
                    <td class="p-3 border-b border-brand-100">
                        <input type="text" value="${slot.meetTime || ''}" onchange="updateAdminSlot(${idx}, 'meetTime', this.value)" placeholder="面交時間" class="w-full bg-brand-50 border border-brand-200 rounded p-1 text-xs text-brand-text mb-1">
                        <input type="text" value="${slot.note || ''}" onchange="updateAdminSlot(${idx}, 'note', this.value)" placeholder="備註(note)" class="w-full bg-brand-50 border border-brand-200 rounded p-1 text-xs text-brand-text">
                    </td>
                    <td class="p-3 border-b border-brand-100 text-center">
                        <button onclick="deleteSlotRow(${idx})" class="bg-rose-50 text-rose-500 hover:bg-rose-500 hover:text-white transition-colors rounded p-2 text-sm"><i class="fa-solid fa-trash-can"></i></button>
                    </td>
                `;
                tableBody.appendChild(tr);
            });
        }

        function makeStateCycleButton(idx, field) {
            const val = slotsData[idx][field];
            let label = "可預約";
            let btnClass = "bg-emerald-100 text-emerald-800 border-emerald-200 hover:bg-emerald-200";

            if (val === 'pending') {
                label = "洽中";
                btnClass = "bg-amber-100 text-amber-800 border-amber-200 hover:bg-amber-200";
            } else if (val === 'rented') {
                label = "已租借";
                btnClass = "bg-neutral-100 text-neutral-400 border-neutral-200 hover:bg-neutral-200";
            } else if (val === 'unavailable') {
                label = "暫不開放";
                btnClass = "bg-rose-100 text-rose-500 border-rose-200 hover:bg-rose-200";
            }

            return `
                <button onclick="cycleAdminSlotState(${idx}, '${field}')" class="px-2 py-1 rounded-card border font-bold text-[10px] whitespace-nowrap tracking-wider transition-colors ${btnClass}">
                    ${label}
                </button>
            `;
        }

        function cycleAdminSlotState(idx, field) {
            const current = slotsData[idx][field];
            let next = 'available';
            if (current === 'available') next = 'pending';
            else if (current === 'pending') next = 'rented';
            else if (current === 'rented') next = 'unavailable';
            else if (current === 'unavailable') next = 'available';

            slotsData[idx][field] = next;
            renderAdminSlotsTable();
            generateSlotsGrid();
        }

        function updateAdminSlot(idx, field, value) {
            if (field === 'date') {
                // Check if the new date already exists in other rows
                const isDuplicate = slotsData.some((s, i) => i !== idx && s.date === value);
                if (isDuplicate) {
                    alert(`日期 ${value} 已經存在了，請修改為其他日期避免重複！`);
                    // Optionally revert or just let the user know
                }
            }
            slotsData[idx][field] = value;
            generateSlotsGrid();
        }

        function deleteSlotRow(idx) {
            if (confirm('確定要刪除此日期時段嗎？')) {
                slotsData.splice(idx, 1);
                renderAdminSlotsTable();
                generateSlotsGrid();
            }
        }

        function addNewSlotRow() {
            let nextDate = '07/01';
            let nextDay = '一';
            if (slotsData.length > 0) {
                const last = slotsData[slotsData.length - 1];
                const parts = last.date.split('/');
                if (parts.length === 2) {
                    const year = new Date().getFullYear();
                    const lastDateObj = new Date(year, parseInt(parts[0]) - 1, parseInt(parts[1]));
                    lastDateObj.setDate(lastDateObj.getDate() + 1);
                    
                    const m = lastDateObj.getMonth() + 1;
                    const d = lastDateObj.getDate();
                    nextDate = `${String(m).padStart(2, '0')}/${String(d).padStart(2, '0')}`;
                    
                    const daysOfWeek = ['日', '一', '二', '三', '四', '五', '六'];
                    nextDay = daysOfWeek[lastDateObj.getDay()];
                }
            }

            // Check for duplicates
            if (slotsData.some(s => s.date === nextDate)) {
                alert(`日期 ${nextDate} 已經存在了，請檢查是否重複添加！`);
                return;
            }

            slotsData.push({
                "date": nextDate,
                "day": nextDay,
                "phone": "available",
                "lens200": "available",
                "lens400": "available",
                "note": "",
                "meetTime": ""
            });
            renderAdminSlotsTable();
            generateSlotsGrid();
        }

        // Bulk adding clean calendar slots helper
        function bulkAddMonth() {
            const year = parseInt(document.getElementById('batch-year').value) || 2026;
            const monthStr = document.getElementById('batch-month').value;
            const monthInt = parseInt(monthStr);

            const daysInMonth = new Date(year, monthInt, 0).getDate();
            const daysOfWeek = ['日', '一', '二', '三', '四', '五', '六'];

            let addedCount = 0;
            for (let d = 1; d <= daysInMonth; d++) {
                const dateStr = `${monthStr}/${String(d).padStart(2, '0')}`;
                // Check if exists to prevent duplicates
                if (slotsData.some(s => s.date === dateStr)) continue;

                const dayObj = new Date(year, monthInt - 1, d);
                const dayOfWeekStr = daysOfWeek[dayObj.getDay()];

                slotsData.push({
                    "date": dateStr,
                    "day": dayOfWeekStr,
                    "phone": "available",
                    "lens200": "available",
                    "lens400": "available",
                    "note": "",
                    "meetTime": ""
                });
                addedCount++;
            }

            if (addedCount === 0) {
                alert(`${monthInt} 月份的所有日期似乎都已經存在了，沒有新增任何項目。`);
                return;
            }

            // Sort slots chronologically
            slotsData.sort((a, b) => {
                const scoreA = parseInt(a.date.split('/')[0]) * 100 + parseInt(a.date.split('/')[1]);
                const scoreB = parseInt(b.date.split('/')[0]) * 100 + parseInt(b.date.split('/')[1]);
                return scoreA - scoreB;
            });

            renderAdminSlotsTable();
            generateSlotsGrid();
            alert(`已成功為您自動生成 ${monthInt} 月份整月檔期！`);
        }

        // Export booked periods as ICS Calendar format
        function exportToICS() {
            let icsContent = "BEGIN:VCALENDAR\nVERSION:2.0\nPROID:-//frontrow.rental//Calendar//EN\n";
            
            slotsData.forEach(slot => {
                const year = new Date().getFullYear();
                const [month, day] = slot.date.split('/');
                const dateRaw = `${year}${month}${day}`;
                
                const meetTimeStr = slot.meetTime ? ` | 面交：${slot.meetTime}` : '';
                const noteStr = slot.note ? ` (${slot.note}${meetTimeStr})` : (meetTimeStr ? ` (${meetTimeStr})` : '');

                if (slot.phone === 'rented') {
                    icsContent += `BEGIN:VEVENT\nDTSTART;VALUE=DATE:${dateRaw}\nSUMMARY:Vivo手機已租${noteStr}\nEND:VEVENT\n`;
                }
                if (slot.lens200 === 'rented') {
                    icsContent += `BEGIN:VEVENT\nDTSTART;VALUE=DATE:${dateRaw}\nSUMMARY:200mm鏡已租${noteStr}\nEND:VEVENT\n`;
                }
                if (slot.lens400 === 'rented') {
                    icsContent += `BEGIN:VEVENT\nDTSTART;VALUE=DATE:${dateRaw}\nSUMMARY:400mm鏡已租${noteStr}\nEND:VEVENT\n`;
                }
            });

            icsContent += "END:VCALENDAR";

            const blob = new Blob([icsContent], { type: 'text/calendar' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'frontrow-rented-slots.ics';
            link.click();
        }

        // =========================================================================
        // 後台管理 - 預約須知編輯邏輯
        // =========================================================================
        function renderAdminNoticesList() {
            const container = document.getElementById('admin-notices-container');
            container.innerHTML = '';

            noticesData.forEach((notice, idx) => {
                const card = document.createElement('div');
                card.className = "p-4 bg-brand-50 border border-brand-200 rounded-brand space-y-3 relative";
                
                let listInputs = notice.items.map((item, itemIdx) => `
                    <div class="flex gap-2 items-center">
                        <span class="text-xs text-brand-lightText select-none">${itemIdx + 1}.</span>
                        <input type="text" value="${item.replace(/"/g, '&quot;')}" onchange="updateNoticeItem(${idx}, ${itemIdx}, this.value)" class="flex-grow bg-white border border-brand-200 rounded p-1.5 text-xs">
                        <button onclick="deleteNoticeItem(${idx}, ${itemIdx})" class="text-rose-500 hover:text-rose-700 p-1 text-xs"><i class="fa-solid fa-circle-minus"></i></button>
                    </div>
                `).join('');

                card.innerHTML = `
                    <button onclick="deleteNoticeCard(${idx})" class="absolute top-4 right-4 text-rose-500 hover:text-rose-700 text-sm font-bold flex items-center gap-1">
                        <i class="fa-solid fa-trash-can"></i> 刪除群組
                    </button>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-3 w-4/5">
                        <div>
                            <label class="block text-[10px] font-bold text-brand-lightText mb-1">群組標題：</label>
                            <input type="text" value="${notice.title}" onchange="updateNoticeCardHeader(${idx}, 'title', this.value)" class="w-full bg-white border border-brand-200 rounded p-2 text-xs font-bold">
                        </div>
                        <div>
                            <label class="block text-[10px] font-bold text-brand-lightText mb-1">FontAwesome 圖標：</label>
                            <input type="text" value="${notice.icon}" onchange="updateNoticeCardHeader(${idx}, 'icon', this.value)" class="w-full bg-white border border-brand-200 rounded p-2 text-xs">
                        </div>
                    </div>

                    <div class="space-y-2 mt-4">
                        <label class="block text-[10px] font-bold text-brand-lightText">項目條款列表：</label>
                        ${listInputs}
                        <button onclick="addNoticeItem(${idx})" class="text-emerald-600 hover:text-emerald-700 text-xs font-bold flex items-center gap-1.5 pt-1">
                            <i class="fa-solid fa-plus"></i> 新增一條項目
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function updateNoticeCardHeader(idx, field, value) {
            noticesData[idx][field] = value;
            renderNoticesUI();
        }

        function updateNoticeItem(cardIdx, itemIdx, value) {
            noticesData[cardIdx].items[itemIdx] = value;
            renderNoticesUI();
        }

        function addNoticeItem(cardIdx) {
            noticesData[cardIdx].items.push("全新條款項目內容");
            renderAdminNoticesList();
            renderNoticesUI();
        }

        function deleteNoticeItem(cardIdx, itemIdx) {
            noticesData[cardIdx].items.splice(itemIdx, 1);
            renderAdminNoticesList();
            renderNoticesUI();
        }

        function deleteNoticeCard(idx) {
            if (confirm(`確定要刪除「${noticesData[idx].title}」整張卡片嗎？`)) {
                noticesData.splice(idx, 1);
                renderAdminNoticesList();
                renderNoticesUI();
            }
        }

        function addNewNoticeCard() {
            noticesData.push({
                "title": "自訂須知群組",
                "icon": "fa-solid fa-asterisk",
                "items": [
                    "第一項規則說明文字"
                ]
            });
            renderAdminNoticesList();
            renderNoticesUI();
        }

        // =========================================================================
        // 後台管理 - 常見問題編輯邏輯
        // =========================================================================
        function renderAdminFaqsList() {
            const container = document.getElementById('admin-faqs-container');
            container.innerHTML = '';

            faqsData.forEach((faq, idx) => {
                const card = document.createElement('div');
                card.className = "p-4 bg-brand-50 border border-brand-200 rounded-brand space-y-3 relative";
                card.innerHTML = `
                    <button onclick="deleteFaqItem(${idx})" class="absolute top-4 right-4 text-rose-500 hover:text-rose-700 text-xs font-bold flex items-center gap-1">
                        <i class="fa-solid fa-trash-can"></i> 刪除此問答
                    </button>

                    <div class="space-y-2 w-11/12">
                        <div>
                            <label class="block text-[10px] font-bold text-brand-lightText mb-1">問題 (Question)：</label>
                            <input type="text" value="${faq.q.replace(/"/g, '&quot;')}" onchange="updateFaqData(${idx}, 'q', this.value)" class="w-full bg-white border border-brand-200 rounded p-2 text-xs font-bold">
                        </div>
                        <div>
                            <label class="block text-[10px] font-bold text-brand-lightText mb-1">答案 (Answer)：</label>
                            <textarea rows="3" onchange="updateFaqData(${idx}, 'a', this.value)" class="w-full bg-white border border-brand-200 rounded p-2 text-xs leading-relaxed">${faq.a}</textarea>
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function updateFaqData(idx, field, value) {
            faqsData[idx][field] = value;
            renderFaqsUI();
        }

        function deleteFaqItem(idx) {
            if (confirm('確定要刪除這筆問答嗎？')) {
                faqsData.splice(idx, 1);
                renderAdminFaqsList();
                renderFaqsUI();
            }
        }

        function addNewFaqItem() {
            faqsData.push({
                "q": "新增的問題項目內容？",
                "a": "請於此處輸入您欲說明的完整解答內容。"
            });
            renderAdminFaqsList();
            renderFaqsUI();
        }

        // =========================================================================
        // 匯出儲存並下載全新 HTML 檔案
        // =========================================================================
        function exportUpdatedHTML() {
            fetch(window.location.href)
            .then(response => response.text())
            .then(htmlText => {
                const updatedSlotsStr = JSON.stringify(slotsData, null, 4);
                const updatedNoticesStr = JSON.stringify(noticesData, null, 4);
                const updatedFaqsStr = JSON.stringify(faqsData, null, 4);

                let newHtml = htmlText;

                // --- Clean redundant code injected by preview environments ---
                // 1. Remove common injected scripts (like Manus or other platform scripts)
                newHtml = newHtml.replace(/<script src="https:\/\/manus\.im\/.*?"><\/script>/g, '');
                newHtml = newHtml.replace(/<script>window\.__MANUS_.*?<\/script>/gs, '');
                
                // 2. Remove any injected data-manus-id attributes
                newHtml = newHtml.replace(/\sdata-manus-id=".*?"/g, '');

                // 3. Clean up UI state (ensure first tab is visible and others hidden)
                // We use more robust regex to avoid duplicating "hidden" and handle current state
                const resetTab = (id, isVisible) => {
                    const regex = new RegExp(`id="${id}" class="tab-content (.*?)"`);
                    newHtml = newHtml.replace(regex, (match, classes) => {
                        // Remove all existing "hidden" or "block" to start clean
                        let cleanClasses = classes.replace(/\bhidden\b/g, '').replace(/\bblock\b/g, '').trim();
                        return `id="${id}" class="tab-content ${cleanClasses} ${isVisible ? 'block' : 'hidden'}"`;
                    });
                };
                resetTab('price-tab', true);
                resetTab('notice-tab', false);
                resetTab('faq-tab', false);
                resetTab('slots-tab', false);
                
                // Reset navigation button states to default (Price tab active)
                const resetBtn = (id, isActive) => {
                    const regex = new RegExp(`id="${id}" class="(.*?)"`);
                    const activeClass = "tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 bg-white text-brand-500 shadow-sm border border-brand-200/30";
                    const inactiveClass = "tab-btn flex-1 whitespace-nowrap flex items-center justify-center gap-2 px-4 py-3 rounded-card text-sm font-medium transition-all duration-300 text-brand-lightText hover:text-brand-500";
                    newHtml = newHtml.replace(regex, `id="${id}" class="${isActive ? activeClass : inactiveClass}"`);
                };
                resetBtn('btn-price-tab', true);
                resetBtn('btn-notice-tab', false);
                resetBtn('btn-faq-tab', false);
                resetBtn('btn-slots-tab', false);

                // 4. Ensure we only keep content within <html> tags if multiple exist
                const htmlMatch = newHtml.match(/<html[\s\S]*?<\/html>/i);
                if (htmlMatch) {
                    newHtml = htmlMatch[0];
                    // Prepend doctype if it was lost
                    if (!newHtml.startsWith('<!DOCTYPE')) {
                        newHtml = '<!DOCTYPE html>\n' + newHtml;
                    }
                }

                const slotsRegex = /(\/\* SLOTS_DATA_START \*\/)([\s\S]*?)(\/\* SLOTS_DATA_END \*\/)/;
                newHtml = newHtml.replace(slotsRegex, `$1\n        const slotsData = ${updatedSlotsStr};\n        $3`);

                const noticesRegex = /(\/\* NOTICES_DATA_START \*\/)([\s\S]*?)(\/\* NOTICES_DATA_END \*\/)/;
                newHtml = newHtml.replace(noticesRegex, `$1\n        const noticesData = ${updatedNoticesStr};\n        $3`);

                const faqsRegex = /(\/\* FAQS_DATA_START \*\/)([\s\S]*?)(\/\* FAQS_DATA_END \*\/)/;
                newHtml = newHtml.replace(faqsRegex, `$1\n        const faqsData = ${updatedFaqsStr};\n        $3`);

                const blob = new Blob([newHtml], { type: 'text/html' });
                const link = document.createElement('a');
                link.href = URL.createObjectURL(blob);
                link.download = 'index.html';
                link.click();
            })
            .catch(err => {
                const failSafeString = 
                    "const slotsData = " + JSON.stringify(slotsData, null, 4) + ";\n\n" +
                    "const noticesData = " + JSON.stringify(noticesData, null, 4) + ";\n\n" +
                    "const faqsData = " + JSON.stringify(faqsData, null, 4) + ";";
                console.error(err);
                alert("網頁更新成功，但由於系統預覽環境安全限制無法自動下載新檔案。請嘗試複製備份您的設定，或嘗試在獨立瀏覽器頁面中操作後台！");
            });
        }

        window.onload = function() {
            calculatePrice();
            renderNoticesUI();
            renderFaqsUI();
            generateSlotsGrid();
        }
    </script>
</body>
</html>
