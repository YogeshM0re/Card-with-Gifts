<script lang="ts">
</script>

<div class="container mx-auto p-2">
  <div
    class="login-container bg-white p-7 shadow-md rounded-md skeleton-gold-nouveau"
  >
    <h1 class="text-3xl font-semibold mb-4 text-center text-purple-600">
      Login
    </h1>

    <form class="flex flex-col space-y-4 items-center">
      <!-- Added 'items-center' class to center contents -->
      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Username</span>
        <input
          class="input w-50 rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your username"
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Password</span>
        <input
          class="input w-50 rounded-md py-2 px-3"
          type="password"
          placeholder="Enter your password"
        />
      </label>

      <button
        type="submit"
        class="btn skeleton-gold-nouveau-bg skeleton-gold-nouveau-text py-2 rounded-md hover:bg-purple-800"
      >
        Login
      </button>
    </form>

    <div class="flex flex-col mt-4">
      <a href="/" class="text-blue-600 text-center">Forgot Password?</a>
      <a href="/registration" class="text-center text-gray-600">
        Don't have an account? <span class="text-purple-600">Create one</span>
      </a>
    </div>
  </div>
</div>
