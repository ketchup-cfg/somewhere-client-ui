<script>
  import {onMount} from 'svelte';

  const baseUrl = 'http://localhost:5018/api';
  let topics = [];

  onMount(async () => {
    fetch(`${baseUrl}/topics`,
      {
        headers: {
          "Accept": "application/json"
        }
      })
      .then(response => response.json())
      .then(response => topics = response)
      .catch((error) => console.error('Error:', error));
  });
</script>

<nav>
  <h1>Browse Forum Topics</h1>
  <menu class="pl-5 space-y-3 text-slate-400 dark:text-white">
    {#each topics as topic}
      <li>
        <a
          href="{baseUrl}/topics/{topic.name}"
          title="{topic.name}"
          target="_blank"
        >
          + {topic.name}
        </a>
      </li>
    {:else}
      <li>loading topics...</li>
    {/each}
  </menu>
</nav>

<style>
</style>