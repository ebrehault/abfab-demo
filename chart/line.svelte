<script>
    import { onMount } from 'svelte';
    import { Chart, registerables} from 'https://unpkg.com/chart.js@3.6.0/dist/chart.esm.js';
    Chart.register(...registerables);
    
    const labels = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
    ];
    const data = {
      labels: labels,
      datasets: [{
        label: 'Extra weight caused by lockdown',
        backgroundColor: 'rgb(255, 99, 132)',
        borderColor: 'rgb(255, 99, 132)',
        data: [0, 10, 5, 2, 20, 30, 45],
      }]
    };
    const config = {
        type: 'line',
        data: data,
        options: {}
    };
    let myChart;
    onMount(() => new Chart(myChart, config));
</script>
<div>
  	<canvas bind:this={myChart}></canvas>
</div>
<style>
    canvas {
        max-height: 100vh;
        max-width: 100vw;
    }
</style>