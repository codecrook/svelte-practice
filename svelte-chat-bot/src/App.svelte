<script>
  import Header from "./Header.svelte";
  import Container from "./Container.svelte";
  import Face from "./Face.svelte";
  import Button from "./Button.svelte";
  import story from "./story";

  let showHeader = false;
  const buttons = story[0].buttons;
  let score = 0;
  $: smilySays = `Hi, there! your score is ${score}`;
  $: if (score < -4) smilySays = "Wow! Your score is really low.";
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
  <div>{smilySays}</div>
  <Face index={2} />
  <Button on:click={e => (score += e.detail.value)} {buttons} />
</Container>
