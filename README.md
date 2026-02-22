<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>UPMED - Plateforme Médicale Éducative</title>

<style>
body{
font-family: "Segoe UI", Arial, sans-serif;
margin:0;
background:#f4f6f9;
color:#222;
}

header{
background:#0b3d91;
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
opacity:0.9;
}

.container{
max-width:1000px;
margin:auto;
padding:20px;
}

.section{
background:white;
padding:25px;
margin:20px 0;
border-radius:12px;
box-shadow:0 5px 15px rgba(0,0,0,0.05);
}

h2{
margin-top:0;
color:#0b3d91;
}

input, select, textarea{
width:100%;
padding:12px;
margin:10px 0;
border-radius:6px;
border:1px solid #ccc;
font-size:15px;
}

textarea{
min-height:120px;
}

button{
background:#0b3d91;
color:white;
border:none;
padding:12px;
width:100%;
font-size:16px;
font-weight:bold;
border-radius:6px;
cursor:pointer;
}

button:hover{
background:#1451b8;
}

.result{
background:#eef3ff;
padding:15px;
margin-top:15px;
border-radius:8px;
white-space:pre-line;
}

footer{
text-align:center;
font-size:12px;
color:gray;
padding:20px;
}
</style>
</head>

<body>

<header>
<h1>UPMED</h1>
<p>
Plateforme médicale éducative internationale<br>
Créée par <strong>Jemali Mavoka</strong><br>
Destinée aux étudiants et professionnels de santé
</p>
</header>

<div class="container">

<div class="section">
<h2>Présentation</h2>
<p>
UPMED est une plateforme pédagogique conçue pour aider les étudiants et professionnels
de santé à améliorer leur raisonnement clinique.

L'utilisateur peut entrer des symptômes, signes cliniques, résultats biologiques ou radiologiques.
Le système génère ensuite une simulation de raisonnement différentiel structurée
adaptée au niveau académique sélectionné.

Cette plateforme est strictement éducative et ne remplace en aucun cas un avis médical réel.
</p>
</div>

<div class="section">
<h2>Créer un Profil</h2>

<input id="nom" placeholder="Nom complet">

<select id="faculte">
<option>Médecine</option>
<option>Sciences Infirmières</option>
<option>Pharmacie</option>
<option>Kinésithérapie</option>
<option>Sage-femme</option>
<option>Autre</option>
</select>

<input id="specialite" placeholder="Spécialité (Anesthésie, Réanimation, Cardiologie...)">

<select id="niveau">
<option>Débutant</option>
<option>Intermédiaire</option>
<option>Avancé</option>
</select>

<button onclick="enregistrerProfil()">Enregistrer le profil</button>
</div>

<div class="section">
<h2>Simulation de Raisonnement Clinique</h2>

<textarea id="donnees" placeholder="Entrer les symptômes, antécédents, résultats biologiques, examens radiologiques..."></textarea>

<button onclick="analyser()">Analyser le cas</button>

<div id="resultat" class="result"></div>
</div>

<div class="section">
<h2>Générateur d’Examen Clinique</h2>

<select id="difficulte">
<option>Facile</option>
<option>Moyen</option>
<option>Difficile</option>
<option>Urgence Critique</option>
</select>

<button onclick="genererExamen()">Générer un cas clinique</button>

<div id="examen" class="result"></div>
</div>

</div>

<footer>
© 2026 UPMED - Créé par Jemali Mavoka  
Plateforme éducative uniquement.
</footer>

<script>

function enregistrerProfil(){
let profil={
nom:document.getElementById("nom").value,
faculte:document.getElementById("faculte").value,
specialite:document.getElementById("specialite").value,
niveau:document.getElementById("niveau").value
};

localStorage.setItem("profilUPMED", JSON.stringify(profil));
alert("Profil enregistré avec succès.");
}

function analyser(){

let profil=JSON.parse(localStorage.getItem("profilUPMED"));
let donnees=document.getElementById("donnees").value;

if(!profil){
alert("Veuillez d'abord enregistrer votre profil.");
return;
}

let texte=
"Profil : "+profil.nom+"\n"+
profil.faculte+" - "+profil.specialite+" ("+profil.niveau+")\n\n"+

"--- Analyse pédagogique du cas ---\n\n"+

"1) Diagnostics différentiels possibles :\n"+
"- Pathologie 1 compatible avec les symptômes\n"+
"- Pathologie 2 à éliminer\n"+
"- Pathologie grave à rechercher en priorité\n\n"+

"2) Examens complémentaires suggérés :\n"+
"- Bilan biologique ciblé\n"+
"- Imagerie adaptée\n"+
"- Surveillance des constantes\n\n"+

"3) Explication physiopathologique :\n"+
"Analyse adaptée au niveau "+profil.niveau+".\n\n"+

"4) Conduite à tenir (simulation éducative) :\n"+
"- Évaluation systématique ABCDE\n"+
"- Stabilisation initiale\n"+
"- Réévaluation continue\n\n"+

"⚠️ Ceci est une simulation éducative.";

document.getElementById("resultat").innerText=texte;
}

function genererExamen(){

let diff=document.getElementById("difficulte").value;

let cas=
"Cas Clinique - Niveau "+diff+"\n\n"+

"Un patient consulte pour des symptômes nécessitant une évaluation clinique.\n\n"+

"Questions :\n"+
"1) Quelle est votre priorité ?\n"+
"2) Quels diagnostics évoquez-vous ?\n"+
"3) Quels examens demandez-vous ?\n"+
"4) Quelle conduite à tenir proposez-vous ?\n\n"+

"Correction pédagogique :\n"+
"- Appliquer un raisonnement structuré\n"+
"- Identifier les urgences vitales\n"+
"- Justifier chaque décision\n\n"+

"Plateforme éducative.";

document.getElementById("examen").innerText=cas;
}

</script>

</body>
</html>
