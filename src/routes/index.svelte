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
  img {
    display: block;
    margin: 0 auto 6rem;
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

<img src="logo.svg" alt="" />

<Select {items} bind:selectedValue />

{#if selectedValue}
  <p>{translations[selectedValue]}</p>
{/if}
