# Greenboys-download-test
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <title>🟢 GreenBoys Downloader</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #e0f7fa;
      padding: 30px;
    }
    h1 {
      color: #00796b;
    }
    input[type="text"] {
      width: 80%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    select,
    button {
      padding: 10px;
      margin: 10px;
      border-radius: 5px;
      border: none;
      background-color: #00796b;
      color: white;
      cursor: pointer;
    }
    .log {
      background: #fff;
      padding: 15px;
      white-space: pre-wrap;
      border-radius: 5px;
      max-height: 200px;
      overflow-y: auto;
      margin-top: 20px;
      text-align: left;
    }
  </style>
</head>
<body>
  <h1>🟢 تنزيل من YouTube</h1>
  <input type="text" id="url" placeholder="أدخل رابط يوتيوب (فيديو أو قائمة)"/>
  <select id="format">
    <option value="bestvideo+bestaudio">MP4 - أفضل جودة</option>
    <option value="bestvideo[ext=webm]+bestaudio">WebM - عالية الجودة</option>
    <option value="worstvideo[ext=3gp]+worstaudio">3GP - منخفضة الجودة</option>
    <option value="bestaudio[ext=m4a]">صوت فقط (M4A)</option>
    <option value="bestaudio[ext=mp3]">صوت فقط (MP3)</option>
  </select>
  <button onclick="download()">⬇️ تنزيل</button>
  <div class="log" id="log">الحالة ستظهر هنا...</div>

  <script>
    function download() {
      const url = document.getElementById("url").value;
      const format = document.getElementById("format").value;
      const log = document.getElementById("log");

      if (!url) {
        log.textContent = "❌ الرجاء إدخال رابط صحيح.";
        return;
      }

      log.textContent = "🔄 الاتصال بالخادم المحلي...";

      fetch(`http://localhost:3000/download?url=${encodeURIComponent(url)}&format=${encodeURIComponent(format)}`)
        .then(res => res.text())
        .then(data => log.textContent = data)
        .catch(err => log.textContent = "⚠️ خطأ في الاتصال.\nتأكد من تشغيل الخادم.");
    }
  </script>
</body>
</html>
