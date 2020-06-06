<script>
  import ContactCard from "./ContactCard.svelte";
  let name = "Deeptiman";
  let age = 23;
  const incrementAge = () => (age += 1);
</script>

<style>

</style>

<main>
  <h1>Hello, I'm {name}! I'm {age} years old.</h1>
  <input type="text" bind:value={name} />
  <button on:click={incrementAge}>Increase Age</button>
</main>
<ContactCard {name} proffession="Frontend Developer" desc="Figuring Out!!" />
