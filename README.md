## Hi there 👋

<!--
**Matheo870tel/Matheo870tel** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

<!DOCTYPE html>
<html>
<head>
  <title>Mon site de posts</title>
</head>
<body>

  <h1>Créer un post</h1>

  <input type="text" id="title" placeholder="Titre"><br><br>
  <textarea id="content" placeholder="Contenu"></textarea><br><br>

  <button onclick="sendPost()">Publier</button>

  <script>
    async function sendPost() {
      const title = document.getElementById("title").value;
      const content = document.getElementById("content").value;

      const response = await fetch("https://api.github.com/repos/TON-USERNAME/TON-REPO/issues", {
        method: "POST",
        headers: {
          "Authorization": "token TON_TOKEN_GITHUB",
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          title: title,
          body: content
        })
      });

      if(response.ok){
        alert("Post publié !");
      } else {
        alert("Erreur");
      }
    }
  </script>

</body>
</html>
