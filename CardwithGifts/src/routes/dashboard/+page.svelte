<script>
  // @ts-nocheck
  import * as yup from "yup";

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

  let currentDate = new Date().toISOString().split("T")[0];
  let currentTime = new Date().toTimeString().split(" ")[0];

  let newCard = {
    Publisher_ID: "",
    Occasion: "",
    Recipient: "",
    Orientation: "Portrait",
    Publisher_Sku: "",
    CardwithGift_Sku: "",
    Created_Date: "",
    Modified_Date: "",
    Activation_Date: `${currentDate}T${currentTime}`,
    Deactivation_Date: `${currentDate}T${currentTime}`,
    Front: "",
    Inside_Left: "",
    Inside_Right: "",
    Back: "",
    Uploaded_By: "",
    Status: "Active",
  };

  const cardSchema = yup.object().shape({
    Occasion: yup.string().required(),
    Recipient: yup.string().required(),
    Publisher_Sku: yup.string().required(),
    CardwithGift_Sku: yup.string().required(),
    Uploaded_By: yup.string().required(),
  });

  let errors = {};

  const addNewCard = async () => {
    try {
      await cardSchema.validate(newCard, { abortEarly: false });
      const uniqueID =
        cards.length > 0
          ? Math.max(...cards.map((card) => Number(card.Publisher_ID))) + 1
          : 1;
      newCard.Publisher_ID = String(uniqueID);
      newCard.Created_Date = new Date().toISOString().split("T")[0];
      cards = [...cards, { ...newCard }];
      console.log("New Cards:", cards);
      resetNewCard();
    } catch (error) {
      error.inner.forEach((err) => {
        errors[err.path] = err.message;
      });
    }
  };

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

  function resetNewCard() {
    newCard = {
      Publisher_ID: "",
      Occasion: "",
      Recipient: "",
      Orientation: "Portrait",
      Publisher_Sku: "",
      CardwithGift_Sku: "",
      Created_Date: "",
      Modified_Date: "",
      Activation_Date: `${currentDate}T${currentTime}`,
      Deactivation_Date: `${currentDate}T${currentTime}`,
      Front: "",
      Inside_Left: "",
      Inside_Right: "",
      Back: "",
      Uploaded_By: "",
      Status: "Active",
    };
    errors = {};
  }

  function handleInputChange(event, field) {
    newCard[field] = event.target.value;
    errors[field] = "";
  }
  let originalCards = [...cards];

  function handleSearch(event) {
    const searchTerm = event.target.value.trim().toLowerCase();

    if (searchTerm === "") {
      cards = [...originalCards];
    } else {
      const filteredCards = originalCards.filter((card) => {
        return Object.values(card).some(
          (value) =>
            value &&
            typeof value === "string" &&
            value.toLowerCase().includes(searchTerm)
        );
      });
      cards = filteredCards;
    }
  }

  let showCatalog = true;
  let showAddCard = false;

  function viewCatalog() {
    showCatalog = true;
    showAddCard = false;
  }

  function showAddCardSection() {
    showCatalog = true;
    showAddCard = true;
  }
</script>

<div class="container">
  <div class="dashboard">
    {#if showCatalog}
      <!-- <div
      class="user-info card bg-gradient-to-r from-purple-500 to-indigo-600 p-6 rounded-lg shadow-lg mb-6"
    >
      <h2 class="text-3xl font-bold text-white">Welcome, {user.username}!</h2>
      <p class="text-gray-300">Email: {user.email}</p>
      <button class="button-primary mt-4" on:click={logout}>Logout</button>
    </div> -->

      <div class="search-box mb-4">
        <input
          type="text"
          placeholder="Search cards..."
          on:input={handleSearch}
          class="w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <div class="action-links text-center">
        <ul class="inline">
          <li class="inline">
            <a href="dashboard" on:click={viewCatalog}>View Catalog</a>
          </li>
          <li class="inline">
            <a href="dashboard" on:click={showAddCardSection}>Create Catalog</a>
          </li>
          <li class="inline">
            <a href="dashboard" on:click={showAddCardSection}>Add Card</a>
          </li>
        </ul>
      </div>

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
    {/if}
    {#if showAddCard}
      <div class="add-card-section card bg-white p-4 rounded shadow-md mb-4">
        <div class="input-fields">
          <div>
            <div
              class="input-row grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
            >
              <div class="input-col">
                <label for="occasion">Occasion:</label>
                <input
                  type="text"
                  bind:value={newCard.Occasion}
                  on:input={(e) => handleInputChange(e, "occasion")}
                />
                {#if errors.Occasion && newCard.Occasion === ""}
                  <p style="color: red;">Occasion is required.</p>
                {/if}

                <label for="recipient">Recipient:</label>

                <input
                  type="text"
                  bind:value={newCard.Recipient}
                  on:input={(e) => handleInputChange(e, "recipient")}
                />
                {#if errors.Recipient && newCard.Recipient === ""}
                  <p style="color: red;">Recipient is required.</p>
                {/if}

                <label for="publisherSku">Publisher SKU:</label>

                <input
                  type="text"
                  bind:value={newCard.Publisher_Sku}
                  on:input={(e) => handleInputChange(e, "publisherSku")}
                />
                {#if errors.Publisher_Sku && newCard.Publisher_Sku === ""}
                  <p style="color: red;">Publisher Sku is required.</p>
                {/if}
              </div>

              <div class="input-col">
                <label for="orientation">Orientation:</label>
                <div class="relative">
                  <select
                    id="orientation"
                    bind:value={newCard.Orientation}
                    class="w-full border border-gray-300 rounded-md p-2 bg-opacity-75"
                    style="color: #777;"
                  >
                    <option value="Landscape">Landscape</option>
                    <option value="Portrait">Portrait</option>
                  </select>
                </div>

                <label for="cardwithGiftSku">Card with Gift SKU:</label>

                <input
                  type="text"
                  bind:value={newCard.CardwithGift_Sku}
                  on:input={(e) => handleInputChange(e, "cardwithGiftSku")}
                />
                {#if errors.CardwithGift_Sku && newCard.CardwithGift_Sku === ""}
                  <p style="color: red;">CardwithGift Sku is required.</p>
                {/if}

                <label for="uploadedBy">Uploaded By:</label>

                <input
                  type="text"
                  bind:value={newCard.Uploaded_By}
                  on:input={(e) => handleInputChange(e, "uploadedBy")}
                />
                {#if errors.Uploaded_By && newCard.Uploaded_By === ""}
                  <p style="color: red;">Uploaded By is required.</p>
                {/if}
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
                    class="w-full border border-gray-300 rounded-md p-2 bg-opacity-75"
                    style=" color: #777;"
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
                <div
                  class="image-container"
                  style={newCard.Front ? "" : "display: none;"}
                >
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
                <div
                  class="image-container"
                  style={newCard.Inside_Left ? "" : "display: none;"}
                >
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
                <div
                  class="image-container"
                  style={newCard.Inside_Right ? "" : "display: none;"}
                >
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
                <div
                  class="image-container"
                  style={newCard.Back ? "" : "display: none;"}
                >
                  <img src={newCard.Back} alt="Back" />
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="button-container">
          <button class="button-primary btn-add-card" on:click={addNewCard}
            >Add Card</button
          >
          <button class="button-secondary btn-cancel" on:click={resetNewCard}
            >Cancel</button
          >
        </div>
      </div>
    {/if}
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

  .input-row {
    display: grid;
    gap: 1rem;
    background: linear-gradient(to bottom, #d5eaf584, #f5ddda7a);
  }

  input {
    @apply w-full border border-gray-300 rounded-md p-2;
  }

  .fancy-table th,
  .fancy-table td {
    @apply p-3;
    font-size: 80%;
    border: 1px solid #ddd;
  }

  .fancy-table tr:hover {
    background-color: #ddd;
  }

  .scroll-cell {
    max-width: 150px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    cursor: pointer;
  }

  .input-col {
    flex: 1;
    margin: 0 5px;
    margin-bottom: 30px;
    position: relative;
  }
  .input-col label {
    font-weight: bold;
    color: black;
    margin-bottom: 0.3rem;
    font-size: 0.9rem;
    margin-top: 25px;
  }

  .input-col p {
    color: red;
    font-size: 15px;
    position: absolute;
  }
  .images {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .image-container {
    margin-top: 10px;
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
  .button-container {
    display: flex;
    justify-content: flex-end;
  }

  .button-primary,
  .button-secondary {
    padding: 10px 25px;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    margin: 5px;
    transition: background 0.3s, box-shadow 0.3s;
    background: linear-gradient(45deg, #ff7e5f, #feb47b, #ffcb91, #ffdca0);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    color: black;
    transition: background 0.3s, box-shadow 0.3s, transform 0.3s;
  }

  .button-primary:hover,
  .button-secondary:hover {
    background: linear-gradient(45deg, #bee8ff, #ffccc5);

    box-shadow: 0 6px 10px rgba(0, 0, 0, 0.3);
    animation: colorTransition 1s ease infinite;
    transform: scale(1.1);
  }
  .button-primary:active,
  .button-secondary:active {
    transform: scale(0.8);
  }
  @keyframes colorTransition {
    0% {
      filter: hue-rotate(0deg);
    }
    100% {
      filter: hue-rotate(360deg);
    }
  }
  .search-box {
    margin-bottom: 20px;
  }

  .action-links {
    text-align: center;
    margin-top: 20px;
    margin-bottom: 20px;
  }

  .inline {
    display: inline;
  }

  .action-links ul {
    list-style: none;
    padding: 0;
  }

  .action-links ul li {
    display: inline;
    margin: 0 10px;
  }

  .action-links ul li a {
    text-decoration: none;
    padding: 8px 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #f0f0f0;
    color: #333;
  }

  .action-links ul li a:hover {
    background: linear-gradient(45deg, #bee8ff, #ffccc5);
  }
</style>
