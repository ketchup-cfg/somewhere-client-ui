<script lang="ts">
  import {onMount} from 'svelte';
  import type {TopicType} from "./types/topic.type";

  const baseUrl = 'http://localhost:5018/api';
  let topics: TopicType[] = [];
  export let shouldShowTopicSidebar = false;

  function toggleSidebar() {
    shouldShowTopicSidebar = !shouldShowTopicSidebar;
  }

  onMount(async () => {
    fetch(`${baseUrl}/topics`,
      {
        headers: {
          "Accept": "application/json"
        }
      })
      .then(response => response.json())
      .then(response => {
        topics = response;
      })
      .catch((error) => console.error('Error:', error));
  });
</script>

<div class="fixed top-4 left-4 z-10 bg-blue-500 rounded shadow-lg p-1 m-1 w-fit">
  <nav>
    <div class="relative grid grid-cols-3 p-1">
      <div class="col-start-2 col-end-2 justify-self-center">
        <h1>Browse Forum Topics</h1>
      </div>
      <div class="col-start-3 col-end-3 justify-self-end">
        <button
          class="bg-inherit text-white font-bold rounded"
          on:click={toggleSidebar}
        >
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>
    </div>
    <ul class="pl-5 space-y-1 text-slate-400 dark:text-white">
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
    </ul>
  </nav>
</div>

<style>
</style>