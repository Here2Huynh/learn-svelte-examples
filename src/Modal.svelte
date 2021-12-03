<script>
  export let isPromo;
  export let showModal;
  /**
   * once - triggers once and removes hanlder
   * preventDefault - prevent default action
   * self - trigger if the clicked element is the target
   */
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <!-- <slot name="title" /> -->
      <!-- <div slot="title">
        <h3>Add a new person</h3>
      </div> -->
      <slot />
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }
  .promo .modal {
    background: crimson;
    color: white;
  }
</style>
