<script>
  import Header from "./Header.svelte";
  import Container from "./Container.svelte";
  import Face from "./Face.svelte";
  import Button from "./Button.svelte";

  let showHeader = false;
  const buttons = [
    { value: 0, text: "ummmmmm......" },
    { value: 1, text: "I sure do!" },
    { value: -2, text: "gross!" }
  ];
  let score = 0;
</script>

<style>
  div {
    color: red;
  }
  :global(*) {
    box-sizing: border-box;
  }
  :global(body, html) {
    margin: 0;
    height: 100vh;
    overflow: hidden;
  }
</style>

{#if showHeader}
  <Header />
{/if}
<Container>
  <div>Do you like pizza 🍕? Score: {score}</div>
  <Button on:click={e => (score += e.detail.value)} {buttons} />
</Container>
