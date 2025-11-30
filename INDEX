<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Faylo AI</title>
    <style>
        body { 
            font-family: Arial;
            background:#0d0d0d;
            color:white;
            margin:0; 
            padding:0;
        }
        header {
            background:#111;
            padding:20px;
            text-align:center;
            font-size:26px;
            font-weight:bold;
            border-bottom:2px solid #00ff99;
        }
        nav {
            display:flex;
            justify-content:center;
            gap:20px;
            margin:20px 0;
        }
        nav button {
            padding:12px 20px;
            background:#00cc66;
            border:none;
            border-radius:10px;
            cursor:pointer;
            color:white;
            font-size:16px;
        }
        section {
            padding:20px;
            display:none;
        }
        #home {
            display:block;
            text-align:center;
        }
        .chat-box { width:100%; max-width:600px; margin:auto; }
        .msg { padding:10px; margin:5px 0; border-radius:10px; }
        .user { background:#0066ff; text-align:right; }
        .ai { background:#333; }
        input,button { padding:10px; width:100%; margin-top:10px; border-radius:8px; border:none; }
        .send-btn { background:#00cc66; color:white; cursor:pointer; }
    </style>
</head>

<body>

<header>Faylo AI</header>

<nav>
    <button onclick="showPage('home')">Home</button>
    <button onclick="showPage('chat')">AI Chat</button>
</nav>

<!-- الصفحة الرئيسية -->
<section id="home">
    <h2>مرحبا بك فـ Faylo</h2>
    <p style="opacity:0.7">اختار من الفوق واش بغيتي الصفحة الرئيسية ولا AI Chat.</p>
    <img src="https://media.tenor.com/HWLvYOhV3ycAAAAj/robot-wave.gif" width="200">
</section>

<!-- صفحة الدردشة مع AI -->
<section id="chat">
    <h2>الدردشة مع Faylo AI</h2>
    
    <div class="chat-box" id="chatBox"></div>

    <input type="text" id="msgInput" placeholder="كتب رسالتك هنا...">
    <button class="send-btn" onclick="sendMessage()">إرسال</button>
</section>

<script>
const API_BASE = "https://YOUR-VERCEL-URL"; // ← هنا بدّل بالرابط ديال السيرفر

function showPage(pageId) {
    document.querySelectorAll("section").forEach(s => s.style.display = "none");
    document.getElementById(pageId).style.display = "block";
}

function addMsg(text, type) {
    const div = document.createElement("div");
    div.className = "msg " + type;
    div.innerText = text;
    document.getElementById("chatBox").appendChild(div);
}

async function sendMessage() {
    let msg = document.getElementById("msgInput").value.trim();
    if (!msg) return;

    addMsg(msg, "user");
    document.getElementById("msgInput").value = "";

    let res = await fetch(API_BASE + "/chat", {
        method: "POST",
        headers: {"Content-Type":"application/json"},
        body: JSON.stringify({ message: msg })
    });

    let data = await res.json();
    addMsg(data.reply, "ai");
}
</script>

</body>
</html>
