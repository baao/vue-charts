<template>
    <div>
        <canvas v-if="!target" ref="canvas" :width="width" :height="height"/>
    </div>
</template>
<script>
  import ChartDefault from '../vue-chartjs-lib.js'

  export default {
    mixins: [
      ChartDefault,
    ],
    props: {
      backgroundcolor: {
        default: () => [
          '#FF6384',
          '#36A2EB',
          '#FFCE56',
          '#00A600'
        ],
      },
      hoverbackgroundcolor: {
        default: () => [
          '#FF6384',
          '#36A2EB',
          '#FFCE56',
          '#00A600'
        ],
      },
      bordercolor: {
        default: () => '#fff',
      },
      hoverbordercolor: {
        default: () => '',
      }
    },
    data () {
      return {
        type: 'doughnut',
        chart_data: {
          labels: this.labels,
          datasets: [{
            label: this.datalabel,
            backgroundColor: this.backgroundcolor,
            borderColor: this.bordercolor,
            hoverBackgroundColor: this.hoverbackgroundcolor,
            hoverBorderColor: this.hoverbackgroundcolor,
            data: this.data
          }],
        },
        options: {
          scales: {
            scale: {
              reverse: true,
              ticks: {
                beginAtZero: this.beginzero || true,
                min: 0
              }
            }
          }
        },
      }
    }
  }
</script>
