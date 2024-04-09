<!-- Login.svelte -->
<script>
    let username = '';
    let password = '';

    function handleLogin() {
        // Your login logic here
        if (username === 'user' && password === 'password') {
            // Assuming login is successful, you can navigate to the app page
            window.location.href = '/app';
        } else {
            alert('Invalid username or password');
        }
    }
</script>

<style>
    /* Your CSS styles for login page */
</style>

<div>
    <h2>Login</h2>
    <input type="text" bind:value={username} placeholder="Username"/>
    <input type="password" bind:value={password} placeholder="Password"/>
    <button on:click={handleLogin}>Login</button>
</div>
