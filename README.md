<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>AUTHENTICATION BLOCKED</title>

<style>
body {
    margin: 0;
    height: 100vh;
    background: radial-gradient(circle, #0b0b0b, #000);
    font-family: Arial, Helvetica, sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ff3b3b;
}

.x {
    position: absolute;
    top: 15px;
    right: 20px;
    font-size: 22px;
    cursor: pointer;
}

.box {
    background: #111;
    border: 2px solid #ff3b3b;
    padding: 30px;
    width: 380px;
    text-align: center;
    box-shadow: 0 0 25px red;
}

input {
    width: 90%;
    padding: 10px;
    margin-top: 15px;
    background: black;
    border: 1px solid #ff3b3b;
    color: #0f0;
    font-size: 16px;
    text-align: center;
}

button {
    margin-top: 15px;
    padding: 10px 20px;
    background: #ff3b3b;
    border: none;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    background: #ff6666;
}

.error {
    color: orange;
    display: none;
    margin-top: 10px;
}

.dashboard {
    display: none;
    color: #0f0;
}

.dashboard button {
    background: #0f0;
    margin: 10px;
}

#blockedScreen {
    display: none;
}
</style>
</head>

<body>

<div class="x" onclick="alert('Window closed (demo)')">✖</div>

<!-- LOCK SCREEN -->
<div class="box" id="lockScreen">
    <h1>AUTHENTICATION BLOCKED</h1>
    <p>Administrator access required</p>

    <input type="password" id="password" placeholder="ENTER ADMIN PASSWORD">
    <button onclick="checkPassword()">UNLOCK</button>

    <div class="error" id="error">ACCESS DENIED</div>
</div>

<!-- DASHBOARD -->
<div class="box dashboard" id="dashboard">
    <h1>ACCESS GRANTED</h1>
    <p>Welcome, Administrator</p>

    <button onclick="openBlank()">OPEN about:blank</button>
    <button onclick="fakeRoblox()">ROBLOX</button>
</div>

<!-- BLOCKED SCREEN -->
<div class="box dashboard" id="blockedScreen">
    <h1 style="color:red;">ACCESS BLOCKED</h1>
    <p>Roblox has been blocked by the network administrator.</p>
    <p style="color:orange;">Reason: Restricted Website</p>

    <button onclick="goBack()">RETURN</button>
</div>

<script>
function checkPassword() {
    const pass = document.getElementById("password").value;
    const error = document.getElementById("error");

    if (pass === "0601") {
        document.getElementById("lockScreen").style.display = "none";
        document.getElementById("dashboard").style.display = "block";
    } else {
        error.style.display = "block";
    }
}

function openBlank() {
    document.body.innerHTML = `
        <div style="color:white; font-family:Arial; text-align:center; margin-top:40vh;">
            <h1>about:blank</h1>
            <p style="color:gray;">Demo page</p>
        </div>
    `;
}

function fakeRoblox() {
    document.getElementById("dashboard").style.display = "none";
    document.getElementById("blockedScreen").style.display = "block";
}

function goBack() {
    document.getElementById("blockedScreen").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
}
</script>

</body>
</html>
