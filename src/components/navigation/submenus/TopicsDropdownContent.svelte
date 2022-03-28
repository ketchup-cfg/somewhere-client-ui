<script lang="ts">
  import {onMount} from 'svelte';
  import {TopicType} from "../../../types/topic.type";
  import {baseApiUrl} from "../../../constants";

  let topics: TopicType[] = [];

  onMount(async () => {
    fetch(`${baseApiUrl}/topics`,
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

<div class="navbar-dropdown">
  <a class="navbar-item">
    Create a New Topic
  </a>
  <hr class="navbar-divider">
  {#each topics as topic}
    <a
      class="navbar-item"
      href="{baseApiUrl}/topics/{topic.name}"
      title="{topic.name}"
      target="_blank"
    >
      {topic.name}
    </a>
  {:else}
    <a class="navbar-item">
      Loading topics...
    </a>
  {/each}
</div>
