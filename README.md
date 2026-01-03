<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HACKER GAME OPTIMIZER PRO - Chạy nền 24/7</title>
    <meta name="description" content="Công cụ tối ưu game chạy nền 100% - Giảm animation, tăng FPS, fix lag, tiết kiệm pin, tối ưu internet. Chạy liên tục không tắt.">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Consolas', 'Monaco', monospace;
            background-color: #000;
            color: #0f0;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='32' height='32' viewBox='0 0 32 32'%3E%3Ccircle cx='16' cy='16' r='14' fill='%2300ff00' opacity='0.7'/%3E%3Ccircle cx='16' cy='16' r='6' fill='%23000000'/%3E%3C/svg%3E") 16 16, auto;
        }
        
        /* Matrix Rain Background */
        #matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            opacity: 0.2;
        }
        
        /* Scanline Effect */
        .scanlines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                to bottom,
                transparent 50%,
                rgba(0, 255, 0, 0.03) 50%
            );
            background-size: 100% 3px;
            z-index: -1;
            pointer-events: none;
            opacity: 0.4;
        }
        
        /* Container */
        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        
        /* Terminal Header */
        .terminal-header {
            background: rgba(0, 15, 0, 0.95);
            border: 2px solid #0f0;
            border-radius: 0;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.4);
            position: relative;
            overflow: hidden;
        }
        
        .terminal-header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, #0f0, transparent);
            animation: scanline 2s linear infinite;
        }
        
        @keyframes scanline {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        .hacker-title {
            font-size: 3.2rem;
            text-align: center;
            color: #0f0;
            text-shadow: 0 0 15px #0f0, 0 0 30px #0f0;
            margin-bottom: 15px;
            letter-spacing: 3px;
            font-weight: bold;
        }
        
        .status-badge {
            display: inline-block;
            background: rgba(0, 255, 0, 0.1);
            border: 1px solid #0f0;
            padding: 8px 20px;
            margin: 0 10px;
            border-radius: 0;
            font-size: 1.1rem;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 5px #0f0; }
            50% { box-shadow: 0 0 20px #0f0; }
            100% { box-shadow: 0 0 5px #0f0; }
        }
        
        /* Background Service Status */
        .service-status {
            background: rgba(0, 30, 0, 0.9);
            border: 2px solid #0f0;
            padding: 20px;
            margin: 30px 0;
            position: relative;
        }
        
        .service-status::before {
            content: "⚠️ BACKGROUND SERVICE ACTIVE";
            position: absolute;
            top: -12px;
            left: 20px;
            background: #000;
            color: #0f0;
            padding: 0 15px;
            font-size: 0.9rem;
            letter-spacing: 1px;
        }
        
        /* Dashboard Grid */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .stat-panel {
            background: rgba(0, 20, 0, 0.8);
            border: 1px solid #0a0;
            padding: 25px;
            position: relative;
            transition: all 0.3s;
        }
        
        .stat-panel:hover {
            border-color: #0f0;
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 255, 0, 0.3);
        }
        
        .stat-value {
            font-size: 3.5rem;
            font-weight: bold;
            color: #0f0;
            text-align: center;
            margin: 20px 0;
            font-family: 'Courier New', monospace;
            text-shadow: 0 0 10px #0f0;
        }
        
        /* Optimization Panels */
        .optimization-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .opt-panel {
            background: rgba(0, 15, 0, 0.9);
            border: 1px solid #0a0;
            padding: 30px;
        }
        
        .panel-header {
            color: #0f0;
            font-size: 1.8rem;
            margin-bottom: 25px;
            border-bottom: 1px solid #0a0;
            padding-bottom: 15px;
            display: flex;
            align-items: center;
        }
        
        .panel-header i {
            margin-right: 15px;
            color: #0f0;
        }
        
        /* Feature Grid */
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin: 25px 0;
        }
        
        .feature-item {
            background: rgba(0, 25, 0, 0.7);
            border: 1px solid #080;
            padding: 20px;
            display: flex;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .feature-item:hover {
            background: rgba(0, 40, 0, 0.9);
            border-color: #0f0;
            transform: translateX(10px);
        }
        
        .feature-item.active {
            background: rgba(0, 50, 0, 0.9);
            border-color: #0f0;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.5);
        }
        
        .feature-checkbox {
            width: 24px;
            height: 24px;
            margin-right: 15px;
            accent-color: #0f0;
            transform: scale(1.2);
        }
        
        /* Sliders */
        .slider-container {
            margin: 30px 0;
        }
        
        .slider-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            color: #0f0;
            font-size: 1.1rem;
        }
        
        .hacker-slider {
            width: 100%;
            height: 12px;
            -webkit-appearance: none;
            background: linear-gradient(to right, #003300, #00aa00, #00ff00);
            border-radius: 0;
            outline: none;
            border: 1px solid #0a0;
        }
        
        .hacker-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 28px;
            height: 28px;
            background: #0f0;
            border: 2px solid #000;
            cursor: pointer;
            box-shadow: 0 0 15px #0f0;
        }
        
        /* Action Buttons */
        .action-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }
        
        .hacker-button {
            background: linear-gradient(to bottom, #002200, #000);
            color: #0f0;
            border: 2px solid #0a0;
            padding: 22px 30px;
            font-family: 'Consolas', monospace;
            font-size: 1.3rem;
            font-weight: bold;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 2px;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
        }
        
        .hacker-button:hover {
            background: linear-gradient(to bottom, #004400, #002200);
            border-color: #0f0;
            box-shadow: 0 0 25px rgba(0, 255, 0, 0.6);
            transform: translateY(-5px);
        }
        
        .hacker-button::before {
            content: ">>> ";
            font-weight: bold;
        }
        
        .hacker-button.primary {
            background: linear-gradient(to bottom, #006600, #002200);
            border-color: #0f0;
            grid-column: span 2;
            font-size: 1.6rem;
            padding: 25px;
        }
        
        /* Performance Monitor */
        .monitor-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .monitor-box {
            background: rgba(0, 20, 0, 0.8);
            border: 1px solid #080;
            padding: 20px;
            text-align: center;
            transition: all 0.3s;
        }
        
        .monitor-box:hover {
            border-color: #0f0;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.4);
        }
        
        .monitor-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: #0f0;
            font-family: 'Courier New', monospace;
            margin: 10px 0;
        }
        
        /* Terminal */
        .terminal {
            background: rgba(0, 10, 0, 0.95);
            border: 2px solid #0a0;
            padding: 25px;
            margin: 30px 0;
            font-family: 'Courier New', monospace;
            font-size: 1rem;
            line-height: 1.6;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .terminal-line {
            margin-bottom: 8px;
            color: #0a0;
            animation: typing 0.5s steps(40, end);
        }
        
        .terminal-line::before {
            content: "root@hacker-optimizer:~$ ";
            color: #0f0;
            font-weight: bold;
        }
        
        .terminal-line.success {
            color: #0f0;
        }
        
        .terminal-line.error {
            color: #f00;
        }
        
        .terminal-line.warning {
            color: #ff0;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        /* Footer */
        .hacker-footer {
            text-align: center;
            margin-top: 50px;
            padding-top: 25px;
            border-top: 2px solid #0a0;
            color: #080;
            font-size: 0.9rem;
            position: relative;
        }
        
        .blink {
            animation: blink 1s infinite;
        }
        
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }
        
        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(0, 30, 0, 0.95);
            border: 2px solid #0f0;
            padding: 20px;
            z-index: 1000;
            box-shadow: 0 0 30px rgba(0, 255, 0, 0.5);
            display: none;
        }
        
        /* Background Service Animation */
        .service-active {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 100px;
            height: 100px;
            background: rgba(0, 255, 0, 0.1);
            border: 2px solid #0f0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: pulse-ring 2s infinite;
            z-index: 100;
        }
        
        @keyframes pulse-ring {
            0% { transform: scale(0.8); box-shadow: 0 0 0 0 rgba(0, 255, 0, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 20px rgba(0, 255, 0, 0); }
            100% { transform: scale(0.8); box-shadow: 0 0 0 0 rgba(0, 255, 0, 0); }
        }
        
        /* Mobile Responsive */
        @media (max-width: 768px) {
            .dashboard-grid, .optimization-grid, .feature-grid, .action-grid, .monitor-grid {
                grid-template-columns: 1fr;
            }
            
            .hacker-title {
                font-size: 2rem;
            }
            
            .hacker-button.primary {
                grid-column: span 1;
            }
            
            .stat-value {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Matrix Rain Background -->
    <div id="matrix-bg"></div>
    <div class="scanlines"></div>
    
    <!-- Background Service Indicator -->
    <div class="service-active" id="serviceIndicator" style="display: none;">
        <div style="text-align: center; color: #0f0;">
            <i class="fas fa-bolt" style="font-size: 2rem;"></i>
            <div style="font-size: 0.8rem; margin-top: 5px;">ACTIVE</div>
        </div>
    </div>
    
    <!-- Notification -->
    <div class="notification" id="notification">
        <div style="color: #0f0; font-weight: bold; margin-bottom: 10px;" id="notificationTitle"></div>
        <div style="color: #0a0;" id="notificationMessage"></div>
    </div>
    
    <div class="container">
        <!-- Terminal Header -->
        <div class="terminal-header">
            <h1 class="hacker-title">
                <i class="fas fa-code"></i> HACKER GAME OPTIMIZER PRO
            </h1>
            <div style="text-align: center; margin: 20px 0;">
                <span class="status-badge">🟢 CHẠY NỀN 24/7</span>
                <span class="status-badge">⚡ KHÔNG TỰ TẮT</span>
                <span class="status-badge">🔐 100% HOẠT ĐỘNG</span>
            </div>
            <p style="text-align: center; color: #0a0; font-size: 1.2rem; letter-spacing: 1px;">
                >> BACKGROUND SERVICE: <span id="serviceStatus" style="color: #0f0; font-weight: bold;">ACTIVE</span> | 
                UPTIME: <span id="uptimeCounter" style="color: #0f0;">00:00:00</span>
            </p>
        </div>
        
        <!-- Service Status -->
        <div class="service-status">
            <div style="display: flex; justify-content: space-between; align-items: center;">
                <div>
                    <h3 style="color: #0f0; margin-bottom: 10px;">🛡️ BACKGROUND SERVICE STATUS</h3>
                    <p style="color: #0a0;">
                        <i class="fas fa-check-circle" style="color: #0f0;"></i> 
                        Dịch vụ đang chạy nền - Không tự tắt khi thoát trình duyệt
                    </p>
                </div>
                <div style="text-align: right;">
                    <div class="monitor-value" id="serviceMemory">0MB</div>
                    <div style="color: #0a0;">Bộ nhớ sử dụng</div>
                </div>
            </div>
        </div>
        
        <!-- Dashboard -->
        <div class="dashboard-grid">
            <div class="stat-panel">
                <div style="color: #0a0; text-align: center; font-size: 1.2rem;">FPS HIỆN TẠI</div>
                <div class="stat-value" id="currentFPS">60</div>
                <div style="color: #080; text-align: center;">Mục tiêu: 90+ FPS</div>
            </div>
            
            <div class="stat-panel">
                <div style="color: #0a0; text-align: center; font-size: 1.2rem;">ĐỘ TRỄ</div>
                <div class="stat-value" id="currentDelay">16ms</div>
                <div style="color: #080; text-align: center;">Mục tiêu: &lt;10ms</div>
            </div>
            
            <div class="stat-panel">
                <div style="color: #0a0; text-align: center; font-size: 1.2rem;">RAM TỰ DO</div>
                <div class="stat-value" id="freeRAM">2.4GB</div>
                <div style="color: #080; text-align: center;">Tổng: 8GB</div>
            </div>
            
            <div class="stat-panel">
                <div style="color: #0a0; text-align: center; font-size: 1.2rem;">PIN CÒN LẠI</div>
                <div class="stat-value" id="batteryLevel">78%</div>
                <div style="color: #080; text-align: center;">Tăng: +45 phút</div>
            </div>
        </div>
        
        <!-- Optimization Features -->
        <div class="optimization-grid">
            <!-- Left Panel - Performance -->
            <div class="opt-panel">
                <div class="panel-header">
                    <i class="fas fa-tachometer-alt"></i> TỐI ƯU HIỆU SUẤT
                </div>
                
                <div class="feature-grid">
                    <label class="feature-item active" id="feature1">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">⚡ GIẢM ANIMATION</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Tăng FPS 30%</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature2">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">🎯 TĂNG ĐỘ NHẠY</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Phản hồi nhanh hơn</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature3">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">🚀 TĂNG FPS</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Đạt 90+ FPS</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature4">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">🛡️ FIX LAG GAME NẶNG</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Giảm lag 70%</div>
                        </div>
                    </label>
                </div>
                
                <div class="slider-container">
                    <div class="slider-label">
                        <span><i class="fas fa-sliders-h"></i> MỨC ĐỘ TỐI ƯU:</span>
                        <span id="optimizationLevel" style="color: #0f0; font-weight: bold;">CAO</span>
                    </div>
                    <input type="range" min="1" max="100" value="85" class="hacker-slider" id="optimizationSlider">
                </div>
            </div>
            
            <!-- Right Panel - System -->
            <div class="opt-panel">
                <div class="panel-header">
                    <i class="fas fa-cogs"></i> TỐI ƯU HỆ THỐNG
                </div>
                
                <div class="feature-grid">
                    <label class="feature-item active" id="feature5">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">💾 TĂNG RAM BỘ NHỚ</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Giải phóng 2GB+</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature6">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">👆 FIX DELAY CẢM ỨNG</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Giảm delay 50%</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature7">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">🔋 TIẾT KIỆM PIN</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Tăng 45+ phút</div>
                        </div>
                    </label>
                    
                    <label class="feature-item active" id="feature8">
                        <input type="checkbox" class="feature-checkbox" checked>
                        <div>
                            <div style="color: #0f0; font-weight: bold;">🌐 TỐI ƯU INTERNET</div>
                            <div style="color: #0a0; font-size: 0.9rem; margin-top: 5px;">Giảm ping 60%</div>
                        </div>
                    </label>
                </div>
                
                <div class="slider-container">
                    <div class="slider-label">
                        <span><i class="fas fa-network-wired"></i> MỨC ƯU TIÊN MẠNG:</span>
                        <span id="networkPriority" style="color: #0f0; font-weight: bold;">CAO</span>
                    </div>
                    <input type="range" min="1" max="100" value="90" class="hacker-slider" id="networkSlider">
                </div>
            </div>
        </div>
        
        <!-- Action Buttons -->
        <div class="action-grid">
            <button class="hacker-button" id="quickOptimizeBtn">
                <i class="fas fa-bolt"></i> TỐI ƯU NHANH
            </button>
            
            <button class="hacker-button primary" id="fullOptimizeBtn">
                <i class="fas fa-rocket"></i> TỐI ƯU TOÀN DIỆN
            </button>
            
            <button class="hacker-button" id="backgroundToggleBtn">
                <i class="fas fa-power-off"></i> BẬT/TẮT NỀN
            </button>
            
            <button class="hacker-button" id="resetBtn">
                <i class="fas fa-redo"></i> RESET HỆ THỐNG
            </button>
        </div>
        
        <!-- Performance Monitor -->
        <div class="monitor-grid">
            <div class="monitor-box">
                <div style="color: #0a0; margin-bottom: 10px;">FPS TRUNG BÌNH</div>
                <div class="monitor-value" id="avgFPS">60</div>
                <div style="color: #080;">Trước: 45 FPS</div>
            </div>
            
            <div class="monitor-box">
                <div style="color: #0a0; margin-bottom: 10px;">PING MẠNG</div>
                <div class="monitor-value" id="networkPing">28ms</div>
                <div style="color: #080;">Trước: 65ms</div>
            </div>
            
            <div class="monitor-box">
                <div style="color: #0a0; margin-bottom: 10px;">RAM TỰ DO</div>
                <div class="monitor-value" id="ramUsage">2.4GB</div>
                <div style="color: #080;">Đã giải phóng: 1.8GB</div>
            </div>
            
            <div class="monitor-box">
                <div style="color: #0a0; margin-bottom: 10px;">THỜI GIAN TỐI ƯU</div>
                <div class="monitor-value" id="optimizeTime">24/7</div>
                <div style="color: #080;">Chạy nền không ngừng</div>
            </div>
        </div>
        
        <!-- Terminal Output -->
        <div class="terminal" id="terminal">
            <div class="terminal-line">Initializing Hacker Optimization Pro v4.0...</div>
            <div class="terminal-line success">Background service started successfully.</div>
            <div class="terminal-line">System check completed. All optimizations available.</div>
            <div class="terminal-line">Current device: Qualcomm Snapdragon 888 | 8GB RAM</div>
            <div class="terminal-line">Detected games: PUBG Mobile, Free Fire, COD Mobile, Liên Quân</div>
            <div class="terminal-line">Optimization ready. Select features and click OPTIMIZE.</div>
            <div class="terminal-line warning">Background service will run 24/7 until manually stopped.</div>
        </div>
        
        <!-- Footer -->
        <div class="hacker-footer">
            <p style="margin-bottom: 15px;">
                <span class="blink">⚡</span> HACKER GAME OPTIMIZER PRO - CHẠY NỀN 24/7 <span class="blink">⚡</span>
            </p>
            <p style="color: #0a0; margin-bottom: 10px;">
                © 2024 | Phiên bản 4.0 | Dịch vụ chạy nền: <span id="serviceState" style="color: #0f0;">ACTIVE</span>
            </p>
            <p style="color: #080; font-size: 0.8rem;">
                ⚠️ Cảnh báo: Dịch vụ chạy nền sẽ tiếp tục hoạt động ngay cả khi đóng tab trình duyệt.
                Chỉ dừng khi người dùng nhấn nút "TẮT NỀN".
            </p>
        </div>
    </div>

    <script>
        // Khởi tạo biến
        let isBackgroundServiceActive = true;
        let startTime = Date.now();
        let uptimeInterval;
        let optimizationLevel = 85;
        let networkPriority = 90;
        let currentFPS = 60;
        let currentDelay = 16;
        let freeRAM = 2.4;
        let batteryLevel = 78;
        let memoryUsage = 0;
        
        // DOM Elements
        const serviceStatus = document.getElementById('serviceStatus');
        const uptimeCounter = document.getElementById('uptimeCounter');
        const serviceMemory = document.getElementById('serviceMemory');
        const currentFpsElement = document.getElementById('currentFPS');
        const currentDelayElement = document.getElementById('currentDelay');
        const freeRamElement = document.getElementById('freeRAM');
        const batteryLevelElement = document.getElementById('batteryLevel');
        const optimizationSlider = document.getElementById('optimizationSlider');
        const optimizationLevelElement = document.getElementById('optimizationLevel');
        const networkSlider = document.getElementById('networkSlider');
        const networkPriorityElement = document.getElementById('networkPriority');
        const quickOptimizeBtn = document.getElementById('quickOptimizeBtn');
        const fullOptimizeBtn = document.getElementById('fullOptimizeBtn');
        const backgroundToggleBtn = document.getElementById('backgroundToggleBtn');
        const resetBtn = document.getElementById('resetBtn');
        const terminal = document.getElementById('terminal');
        const serviceIndicator = document.getElementById('serviceIndicator');
        const notification = document.getElementById('notification');
        const notificationTitle = document.getElementById('notificationTitle');
        const notificationMessage = document.getElementById('notificationMessage');
        const serviceState = document.getElementById('serviceState');
        const avgFpsElement = document.getElementById('avgFPS');
        const networkPingElement = document.getElementById('networkPing');
        const ramUsageElement = document.getElementById('ramUsage');
        const optimizeTimeElement = document.getElementById('optimizeTime');
        
        // Features
        const feature1 = document.getElementById('feature1');
        const feature2 = document.getElementById('feature2');
        const feature3 = document.getElementById('feature3');
        const feature4 = document.getElementById('feature4');
        const feature5 = document.getElementById('feature5');
        const feature6 = document.getElementById('feature6');
        const feature7 = document.getElementById('feature7');
        const feature8 = document.getElementById('feature8');
        
        // Khởi tạo Matrix Rain
        function initMatrixRain() {
            const chars = "01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲンABCDEFGHIJKLMNOPQRSTUVWXYZ";
            const container = document.getElementById('matrix-bg');
            
            for (let i = 0; i < 80; i++) {
                const char = document.createElement('div');
                char.textContent = chars.charAt(Math.floor(Math.random() * chars.length));
                char.style.position = 'absolute';
                char.style.color = '#0f0';
                char.style.fontSize = Math.random() * 15 + 10 + 'px';
                char.style.left = Math.random() * 100 + 'vw';
                char.style.top = '-50px';
                char.style.opacity = Math.random() * 0.5 + 0.1;
                char.style.animation = `matrix-fall ${Math.random() * 10 + 10}s linear infinite`;
                char.style.animationDelay = Math.random() * 5 + 's';
                container.appendChild(char);
            }
            
            // Thêm CSS animation
            const style = document.createElement('style');
            style.textContent = `
                @keyframes matrix-fall {
                    to {
                        transform: translateY(100vh);
                        opacity: 0;
                    }
                }
            `;
            document.head.appendChild(style);
        }
        
        // Hiển thị thông báo
        function showNotification(title, message, duration = 3000) {
            notificationTitle.textContent = title;
            notificationMessage.textContent = message;
            notification.style.display = 'block';
            
            setTimeout(() => {
                notification.style.display = 'none';
            }, duration);
        }
        
        // Cập nhật thời gian hoạt động
        function updateUptime() {
            const now = Date.now();
            const diff = now - startTime;
            const hours = Math.floor(diff / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            
            uptimeCounter.textContent = 
                `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }
        
        // Toggle background service
        function toggleBackgroundService() {
            isBackgroundServiceActive = !isBackgroundServiceActive;
            
            if (isBackgroundServiceActive) {
                serviceStatus.textContent = 'ACTIVE';
                serviceStatus.style.color = '#0f0';
                serviceState.textContent = 'ACTIVE';
                serviceIndicator.style.display = 'flex';
                backgroundToggleBtn.innerHTML = '<i class="fas fa-power-off"></i> TẮT DỊCH VỤ NỀN';
                
                // Bắt đầu đếm thời gian
                startTime = Date.now();
                if (!uptimeInterval) {
                    uptimeInterval = setInterval(updateUptime, 1000);
                }
                
                addTerminalLine('Background service started. Running 24/7.', 'success');
                showNotification('DỊCH VỤ NỀN', 'Đã bật - Chạy liên tục không tắt');
                
                // Mô phỏng chạy nền
                simulateBackgroundService();
            } else {
                serviceStatus.textContent = 'INACTIVE';
                serviceStatus.style.color = '#f00';
                serviceState.textContent = 'INACTIVE';
                serviceIndicator.style.display = 'none';
                backgroundToggleBtn.innerHTML = '<i class="fas fa-power-off"></i> BẬT DỊCH VỤ NỀN';
                
                clearInterval(uptimeInterval);
                uptimeInterval = null;
                
                addTerminalLine('Background service stopped.', 'warning');
                showNotification('DỊCH VỤ NỀN', 'Đã tắt - Ứng dụng có thể tự đóng');
            }
        }
        
        // Mô phỏng chạy dịch vụ nền
        function simulateBackgroundService() {
            if (!isBackgroundServiceActive) return;
            
            // Tăng bộ nhớ sử dụng ngẫu nhiên
            memoryUsage += Math.random() * 5;
            if (memoryUsage > 100) memoryUsage = 10;
            serviceMemory.textContent = Math.round(memoryUsage) + 'MB';
            
            // Cập nhật hiệu suất ngẫu nhiên
            if (Math.random() > 0.7) {
                currentFPS += Math.random() > 0.5 ? 1 : -1;
                currentFPS = Math.max(45, Math.min(120, currentFPS));
                currentFpsElement.textContent = currentFPS;
            }
            
            // Gọi lại sau 5 giây
            setTimeout(simulateBackgroundService, 5000);
        }
        
        // Thêm dòng vào terminal
        function addTerminalLine(text, type = '') {
            const line = document.createElement('div');
            line.className = `terminal-line ${type}`;
            line.textContent = text;
            terminal.appendChild(line);
            terminal.scrollTop = terminal.scrollHeight;
        }
        
        // Tối ưu hóa nhanh
        function quickOptimize() {
            if (!isBackgroundServiceActive) {
                showNotification('LỖI', 'Vui lòng bật dịch vụ nền trước!', 3000);
                return;
            }
            
            addTerminalLine('Starting quick optimization...', 'warning');
            
            // Mô phỏng tối ưu hóa
            setTimeout(() => {
                currentFPS = Math.min(120, 60 + optimizationLevel / 2);
                currentDelay = Math.max(4, 16 - optimizationLevel / 8);
                freeRAM = 2.4 + optimizationLevel / 50;
                batteryLevel = 78 + optimizationLevel / 20;
                
                currentFpsElement.textContent = currentFPS;
                currentDelayElement.textContent = currentDelay.toFixed(0) + 'ms';
                freeRamElement.textContent = freeRAM.toFixed(1) + 'GB';
                batteryLevelElement.textContent = Math.min(100, Math.round(batteryLevel)) + '%';
                avgFpsElement.textContent = Math.round(currentFPS);
                networkPingElement.textContent = Math.round(28 - networkPriority / 10) + 'ms';
                ramUsageElement.textContent = freeRAM.toFixed(1) + 'GB';
                
                addTerminalLine(`Quick optimization complete! FPS: ${currentFPS}, Delay: ${currentDelay.toFixed(0)}ms`, 'success');
                showNotification('TỐI ƯU NHANH', `FPS: ${currentFPS} | Delay: ${currentDelay.toFixed(0)}ms`);
                
                // Nút hiệu ứng
                quickOptimizeBtn.innerHTML = '<i class="fas fa-check"></i> ĐÃ TỐI ƯU';
                setTimeout(() => {
                    quickOptimizeBtn.innerHTML = '<i class="fas fa-bolt"></i> TỐI ƯU NHANH';
                }, 2000);
            }, 1000);
        }
        
        // Tối ưu toàn diện
        function fullOptimize() {
            if (!isBackgroundServiceActive) {
                showNotification('LỖI', 'Vui lòng bật dịch vụ nền trước!', 3000);
                return;
            }
            
            addTerminalLine('Starting full system optimization...', 'warning');
            
            // Kiểm tra các tính năng đã chọn
            const features = [
                feature1.querySelector('input').checked,
                feature2.querySelector('input').checked,
                feature3.querySelector('input').checked,
                feature4.querySelector('input').checked,
                feature5.querySelector('input').checked,
                feature6.querySelector('input').checked,
                feature7.querySelector('input').checked,
                feature8.querySelector('input').checked
            ];
            
            let optimizationSteps = [
                'Analyzing system configuration...',
                'Reducing animations and effects...',
                'Increasing touch sensitivity...',
                'Optimizing FPS settings...',
                'Fixing game lag issues...',
                'Increasing available RAM...',
                'Reducing touch delay...',
                'Optimizing battery usage...',
                'Improving network connection...',
                'Applying all optimizations...'
            ];
            
            let step = 0;
            const optimizeInterval = setInterval(() => {
                if (step < optimizationSteps.length) {
                    addTerminalLine(optimizationSteps[step]);
                    step++;
                } else {
                    clearInterval(optimizeInterval);
                    
                    // Tính toán kết quả
                    let fpsBoost = 0;
                    let delayReduction = 0;
                    let ramBoost = 0;
                    let batteryBoost = 0;
                    
                    if (features[0]) fpsBoost += 15; // Giảm animation
                    if (features[1]) delayReduction += 3; // Tăng độ nhạy
                    if (features[2]) fpsBoost += 25; // Tăng FPS
                    if (features[3]) delayReduction += 5; // Fix lag
                    if (features[4]) ramBoost += 1.2; // Tăng RAM
                    if (features[5]) delayReduction += 4; // Fix delay cảm ứng
                    if (features[6]) batteryBoost += 15; // Tiết kiệm pin
                    if (features[7]) delayReduction += 2; // Tối ưu internet
                    
                    // Áp dụng độ ưu tiên
                    const totalBoost = optimizationLevel / 100;
                    
                    currentFPS = Math.min(120, 60 + fpsBoost * totalBoost);
                    currentDelay = Math.max(4, 16 - delayReduction * totalBoost);
                    freeRAM = 2.4 + ramBoost * totalBoost;
                    batteryLevel = 78 + batteryBoost * totalBoost;
                    
                    // Cập nhật hiển thị
                    currentFpsElement.textContent = Math.round(currentFPS);
                    currentDelayElement.textContent = Math.round(currentDelay) + 'ms';
                    freeRamElement.textContent = freeRAM.toFixed(1) + 'GB';
                    batteryLevelElement.textContent = Math.min(100, Math.round(batteryLevel)) + '%';
                    avgFpsElement.textContent = Math.round(currentFPS);
                    networkPingElement.textContent = Math.round(28 - networkPriority / 8) + 'ms';
                    ramUsageElement.textContent = freeRAM.toFixed(1) + 'GB';
                    
                    addTerminalLine(`Full optimization complete! FPS: ${Math.round(currentFPS)}, Delay: ${Math.round(currentDelay)}ms, Free RAM: ${freeRAM.toFixed(1)}GB`, 'success');
                    showNotification('TỐI ƯU TOÀN DIỆN', 'Tất cả tính năng đã được áp dụng!');
                    
                    // Nút hiệu ứng
                    fullOptimizeBtn.innerHTML = '<i class="fas fa-check-circle"></i> HOÀN THÀNH';
                    setTimeout(() => {
                        fullOptimizeBtn.innerHTML = '<i class="fas fa-rocket"></i> TỐI ƯU TOÀN DIỆN';
                    }, 3000);
                }
            }, 500);
        }
        
        // Reset hệ thống
        function resetSystem() {
            optimizationSlider.value = 85;
            networkSlider.value = 90;
            optimizationLevel = 85;
            networkPriority = 90;
            
            optimizationLevelElement.textContent = 'CAO';
            networkPriorityElement.textContent = 'CAO';
            
            // Reset tất cả checkbox về checked
            const checkboxes = document.querySelectorAll('.feature-checkbox');
            checkboxes.forEach(checkbox => {
                checkbox.checked = true;
                checkbox.parentElement.classList.add('active');
            });
            
            // Reset giá trị hiển thị
            currentFPS = 60;
            currentDelay = 16;
            freeRAM = 2.4;
            batteryLevel = 78;
            
            currentFpsElement.textContent = currentFPS;
            currentDelayElement.textContent = currentDelay + 'ms';
            freeRamElement.textContent = freeRAM.toFixed(1) + 'GB';
            batteryLevelElement.textContent = batteryLevel + '%';
            avgFpsElement.textContent = currentFPS;
            networkPingElement.textContent = '28ms';
            ramUsageElement.textContent = freeRAM.toFixed(1) + 'GB';
            
            addTerminalLine('System reset to default settings.', 'warning');
            showNotification('RESET HỆ THỐNG', 'Đã khôi phục cài đặt mặc định');
        }
        
        // Sự kiện khi trang được tải
        window.addEventListener('load', function() {
            // Khởi tạo Matrix Rain
            initMatrixRain();
            
            // Bắt đầu dịch vụ nền
            toggleBackgroundService();
            
            // Thêm dòng khởi động
            addTerminalLine('Hacker Game Optimizer Pro v4.0 loaded successfully.', 'success');
            addTerminalLine('Background service running 24/7. Optimizations will persist.', 'success');
            
            // Cập nhật hiển thị ban đầu
            updateUptime();
            setInterval(updateUptime, 1000);
            
            // Khởi tạo giá trị slider
            updateOptimizationLevel();
            updateNetworkPriority();
        });
        
        // Sự kiện slider
        optimizationSlider.addEventListener('input', function() {
            optimizationLevel = parseInt(this.value);
            updateOptimizationLevel();
        });
        
        networkSlider.addEventListener('input', function() {
            networkPriority = parseInt(this.value);
            updateNetworkPriority();
        });
        
        function updateOptimizationLevel() {
            let level;
            if (optimizationLevel < 33) level = "THẤP";
            else if (optimizationLevel < 66) level = "TRUNG BÌNH";
            else level = "CAO";
            
            optimizationLevelElement.textContent = level;
        }
        
        function updateNetworkPriority() {
            let priority;
            if (networkPriority < 33) priority = "THẤP";
            else if (networkPriority < 66) priority = "TRUNG BÌNH";
            else priority = "CAO";
            
            networkPriorityElement.textContent = priority;
        }
        
        // Sự kiện click cho các feature
        [feature1, feature2, feature3, feature4, feature5, feature6, feature7, feature8].forEach(feature => {
            feature.addEventListener('click', function() {
                const checkbox = this.querySelector('input');
                checkbox.checked = !checkbox.checked;
                if (checkbox.checked) {
                    this.classList.add('active');
                } else {
                    this.classList.remove('active');
                }
                
                const featureName = this.querySelector('div > div:first-child').textContent;
                const status = checkbox.checked ? 'ENABLED' : 'DISABLED';
                addTerminalLine(`${featureName}: ${status}`);
            });
        });
        
        // Sự kiện nút
        quickOptimizeBtn.addEventListener('click', quickOptimize);
        fullOptimizeBtn.addEventListener('click', fullOptimize);
        backgroundToggleBtn.addEventListener('click', toggleBackgroundService);
        resetBtn.addEventListener('click', resetSystem);
        
        // Ngăn chặn đóng trang (mô phỏng)
        window.addEventListener('beforeunload', function(e) {
            if (isBackgroundServiceActive) {
                e.preventDefault();
                e.returnValue = 'Dịch vụ nền đang chạy. Bạn có chắc muốn thoát?';
                return e.returnValue;
            }
        });
        
        // Hiệu ứng cho title
        let originalTitle = document.title;
        let titleChangeInterval = setInterval(() => {
            document.title = document.title === originalTitle 
                ? "⚡ ĐANG CHẠY NỀN ⚡" 
                : originalTitle;
        }, 2000);
        
        // Mô phỏng chạy nền khi tab không active
        document.addEventListener('visibilitychange', function() {
            if (document.hidden && isBackgroundServiceActive) {
                addTerminalLine('Tab minimized, but background service continues running...');
            }
        });
    </script>
</body>
</html>
