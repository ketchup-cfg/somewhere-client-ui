<script lang="ts">
  import {fly} from 'svelte/transition';
  import TopicsSidebar from "./TopicsSidebar.svelte";

  let shouldShowTopicSidebar = false;

  function toggleSidebar() {
    shouldShowTopicSidebar = !shouldShowTopicSidebar;
  }
</script>

<div class="flex">
  {#if shouldShowTopicSidebar}
    <div transition:fly="{{ x: -200, duration: 300 }}">
      <TopicsSidebar bind:shouldShowTopicSidebar/>
    </div>
  {/if}

  <div class="relative top-4 left-4 z-0">
    <main>
      {#if !shouldShowTopicSidebar}
        <div class="fixed bottom-4 left-4" transition:fly="{{ y: 200, duration: 300 }}">
          <button
            class="bg-blue-500 hover:bg-blue-600 active:bg-blue-700 focus:outline-none focus:ring focus:ring-blue-300 text-white font-bold py-2 px-4 rounded"
            on:click={toggleSidebar}
          >
            <i class="fa-solid fa-bars"></i>
          </button>
        </div>
      {/if}

      <div class="fixed bottom-4 right-4">
        <button
          class="bg-blue-500 hover:bg-blue-600 active:bg-blue-700 focus:outline-none focus:ring focus:ring-blue-300 text-white font-bold py-2 px-4 rounded"
          on:click={() => console.log("Just some stuff")}
        >
          <i class="fa-solid fa-pen"></i>
        </button>
      </div>
    </main>
  </div>
</div>

<style>
</style>