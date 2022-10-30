<script setup>
    
    import {ref, reactive, onMounted} from 'vue'

   
    import {Doughnut} from 'vue-chartjs'

   
    import {Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale} from 'chart.js'

    
    ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

   
    const propChart = defineProps({
        chartId: {type: String, default: 'doughnut-chart'}, 
        datasetIdkey: {type: String, default: 'label'}, 
        width: {type: Number, default: 100}, 
        height: {type: Number, default: 100},
        cssClasses: {type: String, default: ''}, 
        styles : {type: Object, default: () => {}} 
    })

    
        const chartData = reactive({
            
            labels: [],
            datasets : [{}]
        })

        
        const chartOptions = reactive ({
            responsive: true, 
            maintainAspectRatio: false
        })

        
        let liste = ref(null);
        
        let lstOuiNon = [];
        
        let lstNb = [];

        let loading = ref()
        loading.value = false
        
        onMounted(async() => {
             let request = "https://accidentvelo.jmfino.fr/json.php"
            await fetch(request)
            
            .then(response => response.json())
            
            .then(response => {
                liste.value = response
            console.log("liste", liste)
            loading.value = true
                })
                .catch(error => console.log('erreur Ajax', error))

                
                chartData.labels=["En agglomération", "Hors agglomération"]
                let firstLine = true;


                
                
                console.log("tri libellé : ", chartData.labels)

                let cptOui = [];
                let cptNon = [];
                firstLine = true;
                let nbOui = 0
                let nbNon = 0
              
                chartData.labels.forEach(function(ch){
                    
                    liste.value.forEach( (val) => {
                        
                        if(!firstLine){
                            if(val[36] == '1') {nbOui++}
                            if (val[36] == '') {nbNon++}
                        }
                    
                    })
                   
                    
                    firstLine = false 
                })
                cptOui.push(nbOui);
                cptOui.push(nbNon);
                
                chartData.datasets[0].data = cptOui;
                console.log("chartdata, " , chartData.datasets[0])

               
                let bgColor=[];
                    let bdColor = [];
                   
                    cptOui.forEach( function(val){
                        
                        let c1 = couleur(0, 255)
                        let c2 = couleur(0,255)
                        let c3 = couleur(0, 255)
                        let tr = 0.5
                       
                        let color = 'rgba(' + [c1, c2, c3, tr].join(',') +")"
                        bgColor.push(color)
                    })
                   
                    chartData.datasets[0].backgroundColor = bgColor;
                    chartData.datasets[0].borderColor = bdColor;
                    
        
        })
        const couleur = (min, max) => {
            return Math.floor(Math.random() * (max - min));
        }

                
</script>

<template>

    <div v-if="loading" class="container">
        
        <Doughnut
            :chart-otpions="chartOptions"
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
        <img src="../assets/loading-16.gif" class="img-fluid"/>
    </div>

</template>