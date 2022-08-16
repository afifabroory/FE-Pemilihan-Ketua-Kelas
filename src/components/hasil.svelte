<script lang="ts">
    import Card from "./card.svelte";
    import Alert from "./alert.svelte";

    let message: string;
    let isError: boolean;
    let step: number = 4;
    
    import { Bar } from 'svelte-chartjs';
    export const data = {
  labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
  datasets: [
    {
      label: '% of Votes',
      data: [12, 19, 3, 5, 2, 3],
      backgroundColor: [
        'rgba(255, 134,159,0.4)',
        'rgba(98,  182, 239,0.4)',
        'rgba(255, 218, 128,0.4)',
        'rgba(113, 205, 205,0.4)',
        'rgba(170, 128, 252,0.4)',
        'rgba(255, 177, 101,0.4)',
      ],
      borderWidth: 2,
      borderColor: [
        'rgba(255, 134, 159, 1)',
        'rgba(98,  182, 239, 1)',
        'rgba(255, 218, 128, 1)',
        'rgba(113, 205, 205, 1)',
        'rgba(170, 128, 252, 1)',
        'rgba(255, 177, 101, 1)',
      ],
    },
  ],
};

import {
    Chart,
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale,
  } from 'chart.js';

  Chart.register(
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale
  );

</script>

<Alert message={message} isError={isError}></Alert>
<div class="flex h-screen justify-center items-center bg-slate-100">
    <Card step={step} title={"Hasil Pemilihan Ketua Kelas D MI"} subtitle={"Tahun 2022/2023"}>        
        <Bar {data} options={{ responsive: true }} />
    </Card>
</div>