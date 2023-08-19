<script>
  export let mainText;
  export let spanText;
</script>

<main>
  <h1>
    {mainText} <span>{spanText}</span>
  </h1>
  <h3>Use tab to focus. Try running "help".</h3>
</main>

<style>
  h1 {
    font-size: 2.5rem;
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    margin: 6rem 0 2rem 0;
  }
  h3 {
    margin-bottom: 6rem;
  }
  span {
    text-shadow: 0 0 10px rgba(255, 0, 0, 0.5);
    color: red;
  }
</style>
