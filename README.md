<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ethiopia Create Studio - 3D Animation & Learning</title>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;900&family=Scheherazade+New:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* --- 1. CSS Reset and Base Styles --- */
        :root {
            --primary-color: #007bff; /* Vibrant Blue */
            --secondary-color: #28a745; /* Green for success/learning */
            --accent-color: #ffc107; /* Yellow/Gold for highlight */
            --dark-bg: #1a1a2e;
            --light-bg: #f8f9fa;
            --text-color: #333;
            --panel-bg: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Nunito', sans-serif;
            background-color: var(--light-bg);
            color: var(--text-color);
            line-height: 1.6;
        }

        /* Amharic font fallback/specific styling if available in the system */
        .amharic-text {
            font-family: 'Scheherazade New', 'Noto Sans Ethiopic', sans-serif;
        }

        /* --- 2. Layout and Navigation --- */
        .header {
            background-color: var(--dark-bg);
            color: white;
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .header h1 {
            font-size: 1.8rem;
            margin: 0;
        }

        .nav button {
            background: none;
            border: 1px solid white;
            color: white;
            padding: 8px 15px;
            margin-left: 10px;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s;
        }

        .nav button:hover {
            background: var(--primary-color);
            border-color: var(--primary-color);
        }

        .main-container {
            padding: 30px;
            display: flex;
            gap: 30px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .sidebar, .main-content {
            background: var(--panel-bg);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }

        .sidebar {
            flex: 0 0 250px; /* Fixed width sidebar */
        }

        .main-content {
            flex-grow: 1;
        }

        /* --- 3. Sidebar Navigation --- */
        .sidebar h2 {
            color: var(--primary-color);
            margin-bottom: 20px;
            border-bottom: 2px solid var(--accent-color);
            padding-bottom: 5px;
            font-size: 1.2rem;
        }

        .sidebar a {
            display: block;
            padding: 12px 0;
            color: var(--text-color);
            text-decoration: none;
            border-left: 3px solid transparent;
            transition: all 0.2s;
            font-weight: 600;
        }

        .sidebar a:hover, .sidebar .active {
            color: var(--primary-color);
            border-left: 3px solid var(--primary-color);
        }

        /* --- 4. Dashboard View --- */
        .dashboard-card {
            background: var(--panel-bg);
            border: 1px solid #ddd;
            padding: 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
        }

        .dashboard-card h3 {
            color: var(--primary-color);
            margin-bottom: 10px;
        }

        .stat-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        .stat-box {
            background: var(--primary-color);
            color: white;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
        }
        .stat-box strong {
            display: block;
            font-size: 1.8rem;
        }

        /* --- 5. 3D Studio Placeholder Styles --- */
        .studio-interface {
            display: grid;
            grid-template-columns: 1fr 3fr;
            gap: 20px;
            min-height: 600px;
        }

        .asset-panel {
            background: #f0f0f0;
            padding: 15px;
            border-radius: 8px;
            overflow-y: auto;
        }

        .asset-panel h4 {
            border-bottom: 1px solid #ccc;
            padding-bottom: 5px;
            margin-bottom: 10px;
            color: var(--dark-bg);
        }

        .asset-item {
            background: white;
            border: 1px solid #ddd;
            padding: 10px;
            margin-bottom: 8px;
            text-align: center;
            cursor: grab;
            border-radius: 5px;
            transition: transform 0.1s;
        }

        .asset-item:active {
            transform: scale(1.05);
            box-shadow: 0 0 10px var(--accent-color);
        }

        .viewport {
            background: linear-gradient(to bottom right, #e0f7fa, #b2ebf2); /* Sky/Environment look */
            border: 3px dashed var(--primary-color);
            border-radius: 8px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            color: rgba(0, 0, 0, 0.4);
            font-size: 1.5rem;
        }

        .placeholder-char {
            position: absolute;
            width: 80px;
            height: 100px;
            background-color: var(--secondary-color);
            border-radius: 10px 10px 5px 5px;
            bottom: 50px;
            left: 50%;
            transform: translateX(-50%);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            padding-top: 5px;
            color: white;
            font-weight: bold;
            border: 2px solid #1e7e34;
        }
        .lip-sync-indicator {
            position: absolute;
            bottom: 5px;
            width: 10px;
            height: 10px;
            background-color: red;
            border-radius: 50%;
            animation: pulse 1s infinite alternate;
        }

        @keyframes pulse {
            from { opacity: 0.5; transform: scale(1); }
            to { opacity: 1; transform: scale(1.5); }
        }

        /* --- 6. Learning Module Styles --- */
        .learning-module {
            padding: 20px;
            background: #e8f5e9; /* Light Green */
            border-radius: 10px;
        }

        .module-tabs button {
            padding: 10px 20px;
            margin-right: 10px;
            border: 1px solid var(--secondary-color);
            background: white;
            cursor: pointer;
            border-radius: 5px 5px 0 0;
            transition: background 0.3s;
        }
        .module-tabs button.active {
            background: var(--secondary-color);
            color: white;
            font-weight: bold;
        }
        .module-content {
            background: white;
            padding: 25px;
            border: 1px solid var(--secondary-color);
            border-top: none;
            border-radius: 0 5px 5px 5px;
        }

        .alphabet-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(90px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .letter-card {
            background: #fff3e0; /* Light Orange */
            border: 2px solid var(--accent-color);
            padding: 15px;
            text-align: center;
            cursor: pointer;
            border-radius: 8px;
            transition: transform 0.1s, box-shadow 0.2s;
        }
        .letter-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.15);
        }
        .letter-card span {
            display: block;
            font-size: 1.8rem;
            font-weight: bold;
        }
        .letter-card small {
            font-size: 0.75rem;
            color: #555;
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header class="header">
        <h1>🇪🇹 Ethiopia Create Studio</h1>
        <nav class="nav">
            <button onclick="showSection('dashboard')">Dashboard</button>
            <button onclick="showSection('parent-teacher')">Parents/Teachers</button>
        </nav>
    </header>

    <div class="main-container">
        <!-- Sidebar Navigation -->
        <aside class="sidebar">
            <h2>Modules</h2>
            <a href="#" class="active" data-section="studio" onclick="showSection('studio'); return false;">🎨 3D Animation Studio</a>
            <a href="#" data-section="learning" onclick="showSection('learning'); return false;">📚 Bilingual Learning</a>
            <a href="#" data-section="dashboard" onclick="showSection('dashboard'); return false;">🏠 My Dashboard</a>
            <a href="#" data-section="progress" onclick="showSection('progress'); return false;">📈 Progress Tracker</a>
        </aside>

        <!-- Content Area -->
        <main class="main-content">
            
            <!-- 1. Dashboard View -->
            <section id="dashboard" class="content-section">
                <h2>Welcome Back, Young Creator!</h2>
                <p>Your journey in creativity and storytelling starts here. Choose a module from the left sidebar to begin.</p>
                
                <div class="stat-grid">
                    <div class="stat-box">
                        <strong>5</strong>
                        <span>Stories Created</span>
                    </div>
                    <div class="stat-box" style="background-color: var(--secondary-color);">
                        <strong>12</strong>
                        <span>Amharic Words Mastered</span>
                    </div>
                    <div class="stat-box" style="background-color: var(--accent-color); color: var(--text-color);">
                        <strong>3h 45m</strong>
                        <span>Time Spent Creating</span>
                    </div>
                </div>

                <div class="dashboard-card" style="margin-top: 30px;">
                    <h3>Latest Project Snapshot</h3>
                    <p><em>"The Lion, the Goat, and the River Crossing"</em> - Needs Lip Sync Finalized.</p>
                    <button style="background-color: var(--primary-color); color: white; padding: 10px 20px; border: none; border-radius: 5px; margin-top: 10px;" onclick="showSection('studio')">Continue Editing</button>
                </div>
            </section>

            <!-- 2. 3D Animation Studio View -->
            <section id="studio" class="content-section" style="display: none;">
                <h2>🎨 3D Animation & Story Builder</h2>
                <div class="studio-interface">
                    
                    <!-- Asset Panel (Drag & Drop Simulation) -->
                    <aside class="asset-panel">
                        <h4>Characters & Assets</h4>
                        <div class="asset-item" draggable="true" data-asset="lion">Lion Character</div>
                        <div class="asset-item" draggable="true" data-asset="tree">Eucalyptus Tree</div>
                        <div class="asset-item" draggable="true" data-asset="house">Traditional Hut</div>
                        <div class="asset-item" draggable="true" data-asset="sun">Sun/Sky Object</div>

                        <h4>Templates & Actions</h4>
                        <button style="width: 100%; padding: 8px; margin-top: 10px; background: var(--accent-color); border: none; cursor: pointer;" onclick="alert('Narrative structure loaded!')">Load Story Template</button>
                        <button style="width: 100%; padding: 8px; margin-top: 5px; background: #ff9800; color: white; border: none; cursor: pointer;" onclick="recordVoice()">🎤 Record Narration</button>
                    </aside>

                    <!-- Viewport / Canvas -->
                    <div class="viewport">
                        <div id="animation-canvas">
                            <p>Drag assets here to start building your scene!</p>
                            <!-- Placeholder for animated character -->
                            <div class="placeholder-char" id="anim-char">
                                Lion
                                <div class="lip-sync-indicator" id="lip-sync" style="display: none;"></div>
                            </div>
                        </div>
                        <div style="position: absolute; top: 20px; right: 20px; background: white; padding: 5px 10px; border-radius: 5px; box-shadow: 0 2px 5px rgba(0,0,0,0.2);">
                            Cartoon Rendering Mode: ON
                        </div>
                    </div>

                </div>
                <div style="margin-top: 15px; text-align: right;">
                    <button style="background-color: var(--secondary-color); color: white; padding: 12px 25px; border: none; border-radius: 5px; cursor: pointer;">Render & Save Story</button>
                </div>
            </section>
            
            <!-- 3. Bilingual Learning Module View -->
            <section id="learning" class="content-section" style="display: none;">
                <h2>📚 Bilingual Literacy Lab (Amharic & English)</h2>
                
                <div class="module-tabs">
                    <button id="tab-am" class="active" onclick="switchLearningTab('amharic')">Amharic (አማርኛ)</button>
                    <button id="tab-en" onclick="switchLearningTab('english')">English</button>
                </div>

                <div class="module-content">
                    <div id="content-amharic">
                        <h3>Explore the Amharic Alphabet (ፊደል)</h3>
                        <p>Click on any letter to hear the sound and see the word example.</p>
                        <div class="alphabet-grid" id="amharic-letters">
                            <!-- Letters populated by JS -->
                        </div>
                    </div>
                    
                    <div id="content-english" style="display: none;">
                        <h3>Explore English Words</h3>
                        <p>Click on any word to hear the pronunciation.</p>
                        <div class="alphabet-grid" id="english-words">
                            <!-- Words populated by JS -->
                        </div>
                    </div>
                </div>
            </section>

            <!-- 4. Progress Tracker View -->
            <section id="progress" class="content-section" style="display: none;">
                <h2>Your Creative Progress</h2>
                <p>This area tracks your achievements based on completed modules and rendered projects.</p>
                <div class="dashboard-card">
                    <h3>Digital Skills Milestones</h3>
                    <ul>
                        <li>✅ Basic Asset Placement (Completed)</li>
                        <li>⏳ Voice Narration Practice (In Progress)</li>
                        <li>💡 Computational Thinking Puzzles (Locked)</li>
                    </ul>
                </div>
                <div class="dashboard-card">
                    <h3>Literacy Gains</h3>
                    <p>Amharic: Recognized 90% of the first two rows of letters.</p>
                    <p>English: Mastered 15 core vocabulary words.</p>
                </div>
            </section>

            <!-- 5. Parent/Teacher Dashboard View -->
            <section id="parent-teacher" class="content-section" style="display: none;">
                <h2>Parent & Teacher Hub</h2>
                <p>Monitor student engagement, view created stories, and provide guided feedback.</p>
                
                <div class="dashboard-card">
                    <h3>Student Performance Summary (Kid_001)</h3>
                    <p><strong>Activity Level:</strong> High</p>
                    <p><strong>Areas Needing Focus:</strong> English Vocabulary</p>
                    <button style="background-color: var(--accent-color); padding: 10px; border: none; border-radius: 5px; margin-top: 10px;">Review Last Story Render</button>
                </div>
            </section>

        </main>
    </div>

    <script>
        // --- JAVASCRIPT LOGIC ---

        // 1. Section Switching Logic
        function showSection(sectionId) {
            document.querySelectorAll('.content-section').forEach(section => {
                section.style.display = 'none';
            });
            document.getElementById(sectionId).style.display = 'block';

            // Update sidebar active state
            document.querySelectorAll('.sidebar a').forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('data-section') === sectionId) {
                    link.classList.add('active');
                }
            });
            window.scrollTo(0, 0); // Scroll to top on section change
        }
        
        // Initialize on page load
        document.addEventListener('DOMContentLoaded', () => {
            showSection('dashboard');
            initializeLearningModules();
            setupDragAndDropSimulation();
        });

        // 2. Bilingual Learning Module Logic
        const amharicLetters = [
            { char: 'ሀ', sound: 'hə', example: 'ሀገር (Hägar - Country)' },
            { char: 'ለ', sound: 'lə', example: 'ልብ (Ləb - Heart)' },
            { char: 'ሐ', sound: 'ḥə', example: 'ሐኪም (Ḥäkim - Doctor)' },
            { char: 'መ', sound: 'mə', example: 'መጽሐፍ (Mäṣḥaf - Book)' },
            { char: 'ሠ', sound: 'sə', example: 'ሠላም (Sälam - Peace)' },
            { char: 'ረ', sound: 'rə', example: 'ራስ (Ras - Head)' },
            { char: 'ሰ', sound: 'sə', example: 'ሰማይ (Sämay - Sky)' },
            // ... (Add more for a real app)
        ];

        const englishWords = [
            { word: 'Apple', lang: 'en' },
            { word: 'Book', lang: 'en' },
            { word: 'Cat', lang: 'en' },
            { word: 'Dream', lang: 'en' },
            { word: 'Ethiopia', lang: 'en' },
            { word: 'Friend', lang: 'en' },
        ];
        
        function initializeLearningModules() {
            const amharicContainer = document.getElementById('amharic-letters');
            amharicLetters.forEach(item => {
                const card = document.createElement('div');
                card.className = 'letter-card';
                card.innerHTML = `<span>${item.char}</span><small>${item.sound}</small>`;
                card.onclick = () => speak(item.char + " (" + item.example + ")");
                amharicContainer.appendChild(card);
            });

            const englishContainer = document.getElementById('english-words');
            englishWords.forEach(item => {
                const card = document.createElement('div');
                card.className = 'letter-card';
                card.innerHTML = `<span>${item.word}</span><small>English Word</small>`;
                card.onclick = () => speak(item.word);
                englishContainer.appendChild(card);
            });
        }

        function switchLearningTab(lang) {
            document.getElementById('content-amharic').style.display = lang === 'amharic' ? 'block' : 'none';
            document.getElementById('content-english').style.display = lang === 'english' ? 'block' : 'none';
            
            document.getElementById('tab-am').classList.toggle('active', lang === 'amharic');
            document.getElementById('tab-en').classList.toggle('active', lang === 'english');
        }
        
        // 3. Text-to-Speech Simulation (Using browser's built-in TTS)
        function speak(text) {
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(text);
                
                // Attempt to prioritize Amharic voice if available (browser-dependent)
                if (text.includes('ሀ') || text.includes('አ') || text.includes('ቃል')) {
                     utterance.lang = 'am-ET'; // Ethiopian locale is often not perfectly supported, but we try
                } else {
                     utterance.lang = 'en-US'; 
                }
                
                window.speechSynthesis.speak(utterance);
            } else {
                alert(`[TTS Simulation] Playing sound for: ${text}`);
            }
        }

        // 4. Animation/Voice Simulation
        function recordVoice() {
            const indicator = document.getElementById('lip-sync');
            
            if (indicator.style.display === 'block') {
                 // Stop simulation
                indicator.style.display = 'none';
                alert("Narration finished. Lip-sync data processed.");
                return;
            }

            // Start simulation
            indicator.style.display = 'block';
            alert("Recording started! (Simulating voice input and auto lip-sync analysis for 4 seconds...)");
            
            // Simulate a delay for recording/processing
            setTimeout(() => {
                // Simulate the character speaking (e.g., opening mouth/moving)
                const charDiv = document.getElementById('anim-char');
                charDiv.textContent = "Roar!";
                charDiv.style.backgroundColor = '#ffeb3b';
                
                // Auto-stop after a simulated duration
                setTimeout(() => {
                    indicator.style.display = 'none';
                    charDiv.textContent = "Lion";
                    charDiv.style.backgroundColor = 'var(--secondary-color)';
                    alert("Lip-sync data attached to Lion asset.");
                }, 2000);
                
            }, 2000);
        }
        
        // 5. Drag and Drop Simulation for Studio
        function setupDragAndDropSimulation() {
            const assets = document.querySelectorAll('.asset-item');
            const canvas = document.getElementById('animation-canvas');

            assets.forEach(asset => {
                asset.addEventListener('dragstart', (e) => {
                    e.dataTransfer.setData('text/plain', e.target.dataset.asset);
                    e.target.style.opacity = '0.4';
                });
                asset.addEventListener('dragend', (e) => {
                    e.target.style.opacity = '1';
                });
            });

            canvas.addEventListener('dragover', (e) => {
                e.preventDefault(); // Necessary to allow dropping
            });

            canvas.addEventListener('drop', (e) => {
                e.preventDefault();
                const assetType = e.dataTransfer.getData('text/plain');
                
                // Simple display confirmation instead of rendering actual 3D
                const message = document.createElement('div');
                message.style.cssText = `
                    position: absolute; 
                    padding: 5px 10px; 
                    background: rgba(255, 255, 255, 0.9); 
                    border: 1px solid var(--primary-color); 
                    border-radius: 5px;
                    left: ${e.offsetX}px; 
                    top: ${e.offsetY}px;
                    transform: translate(-50%, -50%);
                    z-index: 10;
                `;
                
                if (assetType === 'lion') {
                    message.textContent = "Lion placed in scene!";
                    // Keep the placeholder character visible as the main subject
                } else {
                    message.textContent = `${assetType.charAt(0).toUpperCase() + assetType.slice(1)} placed!`;
                }

                canvas.appendChild(message);
                
                setTimeout(() => {
                    message.remove();
                }, 1500);
            });
        }

    </script>
</body>
</html>
