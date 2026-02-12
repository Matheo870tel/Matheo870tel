<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Gendarmerie LS</title>

<style>
body {
    font-family: Arial;
    margin: 0;
    background-color: #f0f2f5;
    text-align: center;
}

header {
    background-color: navy;
    color: white;
    padding: 20px;
}

button {
    padding: 10px 20px;
    margin: 10px;
    border: none;
    border-radius: 5px;
    background-color: darkblue;
    color: white;
    cursor: pointer;
}

button:hover {
    background-color: blue;
}

.container {
    padding: 20px;
}

.card {
    background: white;
    padding: 15px;
    margin: 10px auto;
    width: 300px;
    border-radius: 10px;
}

input, select {
    padding: 8px;
    margin: 5px;
    width: 200px;
}
</style>
</head>

<body>

<header>
    <h1>Bienvenue sur le site de la gendarmerie LS</h1>
</header>

<div class="container" id="home">
    <button onclick="showEffectif()">Effectif Gendarme</button>
    <button onclick="showSaisie()">Saisie</button>
</div>

<div class="container" id="effectif" style="display:none;">
    <h2>Équipe de Gendarmerie</h2>

    <div id="teamList"></div>

    <div id="adminSection" style="display:none;">
        <h3>Ajouter un membre</h3>
        <input type="text" id="nom" placeholder="Nom">
        <input type="text" id="grade" placeholder="Grade">
        <input type="number" id="anciennete" placeholder="Ancienneté (années)">
        <br>
        <button onclick="addMember()">Ajouter</button>
    </div>

    <br>
    <button onclick="goHome()">Retour</button>
</div>

<div class="container" id="saisie" style="display:none;">
    <h2>Formulaire de Saisie</h2>

    <input type="date" id="date">
    <input type="text" id="objet" placeholder="Objet">
    <input type="text" id="agent" placeholder="Agent">
    <br>
    <button onclick="addSaisie()">Enregistrer</button>

    <h3>Liste des saisies</h3>
    <div id="saisieList"></div>

    <br>
    <button onclick="goHome()">Retour</button>
</div>

<script>

let team = [];
let saisies = [];

// MOT DE PASSE ADMIN
const adminPassword = "admin123";

function showEffectif() {
    document.getElementById("home").style.display = "none";
    document.getElementById("effectif").style.display = "block";

    let password = prompt("Entrez le mot de passe admin pour ajouter un membre (laisser vide si non admin)");

    if(password === adminPassword){
        document.getElementById("adminSection").style.display = "block";
    }

    renderTeam();
}

function showSaisie() {
    document.getElementById("home").style.display = "none";
    document.getElementById("saisie").style.display = "block";
    renderSaisie();
}

function goHome() {
    document.getElementById("home").style.display = "block";
    document.getElementById("effectif").style.display = "none";
    document.getElementById("saisie").style.display = "none";
    document.getElementById("adminSection").style.display = "none";
}

function addMember() {
    let nom = document.getElementById("nom").value;
    let grade = document.getElementById("grade").value;
    let anciennete = document.getElementById("anciennete").value;

    team.push({nom, grade, anciennete});
    renderTeam();
}

function renderTeam() {
    let list = document.getElementById("teamList");
    list.innerHTML = "";

    team.forEach(member => {
        list.innerHTML += `
            <div class="card">
                <b>${member.nom}</b><br>
                Grade: ${member.grade}<br>
                Ancienneté: ${member.anciennete} ans
            </div>
        `;
    });
}

function addSaisie() {
    let date = document.getElementById("date").value;
    let objet = document.getElementById("objet").value;
    let agent = document.getElementById("agent").value;

    saisies.push({date, objet, agent});
    renderSaisie();
}

function renderSaisie() {
    let list = document.getElementById("saisieList");
    list.innerHTML = "";

    saisies.forEach(s => {
        list.innerHTML += `
            <div class="card">
                Date: ${s.date}<br>
                Objet: ${s.objet}<br>
                Agent: ${s.agent}
            </div>
        `;
    });
}

</script>

</body>
</html>
