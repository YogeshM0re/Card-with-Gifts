<script>
  import { loggedIn, username } from "../lib/stores";
</script>

<link
  href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap"
  rel="stylesheet"
/>
<link
  href="https://fonts.googleapis.com/css2?family=MuseoModerno:wght@100;200&family=Rajdhani&display=swap"
  rel="stylesheet"
/>

<div
  class="custom-navbar shadow-md"
  style="background: linear-gradient(to bottom, #D5EAF5, #F5DDDA); padding: 20px; color: white; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;"
>
  <div
    class="container mx-auto"
    style="display: flex; justify-content: space-between; align-items: center; margin-right: 200px;"
  >
    <div class="title-section">
      <h1
        class="text-4xl font-extrabold great-vibes text-black"
        style="margin-bottom: 5px;"
      >
        Card with Gifts
      </h1>
      <p class="text-lg text-black museo-moderno" style="margin-top: -10px;">
        Make an Impression!
      </p>
    </div>

    {#if $loggedIn}
      <div class="user-section text-gray-300 flex items-center">
        <p style="margin-right: -200px;">
          <span style="font-weight: bold; color: black;">Welcome Publisher </span>
          <span style=" color: grey;">{$username}</span>
          <br />
          <span style="color: black;">Publisher ID: 01</span>
        </p>
      </div>
    {/if}
  </div>
</div>

<style>
  .great-vibes {
    font-family: "Great Vibes", cursive;
  }
  .museo-moderno {
    font-family: "MuseoModerno", sans-serif;
    font-weight: 200;
  }
  .custom-navbar {
    padding: 5px 10px;
  }
  @media (max-width: 768px) {
    .container {
      flex-direction: column;
      text-align: center;
      margin-right: 0;
    }
    .user-section {
      margin-right: 0;
    }
  }
</style>
