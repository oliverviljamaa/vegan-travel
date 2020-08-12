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
  export let translations;
</script>

<style>
  img {
    display: block;
    margin: 0 auto;
    height: 3rem;
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

<p>{translations.GB}</p>
