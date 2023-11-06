<script>
  import { loggedIn, username } from '../lib/stores';
  import { goto } from '$app/navigation';

  let user = { username: '', password: '' }; 
  let inputUsername = 'JohnDoe'; 
  let inputPassword = 'JohnDoe'; 

  function handleLogin() {
    user.username = inputUsername;
    user.password = inputPassword;

    if (user.username === 'JohnDoe' && user.password === 'JohnDoe') {
      loggedIn.set(true);
      username.set(user.username);
      goto('/dashboard');
    } else {
      console.log('Login failed. Please check your credentials.');
    }
  }
</script>

<div class="container mx-auto p-2">
  <div class="login-container bg-gradient-to-br from-purple-300 to-purple-500 p-8 shadow-lg rounded-md border-2 border-purple-400">
    <h1 class="text-4xl font-extrabold mb-6 text-center text-white">
      Welcome Back!
    </h1>

    <form class="flex flex-col space-y-6 items-center" on:submit|preventDefault={handleLogin}>
      <label class="flex flex-col">
        <span class="text-white mb-2 text-lg">Username</span>
        <input
          bind:value={inputUsername}
          class="input w-64 rounded-lg py-3 px-4 bg-purple-100 bg-opacity-50"
          type="text"
          placeholder="Enter your username"
        />
      </label>

      <label class="flex flex-col">
        <span class="text-white mb-2 text-lg">Password</span>
        <input
          bind:value={inputPassword} 
          class="input w-64 rounded-lg py-3 px-4 bg-purple-100 bg-opacity-50"
          type="password"
          placeholder="Enter your password"
        />
      </label>

      <button type="submit" class="btn bg-purple-600 text-white py-3 rounded-lg hover:bg-purple-800">
        Login
      </button>
    </form>

    <div class="flex flex-col mt-6 space-y-4">
      <a href="/" class="text-white text-center hover:underline">Forgot Password?</a>
      <a href="/registration" class="text-center text-white">
        Don't have an account? <span class="text-yellow-300">Create one</span>
      </a>
    </div>
  </div>
</div>
