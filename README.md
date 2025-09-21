<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>हरी बातें - एक स्थानीय सस्टेनेबिलिटी पॉडकास्ट</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Earthy Greens & Warm Neutrals -->
    <!-- Application Structure Plan: A top-down narrative SPA. It starts with the mission, defines the problem, introduces the podcast, features an interactive episode explorer, a visual process timeline, an impact dashboard with charts, and concludes with future vision and CTA. This structure guides the user through a compelling story, making the information more engaging and understandable than a linear presentation. -->
    <!-- Visualization & Content Choices: Problem -> Inform -> Text with Icons -> Clarity. Episodes -> Organize -> Interactive Cards (HTML/JS) -> Engagement. Process -> Organize -> CSS-based Flowchart -> Visual Flow. Impact -> Compare/Inform -> Doughnut/Bar/Line Charts (Chart.js/Canvas) -> Data-driven storytelling. Team -> Inform -> Simple Cards. The goal is to transform static points into interactive, exploratory elements. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Poppins', sans-serif;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 450px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 350px;
        }
        @media (min-width: 640px) {
            .chart-container {
                height: 350px;
                max-height: 400px;
            }
        }
        .nav-link {
            transition: color 0.3s, border-bottom-color 0.3s;
            border-bottom: 2px solid transparent;
        }
        .nav-link:hover, .nav-link.active {
            color: #166534; /* green-800 */
            border-bottom-color: #166534; /* green-800 */
        }
        .step-item {
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .step-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
        }
    </style>
</head>
<body class="bg-stone-50 text-gray-800">

    <header class="bg-white/80 backdrop-blur-lg sticky top-0 z-50 shadow-sm">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <h1 class="text-2xl font-bold text-green-800">हरी बातें</h1>
            <div class="hidden md:flex space-x-8">
                <a href="#problem" class="nav-link font-semibold">समस्या</a>
                <a href="#solution" class="nav-link font-semibold">समाधान</a>
                <a href="#episodes" class="nav-link font-semibold">एपिसोड</a>
                <a href="#impact" class="nav-link font-semibold">प्रभाव</a>
                <a href="#vision" class="nav-link font-semibold">हमारा लक्ष्य</a>
            </div>
            <a href="#contact" class="bg-green-700 text-white px-5 py-2 rounded-full font-bold hover:bg-green-800 transition-colors">हमसे जुड़ें</a>
        </nav>
    </header>

    <main class="container mx-auto px-6 py-12">

        <section id="hero" class="text-center py-16">
            <h1 class="text-5xl md:text-7xl font-bold text-green-900 leading-tight">आवाज़ बदलो, कल बदलो</h1>
            <p class="mt-4 text-xl text-gray-600 max-w-3xl mx-auto">एक स्थानीय सस्टेनेबिलिटी पॉडकास्ट सीरीज़, जो सरल कहानियों के माध्यम से हमारे समुदाय में बदलाव ला रही है।</p>
        </section>

        <section id="problem" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold">जलवायु परिवर्तन पर बात क्यों नहीं होती?</h2>
                <p class="mt-2 text-lg text-gray-600">हमारे समुदायों में जागरूकता की एक बड़ी खाई है।</p>
            </div>
            <div class="grid md:grid-cols-3 gap-8 text-center">
                <div class="bg-white p-8 rounded-xl shadow-lg">
                    <div class="text-4xl mb-4">🚫</div>
                    <h3 class="text-2xl font-bold mb-2">सीमित पहुँच</h3>
                    <p class="text-gray-600">ज़रूरी जानकारी हमारे गाँवों और कस्बों तक पहुँच ही नहीं पाती।</p>
                </div>
                <div class="bg-white p-8 rounded-xl shadow-lg">
                    <div class="text-4xl mb-4">📜</div>
                    <h3 class="text-2xl font-bold mb-2">पुराने तरीके</h3>
                    <p class="text-gray-600">पोस्टर और पर्चे अक्सर अनदेखे रह जाते हैं और हर किसी से नहीं जुड़ पाते।</p>
                </div>
                <div class="bg-white p-8 rounded-xl shadow-lg">
                    <div class="text-4xl mb-4">❓</div>
                    <h3 class="text-2xl font-bold mb-2">मुश्किल विषय</h3>
                    <p class="text-gray-600">'नवीकरणीय ऊर्जा' जैसे शब्द आम जीवन से जुड़े हुए नहीं लगते।</p>
                </div>
            </div>
        </section>

        <section id="solution" class="py-16 bg-green-50 rounded-2xl">
            <div class="grid md:grid-cols-2 gap-8 items-center">
                <div class="px-8">
                    <h2 class="text-4xl font-bold mb-4">हमारा समाधान: 'हरी बातें'</h2>
                    <p class="text-lg text-gray-700 mb-6">हमारी अपनी हिंदी भाषा में, समुदाय द्वारा संचालित एक पॉडकास्ट सीरीज़। हम मुश्किल विषयों को सरल, मज़ेदार और अपनेपन वाली कहानियों में बदल रहे हैं।</p>
                    <div class="space-y-4">
                        <p class="flex items-center text-lg"><span class="text-2xl mr-3">🎧</span>सरल ऑडियो कहानियाँ: बिना पढ़े भी आसानी से समझने योग्य।</p>
                        <p class="flex items-center text-lg"><span class="text-2xl mr-3">🤝</span>अपनेपन वाली बातें: हमारे आसपास के लोगों की सच्ची कहानियाँ।</p>
                        <p class="flex items-center text-lg"><span class="text-2xl mr-3">📱</span>कहीं भी सुनें: WhatsApp या स्कूल के लाउडस्पीकर पर।</p>
                    </div>
                </div>
                <div class="px-8 flex justify-center items-center">
                    <div class="bg-white p-6 rounded-full shadow-2xl">
                        <div class="bg-green-700 w-48 h-48 rounded-full flex justify-center items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-24 w-24 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z" /></svg>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="episodes" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold">हमारे एपिसोड्स को जानें</h2>
                <p class="mt-2 text-lg text-gray-600">ऐसे विषय जो हमारे समुदाय के लिए सबसे ज़्यादा मायने रखते हैं। अधिक जानने के लिए किसी भी विषय पर क्लिक करें।</p>
            </div>
            <div id="episode-grid" class="grid md:grid-cols-3 lg:grid-cols-5 gap-6">
            </div>
        </section>
        
        <div id="episode-details" class="hidden bg-white p-8 rounded-xl shadow-xl mt-8 ring-1 ring-green-200">
            <div class="flex justify-between items-start">
                <div>
                    <h3 id="details-title" class="text-2xl font-bold text-green-800"></h3>
                    <p id="details-desc" class="mt-2 text-gray-600"></p>
                </div>
                <button id="close-details" class="text-2xl text-gray-500 hover:text-gray-800">&times;</button>
            </div>
        </div>

        <section id="process" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold">आईडिया से आपके कानों तक</h2>
                <p class="mt-2 text-lg text-gray-600">हमारी 5-चरणीय प्रक्रिया जो हर एपिसोड को जीवंत करती है।</p>
            </div>
            <div class="flex flex-col md:flex-row justify-center items-center gap-4 md:gap-0">
                <div class="step-item bg-white p-6 rounded-lg shadow-md w-full md:w-56 text-center">
                    <div class="text-3xl font-bold text-green-600 mb-2">1</div>
                    <h3 class="font-semibold">विषय चुनना</h3>
                    <p class="text-sm text-gray-500">स्थानीय मुद्दों की पहचान और रिसर्च।</p>
                </div>
                <div class="text-2xl text-green-500 hidden md:block mx-4">→</div>
                 <div class="text-2xl text-green-500 md:hidden my-2">↓</div>
                <div class="step-item bg-white p-6 rounded-lg shadow-md w-full md:w-56 text-center">
                    <div class="text-3xl font-bold text-green-600 mb-2">2</div>
                    <h3 class="font-semibold">स्क्रिप्ट लिखना</h3>
                    <p class="text-sm text-gray-500">हिंदी में सरल, कहानी-आधारित स्क्रिप्ट।</p>
                </div>
                <div class="text-2xl text-green-500 hidden md:block mx-4">→</div>
                 <div class="text-2xl text-green-500 md:hidden my-2">↓</div>
                <div class="step-item bg-white p-6 rounded-lg shadow-md w-full md:w-56 text-center">
                    <div class="text-3xl font-bold text-green-600 mb-2">3</div>
                    <h3 class="font-semibold">रिकॉर्डिंग और एडिटिंग</h3>
                    <p class="text-sm text-gray-500">साधारण फ़ोन और मुफ़्त सॉफ्टवेयर का उपयोग।</p>
                </div>
                <div class="text-2xl text-green-500 hidden md:block mx-4">→</div>
                 <div class="text-2xl text-green-500 md:hidden my-2">↓</div>
                <div class="step-item bg-white p-6 rounded-lg shadow-md w-full md:w-56 text-center">
                    <div class="text-3xl font-bold text-green-600 mb-2">4</div>
                    <h3 class="font-semibold">एपिसोड फैलाना</h3>
                    <p class="text-sm text-gray-500">WhatsApp, स्कूल, और रेडियो पर साझा करना।</p>
                </div>
                 <div class="text-2xl text-green-500 hidden md:block mx-4">→</div>
                 <div class="text-2xl text-green-500 md:hidden my-2">↓</div>
                <div class="step-item bg-white p-6 rounded-lg shadow-md w-full md:w-56 text-center">
                    <div class="text-3xl font-bold text-green-600 mb-2">5</div>
                    <h3 class="font-semibold">श्रोताओं की राय</h3>
                    <p class="text-sm text-gray-500">फीडबैक एकत्र करना और सुधार करना।</p>
                </div>
            </div>
        </section>

        <section id="impact" class="py-16 bg-white rounded-2xl">
             <div class="text-center mb-12">
                <h2 class="text-4xl font-bold">हमारा अनुमानित प्रभाव</h2>
                <p class="mt-2 text-lg text-gray-600">संख्याओं के माध्यम से हमारे काम का असर देखें।</p>
            </div>
            <div class="grid lg:grid-cols-3 gap-12">
                <div class="text-center">
                    <h3 class="text-2xl font-bold mb-4">पहुँच (Reach)</h3>
                    <div class="chart-container"><canvas id="reachChart"></canvas></div>
                    <p class="mt-4 text-gray-600">हमारा लक्ष्य विभिन्न चैनलों के माध्यम से हर घर तक पहुँचना है।</p>
                </div>
                <div class="text-center">
                    <h3 class="text-2xl font-bold mb-4">बचाई गई ऊर्जा (kWh)</h3>
                    <div class="chart-container"><canvas id="energyChart"></canvas></div>
                    <p class="mt-4 text-gray-600">अगर 20 परिवार भी बदलाव अपनाते हैं तो अनुमानित ऊर्जा बचत।</p>
                </div>
                <div class="text-center">
                    <h3 class="text-2xl font-bold mb-4">जुड़ाव (Engagement)</h3>
                    <div class="chart-container"><canvas id="engagementChart"></canvas></div>
                    <p class="mt-4 text-gray-600">समय के साथ श्रोताओं के फीडबैक में अनुमानित वृद्धि।</p>
                </div>
            </div>
        </section>
        
        <section id="vision" class="py-16">
            <div class="text-center mb-12">
                <h2 class="text-4xl font-bold">एक पॉडकास्ट से एक आंदोलन तक</h2>
                <p class="mt-2 text-lg text-gray-600">हमारा दृष्टिकोण कुछ एपिसोड से कहीं आगे है।</p>
            </div>
            <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
                 <div class="bg-green-100 p-8 rounded-lg text-center">
                    <h3 class="text-xl font-bold text-green-900 mb-2">युवाओं का 'क्लाइमेट रेडियो क्लब'</h3>
                    <p>छात्रों को अपने एपिसोड बनाने के लिए प्रशिक्षित करना, ताकि वे खुद जलवायु संचारक बन सकें।</p>
                </div>
                <div class="bg-green-100 p-8 rounded-lg text-center">
                    <h3 class="text-xl font-bold text-green-900 mb-2">एक 'ओपन-सोर्स' गाइड</h3>
                    <p>एक सरल गाइड बनाना ताकि अन्य NGO और स्कूल भी इसे दोहरा सकें।</p>
                </div>
                <div class="bg-green-100 p-8 rounded-lg text-center">
                    <h3 class="text-xl font-bold text-green-900 mb-2">अन्य स्थानीय भाषाओं में सीज़न</h3>
                    <p>अपनी पहुँच और प्रभाव को बढ़ाने के लिए पॉडकास्ट को अन्य भाषाओं में विस्तारित करना।</p>
                </div>
            </div>
        </section>

    </main>

    <footer id="contact" class="bg-gray-800 text-white">
        <div class="container mx-auto px-6 py-12">
            <div class="grid md:grid-cols-2 gap-8">
                <div>
                    <h2 class="text-3xl font-bold mb-4">आइए, मिलकर इस बातचीत को बदलें।</h2>
                    <p class="text-gray-400">हमें भागीदारों, स्वयंसेवकों और आपके सुझावों की तलाश है।</p>
                </div>
                <div class="space-y-4">
                    <h3 class="text-xl font-semibold">टीम से मिलिए</h3>
                    <div class="flex space-x-4">
                        <div class="bg-gray-700 px-3 py-1 rounded-full">पूजा (कहानीकार)</div>
                        <div class="bg-gray-700 px-3 py-1 rounded-full">रोहन (प्रोडक्शन)</div>
                        <div class="bg-gray-700 px-3 py-1 rounded-full">आयशा (आउटरीच)</div>
                    </div>
                     <h3 class="text-xl font-semibold mt-6">संपर्क करें</h3>
                     <p>📧 ईमेल: your.email@example.com</p>
                     <p>📱 WhatsApp: +91 XXXXX XXXXX</p>
                </div>
            </div>
            <div class="mt-12 border-t border-gray-700 pt-6 text-center text-gray-500">
                <p>&copy; 2025 हरी बातें. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            
            const episodeData = [
                { icon: '☀️', title: 'सोलर ऊर्जा', description: 'किसानों और घरों के लिए सोलर ऊर्जा पर केंद्रित। जानें कैसे सोलर लाइट और पंप पैसे और पर्यावरण दोनों को बचा सकते हैं, और इसे अपनाने के लिए सरल कदम क्या हैं।' },
                { icon: '💧', title: 'पानी की समझदारी', description: 'जल संरक्षण के महत्व पर चर्चा। इस एपिसोड में घर और खेतों में पानी बचाने के सरल और प्रभावी उपाय बताए गए हैं, जिन्हें कोई भी अपना सकता है।' },
                { icon: '🛍️', title: 'प्लास्टिक को ना', description: 'प्लास्टिक प्रदूषण के खतरे और उसके विकल्पों पर एक महत्वपूर्ण कड़ी। हम प्लास्टिक की थैलियों और बोतलों के व्यावहारिक विकल्पों पर बात करते हैं।' },
                { icon: '💡', title: 'बिजली बचाओ', description: 'ऊर्जा संरक्षण पर एक व्यावहारिक गाइड। घर पर बिजली के उपयोग में छोटे-छोटे बदलाव कैसे एक बड़ा अंतर ला सकते हैं, इस पर सरल टिप्स दिए गए हैं।' },
                { icon: '♻️', title: 'कचरे से कमाई', description: 'अपशिष्ट प्रबंधन को एक अवसर के रूप में प्रस्तुत करता है। इस एपिसोड में घर के कचरे से खाद बनाने और उसे प्रभावी ढंग से प्रबंधित करने की कहानियाँ हैं।' }
            ];

            const episodeGrid = document.getElementById('episode-grid');
            const detailsSection = document.getElementById('episode-details');
            const detailsTitle = document.getElementById('details-title');
            const detailsDesc = document.getElementById('details-desc');
            const closeDetailsBtn = document.getElementById('close-details');
            
            episodeData.forEach((ep, index) => {
                const card = document.createElement('div');
                card.className = 'bg-white p-6 rounded-xl shadow-lg text-center cursor-pointer transition-transform transform hover:scale-105';
                card.innerHTML = `<div class="text-5xl mb-4">${ep.icon}</div><h3 class="text-xl font-bold">${ep.title}</h3>`;
                card.addEventListener('click', () => {
                    detailsTitle.textContent = `${ep.icon} ${ep.title}`;
                    detailsDesc.textContent = ep.description;
                    detailsSection.classList.remove('hidden');
                });
                episodeGrid.appendChild(card);
            });
            
            closeDetailsBtn.addEventListener('click', () => {
                detailsSection.classList.add('hidden');
            });

            const chartOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom',
                        labels: {
                            padding: 20,
                            boxWidth: 15,
                            font: {
                                size: 14,
                                family: 'Poppins'
                            }
                        }
                    },
                },
            };

            const reachCtx = document.getElementById('reachChart').getContext('2d');
            new Chart(reachCtx, {
                type: 'doughnut',
                data: {
                    labels: ['WhatsApp', 'स्कूल लाउडस्पीकर', 'कम्युनिटी रेडियो'],
                    datasets: [{
                        label: 'पहुँच',
                        data: [50, 30, 20],
                        backgroundColor: ['#22c55e', '#16a34a', '#15803d'],
                        borderColor: '#ffffff',
                        borderWidth: 4
                    }]
                },
                options: chartOptions
            });

            const energyCtx = document.getElementById('energyChart').getContext('2d');
            new Chart(energyCtx, {
                type: 'bar',
                data: {
                    labels: ['महीना 1', 'महीना 2', 'महीना 3', 'महीना 4'],
                    datasets: [{
                        label: 'अनुमानित kWh बचत',
                        data: [50, 80, 120, 180],
                        backgroundColor: '#16a34a',
                        borderRadius: 5
                    }]
                },
                options: { ...chartOptions, scales: { y: { beginAtZero: true } } }
            });

            const engagementCtx = document.getElementById('engagementChart').getContext('2d');
            new Chart(engagementCtx, {
                type: 'line',
                data: {
                    labels: ['सप्ताह 1', 'सप्ताह 2', 'सप्ताह 3', 'सप्ताह 4', 'सप्ताह 5'],
                    datasets: [{
                        label: 'श्रोताओं का फीडबैक',
                        data: [5, 12, 18, 25, 40],
                        borderColor: '#166534',
                        backgroundColor: 'rgba(22, 163, 74, 0.1)',
                        fill: true,
                        tension: 0.4
                    }]
                },
                options: { ...chartOptions, scales: { y: { beginAtZero: true } } }
            });
            
            const navLinks = document.querySelectorAll('.nav-link');
            window.addEventListener('scroll', () => {
                let current = '';
                document.querySelectorAll('section').forEach(section => {
                    const sectionTop = section.offsetTop;
                    if(pageYOffset >= sectionTop - 100) {
                        current = section.getAttribute('id');
                    }
                });

                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if(link.getAttribute('href').includes(current)) {
                        link.classList.add('active');
                    }
                });
            });
        });
    </script>
</body>
</html>
