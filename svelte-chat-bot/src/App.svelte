<script>
  import Face from "./Face.svelte";
  import Container from "./Container.svelte";
  import Header from "./Header.svelte";
  import Buttons from "./Buttons.svelte";
  import story from "./story";

  let showHeader = false;
  let [happyScore, storyIndex] = [0, 0];
  $: question = story[storyIndex];
  $: smileySays = question.end ? setFinalMessage() : question.smileySays;
  $: buttons = question.buttons;

  $: if (happyScore > 0 && storyIndex === 3) showHeader = true;
  function clickHandler(e) {
    if (e.detail.value === "reset") {
      [storyIndex, happyScore, showHeader] = [0, 0, false];
    } else {
      storyIndex += 1;
      happyScore += e.detail.value;
    }
  }
  function setFinalMessage() {
    if (happyScore > 0) {
      return question.end.nice;
    } else if (happyScore < 0) {
      return question.end.mean;
    } else {
      return question.end.neutral;
    }
  }
  let name = "";
</script>

<style>
  h1 {
    text-align: center;
    background: #ff3e00;
    font-size: 2em;
    padding: 0.3em 0.6em;
    color: white;
    border-radius: 50px;
  }
  input {
    margin: 1em;
    width: 250px;
    font-family: "Nunito", sans-serif;
    border: 0;
    outline: 0;
    background: transparent;
    border-bottom: 1px solid black;
    text-align: center;
    font-size: 2em;
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
  <input type="text" bind:value={name} />
  <h1>{name ? `${name}, ` : ''} {smileySays}</h1>
  <Face {happyScore} size={storyIndex + 1} />
  <Buttons {buttons} on:click={clickHandler} />
</Container>
