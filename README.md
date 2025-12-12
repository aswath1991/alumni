<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alumni Club: Strategic Revitalization Analysis</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Plotly.js -->
    <script src="https://cdn.plot.ly/plotly-2.27.0.min.js"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700;900&display=swap" rel="stylesheet">

    <!-- 
        Palette: Vibrant & Energetic (Electric Blue, Lime, Hot Pink) 
        Inspired by "Energetic & Playful" concepts to drive the "Youth" narrative.
        Background: #f0f9ff (Alice Blue)
        Primary Text: #0f172a (Slate 900)
        Card BG: #ffffff
        
        Colors:
        Blue: #2563eb
        Lime: #84cc16
        Pink: #db2777
        Teal: #0d9488
        Warning/Red: #dc2626
    -->

    <style>
        body { font-family: 'Roboto', sans-serif; background-color: #f0f9ff; color: #0f172a; }
        .chart-container { 
            position: relative; 
            width: 100%; 
            max-width: 650px; 
            margin-left: auto; 
            margin-right: auto; 
            height: 400px; 
            max-height: 400px; 
        }
        @media (max-width: 768px) {
            .chart-container { height: 300px; }
        }
        .stat-card { transition: transform 0.2s; }
        .stat-card:hover { transform: translateY(-5px); }
        .gradient-text {
            background: linear-gradient(to right, #2563eb, #db2777);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    </style>
    
    <!-- 
        NARRATIVE PLAN:
        1. Executive Summary: The need for youth & revenue.
        2. Demographics: The "Silver Tsunami" visualization.
        3. Financials: The "Profit Paradox" (High Sales, Low Net).
        4. Participation: Who plays what?
        5. Recommendations: Strategic Roadmap cards.
        
        NO SVG USED. NO MERMAID JS USED.
    -->
</head>
<body class="antialiased">

    <!-- Header / Hook -->
    <header class="bg-white shadow-lg sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
            <h1 class="text-2xl font-black tracking-tight text-slate-800">ALUMNI CLUB <span class="text-blue-600">2.0</span></h1>
            <nav class="hidden md:flex space-x-6">
                <a href="#demographics" class="text-slate-600 hover:text-blue-600 font-bold">Demographics</a>
                <a href="#finance" class="text-slate-600 hover:text-blue-600 font-bold">Financials</a>
                <a href="#activities" class="text-slate-600 hover:text-blue-600 font-bold">Activities</a>
                <a href="#strategy" class="px-4 py-2 bg-blue-600 text-white rounded-full font-bold hover:bg-blue-700 transition">The Strategy</a>
            </nav>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 space-y-20">

        <!-- Intro Section -->
        <section class="text-center space-y-6">
            <h2 class="text-4xl md:text-6xl font-black mb-4">Bridging the <span class="gradient-text">Generation Gap</span></h2>
            <p class="text-xl text-slate-600 max-w-3xl mx-auto">
                Our club is facing a critical juncture. While we have a loyal base, our membership is aging rapidly, and our core revenue streams are underperforming. 
                To ensure longevity, we must pivot to attract <strong>working professionals</strong> and <strong>youthful energy</strong> while optimizing our pricing models.
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-10">
                <div class="bg-white p-6 rounded-xl shadow-md border-b-4 border-blue-600 stat-card">
                    <p class="text-slate-500 font-bold uppercase text-sm">Members > 60 Years</p>
                    <p class="text-5xl font-black text-slate-800">67%</p>
                    <p class="text-xs text-red-500 mt-2">Critical Aging Risk</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-md border-b-4 border-lime-500 stat-card">
                    <p class="text-slate-500 font-bold uppercase text-sm">Zero Spend Members</p>
                    <p class="text-5xl font-black text-slate-800">30%</p>
                    <p class="text-xs text-slate-400 mt-2">481 Inactive Members</p>
                </div>
                <div class="bg-white p-6 rounded-xl shadow-md border-b-4 border-pink-500 stat-card">
                    <p class="text-slate-500 font-bold uppercase text-sm">Bar Net Income</p>
                    <p class="text-5xl font-black text-red-600">-7.4L</p>
                    <p class="text-xs text-slate-400 mt-2">Loss despite high volume</p>
                </div>
            </div>
        </section>

        <!-- Section 1: Demographics -->
        <section id="demographics" class="scroll-mt-24">
            <div class="mb-8 border-l-8 border-blue-600 pl-4">
                <h3 class="text-3xl font-bold text-slate-800">The "Silver Tsunami"</h3>
                <p class="text-slate-600 mt-2">
                    An analysis of our 1,621 members reveals a heavy skew towards retirement age. 
                    The "Under 30" category represents a negligible fraction of our base. 
                    Without an infusion of younger members, activity levels will naturally decline over the next decade.
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Chart: Age Distribution -->
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Membership by Age Group</h4>
                    <div class="chart-container">
                        <canvas id="ageChart"></canvas>
                    </div>
                    <p class="text-sm text-slate-500 mt-4 bg-slate-50 p-3 rounded">
                        <strong>Goal: Compare.</strong> The contrast is stark. The 65+ cohort (882 members) is nearly <strong>9x larger</strong> than the 31-40 cohort (98 members).
                    </p>
                </div>

                <!-- Chart: Membership Categories -->
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Membership Composition</h4>
                    <div class="chart-container">
                        <canvas id="categoryChart"></canvas>
                    </div>
                    <p class="text-sm text-slate-500 mt-4 bg-slate-50 p-3 rounded">
                        <strong>Goal: Inform.</strong> "Regular Members" dominate. Corporate membership is virtually non-existent (only 5), representing a massive <strong>untapped revenue opportunity</strong>.
                    </p>
                </div>
            </div>
        </section>

        <!-- Section 2: Financials -->
        <section id="finance" class="scroll-mt-24">
            <div class="mb-8 border-l-8 border-pink-500 pl-4">
                <h3 class="text-3xl font-bold text-slate-800">The Profitability Paradox</h3>
                <p class="text-slate-600 mt-2">
                    We are moving money, but not keeping it. While Catering and Bar sales (Gross) are high, the Net Income tells a different story. 
                    The Bar is actually <strong>losing money</strong> on every transaction when overheads are factored in.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <!-- Chart: Gross vs Net -->
                <div class="bg-white p-6 rounded-2xl shadow-lg lg:col-span-2">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Revenue Reality Check: Gross vs. Net (Rs Lakhs)</h4>
                    <div class="chart-container" style="max-width: 100%;">
                        <div id="financePlotly"></div>
                    </div>
                    <p class="text-sm text-slate-500 mt-4 bg-slate-50 p-3 rounded">
                        <strong>Goal: Compare.</strong> Note the Bar column. 92.13L in revenue results in a -7.45L loss. Catering is barely breaking even (4.6% margin). Subscription fees are currently subsidizing cheap food and drink.
                    </p>
                </div>

                <!-- Chart: Spending Tiers -->
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Member Engagement by Spend</h4>
                    <div class="chart-container">
                        <canvas id="spendChart"></canvas>
                    </div>
                    <p class="text-sm text-slate-500 mt-4 bg-slate-50 p-3 rounded">
                        <strong>Goal: Organize.</strong> The largest single group is "Zero Spend" (481 members). We need to activate this group or reconsider their membership value.
                    </p>
                </div>
            </div>
        </section>

        <!-- Section 3: Activities -->
        <section id="activities" class="scroll-mt-24">
            <div class="mb-8 border-l-8 border-lime-500 pl-4">
                <h3 class="text-3xl font-bold text-slate-800">Activity & Engagement</h3>
                <p class="text-slate-600 mt-2">
                    Badminton is our primary revenue driver in sports. However, "Club Activities" like Cards and Bridge are heavily dominated by the senior demographic. 
                    Tennis participation is alarmingly low.
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Chart: Sports Revenue -->
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Sports Revenue Contribution</h4>
                    <div class="chart-container">
                        <canvas id="sportsPie"></canvas>
                    </div>
                </div>

                <!-- Chart: Demographics by Sport -->
                <div class="bg-white p-6 rounded-2xl shadow-lg">
                    <h4 class="text-lg font-bold text-slate-700 mb-4">Age Profile by Activity</h4>
                    <div class="chart-container">
                        <canvas id="activityStack"></canvas>
                    </div>
                    <p class="text-sm text-slate-500 mt-4 bg-slate-50 p-3 rounded">
                        <strong>Goal: Relationships.</strong> Notice that Cards and Bridge are almost exclusively played by members >60. Badminton is the only sport with significant <50 participation.
                    </p>
                </div>
            </div>
        </section>

        <!-- Section 4: Strategy Recommendations -->
        <section id="strategy" class="bg-slate-900 text-white -mx-4 sm:-mx-6 lg:-mx-8 px-4 sm:px-6 lg:px-8 py-16 mt-12">
            <div class="max-w-7xl mx-auto">
                <div class="text-center mb-12">
                    <h3 class="text-3xl md:text-5xl font-black text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-lime-400">The Path Forward</h3>
                    <p class="text-slate-400 mt-4 text-xl">Turning Analysis into Action</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                    
                    <!-- Card 1 -->
                    <div class="bg-slate-800 p-6 rounded-xl border border-slate-700 hover:border-blue-500 transition duration-300">
                        <div class="w-12 h-12 bg-blue-600 rounded-lg flex items-center justify-center mb-4 text-2xl">🚀</div>
                        <h4 class="text-xl font-bold mb-2">The "Young Alumni" Tier</h4>
                        <p class="text-slate-400 text-sm mb-4">Create a specific, lower-entry-cost membership for under-35s. Offer monthly payment plans instead of lump sums.</p>
                        <ul class="text-sm text-blue-300 space-y-1">
                            <li>• Networking Nights</li>
                            <li>• Co-working Space Access</li>
                            <li>• Mentorship Programs</li>
                        </ul>
                    </div>

                    <!-- Card 2 -->
                    <div class="bg-slate-800 p-6 rounded-xl border border-slate-700 hover:border-lime-500 transition duration-300">
                        <div class="w-12 h-12 bg-lime-600 rounded-lg flex items-center justify-center mb-4 text-2xl">🏢</div>
                        <h4 class="text-xl font-bold mb-2">Corporate Outreach</h4>
                        <p class="text-slate-400 text-sm mb-4">We only have 5 corporate members. This is a massive gap. Target local tech firms for bulk memberships.</p>
                        <ul class="text-sm text-lime-300 space-y-1">
                            <li>• Offsite Meeting Packages</li>
                            <li>• "Happy Hour" Deals</li>
                            <li>• Team Building Sports Days</li>
                        </ul>
                    </div>

                    <!-- Card 3 -->
                    <div class="bg-slate-800 p-6 rounded-xl border border-slate-700 hover:border-pink-500 transition duration-300">
                        <div class="w-12 h-12 bg-pink-600 rounded-lg flex items-center justify-center mb-4 text-2xl">📈</div>
                        <h4 class="text-xl font-bold mb-2">Price Correction</h4>
                        <p class="text-slate-400 text-sm mb-4">The Bar cannot lose money. A 15-20% price increase is necessary to break even, positioning it as "Premium" rather than "Cheap".</p>
                        <ul class="text-sm text-pink-300 space-y-1">
                            <li>• Introduce Premium Spirits</li>
                            <li>• Guest Cover Charges</li>
                            <li>• Revamp Menu for higher margin</li>
                        </ul>
                    </div>

                    <!-- Card 4 -->
                    <div class="bg-slate-800 p-6 rounded-xl border border-slate-700 hover:border-teal-500 transition duration-300">
                        <div class="w-12 h-12 bg-teal-600 rounded-lg flex items-center justify-center mb-4 text-2xl">🎾</div>
                        <h4 class="text-xl font-bold mb-2">Modernize Activities</h4>
                        <p class="text-slate-400 text-sm mb-4">Bridge doesn't attract 30-year-olds. We need high-energy, social activities.</p>
                        <ul class="text-sm text-teal-300 space-y-1">
                            <li>• Pickleball (Trendy/Social)</li>
                            <li>• Weekend Cricket Leagues</li>
                            <li>• Trivia & Karaoke Nights</li>
                        </ul>
                    </div>

                </div>
            </div>
        </section>
        
        <footer class="text-center text-slate-400 py-8 text-sm">
            <p>Generated for Alumni Club Strategy Review | Data Sources: 2024-25 Financial & Demographic Records</p>
        </footer>

    </main>

    <!-- SCRIPT SECTION -->
    <script>
        // --- UTILITY FUNCTIONS ---
        
        // Label Wrapper for Chart.js (16 char limit)
        const wrapLabel = (str) => {
            if (str.length <= 16) return str;
            const words = str.split(' ');
            const lines = [];
            let currentLine = words[0];

            for (let i = 1; i < words.length; i++) {
                if (currentLine.length + 1 + words[i].length <= 16) {
                    currentLine += " " + words[i];
                } else {
                    lines.push(currentLine);
                    currentLine = words[i];
                }
            }
            lines.push(currentLine);
            return lines;
        };

        // Standard Tooltip Config
        const tooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels[item.dataIndex];
                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            }
        };

        // --- DATA SETS ---

        // 1. Demographics Data
        const ageLabels = ["< 30", "31-40", "41-50", "51-60", "61-65", "> 65"];
        const ageData = [24, 98, 128, 287, 202, 882];
        const categoryLabels = ["Corporate", "Life Member", "Regular Member"];
        const categoryData = [5, 556, 1060];

        // 2. Financial Data
        const depts = ["Bar", "Catering", "Sports", "Chambers", "Subscription"];
        const grossIncome = [92.13, 282.34, 28.92, 29.19, 56.55]; // Subscription gross approx same as net for visual
        const netIncome = [-7.45, 12.98, 2.98, 12.25, 56.55];

        const spendLabels = ["0 (Inactive)", "< 2,500", "2,500-5k", "5k-10k", "10k-25k", "25k-50k", "50k-1L", "1L-2L"];
        const spendData = [481, 268, 227, 284, 242, 81, 26, 12];

        // 3. Activity Data
        const sportsRevenueLabels = ["Badminton", "Billiards", "Cards/Bridge", "Cricket", "Fitness", "Gym", "Tennis"];
        const sportsRevenueData = [10.47, 1.86, 6.86, 4.52, 3.7, 1.14, 0.37];

        // Activity Age Breakdown (Approx based on provided sheets)
        // Normalizing data for stacked bar: <50, 50-65, >65
        const activityStackLabels = ["Badminton", "Tennis", "Cards/Bridge", "Billiards"];
        const actUnder50 = [10, 4, 1, 0]; // Sampled counts
        const act50to65 = [29, 12, 6, 0];
        const actOver65 = [54, 2, 80, 12]; // Cards heavily weighted >65

        // --- CHART GENERATION ---

        // Chart 1: Age Distribution (Bar)
        const ctxAge = document.getElementById('ageChart').getContext('2d');
        new Chart(ctxAge, {
            type: 'bar',
            data: {
                labels: ageLabels.map(wrapLabel),
                datasets: [{
                    label: 'Number of Members',
                    data: ageData,
                    backgroundColor: ['#2563eb', '#2563eb', '#2563eb', '#84cc16', '#db2777', '#dc2626'],
                    borderRadius: 4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false },
                    tooltip: tooltipConfig
                },
                scales: {
                    y: { beginAtZero: true, grid: { color: '#e2e8f0' } },
                    x: { grid: { display: false } }
                }
            }
        });

        // Chart 2: Categories (Doughnut)
        const ctxCat = document.getElementById('categoryChart').getContext('2d');
        new Chart(ctxCat, {
            type: 'doughnut',
            data: {
                labels: categoryLabels.map(wrapLabel),
                datasets: [{
                    data: categoryData,
                    backgroundColor: ['#db2777', '#84cc16', '#2563eb'],
                    borderWidth: 0
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: tooltipConfig
                }
            }
        });

        // Chart 3: Gross vs Net (Plotly Grouped Bar)
        // Using Plotly for better side-by-side comparison
        const trace1 = {
            x: depts,
            y: grossIncome,
            name: 'Gross Income',
            type: 'bar',
            marker: { color: '#2563eb' } // Blue
        };
        const trace2 = {
            x: depts,
            y: netIncome,
            name: 'Net Income',
            type: 'bar',
            marker: { color: '#84cc16' } // Lime
        };
        
        const plotlyLayout = {
            barmode: 'group',
            margin: { t: 20, b: 40, l: 40, r: 20 },
            paper_bgcolor: 'rgba(0,0,0,0)',
            plot_bgcolor: 'rgba(0,0,0,0)',
            showlegend: true,
            legend: { orientation: 'h', y: 1.1 },
            font: { family: 'Roboto, sans-serif' }
        };
        
        const plotlyConfig = { responsive: true, displayModeBar: false, renderer: 'canvas' }; // Force Canvas
        Plotly.newPlot('financePlotly', [trace1, trace2], plotlyLayout, plotlyConfig);


        // Chart 4: Spend Tiers (Horizontal Bar)
        const ctxSpend = document.getElementById('spendChart').getContext('2d');
        new Chart(ctxSpend, {
            type: 'bar',
            indexAxis: 'y',
            data: {
                labels: spendLabels.map(wrapLabel),
                datasets: [{
                    label: 'Member Count',
                    data: spendData,
                    backgroundColor: (ctx) => {
                        const val = ctx.raw;
                        // Highlight 0 spenders in Red/Pink
                        if(ctx.dataIndex === 0) return '#db2777'; 
                        return '#0d9488';
                    },
                    borderRadius: 4
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { display: false },
                    tooltip: tooltipConfig
                },
                scales: {
                    x: { beginAtZero: true, grid: { color: '#e2e8f0' } },
                    y: { grid: { display: false } }
                }
            }
        });

        // Chart 5: Sports Revenue (Pie)
        const ctxSports = document.getElementById('sportsPie').getContext('2d');
        new Chart(ctxSports, {
            type: 'pie',
            data: {
                labels: sportsRevenueLabels.map(wrapLabel),
                datasets: [{
                    data: sportsRevenueData,
                    backgroundColor: [
                        '#2563eb', // Badminton (Blue)
                        '#64748b', // Billiards
                        '#db2777', // Cards (Pink)
                        '#84cc16', // Cricket (Lime)
                        '#0d9488', // Fitness (Teal)
                        '#f59e0b', // Gym
                        '#ef4444'  // Tennis
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'right', labels: { boxWidth: 12 } },
                    tooltip: tooltipConfig
                }
            }
        });

        // Chart 6: Activity Age Stack (Stacked Bar)
        const ctxStack = document.getElementById('activityStack').getContext('2d');
        new Chart(ctxStack, {
            type: 'bar',
            data: {
                labels: activityStackLabels.map(wrapLabel),
                datasets: [
                    {
                        label: '< 50 Years',
                        data: actUnder50,
                        backgroundColor: '#84cc16', // Youth = Lime
                    },
                    {
                        label: '50-65 Years',
                        data: act50to65,
                        backgroundColor: '#2563eb', // Mid = Blue
                    },
                    {
                        label: '> 65 Years',
                        data: actOver65,
                        backgroundColor: '#db2777', // Senior = Pink
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' },
                    tooltip: tooltipConfig
                },
                scales: {
                    x: { stacked: true, grid: { display: false } },
                    y: { stacked: true, beginAtZero: true, grid: { color: '#e2e8f0' } }
                }
            }
        });

    </script>
</body>
</html>