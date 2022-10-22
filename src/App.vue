<script setup>

import LineChart from "./components/LineChart.vue"
import Donut from "./components/DoughnutChart.vue"
import Bar from "./components/BarChart.vue"
</script>


<template>
  <div class="mx-96">
  <h1 class="bg-vertPomme m-5 rounded-xs text-4xl text-center font-montserrat text-white">Comment mixer écologie et sécurité dans sa région ?</h1>
  <p class="text-center mx-10 font-montserrat text-xl">Avec le <strong>réchauffement climatique</strong> et la <strong>pollution</strong>, il est devenu de plus en plus nécessaire pour les communes de limiter les trajets en <strong>voitures</strong>. Le <strong>vélo</strong> est une très bonne alternative, mais en ville cette pratique peut vite devenir <strong>dangereuse</strong>. Ici, vous trouverez toutes les données nécessaires pour vous aider à faire les bons choix !</p>
  </div>

  <div class="flex mx-5 mt-20">
    <div class="w-1/2">
      <h2 class="text-3xl font-montserrat text-titres">Les pistes cyclables : la solution</h2>
      <p class="font-montserrat text-base">Les premières pistes cyclables ont été créées en 1970. Cependant, alors que plusieurs villes avaient déjà sauté le pas pour rendre leur ville plus agréable et plus verte comme Paris, Grenoble, ou encore Strasbourg, c’est en 2018 avec le plan Vélo lancé par le gouvernement que les pistes cyclables se sont développées dans toute la France. Le but : financer les communes pour qu’elles rénovent leurs infrastructures, et développent le réseaux des pistes cyclables.</p>
      <p class="font-montserrat text-base">Même avant le lancement de ce plan Vélo, les pistes cyclcables sont devenues des infrasctructures recherchées dans les villes dès 2014. Ainsi, on peut voir sur ce graphique que le devéloppement des pistes cyclables a eu un effet positif sur l’accidentologie des vélos. En effet, entre 2005 et 2017, le nombre de blessés légers et de blessés graves diminuaient d’année en année mais de manière faible, passant de 3 100 blessés légers à vélo en 2005 à 2 800 en 2017. Cependant, à partir de 2017, les chiffres chutes a une vitesse fascinante, passant de 2 800 blessés à vélo en 2017 à 1 250 en 2018. </p>
    </div>
    <div class="w-1/2 items-center">
    <h3 class="text-2xl font-montserrat text-center">Évolution des blessés légers, blessés hospitalisés, personnes indemnes et de tués dans des accidents à vélo entre 2005 et 2018</h3>
    <LineChart/>
    </div>
  </div>

  
</template>


