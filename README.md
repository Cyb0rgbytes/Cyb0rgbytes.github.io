<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CyberShield - QR Code Security Awareness</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Exo+2:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-red: #ff003c;
            --dark-red: #cc002f;
            --cyber-red: #ff073a;
            --primary-black: #0a0a0a;
            --dark-gray: #1a1a1a;
            --medium-gray: #2a2a2a;
            --light-gray: #3a3a3a;
            --text-light: #f0f0f0;
            --text-dim: #b0b0b0;
            --glow: 0 0 10px rgba(255, 0, 60, 0.7);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Exo 2', sans-serif;
            background-color: var(--primary-black);
            color: var(--text-light);
            line-height: 1.6;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(255, 0, 60, 0.05) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(255, 0, 60, 0.05) 0%, transparent 20%);
        }

        .cyber-border {
            position: relative;
            border: 1px solid var(--primary-red);
            box-shadow: var(--glow);
        }

        .cyber-border::before {
            content: '';
            position: absolute;
            top: -3px;
            left: -3px;
            right: -3px;
            bottom: -3px;
            border: 1px solid var(--primary-red);
            z-index: -1;
            opacity: 0.5;
        }

        header {
            background-color: rgba(10, 10, 10, 0.95);
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 2px solid var(--primary-red);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            color: var(--primary-red);
            font-size: 2.2rem;
            text-shadow: var(--glow);
        }

        .logo-text {
            font-family: 'Orbitron', sans-serif;
            font-weight: 900;
            font-size: 1.8rem;
            background: linear-gradient(to right, var(--primary-red), #ff3366);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 1px;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 600;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            transition: all 0.3s ease;
            position: relative;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.9rem;
            letter-spacing: 1px;
        }

        nav a:hover {
            color: var(--primary-red);
            background-color: rgba(255, 0, 60, 0.1);
        }

        nav a.active {
            color: var(--primary-red);
            background-color: rgba(255, 0, 60, 0.15);
        }

        nav a.active::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 10%;
            width: 80%;
            height: 2px;
            background-color: var(--primary-red);
            box-shadow: var(--glow);
        }

        .hero {
            padding: 4rem 2rem;
            text-align: center;
            background-color: rgba(26, 26, 26, 0.7);
            margin: 2rem auto;
            max-width: 1200px;
            border-radius: 8px;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(45deg, transparent 48%, rgba(255, 0, 60, 0.03) 50%, transparent 52%),
                linear-gradient(-45deg, transparent 48%, rgba(255, 0, 60, 0.03) 50%, transparent 52%);
            background-size: 20px 20px;
            z-index: 0;
        }

        .hero-content {
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 3rem;
            margin-bottom: 1.5rem;
            color: var(--text-light);
            text-shadow: 0 0 10px rgba(255, 0, 60, 0.5);
        }

        .hero h1 span {
            color: var(--primary-red);
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 2rem;
            color: var(--text-dim);
        }

        .warning-banner {
            background-color: rgba(255, 0, 60, 0.1);
            border-left: 4px solid var(--primary-red);
            padding: 1.5rem;
            margin: 2rem 0;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .warning-icon {
            color: var(--primary-red);
            font-size: 2rem;
            flex-shrink: 0;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2rem;
            margin: 3rem 0 1.5rem;
            color: var(--text-light);
            position: relative;
            padding-bottom: 10px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100px;
            height: 3px;
            background-color: var(--primary-red);
            box-shadow: var(--glow);
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .card {
            background-color: var(--dark-gray);
            border-radius: 8px;
            padding: 1.5rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5), var(--glow);
        }

        .card-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
            margin-bottom: 1rem;
            color: var(--primary-red);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card-icon {
            color: var(--primary-red);
        }

        .qr-simulator {
            grid-column: span 2;
            background-color: var(--medium-gray);
            padding: 2rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .qr-display {
            width: 200px;
            height: 200px;
            background-color: white;
            margin: 1rem 0;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .qr-pattern {
            width: 180px;
            height: 180px;
            background-image: 
                linear-gradient(to right, black 25%, transparent 25%, transparent 75%, black 75%),
                linear-gradient(to bottom, black 25%, transparent 25%, transparent 75%, black 75%);
            background-size: 20px 20px;
            position: relative;
        }

        .qr-pattern::before {
            content: '?';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 3rem;
            color: var(--primary-red);
            font-weight: bold;
        }

        .scan-btn {
            background-color: var(--primary-red);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            cursor: pointer;
            margin-top: 1rem;
            transition: all 0.3s ease;
        }

        .scan-btn:hover {
            background-color: var(--dark-red);
            box-shadow: var(--glow);
        }

        .threat-list {
            list-style: none;
        }

        .threat-list li {
            padding: 0.8rem 0;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .threat-list li:last-child {
            border-bottom: none;
        }

        .threat-icon {
            color: var(--primary-red);
        }

        .stats {
            display: flex;
            justify-content: space-around;
            margin: 3rem 0;
            flex-wrap: wrap;
            gap: 1.5rem;
        }

        .stat-box {
            text-align: center;
            padding: 1.5rem;
            background-color: rgba(255, 0, 60, 0.1);
            border-radius: 8px;
            min-width: 200px;
            flex: 1;
        }

        .stat-number {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            color: var(--primary-red);
            margin-bottom: 0.5rem;
            text-shadow: 0 0 5px rgba(255, 0, 60, 0.5);
        }

        .stat-label {
            font-size: 1rem;
            color: var(--text-dim);
        }

        .security-tips {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .tip {
            background-color: var(--dark-gray);
            padding: 1.5rem;
            border-left: 4px solid var(--primary-red);
            display: flex;
            align-items: flex-start;
            gap: 1rem;
        }

        .tip-icon {
            color: var(--primary-red);
            font-size: 1.5rem;
            margin-top: 5px;
        }

        footer {
            background-color: var(--dark-gray);
            padding: 3rem 2rem;
            margin-top: 4rem;
            border-top: 2px solid var(--primary-red);
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-section h3 {
            font-family: 'Orbitron', sans-serif;
            color: var(--primary-red);
            margin-bottom: 1.5rem;
            font-size: 1.2rem;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: var(--text-dim);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: var(--primary-red);
        }

        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 1.5rem;
            border-top: 1px solid var(--light-gray);
            color: var(--text-dim);
            font-size: 0.9rem;
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.7; }
            100% { opacity: 1; }
        }

        .scan-line {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background-color: var(--primary-red);
            box-shadow: var(--glow);
            display: none;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: var(--dark-gray);
            padding: 2rem;
            border-radius: 8px;
            max-width: 500px;
            width: 90%;
            text-align: center;
            border: 2px solid var(--primary-red);
            box-shadow: 0 0 30px rgba(255, 0, 60, 0.5);
        }

        .modal h3 {
            color: var(--primary-red);
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .close-modal {
            background-color: var(--primary-red);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            font-family: 'Orbitron', sans-serif;
            cursor: pointer;
            margin-top: 1.5rem;
        }

        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .qr-simulator {
                grid-column: span 1;
            }
            
            .hero h1 {
                font-size: 2.2rem;
            }
            
            nav ul {
                gap: 1rem;
            }
            
            .stats {
                flex-direction: column;
            }
            
            .footer-content {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <header class="cyber-border">
        <div class="logo">
            <div class="logo-icon">
                <i class="fas fa-shield-alt"></i>
            </div>
            <div class="logo-text">CYBERSHIELD</div>
        </div>
        <nav>
            <ul>
                <li><a href="#" class="active"><i class="fas fa-home"></i> Dashboard</a></li>
                <li><a href="#"><i class="fas fa-qrcode"></i> QR Risks</a></li>
                <li><a href="#"><i class="fas fa-shield-alt"></i> Protection</a></li>
                <li><a href="#"><i class="fas fa-newspaper"></i> Resources</a></li>
                <li><a href="#"><i class="fas fa-phone-alt"></i> Contact</a></li>
            </ul>
        </nav>
    </header>

    <div class="container">
        <section class="hero cyber-border">
            <div class="hero-content">
                <h1>QR CODE <span>SECURITY THREATS</span></h1>
                <p>QR codes are convenient but can be weaponized by cybercriminals. Learn how to identify malicious QR codes and protect your data from phishing, malware, and financial fraud attacks.</p>
                <div class="warning-banner">
                    <div class="warning-icon">
                        <i class="fas fa-exclamation-triangle"></i>
                    </div>
                    <div>
                        <strong>SECURITY ALERT:</strong> Over 75% of QR code attacks target mobile payment systems. Always verify QR codes before scanning.
                    </div>
                </div>
            </div>
        </section>

        <h2 class="section-title">QR Code Threat Dashboard</h2>
        
        <div class="dashboard-grid">
            <div class="card cyber-border">
                <h3 class="card-title"><i class="fas fa-biohazard card-icon"></i> Common Attack Vectors</h3>
                <ul class="threat-list">
                    <li><i class="fas fa-skull-crossbones threat-icon"></i> Malicious URL Redirects</li>
                    <li><i class="fas fa-file-invoice-dollar threat-icon"></i> Payment Diversion</li>
                    <li><i class="fas fa-download threat-icon"></i> Malware Downloads</li>
                    <li><i class="fas fa-envelope threat-icon"></i> Phishing Data Capture</li>
                    <li><i class="fas fa-wifi threat-icon"></i> Rogue Wi-Fi Networks</li>
                </ul>
            </div>

            <div class="card cyber-border">
                <h3 class="card-title"><i class="fas fa-chart-line card-icon"></i> Attack Statistics</h3>
                <div class="stats">
                    <div class="stat-box">
                        <div class="stat-number">+450%</div>
                        <div class="stat-label">QR phishing increase (2022-2023)</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-number">68%</div>
                        <div class="stat-label">of attacks target financial data</div>
                    </div>
                </div>
                <p>QR code attacks have skyrocketed with the increased adoption of contactless transactions and digital menus.</p>
            </div>

            <div class="card qr-simulator cyber-border">
                <h3 class="card-title"><i class="fas fa-eye card-icon"></i> QR Code Scanner Simulator</h3>
                <p>Simulate scanning a potentially malicious QR code to understand the risks.</p>
                <div class="qr-display cyber-border">
                    <div class="qr-pattern"></div>
                    <div class="scan-line" id="scanLine"></div>
                </div>
                <button class="scan-btn" id="scanBtn">Simulate QR Scan</button>
                <p class="pulse"><small>Warning: This is a simulation for educational purposes</small></p>
            </div>
        </div>

        <h2 class="section-title">Protection Guidelines</h2>
        
        <div class="security-tips">
            <div class="tip">
                <div class="tip-icon"><i class="fas fa-check-circle"></i></div>
                <div>
                    <h4>Inspect Before Scanning</h4>
                    <p>Check if the QR code has been tampered with or placed over a legitimate code.</p>
                </div>
            </div>
            <div class="tip">
                <div class="tip-icon"><i class="fas fa-mobile-alt"></i></div>
                <div>
                    <h4>Use Secure Scanners</h4>
                    <p>Choose QR scanner apps that preview URLs before opening them.</p>
                </div>
            </div>
            <div class="tip">
                <div class="tip-icon"><i class="fas fa-globe"></i></div>
                <div>
                    <h4>Verify URLs</h4>
                    <p>Check if the destination URL matches the expected website address.</p>
                </div>
            </div>
            <div class="tip">
                <div class="tip-icon"><i class="fas fa-shield-alt"></i></div>
                <div>
                    <h4>Keep Software Updated</h4>
                    <p>Ensure your device and security software have the latest patches.</p>
                </div>
            </div>
        </div>

        <div class="stats">
            <div class="stat-box cyber-border">
                <div class="stat-number">94%</div>
                <div class="stat-label">of users cannot identify malicious QR codes</div>
            </div>
            <div class="stat-box cyber-border">
                <div class="stat-number">1 in 5</div>
                <div class="stat-label">QR codes in public spaces are potentially risky</div>
            </div>
            <div class="stat-box cyber-border">
                <div class="stat-number">$3.2M</div>
                <div class="stat-label">average loss in QR code payment diversion attacks</div>
            </div>
        </div>
    </div>

    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>CYBERSHIELD</h3>
                <p>Raising awareness about digital security threats in the modern connected world.</p>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul class="footer-links">
                    <li><a href="#">QR Code Security Guidelines</a></li>
                    <li><a href="#">Report Suspicious QR Codes</a></li>
                    <li><a href="#">Latest Threat Intelligence</a></li>
                    <li><a href="#">Security Training</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Contact Security Team</h3>
                <ul class="footer-links">
                    <li><i class="fas fa-envelope"></i> security@cybershield.example</li>
                    <li><i class="fas fa-phone"></i> 1-800-CYBER-HELP</li>
                    <li><i class="fas fa-exclamation-triangle"></i> Report Incident</li>
                </ul>
            </div>
        </div>
        <div class="copyright">
            &copy; 2023 CyberShield QR Security Initiative. This is a demonstration for cybersecurity awareness.
        </div>
    </footer>

    <!-- Scan Result Modal -->
    <div class="modal" id="resultModal">
        <div class="modal-content cyber-border">
            <h3>QR CODE SCAN RESULT</h3>
            <div class="warning-banner" style="margin: 1rem 0;">
                <div class="warning-icon">
                    <i class="fas fa-exclamation-triangle"></i>
                </div>
                <div>
                    <strong>POTENTIAL THREAT DETECTED</strong>
                </div>
            </div>
            <p>The QR code redirected to: <span style="color: var(--primary-red)">paym3nt-update.com/secure</span></p>
            <p style="margin: 1rem 0; color: var(--text-dim);">This URL is suspicious because:</p>
            <ul style="text-align: left; margin: 1rem 0; padding-left: 1.5rem;">
                <li>Domain name is misspelled ("paym3nt" instead of "payment")</li>
                <li>No valid security certificate detected</li>
                <li>Redirects to an unfamiliar payment portal</li>
            </ul>
            <p><strong>Recommendation:</strong> Do not proceed. Report this QR code to the appropriate authority.</p>
            <button class="close-modal" id="closeModal">Close & Learn More</button>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const scanBtn = document.getElementById('scanBtn');
            const scanLine = document.getElementById('scanLine');
            const resultModal = document.getElementById('resultModal');
            const closeModal = document.getElementById('closeModal');
            
            // QR scanning simulation
            scanBtn.addEventListener('click', function() {
                // Show scanning animation
                scanLine.style.display = 'block';
                scanLine.style.animation = 'none';
                
                // Reset animation
                setTimeout(() => {
                    scanLine.style.animation = 'pulse 0.7s linear';
                    scanLine.style.top = '0';
                }, 10);
                
                // Move scan line down
                let position = 0;
                const interval = setInterval(() => {
                    position += 2;
                    scanLine.style.top = position + 'px';
                    
                    if (position >= 200) {
                        clearInterval(interval);
                        scanLine.style.display = 'none';
                        
                        // Show result modal after delay
                        setTimeout(() => {
                            resultModal.style.display = 'flex';
                        }, 500);
                    }
                }, 10);
            });
            
            // Close modal
            closeModal.addEventListener('click', function() {
                resultModal.style.display = 'none';
            });
            
            // Close modal if clicking outside content
            resultModal.addEventListener('click', function(e) {
                if (e.target === resultModal) {
                    resultModal.style.display = 'none';
                }
            });
            
            // Add interactive effect to cards on hover
            const cards = document.querySelectorAll('.card');
            cards.forEach(card => {
                card.addEventListener('mouseenter', function() {
                    const icon = this.querySelector('.card-icon');
                    if (icon) {
                        icon.style.transform = 'scale(1.2)';
                        icon.style.transition = 'transform 0.3s ease';
                    }
                });
                
                card.addEventListener('mouseleave', function() {
                    const icon = this.querySelector('.card-icon');
                    if (icon) {
                        icon.style.transform = 'scale(1)';
                    }
                });
            });
            
            // Animate stats counting up
            const statNumbers = document.querySelectorAll('.stat-number');
            const observerOptions = {
                threshold: 0.5
            };
            
            const observer = new IntersectionObserver(function(entries) {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const statNumber = entry.target;
                        const finalValue = statNumber.textContent;
                        
                        // If it's a percentage or has + sign, handle differently
                        if (finalValue.includes('%') || finalValue.includes('+')) {
                            statNumber.style.color = 'var(--primary-red)';
                            statNumber.style.textShadow = '0 0 10px rgba(255, 0, 60, 0.7)';
                        }
                    }
                });
            }, observerOptions);
            
            statNumbers.forEach(stat => observer.observe(stat));
        });
    </script>
</body>
</html>
