<script>
  import TopicsSidebar from "./TopicsSidebar.svelte";

  let shouldShowTopicSidebar = false;

  function toggleSidebar() {
    shouldShowTopicSidebar = !shouldShowTopicSidebar;
  }
</script>

<div>
  {#if shouldShowTopicSidebar}
    <TopicsSidebar/>
  {/if}

  <main>
    <button
      class="bg-blue-500 hover:bg-blue-600 active:bg-blue-700 focus:outline-none focus:ring focus:ring-blue-300 text-white font-bold py-2 px-4 rounded"
      on:click={toggleSidebar}
    >
      Topics
    </button>
  </main>
</div>

<style>
</style>