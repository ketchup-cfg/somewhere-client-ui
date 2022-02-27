<script lang="ts">
  import {fly} from 'svelte/transition';
  import TopicsSidebar from "./TopicsSidebar.svelte";

  let shouldShowTopicSidebar = false;

  function toggleSidebar() {
    shouldShowTopicSidebar = !shouldShowTopicSidebar;
  }
</script>


  <nav id="forum-navbar" class="bm-0 md:tm-0 bg-slate-700 h-16 p-4 w-screen">
    <ul>
      <li class="inline-block float-left left-4">
        <button
          class="bg-inherit hover:bg-slate-800 active:bg-slate-900 focus:outline-none focus:ring focus:ring-slate-300 text-white font-bold py-2 px-4 rounded drop-shadow-2xl"
          on:click={toggleSidebar}
        >
          <i class="fa-solid fa-bars"></i>
        </button>
      </li>

      <li class="inline-block float-right">
        <button
          class="bg-inherit hover:bg-slate-800 active:bg-slate-900 focus:outline-none focus:ring focus:ring-slate-300 text-white font-bold py-2 px-4 rounded drop-shadow-2xl"
          on:click={() => console.log("Just some stuff")}
        >
          <i class="fa-solid fa-pen"></i>
        </button>
      </li>
    </ul>
  </nav>

  {#if shouldShowTopicSidebar}
    <div transition:fly="{{ x: -200, duration: 300 }}">
      <TopicsSidebar bind:shouldShowTopicSidebar/>
    </div>
  {/if}

  <main class="flex">
    <p class="{shouldShowTopicSidebar ? 'blur' : ''}">stuff</p>
  </main>


<style>
</style>