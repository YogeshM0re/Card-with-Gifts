<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=MuseoModerno:wght@100;200&family=Rajdhani&display=swap" rel="stylesheet">

<style>
  .great-vibes {
    font-family: 'Great Vibes', cursive;
  }
  .museo-moderno {
    font-family: 'MuseoModerno', sans-serif;
    font-weight: 200;
  }
  
  .custom-navbar {
    padding: 5px 10px; /* Adjust the padding to make the navbar thinner */
  }
</style>

<script>
  import { loggedIn, username } from '../lib/stores';
</script>

<div class="custom-navbar shadow-md" style="background: linear-gradient(to bottom, #CCABD8, #86E3CE); padding: 20px; color: white; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;">
  <div class="container mx-auto" style="display: flex; justify-content: space-between; align-items: center;">
    <div>
      <h1 class="text-4xl font-extrabold great-vibes" style="margin-bottom: 5px;">Card with Gifts</h1>
      <p class="text-lg text-gray-300 museo-moderno" style="margin-top: -10px;">Make an Impression!</p>
    </div>
    {#if $loggedIn}
      <div class="text-gray-300 flex items-center">
        <p style="color: #ff7ce5; font-weight: bold; margin-right: 10px;">Welcome, {$username}</p>
        <img src="https://m.media-amazon.com/images/I/81OcZThCE9L.jpg" alt="User Avatar" style="border-radius: 50%; box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); animation: pulse-avatar 2s infinite; width: 50px; height: 50px;">
      </div>
    {/if}
  </div>
</div>
