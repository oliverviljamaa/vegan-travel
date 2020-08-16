<style>
  div {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
  }

  main {
    position: relative;
    max-width: 48rem;
    padding: 2rem;
    margin: 0 auto 6rem;
    box-sizing: border-box;
  }
</style>

<div>
  <main>
    <slot />
  </main>
</div>
