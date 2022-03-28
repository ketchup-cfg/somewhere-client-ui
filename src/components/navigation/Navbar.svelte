<script lang="ts">
  import NavbarDropdown from "./items/NavbarDropdown.svelte";
  import TopicsDropdownContent from "./submenus/TopicsDropdownContent.svelte";

  let menuIsActive = false;

  function toggleMenuActiveState() {
    menuIsActive = !menuIsActive;
  }
</script>

<nav class="navbar is-light" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item">
      Somewhere
    </a>

    <a role="button" class="navbar-burger {menuIsActive ? 'is-active' : ''}" on:click={toggleMenuActiveState} aria-label="menu" aria-expanded="false" data-target="somewhere-navbar-content">
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>

  <div id="somewhere-navbar-content" class="navbar-menu {menuIsActive ? 'is-active' : ''}">
    <div class="navbar-start">

      <NavbarDropdown>
        <span slot="navbar-item-content">
          Topics
        </span>
        <TopicsDropdownContent slot="dropdown-content"/>
      </NavbarDropdown>

    </div>
  </div>
</nav>