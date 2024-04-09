<script>
  import { onMount } from 'svelte';
  import Login from "./Login.svelte";
  import AppContent from "./form.svelte"; 

  let isLoggedIn = false;

  // Function to handle successful login
  function handleLoginSuccess() {
    isLoggedIn = true;
  }

  // Check login status on mount
  onMount(() => {
    // You can implement more sophisticated logic here to check if user is logged in
    // For demo purpose, let's assume user is not logged in initially
    isLoggedIn = false;
  });
</script>

{#if isLoggedIn}
  <!-- Render app content if user is logged in -->
  <AppContent />
{:else}
  <!-- Render login component if user is not logged in -->
  <Login on:loginSuccess={handleLoginSuccess} />
{/if}
