<script>
  export let selectedValue;
  export let items;
</script>

<style>
  div {
    position: relative;
  }

  select {
    background: transparent;
    padding: 0.5rem 0.75rem;
    width: 100%;
    font-size: 1.25rem;
    border-color: #888;
    border-radius: 0.25rem;
    appearance: none;
  }

  @media (prefers-color-scheme: dark) {
    select {
      color: white;
      border-color: #ccc;
    }
  }

  svg {
    position: absolute;
    top: 1rem;
    right: 0.75rem;
  }
</style>

<div>
  <select bind:value={selectedValue}>
    {#each items as { value, label }}
      <option {value}>{label}</option>
    {/each}
  </select>

  <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path
      fill-rule="evenodd"
      clip-rule="evenodd"
      d="M8.00002 11.8L1.40002 5.14655L2.53731 4.00005L8.00001 9.507L13.4627 4L14.6 5.14649L8.00002
      11.8Z"
      fill="currentColor" />
  </svg>
</div>
