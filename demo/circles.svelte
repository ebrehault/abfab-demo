<script>
    export let content;
  </script>
  
  <svg>
    {#each content.circles as d}
      <circle cx={d.x + "%"} cy="50%" r={d.r} fill={content.color} />
    {/each}
  </svg>