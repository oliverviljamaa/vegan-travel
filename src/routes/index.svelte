<script context="module">
  export async function preload() {
    const res = await this.fetch('translations.json');
    const data = await res.json();

    if (res.status === 200) {
      return { translations: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  let selected;
  export let translations;
</script>

<style>
  img {
    display: block;
    margin: 0 auto;
    height: 3rem;
  }

  select {
    margin-top: 2rem;
    padding: 0.5rem;
    width: 100%;
    font-size: 1.25rem;
    border-color: #888;
    border-radius: 0.25rem;
    appearance: none;
    background: url('/vegan-translations/chevron.svg') no-repeat calc(100% - 0.5rem);
  }

  p {
    font-size: 1.75rem;
    text-align: center;
  }
</style>

<svelte:head>
  <title>🌱 Vegan translations</title>
</svelte:head>

<img src="logo.svg" alt="" />

<select bind:value={selected}>
  {#each Object.keys(translations) as country}
    <option value={country}>{country}</option>
  {/each}
</select>

{#if selected}
  <p>{translations[selected]}</p>
{/if}
