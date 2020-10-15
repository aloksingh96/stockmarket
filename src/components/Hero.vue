<template>
  <div class="hero is-primary" >
    <div class="hero-body">
        <div class="container"> 
          <h1>{{ msg }}</h1>
        </div> 
    </div> 
  </div>
</template>

<script> 
 import axios from 'axios'
// import Highcharts from 'highcharts-vue'
// import apexchart from 'apexcharts'
// import VueApexCharts from 'vue-apexcharts'
 
 export default {
  name: 'Hero',
  props: {
    msg: String
  },
  data(){
      return {
      
      series: [{
            data: [{
                x: new Date(1538778600000),
                y: [6629.81, 6650.5, 6623.04, 6633.33]
              },
            ]
          }],
          chartOptions: {
            chart: {
              type: 'candlestick',
              height: 350
            },
            title: {
              text: 'CandleStick Chart',
              align: 'left'
            },
            xaxis: {
              type: 'datetime'
            },
            yaxis: {
              tooltip: {
                enabled: true
              }
            }
          },
          
      }
  },
  
 
  mounted(){
        axios.get('https://www.alphavantage.co/query?function=TIME_SERIES_INTRADAY_EXTENDED&symbol=IBM&interval=15min&slice=year1month1&apikey=N5ZU0ED9YL7HEVQK')
        .then((resp)=>{
           this.list=resp.data
          console.warn(resp.data)
        } )
        
 
      
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 
</style>
