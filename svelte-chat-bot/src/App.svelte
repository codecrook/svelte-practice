<script>
  import Face from "./Face.svelte";
  import Container from "./Container.svelte";
  let say = "hi";
  setTimeout(() => (say = "bye"), 1000);
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

<Container>
  <div>{say}</div>
  <Face size={4} index={2} />
  <Face size={3} index={1} />
  <Face />
</Container>
