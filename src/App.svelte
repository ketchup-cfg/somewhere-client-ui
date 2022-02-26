<script lang="ts">
  import TopicsSidebar from "./TopicsSidebar.svelte";

  let shouldShowTopicSidebar = false;

  function toggleSidebar() {
    shouldShowTopicSidebar = !shouldShowTopicSidebar;
  }
</script>

<div class="flex">
  {#if shouldShowTopicSidebar}
    <TopicsSidebar bind:shouldShowTopicSidebar/>
  {/if}

  <div class="relative top-4 left-4 z-0">
    <main>
      <button
        class="bg-blue-500 hover:bg-blue-600 active:bg-blue-700 focus:outline-none focus:ring focus:ring-blue-300 text-white font-bold py-2 px-4 rounded"
        on:click={toggleSidebar}
      >
        Topics
      </button>
    </main>
  </div>
</div>

<style>
</style>