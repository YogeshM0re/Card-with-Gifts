<script>
  // @ts-nocheck

  let companyName = "";
  let phone = "";
  let phoneType = "mobile";
  let email = "";
  let streetAddress = "";
  let address2 = "";
  let city = "";
  let state = "";
  let zipCode = "";
  let username = "";
  let password = "";

  function handleSubmit() {
    const formData = {
      companyName,
      phone,
      phoneType,
      email,
      streetAddress,
      address2,
      city,
      state,
      zipCode,
      username,
      password,
    };

    console.log("Form Data:", formData);
  }
</script>

<div class="container mx-auto p-4">
  <div
    class="registration-form bg-gradient-to-br from-purple-300 to-purple-300 p-8 shadow-lg rounded-md border-2 border-purple-400"
  >
    <h1 class="text-4xl  mb-6 text-center text-white">
      User Registration
    </h1>

    <form
      class="flex flex-col space-y-6"
      style="width: 400px; margin: 0 auto;"
      on:submit|preventDefault={handleSubmit}
    >
      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Company Name</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your company name"
          bind:value={companyName}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Phone</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your phone number"
          bind:value={phone}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Phone Type</span>
        <select class="input rounded-md py-2 px-3" bind:value={phoneType}>
          <option value="mobile">Mobile</option>
          <option value="landline">Landline</option>
          <option value="other">Other</option>
        </select>
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Email Address</span>
        <input
          class="input rounded-md py-2 px-3"
          type="email"
          placeholder="Enter your email"
          bind:value={email}
        />
      </label>
      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Street Address</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your street address"
          bind:value={streetAddress}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Suite/Street Address 2</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your suite/street address 2"
          bind:value={address2}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">City</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your city"
          bind:value={city}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">State</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your state"
          bind:value={state}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Zip code</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your zip code"
          bind:value={zipCode}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Username</span>
        <input
          class="input rounded-md py-2 px-3"
          type="text"
          placeholder="Enter your username"
          bind:value={username}
        />
      </label>

      <label class="flex flex-col">
        <span class="text-gray-700 mb-1">Password</span>
        <input
          class="input rounded-md py-2 px-3"
          type="password"
          placeholder="Enter your password"
          bind:value={password}
        />
      </label>

      <button
        type="submit"
        class="btn skeleton-gold-nouveau-bg skeleton-gold-nouveau-text py-3 rounded-lg hover:bg-purple-800 transform transition duration-300 hover:scale-105"
      >
        Register
      </button>
      <p class="text-center mt-6">
        Already have an account?
        <a
          href="/"
          style="text-decoration: none; color: #1a73e8; font-weight: bold; transition: color 0.3s ease;"
          onmouseover="this.style.color='#ea4335'"
          onmouseout="this.style.color='#1a73e8'"
        >
          Login here
        </a>
      </p>
    </form>
  </div>
</div>

<style>
  input[type="text"],
  input[type="email"],
  input[type="password"],
  select {
    border: 1px solid #ccc;
    transition: border-color 0.3s;
    border: 1px solid #ccc;
  transition: border-color 0.3s;
  color: black; 
  background-color: white;
  }

  input[type="text"]:focus,
  input[type="email"]:focus,
  input[type="password"]:focus,
  select:focus {
    border-color: blue;
  }

  .registration-form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

  }

  .bg-gradient-to-br {
    background: linear-gradient( #D5EAF5 , #F5DDDA);
  }

  .btn:hover {
    background: linear-gradient(#eab9fd , #F5DDDA);
  }
</style>
