<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Next-Gen Developer Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #00ff88;
            --bg: #0a192f;
            --light-bg: #112240;
            --text: #ccd6f6;
            --dark-text: #8892b0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            transition: 0.3s ease;
        }

        body {
            background: var(--bg);
            color: var(--text);
            font-family: 'Segoe UI', sans-serif;
            overflow-x: hidden;
        }

        /* 3D Cube Loader */
        .loader {
            position: fixed;
            width: 100vw;
            height: 100vh;
            background: var(--bg);
            display: grid;
            place-items: center;
            z-index: 1000;
        }

        .cube {
            width: 50px;
            height: 50px;
            transform-style: preserve-3d;
            animation: rotate 3s infinite linear;
        }

        @keyframes rotate {
            0% { transform: rotateX(0) rotateY(0); }
            100% { transform: rotateX(360deg) rotateY(360deg); }
        }

        /* Dynamic Grid Layout */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            padding: 2rem;
        }

        .project-card {
            background: var(--light-bg);
            border-radius: 10px;
            padding: 1.5rem;
            position: relative;
            overflow: hidden;
        }

        .project-card:hover {
            transform: translateY(-10px);
        }

        /* Holographic Effect */
        .holographic-border {
            position: relative;
        }

        .holographic-border::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 10px;
            padding: 2px;
            background: linear-gradient(45deg, var(--primary), #00ffff);
            -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
            mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
        }

        /* Responsive Navigation */
        .nav-container {
            position: fixed;
            top: 0;
            width: 100%;
            backdrop-filter: blur(10px);
            z-index: 100;
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: var(--light-bg);
            }
        }
    </style>
</head>
<body>
    <!-- 3D Loader -->
    <div class="loader">
        <div class="cube"></div>
    </div>

    <!-- AI-Powered Search -->
    <div class="ai-search">
        <input type="text" placeholder="Ask AI to find something...">
        <button><i class="fas fa-robot"></i></button>
    </div>

    <!-- Dynamic Project Showcase -->
    <div class="projects-grid">
        <div class="project-card holographic-border">
            <h3>AI Chat Application</h3>
            <p>Next-gen conversational interface with GPT-5 integration</p>
            <div class="tech-stack">
                <span>React</span>
                <span>TensorFlow.js</span>
                <span>WebSocket</span>
            </div>
        </div>
    </div>

    <!-- Quantum Computing Badge -->
    <div class="quantum-badge">
        <i class="fas fa-atom"></i>
        <span>Quantum Ready</span>
    </div>

    <script>
        // Loader timeout
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.querySelector('.loader').style.display = 'none';
            }, 2000);
        });

        // AI Search Functionality
        const aiSearch = {
            init() {
                document.querySelector('.ai-search button').addEventListener('click', () => {
                    const query = document.querySelector('.ai-search input').value;
                    this.processQuery(query);
                });
            },
            processQuery(query) {
                // Add AI processing logic here
                alert(`AI is searching for: ${query}`);
            }
        };
        aiSearch.init();

        // Web3 Integration
        async function connectWallet() {
            if (window.ethereum) {
                try {
                    const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
                    console.log('Connected:', accounts[0]);
                } catch (error) {
                    console.error(error);
                }
            }
        }

        // Theme Switching
        const themes = {
            cyber: { primary: '#00ff88', bg: '#0a192f' },
            dark: { primary: '#7b61ff', bg: '#000000' },
            light: { primary: '#2d3436', bg: '#ffffff' }
        };

        function setTheme(themeName) {
            const theme = themes[themeName];
            document.documentElement.style.setProperty('--primary', theme.primary);
            document.documentElement.style.setProperty('--bg', theme.bg);
        }
    </script>
</body>
</html>
