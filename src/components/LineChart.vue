<script setup>
    import {reactive, ref, onMounted} from 'vue';


    import {Line} from 'vue-chartjs'

    
    import { Chart as ChartJS, Title, Tooltip, Legend, PointElement, LineElement, LineController, CategoryScale, LinearScale, Filler} from 'chart.js'

    
    ChartJS.register(Title, Tooltip, Legend, PointElement, LineElement, LineController, CategoryScale, LinearScale, Filler)

   
    const propChart = defineProps({
        chartId: {type: String,     default: 'line-chart'},
        datasetIdKey: {type: String, default: 'label'}, 
        width: {type: Number, default: 50},
        height: {type: Number, default: 175}, 
        cssClasses: {type:String, default:''},
        styles: {type: Object, default: () => {}}, 
        plugins: {type: Object, default: () => {}}, 
    });
       
        let chartData = reactive({
            
            labels: ['Janvier', 'Février', 'Mars', 'Avril', 'Mai'],
            
            datasets: [
                {
                    
                    label : 'Blessés grave',
                    
                    data: [40, 20, 12, 14, 24],
                    borderColor: 'rgba(255, 0, 0, 0.5)',
                    tension: 0.5,
                    fill: true,
                    
                    pointBackgroundColor: "#DC143C", 
                    pointBorderColor: "#B22222", 
                    pointHoverBackgroundColor: "#B22222", 
                    pointHoverBorderColor: "#DC143C",
                    pointRadius: 4, 
                    pointHoverRadius: 6, 
                },
                {
                   
                    label : 'Blessés légers',
                    
                    data: [40, 20, 12, 14, 24],
                    borderColor: 'rgba(0, 0, 255, 0.5)',
                    tension: 0.5,
                    fill: true,

                    
                    pointBackgroundColor: "#00BFFF",
                    pointBorderColor: "#1E90FF", 
                    pointHoverBackgroundColor: "#1E90FF", 
                    pointHoverBorderColor: "#00BFFF", 
                    pointRadius: 4,
                    pointHoverRadius: 6,
                },
                {
                   
                    label:'Indemnes',
                    
                    data: [80, 40, 24, 28, 48],
                    borderColor: 'rgba(255, 255, 0, 0.4)',
                    tension: 0.5,
                    fill: true,

                    
                    pointBackgroundColor: "#FFFF00",
                    pointBorderColor: "#ffb88c", 
                    pointHoverBackgroundColor: "ffb88c", 
                    pointHoverBorderColor: "#FFFF00", 
                    pointRadius: 4, 
                    pointHoverRadius: 6, 
                },
                {
                    
                    label : 'Tués',
                    
                    data: [40, 20, 12, 14, 24],
                    borderColor: 'rgba(0, 255, 0, 0.5)',
                    tension: 0.5,
                    fill: true,
                    
                    pointBackgroundColor: "#00FF00", 
                    pointBorderColor: "#00561B", 
                    pointHoverBackgroundColor: "#00FF00", 
                    pointHoverBorderColor: "#00561B", 
                    pointRadius: 4,
                    pointHoverRadius: 6, 
                },
            ]
        });

        
        let chartOptions = reactive({
            
            responsive: true,
            
            plugins:{
                
                title: {
                    
                    display: true,
                    
                    text: '',
                   
                    font: {
                        size: 16
                    }
                }
            }
        });

        
        let liste = ref()
        let total = ref()
        total.value = 0
        let loading = ref()
        loading.value = false

        onMounted(async() => {
            let request = "https://accidentvelo.jmfino.fr/json.php"
            await fetch(request)
            
            .then(response => response.json())
            
            .then(response => {
                liste.value = response
        console.log("liste", liste)
        console.log("nb lignes", liste.value.length)
        loading.value = true
                byYear()
                })
                .catch(error => console.log('erreur Ajax', error))

        })
        
        const byYear = () => {
           
            let setAnnee = new Set()
            let firstLine = true;
            liste.value.forEach( (el) => {
                if(!firstLine){
                    let dt = el[1].split('-') 
                    setAnnee.add(dt[0]) 
                }
                firstLine = false
            })
            
            chartData.labels = Array.from(setAnnee)
            chartData.labels.sort() 


            let cptBG = [] 
            let cptBL = [] 
            let cptT = [] 
            let cptI = [] 
            
            firstLine = true;
            total.value = 0 
            chartData.labels.forEach( (an) => {
                let nbBG = 0 
                let nbBL = 0 
                let nbT = 0 
                let nbI = 0 
                liste.value.forEach((el) => { 
                    if(!firstLine){
                        let dt = el[1].split('-')
                        if(an ==dt[0]){
                            if(el[22] == '2 - Blessé hospitalisé') {nbBG++}
                            if(el[22] == '1 - Blessé léger') {nbBL++}
                            if(el[22] == '0 - Indemne') {nbI++}
                            if(el[22] == '3 - Tué') {nbT++}
                        }
                    }
                    firstLine = false
                    
                })
                cptBG.push(nbBG) 
                cptBL.push(nbBL) 
                cptT.push(nbT) 
                cptI.push(nbI) 
            })
            chartData.datasets[0].data = cptBG 
            chartData.datasets[1].data = cptBL 
            chartData.datasets[2].data = cptT 
            chartData.datasets[3].data = cptI 
        
       }
    

        
</script>

<template>
    <div v-if="loading" class="container">
        <Line
            :chart-options="chartOptions"
            :chart-data="chartData"
            :chart-id="chartId"
            :dataset-id-key="datasetIdKey"
            :plugins="plugins"
            :css-classes="cssClasses"
            :styles="styles"
            :witdh="width"
            :height="height"
        />
    </div>
    <div v-else>
        <img src="../assets/loading-16.gif" class=" img-fluid"/>
    </div>
</template>