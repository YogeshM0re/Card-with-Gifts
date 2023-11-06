<script>
  import { loggedIn, username } from '../lib/stores';
</script>

<div class="custom-navbar shadow-md" style="background: linear-gradient(135deg, #7b3ff2, #e100ff); padding: 20px; color: white; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">
  <div class="container mx-auto " style="display: flex; justify-content: space-between; align-items: center;">
    <div>
      <h1 class="text-4xl font-extrabold mb-2" style="font-family: 'Great Vibes', cursive;">Card with Gifts</h1>
      <p class="text-lg text-gray-300" style="font-family: 'Sacramento', cursive;">Make an Impression!</p>
    </div>
    {#if $loggedIn}
      <div class="text-gray-300 flex items-center">
        <p style="color: #ff7ce5; font-weight: bold; margin-right: 10px;">Welcome, {$username}</p>
        <img src="https://via.placeholder.com/50" alt="User Avatar" style="border-radius: 50%; box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); animation: pulse-avatar 2s infinite;">
      </div>
    {/if}
  </div>
</div>
