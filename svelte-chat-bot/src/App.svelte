<script>
  import Face from "./Face.svelte";
  let say = "hi";
  setTimeout(() => (say = "bye"), 1000);
</script>

<style>
  div {
    color: red;
  }
</style>

<div>{say}</div>
<Face size={4} />
