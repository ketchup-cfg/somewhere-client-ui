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

  function handleWindowClick(e) {
    if (!document.querySelector("#topics-sidebar")?.contains(e.target as Node)
      && !document.querySelector("#forum-navbar")?.contains(e.target as Node)) {
      toggleSidebar();
    }
  }
</script>

<svelte:window on:click={handleWindowClick}/>

<div id="topics-sidebar" class="fixed bottom-16 md:bottom-auto md:top-16 z-10 rounded-t md:rounded-t-none md:rounded-b drop-shadow-2xl w-80 max-w-[calc(100%-3rem)] p-6 bg-slate-500 text-white">
  <h1 class="inline">Browse Forum Topics</h1>
    <button
      class="bg-inherit float-right"
      on:click={toggleSidebar}
    >
      <i class="fa-solid fa-xmark"></i>
    </button>
  <nav>
    <ul class="pl-5 space-y-1">
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