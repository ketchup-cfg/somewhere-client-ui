<script>
  import {onMount} from 'svelte';

  const baseUrl = 'http://localhost:5018/api';
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

<nav>
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
</nav>

<style>
  nav {
    display: inline-block;
  }

  ul {
    list-style-type: " + ";
  }

  li {
    border: 1px solid black;
  }

  a:hover {
    text-decoration: none;
  }
</style>