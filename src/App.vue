<script setup>

import LineChart from "./components/LineChart.vue"
import Donut from "./components/DoughnutChart.vue"
import Bar from "./components/BarChart.vue"
</script>


<template>
  <div class="mx-96">
  <h1 class=" bg-vertPomme m-5 rounded-xs text-4xl text-center font-montserrat text-white">Comment mixer écologie et sécurité dans sa région ?</h1>
  </div>
  <p class="mx-80 text-center font-montserrat text-xl">Avec le <strong>réchauffement climatique</strong> et la <strong>pollution</strong>, il est devenu de plus en plus nécessaire pour les communes de limiter les trajets en <strong>voitures</strong>. Le <strong>vélo</strong> est une très bonne alternative, mais en ville cette pratique peut vite devenir <strong>dangereuse</strong>. Ici, vous trouverez toutes les données nécessaires pour vous aider à faire les bons choix !</p>

  <div class="flex gap-12 mx-5 mt-20 items-center">
    <div class="w-1/2">
      <h2 class="text-3xl font-montserrat font-bold text-titres">Les pistes cyclables : la solution</h2>
      <p class="font-montserrat text-base">Les premières pistes cyclables ont été créées en 1970. Cependant, alors que plusieurs villes avaient déjà sauté le pas pour rendre leur ville plus agréable et plus verte comme Paris, Grenoble, ou encore Strasbourg, c’est en 2018 avec le plan Vélo lancé par le gouvernement que les pistes cyclables se sont développées dans toute la France. Le but : financer les communes pour qu’elles rénovent leurs infrastructures, et développent le réseaux des pistes cyclables.</p>
      <p class="font-montserrat text-base">Même avant le lancement de ce plan Vélo, les pistes cyclcables sont devenues des infrasctructures recherchées dans les villes dès 2014. Ainsi, on peut voir sur ce graphique que le devéloppement des pistes cyclables a eu un effet positif sur l’accidentologie des vélos. En effet, entre 2005 et 2017, le nombre de blessés légers et de blessés graves diminuaient d’année en année mais de manière faible, passant de 3 100 blessés légers à vélo en 2005 à 2 800 en 2017. Cependant, à partir de 2017, les chiffres chutes a une vitesse fascinante, passant de 2 800 blessés à vélo en 2017 à 1 250 en 2018. </p>
    </div>
  <div class="w-1/2">
    <h3 class="text-xl font-montserrat text-center">Évolution des blessés légers, blessés hospitalisés, personnes indemnes et de tués dans des accidents à vélo entre 2005 et 2018</h3>
    <LineChart/>
  </div>
  </div>

    <p class="mx-5 my-16 text-2xl font-semibold font-montserrat text-center">Les pistes cyclables sont la solution pour une région écologique et sûre, mais où les installer pour les rendre efficaces ?</p>
    <figure class="my-5">
    <img src="../public/routecyclable.jpg" alt="image route cyclable">
    <figcaption class="mt-3 font-montserrat text-center italic">Piste cyclable</figcaption>
    </figure> 

    <div class="flex mx-5 gap-12 mt-20 items-center">
      <div class="w-1/3">
        <h3 class="text-xl mb-5 font-montserrat text-center">Taux d’accidents en agglomération ou non entre 2005 et 2018</h3>
        <Donut/>
      </div>
      <div class="w-2/3">
      <h2 class="text-3xl font-montserrat font-bold text-titres">L’agglomération : place critique</h2>
      <p class="font-montserrat text-base">Les premières pistes cyclables ont été créées en 1970. Cependant, alors que plusieurs villes avaient déjà sauté le pas pour rendre leur ville plus agréable et plus verte comme Paris, Grenoble, ou encore Strasbourg, c’est en 2018 avec le plan Vélo lancé par le gouvernement que les pistes cyclables se sont développées dans toute la France. Le but : financer les communes pour qu’elles rénovent leurs infrastructures, et développent le réseaux des pistes cyclables.</p>
      <p class="font-montserrat text-base">Même avant le lancement de ce plan Vélo, les pistes cyclcables sont devenues des infrasctructures recherchées dans les villes dès 2014. Ainsi, on peut voir sur ce graphique que le devéloppement des pistes cyclables a eu un effet positif sur l’accidentologie des vélos. En effet, entre 2005 et 2017, le nombre de blessés légers et de blessés graves diminuaient d’année en année mais de manière faible, passant de 3 100 blessés légers à vélo en 2005 à 2 800 en 2017. Cependant, à partir de 2017, les chiffres chutes a une vitesse fascinante, passant de 2 800 blessés à vélo en 2017 à 1 250 en 2018. </p>
    </div>
    </div>

    <div class="flex items-center">
      <h3 class="flex flex-wrap justify-center w-1/2 text-center font-montserrat font-bold text-3xl">En agglomération oui, mais sur quelles types de routes ?</h3>
      <div class="w-1/2">
        <div class="flex">
          <img class="w-1/2" src="../public/autoroute.jpg" alt="image autoroute">
          <img class="w-1/2" src="../public/routenationale.jpg" alt="image route nationale">
        </div>
        <img  src="../public/velo.jpg" alt="image vélo">
      </div>
    </div>

    <h3 class="text-xl mt-16 mb-5 font-montserrat text-center">Taux d’accidents à vélo selon le types de routes, entre 2005 et 2018</h3>
    <Bar class="mx-5"/>

    <div class="flex items-center m-5">
      <div class="w-1/2">
        <p class="font-montserrat text-base">Certes nous avons vu précédemment que l’agglomération était le lieu le plus dangereux à vélo. Mais il s’agit d’un lieu très vaste ! Nous allons donc voir sur ce troisième graphique quelles types de routes plus précisément sont plus sujets aux accidents à vélo. </p>
        <p class="font-montserrat text-base">Sur ce graphique à barre, nous pouvons voir qu’une colonne se détache largement des autres : en effet, 65% des accidents à vélo ont lieu sur des voies communales. Il s’agit donc d’un lieu à sécuriser en priorité pour les vélos. Un autre type de route se détache : il s’agit des routes départementales. Les voitures roulent très vite sur ce type de route qui permet souvent de se déplacer à une vitesse importante. Ainsi, la capacité à s’arrêter à la rencontre d’un vélo ou même tout simplement à freiner est réduite, il est donc logique que le nombre d’accidents avec les vélos y soit élevé.</p>
        <p class="font-montserrat text-base">Pour rendre votre région écologique et propice aux circulations à vélo, les voies communales et les routes départementales sont des lieux à aménager en infrastructures et pistes cyclables, en priorité.</p>
      </div>
      <div class="flex w-1/2 justify-center">
        <p class="text-[300px] text-titres font-montserrat font-bold">65%</p>
      </div>
    </div>

    <div class="flex items-center m-5 gap-12 ">
      <div class="w-1/3">
        <figure>
          <img  src="../public/devantvelo.jpg" alt="image artistique vélo">
          <figcaption class="mt-3 font-montserrat text-center italic">Vélo</figcaption>
        </figure>
      </div>
      <div class="w-2/3">
        <h2 class="text-3xl mb-10 text-center font-montserrat font-bold text-titres">Conclusion</h2>
        <p class="font-montserrat text-base">Ainsi, d’après les différents graphiques que nous avons pu analyser, il nous apparaît plus facile de prendre les bonnes décisions pour rendre notre région plus écologique et surtout davantage sécurisée pour les cyclistes. 
</p>
        <p class="font-montserrat text-base">De ce fait, les pistes cyclables apparaissent vraiment comme les structures les mieux adaptées pour protéger les cyclistes et encourager les déplacements en vélo. En effet, nous avons pu voir que depuis qu’avec le temps et le développement des infrastructures cyclables, les accidents à vélo ont diminué. Ensuite, il convient de construire et d’améliorer les pistes cyclables en agglomération, où les vélos sont plus suceptibles d’être objets à des accidents.  
        </p>
        <p class="font-montserrat text-base">Enfin, c’est plus précisément sur les voies communales et les routes départementales que les accidents à vélo sont les plus nombreux. Il s’agit donc des deux lieux qu’il faut particulièrement sécuriser pour les vélos, avec la rénovation des infrasctuctures cyclables, et la création de pistes cyclables.
</p>
        <div class="mt-32 mx-5">
          <p class="font-montserrat flex justify-end font-semibold">“Comment mixer écologie et sécurité dans sa région ?”</p>
          <p class="font-montserrat flex justify-end">Julie Albini - octobre 2022</p>
        </div>
      </div>
    </div>
  
</template>


