<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let tabs;
  export let activeTab;
</script>

<div class="tabs">
  <ul>
    {#each tabs as tab}
      <li on:click={() => dispatch('tabChange', tab)}>
        <div class:active={tab === activeTab}>
          {tab}
        </div>
      </li>
    {/each}
  </ul>
</div>

<style>
  .tabs {
    margin-bottom: 40px;
  }
  ul {
    display: flex;
    justify-content: center;
    padding: 0;
    list-style-type: none;
  }
  li {
    margin: 0 16px;
    font-size: 18px;
    color: #555;
    cursor: pointer;
    -ms-user-select:none;
    -moz-user-select:none;
    -webkit-user-select:none;
    -webkit-touch-callout: none;
    -khtml-user-select: none;
    user-select:none;
  }
  .active {
    color: var(--red);
    border-bottom: 2px solid var(--red);
    padding-bottom: 8px;
  }
</style>