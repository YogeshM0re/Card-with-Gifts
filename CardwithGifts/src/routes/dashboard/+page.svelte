<script>
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
      // Add your logout functionality here
    };
  
    const addNewCard = () => {
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
  </script>
  
  <div class="container">
    <div class="dashboard">
      <div class="user-info card">
        <h2>Welcome, {user.username}!</h2>
        <p>Email: {user.email}</p>
        <button class="button-primary" on:click={logout}>Logout</button>
      </div>
  
      <div class="card-management card">
        <h3>Your Cards</h3>
        <div class="table-wrapper">
          <table class="u-full-width fancy-table">
            <thead>
              <tr>
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
                <tr>
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
                  <td>{card.Front}</td>
                  <td>{card.Inside_Left}</td>
                  <td>{card.Inside_Right}</td>
                  <td>{card.Back}</td>
                  <td>{card.Uploaded_By}</td>
                  <td>{card.Status}</td>
                </tr>
              {/each}
            </tbody>
          </table>
        </div>
      </div>
  
      <div class="add-card-section card">
          <h3>Add New Card</h3>
          <div class="input-fields">
              <div class="input-row">
                <div class="input-col">
                  <label for="occasion">Occasion:</label>
                  <input type="text" id="occasion" bind:value={newCard.Occasion} />
            
                  <label for="recipient">Recipient:</label>
                  <input type="text" id="recipient" bind:value={newCard.Recipient} />
            
                  <label for="publisherSku">Publisher SKU:</label>
                  <input type="text" id="publisherSku" bind:value={newCard.Publisher_Sku} />
            
                  <label for="orientation">Orientation:</label>
                  <input type="text" id="orientation" bind:value={newCard.Orientation} />
                </div>
            
                <div class="input-col">
                  <label for="cardwithGiftSku">Card with Gift SKU:</label>
                  <input type="text" id="cardwithGiftSku" bind:value={newCard.CardwithGift_Sku} />
            
                  <label for="activationDate">Activation Date:</label>
                  <input type="text" id="activationDate" bind:value={newCard.Activation_Date} />
            
                  <label for="deactivationDate">Deactivation Date:</label>
                  <input type="text" id="deactivationDate" bind:value={newCard.Deactivation_Date} />
            
                  <label for="uploadedBy">Uploaded By:</label>
                  <input type="text" id="uploadedBy" bind:value={newCard.Uploaded_By} />
                </div>
            
                <div class="input-col">
                  <label for="frontImage">Front Image URL:</label>
                  <input type="text" id="frontImage" bind:value={newCard.Front} />
            
                  <label for="insideLeftImage">Inside Left Image URL:</label>
                  <input type="text" id="insideLeftImage" bind:value={newCard.Inside_Left} />
            
                  <label for="insideRightImage">Inside Right Image URL:</label>
                  <input type="text" id="insideRightImage" bind:value={newCard.Inside_Right} />
            
                  <label for="backImage">Back Image URL:</label>
                  <input type="text" id="backImage" bind:value={newCard.Back} />
            
                  <label for="status">Status:</label>
                  <input type="text" id="status" bind:value={newCard.Status} />
                </div>
              </div>
              <button on:click={addNewCard}>Add Card</button>
            </div>
            
        </div>
        
        
  </div>
  </div>
  <style>
    .container {
      max-width: 960px;
      margin: 0 auto;
      padding: 20px;
    }
  
    .card {
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    background: #f9f9f9;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  
    .button-primary {
      background-color: #2ecc71;
      color: white;
      border: none;
      padding: 12px 24px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 18px;
      margin: 10px 0;
      cursor: pointer;
      border-radius: 8px;
      transition: background-color 0.3s ease;
    }
  
    .button-primary:hover {
      background-color: #29d269;
    }
  
    .table-wrapper {
      overflow-x: auto;
    }
  
    .card-management table {
      width: 100%;
      border-collapse: collapse;
      border-spacing: 0;
    }
  
    .card-management th,
    .card-management td {
      border: 1px solid #e0e0e0;
      padding: 12px;
      text-align: left;
    }
  
    .card-management th {
      background: linear-gradient(to bottom, #f0f0f0, #e5e5e5);
    }
  
    .card-management td {
      transition: background-color 0.3s ease;
    }
  
    .card-management td:hover {
      background-color: #f9f9f9;
    }
  
    .add-card-section {
    padding: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    background: #f9f9f9;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .add-card-section input,
  .add-card-section button {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
  }
  
  .add-card-section label {
    margin-top: 12px;
    font-weight: bold;
  }
  
  .add-card-section button {
    background-color: #2ecc71;
    color: white;
    border: none;
    text-align: center;
    cursor: pointer;
    border-radius: 8px;
    transition: background-color 0.3s ease;
  }
  
  .add-card-section button:hover {
    background-color: #29d269;
  }
  
  .input-fields {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .input-row {
    display: flex;
    width: 100%;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  
  .input-col {
    width: calc(33.33% - 20px);
    margin: 0 10px;
    padding: 10px;
  }
  
  .input-col label {
    display: block;
    margin-bottom: 5px;
  }
  
  .input-col input {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-sizing: border-box;
  }
  button {
    background-color: #2ecc71;
    color: white;
    border: none;
    padding: 12px 24px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 18px;
    cursor: pointer;
    border-radius: 8px;
    transition: background-color 0.3s ease;
    margin-top: 10px;
  }
  
  button:hover {
    background-color: #29d269;
  }
  
  
  </style>
  