<script>
  export let name, proffession, desc;
</script>

<style>
  .card-container {
    border: 1px solid black;
    margin: 25px;
    padding: 15px;
  }
</style>

<div class="card-container">
  <h2>{name}</h2>
  <h3>{proffession}</h3>
  <hr />
  <p>{desc}</p>
</div>
