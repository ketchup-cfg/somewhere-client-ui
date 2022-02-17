<script>
  import { onMount } from 'svelte';

  let baseUrl = 'http://localhost:5018/api';
  let topics = [];

  onMount(async () => {
    const res = await fetch(`${baseUrl}/topics`,
      {
        headers: {
          "Accept": "application/json"
        }
      });
    topics = await res.json();
  });
</script>

<h1>Forum Topics</h1>
<ul>
  {#each topics as topic}
    <li>
      <a
        href="{baseUrl}/topics/{topic.name}"
        title="{topic.name}"
        target="_blank"
      >
        {topic.name}
      </a>
    </li>
  {:else}
    <li>loading topics...</li>
  {/each}
</ul>

<style>
</style>