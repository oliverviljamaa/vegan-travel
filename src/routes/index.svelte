<script context="module">
  import countries from './_countries';
  import Select from './_Select.svelte';

  export async function preload() {
    const res = await this.fetch('translations.json');
    const data = await res.json();

    if (res.status === 200) {
      return {
        translations: data,
        items: Object.entries(data).map(([countryCode]) => ({
          value: countryCode,
          label: countries[countryCode],
        })),
      };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  let selectedValue;
  export let translations;
  export let items;
</script>

<style>
  main {
    max-width: 48rem;
    padding: 6rem 2rem;
    margin: 0 auto;
    box-sizing: border-box;
  }

  nav {
    position: fixed;
    bottom: 0;
    width: 100%;
  }

  nav div {
    margin: 2rem;
  }

  img {
    display: block;
    margin: 0 auto 4rem;
    height: 3rem;
  }

  p {
    margin-top: 3rem;
    font-size: 1.75rem;
    text-align: center;
  }
</style>

<svelte:head>
  <title>Vegan Travel</title>
</svelte:head>

<main>
  <img src="logo.svg" alt="" />

  {#if selectedValue}
    <p>{translations[selectedValue]}</p>
  {/if}

</main>

<nav>
  <div>
    <Select {items} bind:selectedValue />
  </div>
</nav>
