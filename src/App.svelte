<script>
  import Modal from "./Modal.svelte";

  let people = [
    { name: "", beltColour: "black", age: 25, id: 1 },
    { name: "mario", beltColour: "orange", age: 45, id: 2 },
    { name: "luigi", beltColour: "brown", age: 35, id: 3 },
  ];
  let showModal = false;

  const handleDelete = (personId) => {
    people = people.filter((p) => p.id != personId);
  };

  const toggleModal = () => {
    showModal = !showModal;
  };
</script>

<!-- {#if num > 20}
  <p>greater than 20</p>
{:else if num > 5}
  <p>greater than 5</p>
{:else}
  <p>not greater than 5</p>
{/if} -->

<Modal
  message="Hey I am prop value."
  isPromo={true}
  {showModal}
  on:click={toggleModal}
/>

<main>
  <button on:click|once={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === "black"}
        <p><strong>MASTER NINJA</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt.</p>
      <button
        on:click={() => {
          handleDelete(person.id);
        }}>delete</button
      >
    </div>
  {:else}
    <p>There are no person to show...</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
