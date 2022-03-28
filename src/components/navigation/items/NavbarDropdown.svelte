<script lang="ts">
  let dropdownIsActive = false;

  function toggleActiveState() {
    dropdownIsActive = !dropdownIsActive;
  }
</script>

<div class="navbar-item has-dropdown {dropdownIsActive ? 'is-active' : ''}" on:click={toggleActiveState}>
  <a class="navbar-link">
    <slot name="navbar-item-content">
    </slot>
  </a>

  <slot name="dropdown-content">
  </slot>
</div>
