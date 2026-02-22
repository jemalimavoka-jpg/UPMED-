<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>UPMED - International Medical Learning Platform</title>

<style>
body{
font-family:Arial, sans-serif;
margin:0;
background:#eef2f7;
color:#1a1a1a;
}

header{
background:#0d47a1;
color:white;
padding:30px 20px;
text-align:center;
}

header h1{
margin:0;
font-size:32px;
}

header p{
margin-top:10px;
font-size:15px;
}

.container{
padding:20px;
max-width:900px;
margin:auto;
}

.box{
background:white;
padding:20px;
margin:20px 0;
border-radius:10px;
box-shadow:0 4px 10px rgba(0,0,0,0.08);
}

h2{
color:#0d47a1;
margin-top:0;
}

input, select, textarea, button{
width:100%;
padding:12px;
margin:8px 0;
font-size:16px;
border-radius:6px;
border:1px solid #ccc;
}

button{
background:#0d47a1;
color:white;
border:none;
font-weight:bold;
}

button:hover{
background:#1565c0;
}

footer{
text-align:center;
font-size:12px;
padding:20px;
color:gray;
}
.small{
font-size:12px;
color:gray;
}
</style>
</head>

<body>

<header>
<h1>🌍 UPMED</h1>
<p>
International Medical Educational Platform  
Created by <strong>Jemali Mavoka</strong>
</p>
</header>

<div class="container">

<div class="box">
<h2>About UPMED</h2>
<p>
UPMED is an international educational medical platform created by Jemali Mavoka, 
designed to support students and healthcare professionals worldwide.  
It provides structured clinical reasoning simulations, exam generation tools, 
and adaptive explanations tailored to the user's academic level and specialty.
</p>

<p>
The platform aims to enhance understanding in medicine, nursing, anesthesia, 
critical care, pharmacy, and all healthcare disciplines.
</p>

<p class="small">
UPMED is strictly for educational purposes and does not provide medical diagnosis or clinical decision-making support.
</p>
</div>

<div class="box">
<h2>Create Your Profile</h2>

<select id="language">
<option>English</option>
<option>Français</option>
<option>Español</option>
<option>Português</option>
</select>

<input id="country" placeholder="Country">

<select id="faculty">
<option>Medicine</option>
<option>Nursing</option>
<option>Pharmacy</option>
<option>Physiotherapy</option>
<option>Midwifery</option>
<option>Other</option>
</select>

<input id="specialty" placeholder="Specialty (Anesthesia, ICU, Cardiology...)">

<select id="level">
<option>Beginner</option>
<option>Intermediate</option>
<option>Advanced</option>
</select>

<button onclick="saveProfile()">Save Profile</button>
</div>

<div class="box">
<h2>Clinical Reasoning Simulator</h2>

<textarea id="clinicalInput" placeholder="Enter symptoms, vital signs, lab results, imaging findings..."></textarea>

<button onclick="analyzeCase()">Analyze Case</button>

<pre id="analysisResult"></pre>
</div>

<div class="box">
<h2>Exam Generator</h2>

<select id="examLevel">
<option>Easy</option>
<option>Medium</option>
<option>Hard</option>
<option>Critical Emergency</option>
</select>

<button onclick="generateExam()">Generate Clinical Case</button>

<pre id="examResult"></pre>
</div>

</div>

<footer>
© 2026 UPMED – Created by Jemali Mavoka  
Educational platform only – Not for real patient care.
</footer>

<script>

function saveProfile(){
let profile={
language:document.getElementById("language").value,
country:document.getElementById("country").value,
faculty:document.getElementById("faculty").value,
specialty:document.getElementById("specialty").value,
level:document.getElementById("level").value
};

localStorage.setItem("upmedProfile", JSON.stringify(profile));
alert("Profile saved successfully.");
}

function analyzeCase(){

let profile=JSON.parse(localStorage.getItem("upmedProfile"));
let input=document.getElementById("clinicalInput").value;

if(!profile){
alert("Please create your profile first.");
return;
}

let output=
"User Profile:\n"+
profile.faculty+" - "+profile.specialty+" ("+profile.level+")\n\n"+

"Clinical Reasoning Simulation:\n\n"+

"1. Possible Differential Diagnoses:\n"+
"- Condition A related to symptoms\n"+
"- Condition B based on clinical findings\n"+
"- Condition C to exclude urgently\n\n"+

"2. Suggested Investigations:\n"+
"- Laboratory tests\n"+
"- Imaging\n"+
"- Monitoring parameters\n\n"+

"3. Physiopathological Explanation:\n"+
"Adapted to "+profile.level+" level.\n\n"+

"4. Priority Actions (Educational Simulation):\n"+
"- ABCDE assessment\n"+
"- Stabilize airway, breathing, circulation\n"+
"- Identify red flags\n\n"+

"⚠️ Educational simulation only.";

document.getElementById("analysisResult").textContent=output;
}

function generateExam(){

let level=document.getElementById("examLevel").value;

let caseText=
"Clinical Case - Level: "+level+"\n\n"+

"A patient presents with acute symptoms requiring clinical evaluation.\n\n"+

"Questions:\n"+
"1) What are the immediate priorities?\n"+
"2) What are the differential diagnoses?\n"+
"3) What investigations are needed?\n"+
"4) What is the management plan?\n\n"+

"Correction:\n"+
"- Perform systematic assessment\n"+
"- Identify life-threatening conditions\n"+
"- Provide stabilization\n"+
"- Reassess continuously\n\n"+

"Educational purpose only.";

document.getElementById("examResult").textContent=caseText;
}

</script>

</body>
</html>
