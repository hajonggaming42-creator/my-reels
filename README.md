# my-reels
My Reels Social Media App 

<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>My Reels</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#101010;color:white;font-family:Arial}
header{padding:16px;background:#202020;font-size:25px;font-weight:bold;position:sticky;top:0}
.box{padding:16px;max-width:500px;margin:auto}
input,button{padding:13px;border:0;border-radius:10px;margin:6px 0;font-size:15px}
input{width:100%;background:#eee;color:#111}
button{background:#ff0060;color:white;cursor:pointer}
.full{width:100%}
#app{display:none}
.profile{text-align:center;padding:20px}
.avatar{width:95px;height:95px;border-radius:50%;object-fit:cover;background:#333}
.post{background:#222;margin:16px 0;padding:12px;border-radius:14px}
.post img,.post video{width:100%;max-height:550px;object-fit:contain;border-radius:10px}
.actions{display:flex;gap:8px}
.actions button{flex:1}
.comment{background:#333;padding:8px;margin:5px 0;border-radius:8px}
small{color:#aaa}
</style>
</head>
<body>

<header>📸 My Reels</header>

<section id="login" class="box">
<h2>Welcome to My Reels</h2>
<input id="email" type="email" placeholder="Email">
<input id="password" type="password" placeholder="Password">
<button class="full" onclick="signup()">Sign Up</button>
<button class="full" onclick="loginUser()">Login</button>
<p id="message"></p>
</section>

<section id="app">
<div class="profile">
<img id="avatar" class="avatar"
src="https://placehold.co/100x100?text=User">
<h2 id="username">My Profile</h2>
<input type="file" id="profileFile" accept="image/*">
<button onclick="changeProfile()">Change Profile Photo</button>
<button onclick="logout()">Logout</button>
</div>

<div class="box">
<h2>➕ Create Post</h2>
<input type="file" id="mediaFile"
accept="image/*,video/*">
<input id="caption" placeholder="Write something...">
<button class="full" onclick="uploadPost()">Share Post</button>
</div>

<div class="box">
<h2> Feed</h2>
<div id="feed"></div>
</div>
</section>

<script type="module">

import {initializeApp}
from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";

import {
getAuth,createUserWithEmailAndPassword,
signInWithEmailAndPassword,signOut,
onAuthStateChanged
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";

const firebaseConfig={
apiKey:"AIzaSyCirCxl-fFIDyZBavs0tWp4vNIdduQne84",
authDomain:"my-reeal.firebaseapp.com",
projectId:"my-reeal",
storageBucket:"my-reeal.firebasestorage.app",
messagingSenderId:"140289292488",
appId:"1:140289292488:web:56ed247e2a36e102ad4dfd",
measurementId:"G-V6BN04X85T"
};

const firebaseApp=initializeApp(firebaseConfig);
const auth=getAuth(firebaseApp);

let posts=[];
let currentUser=null;
let profileURL="https://placehold.co/100x100?text=User";

window.signup=async()=>{
try{
await createUserWithEmailAndPassword(
auth,email.value,password.value);
message.textContent="Account created!";
}catch(e){message.textContent=e.message}
};
