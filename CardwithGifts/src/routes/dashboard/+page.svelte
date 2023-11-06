<script>
  // @ts-nocheck

  let user = {
    username: "John Doe",
    email: "john@example.com",
  };

  let cards = [
    {
      Publisher_ID: "123",
      Occasion: "Birthday",
      Recipient: "Friend",
      Orientation: "Landscape",
      Publisher_Sku: "SKU123",
      CardwithGift_Sku: "CardSKU123",
      Created_Date: "2023-10-12",
      Modified_Date: "2023-10-15",
      Activation_Date: "2023-10-20",
      Deactivation_Date: "2023-12-01",
      Front: "Front Image URL",
      Inside_Left: "Inside Left Image URL",
      Inside_Right: "Inside Right Image URL",
      Back: "Back Image URL",
      Uploaded_By: "John",
      Status: "Active",
    },
    {
      Publisher_ID: "456",
      Occasion: "Anniversary",
      Recipient: "Spouse",
      Orientation: "Portrait",
      Publisher_Sku: "SKU456",
      CardwithGift_Sku: "CardSKU456",
      Created_Date: "2023-09-20",
      Modified_Date: "2023-09-25",
      Activation_Date: "2023-09-30",
      Deactivation_Date: "2023-11-15",
      Front: "Front Image URL 2",
      Inside_Left: "Inside Left Image URL 2",
      Inside_Right: "Inside Right Image URL 2",
      Back: "Back Image URL 2",
      Uploaded_By: "Jane",
      Status: "Inactive",
    },
    {
      Publisher_ID: "457",
      Occasion: "Anniversary",
      Recipient: "Friend",
      Orientation: "Landscape",
      Publisher_Sku: "SKU987",
      CardwithGift_Sku: "CardSKU983",
      Created_Date: "2023-10-12",
      Modified_Date: "2023-10-15",
      Activation_Date: "2023-10-20",
      Deactivation_Date: "2023-12-01",
      Front: "Front Image URL",
      Inside_Left: "Inside Left Image URL",
      Inside_Right: "Inside Right Image URL",
      Back: "Back Image URL",
      Uploaded_By: "John",
      Status: "Active",
    },
    {
      Publisher_ID: "500",
      Occasion: "Birthday",
      Recipient: "Spouse",
      Orientation: "Landscape",
      Publisher_Sku: "SKU453",
      CardwithGift_Sku: "CardSKU453",
      Created_Date: "2022-08-20",
      Modified_Date: "2023-10-15",
      Activation_Date: "2023-10-20",
      Deactivation_Date: "2023-12-01",
      Front: "Front Image URL",
      Inside_Left: "Inside Left Image URL",
      Inside_Right: "Inside Right Image URL",
      Back: "Back Image URL",
      Uploaded_By: "John",
      Status: "Active",
    },
  ];

  let notifications = [
    {
      message: "New card added",
    },
    {
      message: "Reminder: Cards due soon",
    },
  ];

  let newCard = {
    Publisher_ID: "",
    Occasion: "",
    Recipient: "",
    Orientation: "",
    Publisher_Sku: "",
    CardwithGift_Sku: "",
    Created_Date: "",
    Modified_Date: "",
    Activation_Date: "",
    Deactivation_Date: "",
    Front: "",
    Inside_Left: "",
    Inside_Right: "",
    Back: "",
    Uploaded_By: "",
    Status: "Active",
  };

  const logout = () => {
    console.log("Logging out");
  };

  const addNewCard = () => {
    const uniqueID =
      cards.length > 0
        ? Math.max(...cards.map((card) => card.Publisher_ID)) + 1
        : 1;

    newCard.Publisher_ID = uniqueID;

    newCard.Created_Date = new Date().toISOString().split("T")[0];
    cards = [...cards, newCard];
    resetNewCard();
  };

  function resetNewCard() {
    newCard = {
      Publisher_ID: "",
      Occasion: "",
      Recipient: "",
      Orientation: "",
      Publisher_Sku: "",
      CardwithGift_Sku: "",
      Created_Date: "",
      Modified_Date: "",
      Activation_Date: "",
      Deactivation_Date: "",
      Front: "",
      Inside_Left: "",
      Inside_Right: "",
      Back: "",
      Uploaded_By: "",
      Status: "Active",
    };
  }

  function handleImageSelect(event, imageType) {
    const file = event.target.files[0];

    if (file) {
      const reader = new FileReader();

      reader.onload = () => {
        newCard[imageType] = reader.result;
      };

      reader.readAsDataURL(file);
    }
  }
</script>

<div class="container">
  <div class="dashboard">
    <!-- <div
      class="user-info card bg-gradient-to-r from-purple-500 to-indigo-600 p-6 rounded-lg shadow-lg mb-6"
    >
      <h2 class="text-3xl font-bold text-white">Welcome, {user.username}!</h2>
      <p class="text-gray-300">Email: {user.email}</p>
      <button class="button-primary mt-4" on:click={logout}>Logout</button>
    </div> -->

    <div
      class="card-management card bg-white p-6 rounded-lg shadow-lg mb-6 border border-grey"
    >
      <div class="overflow-x-auto border border-grey">
        <table class="w-full fancy-table">
          <thead>
            <tr class="border border-black scroll-cell">
              <th>Publisher ID</th>
              <th>Occasion</th>
              <th>Recipient</th>
              <th>Orientation</th>
              <th>Publisher Sku</th>
              <th>CardwithGift Sku</th>
              <th>Created Date</th>
              <th>Modified Date</th>
              <th>Activation Date</th>
              <th>Deactivation Date</th>
              <th>Front</th>
              <th>Inside Left</th>
              <th>Inside Right</th>
              <th>Back</th>
              <th>Uploaded By</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            {#each cards as card}
              <tr class="border border-black scroll-cell">
                <td>{card.Publisher_ID}</td>
                <td>{card.Occasion}</td>
                <td>{card.Recipient}</td>
                <td>{card.Orientation}</td>
                <td>{card.Publisher_Sku}</td>
                <td>{card.CardwithGift_Sku}</td>
                <td>{card.Created_Date}</td>
                <td>{card.Modified_Date}</td>
                <td>{card.Activation_Date}</td>
                <td>{card.Deactivation_Date}</td>
                <td class="scroll-cell">{card.Front}</td>
                <td class="scroll-cell">{card.Inside_Left}</td>
                <td class="scroll-cell">{card.Inside_Right}</td>
                <td class="scroll-cell">{card.Back}</td>
                <td>{card.Uploaded_By}</td>
                <td>{card.Status}</td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
    </div>

    <div class="add-card-section card bg-white p-4 rounded shadow-md mb-4">
      <h3 class="text-xl font-semibold mb-4">Add New Card</h3>
      <div class="input-fields">
        <div>
          <div
            class="input-row grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
          >
            <div class="input-col">
              <label for="occasion">Occasion:</label>
              <input type="text" id="occasion" bind:value={newCard.Occasion} />

              <label for="recipient">Recipient:</label>
              <input
                type="text"
                id="recipient"
                bind:value={newCard.Recipient}
              />

              <label for="publisherSku">Publisher SKU:</label>
              <input
                type="text"
                id="publisherSku"
                bind:value={newCard.Publisher_Sku}
              />
            </div>

            <div class="input-col">
              <label for="orientation">Orientation:</label>
              <input
                type="text"
                id="orientation"
                bind:value={newCard.Orientation}
              />
              <label for="cardwithGiftSku">Card with Gift SKU:</label>
              <input
                type="text"
                id="cardwithGiftSku"
                bind:value={newCard.CardwithGift_Sku}
              />
              <label for="uploadedBy">Uploaded By:</label>
              <input
                type="text"
                id="uploadedBy"
                bind:value={newCard.Uploaded_By}
              />
            </div>
            <div class="input-col">
              <label for="activationDate">Activation Date:</label>
              <input
                type="datetime-local"
                id="activationDate"
                bind:value={newCard.Activation_Date}
              />
              <label for="deactivationDate">Deactivation Date:</label>
              <input
                type="datetime-local"
                id="deactivationDate"
                bind:value={newCard.Deactivation_Date}
              />

              <label for="status">Status:</label>
              <div class="relative">
                <select
                  id="status"
                  bind:value={newCard.Status}
                  class="w-full border border-gray-300 rounded-md p-2 bg-opacity-75 bg-purple-200 text-gray-700 mb-5"
                >
                  <option value="Active">Active</option>
                  <option value="Inactive">Inactive</option>
                </select>
              </div>
            </div>
          </div>

          <div class="images">
            <div class="input-col">
              <label for="frontImage">Front Image:</label>
              <input
                type="file"
                id="frontImage"
                on:change={(e) => handleImageSelect(e, "Front")}
              />
              <div class="image-container">
                <img src={newCard.Front} alt="Front" />
              </div>
            </div>

            <div class="input-col">
              <label for="insideLeftImage">Inside Left Image:</label>
              <input
                type="file"
                id="insideLeftImage"
                on:change={(e) => handleImageSelect(e, "Inside_Left")}
              />
              <div class="image-container">
                <img src={newCard.Inside_Left} alt="Inside Left" />
              </div>
            </div>

            <div class="input-col">
              <label for="insideRightImage">Inside Right Image:</label>
              <input
                type="file"
                id="insideRightImage"
                on:change={(e) => handleImageSelect(e, "Inside_Right")}
              />
              <div class="image-container">
                <img src={newCard.Inside_Right} alt="Inside Right" />
              </div>
            </div>

            <div class="input-col">
              <label for="backImage">Back Image:</label>
              <input
                type="file"
                id="backImage"
                on:change={(e) => handleImageSelect(e, "Back")}
              />
              <div class="image-container">
                <img src={newCard.Back} alt="Back" />
              </div>
            </div>
          </div>
        </div>
      </div>

      <button class="button-primary mt-4" on:click={addNewCard}>Add Card</button
      >
    </div>
  </div>
</div>

<style>
  @import "tailwindcss/base";
  @import "tailwindcss/components";
  @import "tailwindcss/utilities";

  .container {
    @apply mx-auto p-4;
    max-width: 100%;
  }

  .card {
    @apply rounded shadow-md;
  }

  .button-primary {
    @apply bg-green-500 text-white py-2 px-4 rounded transition duration-300;
  }

  .input-row {
    display: grid;
    gap: 1rem;
    background-color: aliceblue;
    
  }

  input {
    @apply w-full border border-gray-300 rounded-md p-2;
    background-color: rgba(254, 204, 254, 0.649);
    
  }

  .fancy-table th,
  .fancy-table td {
    @apply p-3;
    font-size: 80%;
  }
  .scroll-cell {
    max-width: 150px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    cursor: pointer;
  }

  .button-primary {
    display: block;
    width: 100%;
    background-color: #2ecc71;
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .button-primary:hover {
    background-color: #27ae60;
  }
  .input-col {
    flex: 1;
    margin: 0 5px;
  }
  .input-col label {
    font-weight: bold;
    color: black;
    margin-bottom: 0.3rem;
    font-size: 0.9rem;
  }


  .images {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .image-container {
    margin-top:10px;
    text-align: center;
    border: 1px solid #ccc;
    padding: 10px;
  }

  .image-container img {
    margin-top: 10px;
    width: 200px;
    height: 150px;
    object-fit: cover;
    border: 2px solid #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  .image-container img:hover {
    transform: scale(1.05);
    box-shadow: 0 4px 8px rgba(142, 96, 227, 0.518);
  }
</style>
