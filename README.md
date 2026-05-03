<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Peter's Tokyo Trip 2026</title>
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="東京2026">
    <style>
        :root { --primary-dark: #2c3e50; --accent-orange: #e67e22; --success-green: #27ae60; }
        body { font-family: -apple-system, system-ui; line-height: 1.6; color: #333; max-width: 800px; margin: 0 auto; padding: 20px; background-color: #f4f7f6; }
        header { background: var(--primary-dark); color: white; padding: 2rem 1rem; text-align: center; border-radius: 15px; margin-bottom: 20px; }
        .card { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.08); margin-bottom: 20px; }
        h2 { color: var(--primary-dark); font-size: 1.2rem; margin-top: 0; border-left: 4px solid var(--accent-orange); padding-left: 10px; }
        table { width: 100%; border-collapse: collapse; }
        th, td { text-align: left; padding: 15px 10px; border-bottom: 1px solid #eee; }
        textarea { width: 100%; border: 1px solid #ddd; border-radius: 8px; padding: 10px; box-sizing: border-box; font-size: 16px; min-height: 100px; }
    </style>
</head>
<body>
    <header>
        <h1>🇯🇵 東京自由行 2026</h1>
        <p>5月7日出發 | Peter</p>
    </header>
    <div class="card">
        <h2>🚀 交通筆記</h2>
        <p><strong>機場 -> T-CAT:</strong> 利木津巴士 (¥3,100)</p>
        <p><strong>飯店:</strong> 相鐵 FRESA INN 日本橋人形町</p>
    </div>
    <div class="card">
        <h2>🛍️ 退稅清單</h2>
        <table>
            <tr><td>藥妝 (松本清)</td><td><input type="checkbox" id="tax1"></td></tr>
            <tr><td>精品 (銀座三越)</td><td><input type="checkbox" id="tax2"></td></tr>
        </table>
    </div>
    <div class="card">
        <h2>🎬 影評筆記隨手記</h2>
        <textarea id="notes" placeholder="在此輸入筆記..."></textarea>
    </div>
    <script>
        const ids = ['tax1', 'tax2', 'notes'];
        window.onload = () => ids.forEach(id => {
            const val = localStorage.getItem(id);
            const el = document.getElementById(id);
            if (val !== null) el.type === 'checkbox' ? el.checked = val === 'true' : el.value = val;
        });
        ids.forEach(id => {
            const el = document.getElementById(id);
            el.onchange = () => localStorage.setItem(id, el.type === 'checkbox' ? el.checked : el.value);
            if (el.tagName === 'TEXTAREA') el.oninput = () => localStorage.setItem(id, el.value);
        });
    </script>
</body>
</html>
