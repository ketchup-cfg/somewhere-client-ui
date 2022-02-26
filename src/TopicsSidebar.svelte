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

<div class="absolute top-4 left-4 z-10 bg-blue-500 rounded shadow-lg p-1 m-1">
  <nav>
   <div class="grid grid-cols-3 gap-4 w-full">
     <div class="col-start-2 col-end-2 justify-self-center">
       <h1>Browse Forum Topics</h1>
     </div>
     <div class="col-auto justify-self-end">
      <button
        class="bg-red-500 hover:bg-red-600 active:bg-red-700 focus:outline-none focus:ring focus:ring-red-300 text-white font-bold rounded"
        on:click={toggleSidebar}
      >
        X
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