<script>
  // @ts-nocheck

  import { loggedIn, username } from "../lib/stores";
  import { goto } from "$app/navigation";

  let user = { username: "", password: "" };
  let inputUsername = "JohnDoe";
  let inputPassword = "JohnDoe";

  function handleLogin() {
    user.username = inputUsername;
    user.password = inputPassword;

    if (user.username === "JohnDoe" && user.password === "JohnDoe") {
      loggedIn.set(true);
      username.set(user.username);
      goto("/dashboard");
    } else {
      console.log("Login failed. Please check your credentials.");
    }
  }
</script>

<div class="container mx-auto p-2 flex justify-center items-center h-screen">
  <div
    class="login-container"
    style="background: linear-gradient(#F5DDDA, #D5EAF5); padding: 2rem; box-shadow: 0 4px 14px 0 rgba(0, 0, 0, 0.1); border: 0.1px solid grey; border-radius: 0.375rem;"
  >
    <h1 class="text-2xl  mb-4 text-center text-white">
      Welcome Back!
    </h1>

    <form
      class="flex flex-col space-y-6 items-center"
      on:submit|preventDefault={handleLogin}
    >
      <label class="flex flex-col">
        <span class="text-gray-700 mb-2 text-lg">Username</span>
        <input
          bind:value={inputUsername}
          class="input w-64 rounded-lg py-3 px-4 bg-white"
          type="text"
          placeholder="Enter your username"
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-2 text-lg">Password</span>
        <input
          bind:value={inputPassword}
          class="input w-64 rounded-lg py-3 px-4 bg-white"
          type="password"
          placeholder="Enter your password"
        />
      </label>

      <button
        type="submit"
        class="btn bg-purple-400 text-white py-2 rounded-lg hover:bg-purple-800"
      >
        Login
      </button>
    </form>

    <div class="flex flex-col mt-6 space-y-4">
      <a href="/" class="text-black text-center hover:underline"
        >Forgot Password?</a
      >

      <p class="text-center mt-6">
        Don't have an account?
        <a
          href="/registration"
          style="text-decoration: none; color: #1a73e8; font-weight: bold; transition: color 0.3s ease;"
          onmouseover="this.style.color='#ea4335'"
          onmouseout="this.style.color='#1a73e8'"
        >
          Create one
        </a>
      </p>
    </div>
  </div>
</div>
