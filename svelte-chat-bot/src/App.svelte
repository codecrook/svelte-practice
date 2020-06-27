<script>
  import Header from "./Header.svelte";
  import Container from "./Container.svelte";
  import Face from "./Face.svelte";
  import Button from "./Button.svelte";

  let [say, showHeader] = [false, false];
  setTimeout(() => (say = true), 3000);
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
  {#if say}
    <div>Hi!!</div>
  {:else}
    <div>Not saying anything...</div>
  {/if}

  {#each [2, 1, 0] as index}
    <Face size={4} {index} />
  {/each}
  <Button
    on:show={() => (showHeader = true)}
    on:hide={() => (showHeader = false)}>
    Show Header
  </Button>
</Container>
