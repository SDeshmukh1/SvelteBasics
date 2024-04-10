<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Shubham ";
  let title = "";//Senior SDET
  let image = "";//https://media.licdn.com/dms/image/D5603AQEBdRfsGjcGrA/profile-displayphoto-shrink_800_800/0/1671793172314?e=1718236800&v=beta&t=3M2NGa__g60n0JDu2VLqO4ersdugFTXf-8cw7nSLiLA
  let description = "";//(8+ yrs Exp) Automation Tester With Key Skills like Selenium, Core Java
  let formState = 'empty';

  function addContact(){
    console.log('add Contact called')
    if(name.trim().length==0||title.trim().length==0||image.trim().length==0||description.trim().length==0){
      console.log('Checking if condition')
      formState='invalid';
      return
    }
    console.log('Checking else condition')
    formState = 'done';
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>

<button onclick = {addContact} >Add Contact Card</button>

{#if formState ==='done'}
  <ContactCard 
    userName={name} 
    jobTitle={title} 
    {description} 
    userImage={image} />
{:else if formState === 'invalid' }
  <p>Please provide all the inputs</p>
{/if}