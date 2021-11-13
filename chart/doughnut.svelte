<script>
    import { onMount } from 'svelte';
    import { Chart, registerables} from 'https://unpkg.com/chart.js@3.6.0/dist/chart.esm.js';
    Chart.register(...registerables);
    
    const data = {
      labels: [
        'Probably not the color I thought',
        'Blue, I guess',
        'Definitely green',
        'This one is new, never seen so far',
      ],
      datasets: [{
        label: 'Color-blind facts',
        data: [300, 50, 100, 20],
        backgroundColor: [
          'rgb(255, 99, 132)',
          'rgb(54, 162, 235)',
          'rgb(255, 205, 86)',
          'rgb(45, 205, 86)'
        ],
        hoverOffset: 4
      }]
    };
    const config = {
        type: 'doughnut',
        data: data,
        options: {
        plugins: {
            title: {
                display: true,
                text: 'Color-blind facts'
            },
            subtitle: {
                display: true,
                text: '(That is not how a doughnut chart works)'
            }
        }
    }
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