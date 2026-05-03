<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Peter's Tokyo Trip 2026</title>
    
    <!-- iOS App 模式設定 -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="東京2026">
    
    <style>
        :root {
            --primary-dark: #2c3e50;
            --accent-orange: #e67e22;
            --success-green: #27ae60;
        }
        body { 
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; 
            line-height: 1.6; 
            color: #333; 
            max-width: 800px; 
            margin: 0 auto; 
            padding: 20px; 
            background-color: #f4f7f6; 
        }
        header { 
            background: var(--primary-dark); 
            color: white; 
            padding: 2rem 1rem; 
            text-align: center; 
            border-radius: 15px; 
            margin-bottom: 20px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }
        .card { 
            background: white; 
            padding: 20px; 
            border-radius: 12px; 
            box-shadow: 0 2px 8px rgba(0,0,0,0.08); 
            margin-bottom: 20px; 
        }
        h2 { color: var(--primary-dark); font-size: 1.2rem; margin-top: 0; border-left: 4px solid var(--accent-orange); padding-left: 10px; }
        .highlight { color: var(--accent-orange); font-weight: bold; }
        .status-tag { background: var(--success-green); color: white; padding: 3px 10px; border-radius: 20px; font-size: 0.8rem; }
        
        table { width: 100%; border-collapse: collapse; margin-top: 10px; }
        th, td { text-align: left; padding: 15px 10px; border-bottom: 1px solid #eee; }
        
        .btn { 
            background: #3498db; 
            color: white; 
            border: none; 
            padding: 12px 20px; 
            border-radius: 8px; 
            cursor: pointer; 
            width: 100%;
            font-size: 1rem;
            margin-top: 10px;
        }
        textarea {
            width: 100%;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 10px;
            box-sizing: border-box;
            font-size: 16px; /* 防止 iOS 自動放大 */
        }
    </style>
</head>
<body>

<header>
    <h1>🇯🇵 東京自由行 2026</h1>
    <p>5月7日出發 | 電影評論家 Peter</p>
</header>

<div class="card">
    <h2>🚀 機場交通</h2>
    <p><strong>方式：</strong> 利木津巴士 (Limousine Bus)</p>
    <p><strong>站點：</strong> T-CAT (東京城市航空總站)</p>
    <p><strong>飯店：</strong> 相鐵 FRESA INN 日本橋人形町</p>
    <button class="btn" onclick="alert('下車後步行 5 分鐘抵達飯店。記得在 T-CAT 二樓確認回程班次！')">查看交通導覽</button>
</div>

<div class="card">
    <h2>🛍️ 退稅進度 (現場免稅制)</h2>
    <table>
        <tr>
            <th>項目</th>
            <th>狀態</th>
        </tr>
        <tr>
            <td>藥妝 (松本清)</td>
            <td><label><input type="checkbox" id="tax_drugstore"> 已完成</label></td>
        </tr>
        <tr>
            <td>精品 (銀座三越)</td>
            <td><label><input type="checkbox" id="tax_ginza"> 已完成</label></td>
        </tr>
        <tr>
            <td>電器 (Bic Camera)</td>
            <td><label><input type="checkbox" id="tax_bic"> 已完成</label></td>
        </tr>
    </table>
</div>

<div class="card">
    <h2>🎬 Peter 的影評隨筆</h2>
    <textarea id="movieNotes" placeholder="在東京街頭想到的哲學觀點..."></textarea>
    <p style="font-size: 0.8rem; color: #888;">* 內容將自動儲存在此手機中</p>
</div>

<script>
    // --- 自動儲存邏輯 ---
    const elements = ['tax_drugstore', 'tax_ginza', 'tax_bic', 'movieNotes'];

    // 頁面載入時讀取資料
    window.onload = () => {
        elements.forEach(id => {
            const savedValue = localStorage.getItem(id);
            const el = document.getElementById(id);
            if (savedValue !== null) {
                if (el.type === 'checkbox') {
                    el.checked = savedValue === 'true';
                } else {
                    el.value = savedValue;
                }
            }
        });
        console.log("資料已從 LocalStorage 恢復");
    };

    // 監聽變動並儲存
    elements.forEach(id => {
        const el = document.getElementById(id);
        el.addEventListener('change', () => {
            const value = el.type === 'checkbox' ? el.checked : el.value;
            localStorage.setItem(id, value);
        });
        // 針對 textarea 增加即時輸入儲存
        if (el.tagName === 'TEXTAREA') {
            el.addEventListener('input', () => {
                localStorage.setItem(id, el.value);
            });
        }
    });
</script>

</body>
</html>
