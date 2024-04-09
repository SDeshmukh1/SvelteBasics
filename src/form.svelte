<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "";
  let title = "";
  let image = "";
  let description = "";
  let showError = false;

  function handleSubmit() {
    if (name && title && image && description) {
      showError = false; // Reset error state
    } else {
      showError = true;
    }
  }

  // Focus the first input field on mount
  onMount(() => {
    document.getElementById('userName').focus();
  });
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
    margin-bottom: 1rem;
  }

  .error {
    color: red;
    margin-top: 0.5rem;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" required />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" required />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="url" bind:value={image} id="image" required />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" required />
  </div>
  {#if showError}
    <p class="error">Please fill out all fields.</p>
  {/if}
  <button on:click={handleSubmit}>Submit</button>
</div>

<ContactCard userName={name} jobTitle={title} userImage={image} {description} />
