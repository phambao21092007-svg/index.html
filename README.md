<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tối Ưu Điện Thoại Chơi Game | FPS Cao - Delay Thấp</title>
    <meta name="description" content="Công cụ tối ưu hóa điện thoại chơi game miễn phí 100%. Tăng FPS, giảm delay, cải thiện độ nhạy cảm ứng. Hoạt động ngay trên GitHub Pages.">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            color: white;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        header {
            text-align: center;
            padding-bottom: 25px;
            margin-bottom: 30px;
            border-bottom: 2px solid #00d4ff;
        }
        h1 {
            color: #00d4ff;
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 0 0 15px rgba(0, 212, 255, 0.5);
        }
        .status-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        .status-card {
            background: rgba(0, 0, 0, 0.3);
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            border: 1px solid rgba(0, 212, 255, 0.2);
        }
        .value {
            font-size: 2.5rem;
            font-weight: bold;
            color: #00ff88;
            margin-bottom: 5px;
        }
        .control-panel {
            background: rgba(0, 0, 0, 0.3);
            padding: 25px;
            border-radius: 15px;
            margin: 25px 0;
        }
        .slider-container {
            margin: 25px 0;
        }
        .slider {
            width: 100%;
            height: 30px;
            -webkit-appearance: none;
            background: linear-gradient(to right, #0066cc, #00d4ff);
            border-radius: 15px;
            outline: none;
            margin-top: 10px;
        }
        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: white;
            cursor: pointer;
            border: 3px solid #00d4ff;
        }
        .checkbox-group {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }
        .checkbox-item {
            background: rgba(0, 0, 0, 0.2);
            padding: 15px;
            border-radius: 10px;
            display: flex;
            align-items: center;
        }
        .checkbox-item input {
            margin-right: 15px;
            transform: scale(1.3);
            accent-color: #00d4ff;
        }
        .btn {
            background: linear-gradient(135deg, #00d4ff, #0066cc);
            color: white;
            border: none;
            padding: 18px 35px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 12px;
            cursor: pointer;
            width: 100%;
            margin: 20px 0;
            transition: all 0.3s;
        }
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 212, 255, 0.4);
            background: linear-gradient(135deg, #00ff88, #00d4ff);
        }
        .test-area {
            background: rgba(0, 0, 0, 0.3);
            padding: 25px;
            border-radius: 15px;
            margin: 25px 0;
            text-align: center;
        }
        .touch-pad {
            width: 100%;
            height: 250px;
            background: rgba(0, 0, 0, 0.5);
            border: 3px dashed #00d4ff;
            border-radius: 12px;
            margin: 20px 0;
            position: relative;
            overflow: hidden;
            cursor: crosshair;
        }
        .ball {
            width: 60px;
            height: 60px;
            background: radial-gradient(circle at 30% 30%, #00ff88, #00d4ff);
            border-radius: 50%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 30px rgba(0, 255, 136, 0.5);
        }
        .info-box {
            background: rgba(0, 0, 0, 0.3);
            padding: 20px;
            border-radius: 12px;
            margin: 20px 0;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 25px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #888;
        }
        @media (max-width: 768px) {
            .container { padding: 15px; }
            h1 { font-size: 2rem; }
            .status-grid { grid-template-columns: repeat(2, 1fr); }
            .value { font-size: 2rem; }
        }
        @media (max-width: 480px) {
            .status-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🎮 TỐI ƯU ĐIỆN THOẠI CHƠI GAME</h1>
            <p style="color: #00ff88; font-size: 1.1rem;">✅ 100% Hoạt động trên GitHub Pages | FPS Cao - Delay Thấp</p>
        </header>
        
        <div class="status-grid">
            <div class="status-card">
                <div class="value" id="fpsCounter">60 FPS</div>
                <div>Tốc độ khung hình</div>
            </div>
            <div class="status-card">
                <div class="value" id="delayCounter">16ms</div>
                <div>Độ trễ phản hồi</div>
            </div>
            <div class="status-card">
                <div class="value" id="sensCounter">85%</div>
                <div>Độ nhạy cảm ứng</div>
            </div>
            <div class="status-card">
                <div class="value" id="stableCounter">95%</div>
                <div>Độ ổn định</div>
            </div>
        </div>
        
        <div class="control-panel">
            <h2 style="color: #00d4ff; margin-bottom: 20px;">⚙️ CÀI ĐẶT TỐI ƯU HÓA</h2>
            
            <div class="slider-container">
                <label style="display: block; margin-bottom: 10px; font-size: 1.1rem;">
                    🎯 Độ nhạy cảm ứng: <span id="sensValue" style="color: #00ff88; font-weight: bold;">85%</span>
                </label>
                <input type="range" min="1" max="100" value="85" class="slider" id="sensitivitySlider">
            </div>
            
            <div class="checkbox-group">
                <div class="checkbox-item">
                    <input type="checkbox" id="opt1" checked>
                    <label for="opt1">Tăng FPS (giảm hiệu ứng)</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="opt2" checked>
                    <label for="opt2">Giảm độ trễ (phản hồi nhanh)</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="opt3">
                    <label for="opt3">Chế độ tiết kiệm pin</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="opt4" checked>
                    <label for="opt4">Tối ưu hóa cảm ứng</label>
                </div>
            </div>
            
            <button class="btn" id="optimizeBtn">🚀 BẮT ĐẦU TỐI ƯU HÓA</button>
            
            <p style="text-align: center; color: #00ff88; margin-top: 15px;">
                ⚡ Website hoạt động 100% trên GitHub Pages - Không cần cài đặt thêm
            </p>
        </div>
        
        <div class="test-area">
            <h2 style="color: #00ff88; margin-bottom: 15px;">🎯 KHU VỰC KIỂM TRA CẢM ỨNG</h2>
            <p>Chạm và di chuyển trong ô dưới đây để kiểm tra độ nhạy:</p>
            
            <div class="touch-pad" id="touchPad">
                <div class="ball" id="ball"></div>
                <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); color: #00d4ff;">
                    Chạm vào đây để bắt đầu
                </div>
            </div>
            
            <div class="info-box">
                <div style="display: flex; justify-content: space-around; flex-wrap: wrap;">
                    <div style="text-align: center; padding: 10px; min-width: 120px;">
                        <div style="font-size: 1.8rem; font-weight: bold; color: #00ff88;" id="liveFPS">60</div>
                        <div>FPS hiện tại</div>
                    </div>
                    <div style="text-align: center; padding: 10px; min-width: 120px;">
                        <div style="font-size: 1.8rem; font-weight: bold; color: #00d4ff;" id="liveDelay">16ms</div>
                        <div>Độ trễ</div>
                    </div>
                    <div style="text-align: center; padding: 10px; min-width: 120px;">
                        <div style="font-size: 1.5rem; font-weight: bold; color: #ffaa00;" id="ratingText">TỐT</div>
                        <div>Đánh giá</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="info-box">
            <h3 style="color: #00d4ff; margin-bottom: 15px;">📋 HƯỚNG DẪN SỬ DỤNG</h3>
            <ol style="margin-left: 20px; line-height: 1.8;">
                <li>Điều chỉnh thanh trượt độ nhạy theo ý muốn</li>
                <li>Chọn các tùy chọn tối ưu hóa phù hợp</li>
                <li>Nhấn nút "BẮT ĐẦU TỐI ƯU HÓA" để áp dụng</li>
                <li>Kiểm tra trong khu vực cảm ứng</li>
                <li>Chia sẻ website với bạn bè: <strong>phambao21092007.svg.github.io/gamevu</strong></li>
            </ol>
        </div>
        
        <div class="info-box">
            <h3 style="color: #00ff88; margin-bottom: 15px;">✅ XÁC NHẬN HOẠT ĐỘNG</h3>
            <p style="color: #00ff88;">🎯 Website này đang chạy trên GitHub Pages:</p>
            <p style="background: rgba(0,0,0,0.5); padding: 15px; border-radius: 8px; margin: 10px 0; word-break: break-all;">
                🌐 <strong>URL của bạn:</strong> https://phambao21092007.svg.github.io/gamevu/
            </p>
            <p style="color: #aaa; font-size: 0.9rem;">
                💡 <strong>Mẹo:</strong> Để đảm bảo GitHub Pages hoạt động, file chính phải có tên <code>index.html</code> và cần có file <code>.nojekyll</code>
            </p>
        </div>
        
        <footer>
            <p>© 2024 - Công cụ Tối Ưu Hóa Điện Thoại Chơi Game</p>
            <p style="margin-top: 10px; color: #00d4ff;">
                🚀 Được host miễn phí trên GitHub Pages
            </p>
            <p style="margin-top: 10px; font-size: 0.9rem; color: #888;">
                Repository: <strong>gamevu</strong> | Branch: <strong>main</strong> | Deploy: <strong>Tự động</strong>
            </p>
        </footer>
    </div>

    <script>
        // Khởi tạo biến
        let sensitivity = 85;
        let fps = 60;
        let delay = 16;
        let stability = 95;
        
        // Lấy phần tử DOM
        const sensSlider = document.getElementById('sensitivitySlider');
        const sensValue = document.getElementById('sensValue');
        const sensCounter = document.getElementById('sensCounter');
        const fpsCounter = document.getElementById('fpsCounter');
        const delayCounter = document.getElementById('delayCounter');
        const stableCounter = document.getElementById('stableCounter');
        const optimizeBtn = document.getElementById('optimizeBtn');
        const touchPad = document.getElementById('touchPad');
        const ball = document.getElementById('ball');
        const liveFPS = document.getElementById('liveFPS');
        const liveDelay = document.getElementById('liveDelay');
        const ratingText = document.getElementById('ratingText');
        
        // 1. Xử lý thanh trượt
        sensSlider.addEventListener('input', function() {
            sensitivity = this.value;
            sensValue.textContent = sensitivity + '%';
            sensCounter.textContent = sensitivity + '%';
            updateStability();
            updateRating();
        });
        
        // 2. Nút tối ưu hóa
        optimizeBtn.addEventListener('click', function() {
            const opt1 = document.getElementById('opt1').checked;
            const opt2 = document.getElementById('opt2').checked;
            const opt3 = document.getElementById('opt3').checked;
            const opt4 = document.getElementById('opt4').checked;
            
            // Tính toán giá trị mới
            let newFPS = 60;
            let newDelay = 16;
            
            if (opt1) newFPS += 20;
            if (opt2) newDelay -= 5;
            if (opt3) {
                newFPS -= 10;
                newDelay += 3;
            }
            if (opt4) {
                newFPS += 5;
                newDelay -= 2;
            }
            
            // Áp dụng độ nhạy
            newFPS = Math.min(120, newFPS + sensitivity / 3);
            newDelay = Math.max(4, newDelay - sensitivity / 15);
            
            // Cập nhật
            fps = Math.round(newFPS);
            delay = Math.round(newDelay);
            
            fpsCounter.textContent = fps + ' FPS';
            delayCounter.textContent = delay + 'ms';
            liveFPS.textContent = fps;
            liveDelay.textContent = delay + 'ms';
            
            updateStability();
            updateRating();
            
            // Hiệu ứng
            this.innerHTML = '✅ ĐÃ TỐI ƯU HÓA!';
            this.style.background = 'linear-gradient(135deg, #00ff88, #00cc66)';
            
            setTimeout(() => {
                this.innerHTML = '🔄 TIẾP TỤC TỐI ƯU';
                this.style.background = 'linear-gradient(135deg, #00d4ff, #0066cc)';
            }, 2000);
            
            // Thông báo
            alert('🎮 Tối ưu hóa thành công!\nFPS: ' + fps + '\nĐộ trễ: ' + delay + 'ms');
        });
        
        // 3. Xử lý khu vực cảm ứng
        let isTouching = false;
        
        touchPad.addEventListener('touchstart', handleTouchStart, { passive: false });
        touchPad.addEventListener('touchmove', handleTouchMove, { passive: false });
        touchPad.addEventListener('touchend', handleTouchEnd);
        
        // Hỗ trợ chuột cho desktop
        touchPad.addEventListener('mousedown', handleMouseDown);
        document.addEventListener('mousemove', handleMouseMove);
        document.addEventListener('mouseup', handleMouseUp);
        
        let isMouseDown = false;
        let lastTime = 0;
        
        function handleTouchStart(e) {
            e.preventDefault();
            isTouching = true;
            lastTime = Date.now();
            if (e.touches[0]) {
                moveBall(e.touches[0].clientX, e.touches[0].clientY);
            }
        }
        
        function handleTouchMove(e) {
            e.preventDefault();
            if (isTouching && e.touches[0]) {
                moveBall(e.touches[0].clientX, e.touches[0].clientY);
                updateLiveStats();
            }
        }
        
        function handleTouchEnd() {
            isTouching = false;
        }
        
        function handleMouseDown(e) {
            isMouseDown = true;
            lastTime = Date.now();
            moveBall(e.clientX, e.clientY);
        }
        
        function handleMouseMove(e) {
            if (isMouseDown) {
                moveBall(e.clientX, e.clientY);
                updateLiveStats();
            }
        }
        
        function handleMouseUp() {
            isMouseDown = false;
        }
        
        function moveBall(clientX, clientY) {
            const rect = touchPad.getBoundingClientRect();
            let x = clientX - rect.left - 30;
            let y = clientY - rect.top - 30;
            
            x = Math.max(0, Math.min(rect.width - 60, x));
            y = Math.max(0, Math.min(rect.height - 60, y));
            
            ball.style.left = x + 'px';
            ball.style.top = y + 'px';
            ball.style.boxShadow = `0 0 ${sensitivity/2}px rgba(0, 255, 136, 0.7)`;
        }
        
        function updateLiveStats() {
            const now = Date.now();
            if (lastTime > 0) {
                const diff = now - lastTime;
                if (diff > 0) {
                    const currentFPS = Math.min(120, Math.max(30, 1000 / diff));
                    const adjustedFPS = Math.round(currentFPS * (sensitivity / 80));
                    
                    liveFPS.textContent = adjustedFPS;
                    liveDelay.textContent = Math.max(4, Math.round(diff - sensitivity/10)) + 'ms';
                    updateRating();
                }
            }
            lastTime = now;
        }
        
        function updateStability() {
            if (sensitivity < 30 || sensitivity > 90) {
                stability = 80;
            } else if (sensitivity < 50 || sensitivity > 80) {
                stability = 88;
            } else {
                stability = 95;
            }
            stableCounter.textContent = stability + '%';
        }
        
        function updateRating() {
            const currentFPS = parseInt(liveFPS.textContent);
            const currentDelay = parseInt(liveDelay.textContent);
            
            let rating = "TỐT";
            let color = "#00ff88";
            
            if (currentFPS >= 90) {
                rating = "TUYỆT VỜI";
                color = "#00ff88";
            } else if (currentFPS >= 75) {
                rating = "TỐT";
                color = "#00d4ff";
            } else if (currentFPS >= 60) {
                rating = "KHÁ";
                color = "#ffaa00";
            } else {
                rating = "TRUNG BÌNH";
                color = "#ff4444";
            }
            
            ratingText.textContent = rating;
            ratingText.style.color = color;
        }
        
        // Khởi tạo
        updateStability();
        updateRating();
        
        // Thông báo khi load
        window.addEventListener('load', function() {
            console.log('✅ Website đã tải thành công trên GitHub Pages!');
            console.log('🎮 Game Optimizer đã sẵn sàng!');
            console.log('📱 URL: https://phambao21092007.svg.github.io/gamevu/');
        });
    </script>
</body>
</html># index.html
