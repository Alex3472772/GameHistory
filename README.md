# GameHistory
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Histoires Immersives de Jeux Vidéo</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 20px;
      color: #fff;
      transition: background 1s ease;
      background: linear-gradient(to right, #222, #555);
    }

    h1 {
      text-align: center;
      font-size: 2.5em;
      margin-bottom: 20px;
      text-shadow: 2px 2px 5px #000;
    }

    select {
      width: 100%;
      padding: 12px;
      font-size: 18px;
      margin-bottom: 20px;
      border-radius: 8px;
      border: none;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }

    .story-box {
      position: relative;
      background-color: rgba(0, 0, 0, 0.85);
      padding: 30px;
      border-radius: 15px;
      white-space: pre-wrap;
      font-size: 1.1em;
      line-height: 1.7;
      animation: fadeIn 1s ease;
      overflow: hidden;
      z-index: 1;
    }

    .story-box::before {
      content: "";
      position: absolute;
      top: -10px;
      left: -10px;
      right: -10px;
      bottom: -10px;
      background: var(--flame-color, rgba(255, 100, 0, 0.5));
      animation: flameGlow 3s linear infinite;
      filter: blur(20px);
      border-radius: 20px;
      z-index: 0;
    }

    .story-box p {
      position: relative;
      z-index: 1;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.98); }
      to { opacity: 1; transform: scale(1); }
    }

    @keyframes flameGlow {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
  </style>
</head>
<body>
  <h1>🔥 Histoires Immersives de Jeux Vidéo 🔥</h1>
  <select id="gameSelect" onchange="showStory()">
    <option value="">-- Choisissez un jeu --</option>
    <option value="witcher">The Witcher 3</option>
    <option value="skyrim">Skyrim</option>
    <option value="reddead">Red Dead Redemption 2</option>
    <option value="godofwar">God of War</option>
    <option value="zelda">The Legend of Zelda</option>
    <option value="finalfantasy">Final Fantasy VII</option>
    <option value="assassins">Assassin’s Creed</option>
    <option value="metalgear">Metal Gear Solid</option>
    <option value="minecraft">Minecraft</option>
    <option value="undertale">Undertale</option>
  </select>

  <div class="story-box" id="storyContent">
    <p>Sélectionnez un jeu pour découvrir son histoire immersive.</p>
  </div>
  <script>
    const themes = {
      witcher: "linear-gradient(to right, #3e5151, #decba4)",
      skyrim: "linear-gradient(to right, #1e3c72, #2a5298)",
      reddead: "linear-gradient(to right, #b92b27, #1565c0)",
      godofwar: "linear-gradient(to right, #000000, #434343)",
      zelda: "linear-gradient(to right, #56ab2f, #a8e063)",
      finalfantasy: "linear-gradient(to right, #8e9eab, #eef2f3)",
      assassins: "linear-gradient(to right, #bdc3c7, #2c3e50)",
      metalgear: "linear-gradient(to right, #232526, #414345)",
      minecraft: "linear-gradient(to right, #76b852, #8DC26F)",
      undertale: "linear-gradient(to right, #000000, #434343)"
    };

    const flames = {
      witcher: "conic-gradient(from 0deg, rgba(255,80,0,0.5), rgba(255,140,0,0.6), rgba(255,0,0,0.4))",
      skyrim: "conic-gradient(from 0deg, rgba(0,100,255,0.5), rgba(0,150,255,0.6), rgba(0,200,255,0.4))",
      reddead: "conic-gradient(from 0deg, rgba(255,0,0,0.5), rgba(255,80,0,0.6), rgba(255,0,0,0.4))",
      godofwar: "conic-gradient(from 0deg, rgba(255,255,255,0.3), rgba(200,200,200,0.4), rgba(100,100,100,0.3))",
      zelda: "conic-gradient(from 0deg, rgba(0,255,100,0.4), rgba(100,255,150,0.5), rgba(0,200,100,0.3))",
      finalfantasy: "conic-gradient(from 0deg, rgba(180,0,255,0.4), rgba(220,100,255,0.5), rgba(150,0,200,0.3))",
      assassins: "conic-gradient(from 0deg, rgba(255,255,255,0.4), rgba(180,180,180,0.5), rgba(100,100,100,0.3))",
      metalgear: "conic-gradient(from 0deg, rgba(100,255,255,0.4), rgba(150,255,255,0.5), rgba(50,200,200,0.3))",
      minecraft: "conic-gradient(from 0deg, rgba(0,255,0,0.4), rgba(100,255,100,0.5), rgba(0,200,0,0.3))",
      undertale: "conic-gradient(from 0deg, rgba(255,255,0,0.4), rgba(255,200,0,0.5), rgba(255,150,0,0.3))"
    };

    const stories = {
      witcher: `Geralt de Riv, sorceleur solitaire, arpente les terres ravagées de Velen, à la recherche de Ciri, sa fille adoptive. Dans un monde où les monstres ne sont pas toujours ceux que l’on croit, il affronte goules, spectres, et la corruption des hommes. Chaque village cache un secret, chaque contrat révèle une tragédie. Entre les intrigues politiques de Novigrad, les dieux oubliés de Skellige et les souvenirs brisés de son passé, Geralt doit choisir : suivre son cœur ou son code. Car la Chasse Sauvage approche, et le destin du monde repose sur ses épaules.`,

      skyrim: `Vous vous réveillez dans une charrette, prisonnier, sans nom. Le ciel s’ouvre, un dragon surgit. Vous êtes l’Enfant de Dragon, porteur d’un pouvoir ancien. Bordeciel est en guerre, les jarls divisés, les légendes oubliées. Vous apprenez les cris, rejoignez les Compagnons, infiltrez la Confrérie Noire, ou devenez archimage. Chaque choix façonne le monde. Alduin, le dévoreur de mondes, menace l’existence même. Mais au sommet de la Gorge du Monde, vous affrontez votre destin. Skyrim est une épopée de liberté, de puissance, et de légende.`,

      reddead: `Arthur Morgan est un hors-la-loi loyal, mais le monde change. Les cowboys disparaissent, les villes s’élèvent. La bande de Dutch s’effondre, rongée par la paranoïa et la cupidité. Arthur, malade, doute. Il aide les faibles, protège les siens, ou sombre dans la violence. Chaque braquage, chaque trahison, chaque coucher de soleil est un pas vers la fin. Red Dead Redemption 2 est une ballade mélancolique, une ode à l’honneur perdu, un dernier souffle de liberté.`,

      godofwar: `Kratos, ancien dieu de la guerre, vit reclus dans les terres nordiques. À la mort de sa femme, il part avec son fils Atreus pour répandre ses cendres au sommet du monde. Mais les dieux nordiques ne dorment pas. Baldur, fils d’Odin, les traque. Kratos cache son passé, sa rage, sa divinité. Atreus découvre qu’il est plus qu’un enfant. Ensemble, ils affrontent géants, dragons, et vérités. God of War est une saga de rédemption, de transmission, et de puissance contenue.`,

      zelda: `Link s’éveille après cent ans de sommeil. Hyrule est en ruines, Zelda retient Ganon dans un combat sans fin. Guidé par les souvenirs, Link explore un monde libre, vivant, dangereux. Il retrouve les prodiges, maîtrise les pouvoirs anciens, et reconstruit son identité. Chaque montagne gravie, chaque sanctuaire résolu, chaque silence partagé avec un cheval est une prière pour la lumière. Breath of the Wild est une légende vivante, une aventure sans limites.`,

      finalfantasy: `Cloud Strife, mercenaire taciturne, rejoint Avalanche pour saboter les réacteurs Mako de Midgar. Mais son passé est un puzzle. Sephiroth, guerrier mythique devenu fou, veut invoquer une météorite. Cloud doute de sa mémoire, de son identité. Avec Tifa, Aerith, Barret et d’autres, il traverse un monde blessé, affronte des armes vivantes, et plonge dans les abysses de son esprit. Final Fantasy VII est une quête de soi, une lutte écologique, une tragédie cosmique.`,

      assassins: `Desmond Miles revit les souvenirs de ses ancêtres assassins : Altaïr, Ezio, Connor. À travers l’Animus, il découvre une guerre millénaire entre Assassins et Templiers. Chaque époque révèle des secrets, des artefacts anciens, des choix moraux. De la Renaissance italienne à la Révolution américaine, les lames se croisent dans l’ombre. Les Fragments d’Éden, puissants reliques, peuvent contrôler les esprits. Desmond doit comprendre, agir, et sauver le monde moderne. Assassin’s Creed est une fresque historique, une quête de liberté, une danse entre mémoire et destin.`,

      metalgear: `Solid Snake, soldat d’élite, est envoyé sur Shadow Moses pour stopper Metal Gear Rex, un robot nucléaire. Mais la mission est un piège. Liquid Snake, son frère génétique, l’attend. Derrière les murs : manipulations, clones, guerre froide prolongée. Snake découvre qu’il est lui-même un produit d’expériences. Chaque ennemi est un miroir : Sniper Wolf, Revolver Ocelot, Psycho Mantis. Le combat n’est pas seulement physique, mais moral. Metal Gear Solid est un thriller politique, une réflexion sur l’identité, la guerre, et le libre arbitre.`,

      minecraft: `Vous ouvrez les yeux dans un monde infini. Pas de règles, pas de but. Juste vous, et votre imagination. Vous construisez un abri, explorez des grottes, trouvez du diamant. Vous affrontez des creepers, traversez le Nether, domptez des loups. Chaque bloc posé est une décision, chaque structure une œuvre. En mode survie, chaque nuit est une épreuve. En mode créatif, chaque jour est une toile. Minecraft est un monde à façonner, une aventure à inventer, un miroir de votre esprit.`,

      undertale: `Un enfant tombe dans un monde souterrain peuplé de monstres. Mais ici, tout dépend de vos choix. Tuez, ou épargnez. Combattez, ou discutez. Chaque action a des conséquences. Vous rencontrez Toriel, Sans, Papyrus, Undyne, Alphys, et Flowey. Le système de combat est unique : esquivez, parlez, comprenez. Le jeu se souvient. Il brise le quatrième mur. Il vous juge. Il vous pousse à réfléchir : qui êtes-vous ? Pourquoi jouez-vous ? Que signifie la compassion ? Undertale est une œuvre introspective, drôle, émouvante et parfois terrifiante. Un jeu qui vous regarde dans les yeux.`
    };

    function showStory() {
      const selected = document.getElementById("gameSelect").value;
      const story = stories[selected] || "Histoire non disponible.";
      const flame = flames[selected] || "rgba(255,100,0,0.5)";
      document.getElementById("storyContent").innerHTML = `<p>${story}</p>`;
      document.body.style.background = themes[selected] || "linear-gradient(to right, #222, #555)";
      document.querySelector(".story-box").style.setProperty("--flame-color", flame);
    }
  </script>
</body>
</html>
