<script>
  export let type = 'primary';
  export let flat = false;
  export let inverse = false;
</script>

<button class={type} class:flat={flat} class:inverse={inverse}>
  <slot></slot>
</button>

<style>
  button {
    border: 0;
    cursor: pointer;
    border-radius: 6px;
    padding: 8px 12px;
    font-weight: bold;
    box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
  }
  .primary {
    background-color: var(--red);
    color: white;
  }
  .primary.inverse {
    color: var(--red);
    background: white;
    border: 2px solid var(--red);
  }
  .secondary {
    background: var(--green);
    color: white;
  }
  .secondary.inverse {
    color: var(--green);
    background: white;
    border: 2px solid var(--green);
  }
  .flat {
    box-shadow: none;
  }
</style>