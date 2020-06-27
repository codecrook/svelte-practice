<script>
  import Face from "./Face.svelte";
  import Container from "./Container.svelte";
  import Header from "./Header.svelte";
  import Buttons from "./Buttons.svelte";
  import story from "./story";

  let showHeader = false;
  let [happyScore, storyIndex] = [0, 0];
  $: smileySays = story[storyIndex].smileySays;
  $: buttons = story[storyIndex].buttons;
  function clickHandler(e) {
    storyIndex += 1;
    happyScore += e.detail.value;
  }
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
  <div>{smileySays}</div>
  <Face {happyScore} size={storyIndex + 1} />
  <Buttons {buttons} on:click={clickHandler} />
</Container>
