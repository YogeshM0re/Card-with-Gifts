<!-- Include Skeleton CSS from a CDN -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/skeleton/2.0.4/skeleton.min.css">

<script lang="ts">
  let retailerName = "Your Retailer";
  let retailerID = "12345";
  let cards = [] as { id: number, title: string }[];

  // Sample data for retailer's cards
  cards = [
    { id: 1, title: "Birthday Card" },
    { id: 2, title: "Anniversary Card" },
    // Add more sample cards as needed
  ];

  function viewCardDetails(card: { id: number, title: string }) {
    // Function to display card details
    // Implement functionality to display the selected card details
  }

  function addCardToCatalog(card: { id: number, title: string }) {
    // Function to add a selected card to the retailer's catalog
    // Implement functionality to add the card to the retailer's catalog
  }

  function publishCardsToCatalog() {
    // Function to publish cards to the retailer's catalog
    // Implement functionality to publish cards to the catalog
  }

  function viewCardwithGiftsCatalog() {
    // Function to view CardwithGifts Catalog
    // Implement functionality to view the CardwithGifts Catalog
  }
</script>

<div class="container">


  <main class="row">
    <nav class="three columns" style="padding: 20px;">
      <h4>Catalog Management</h4>
      <ul>
        <li>Create Catalog</li>
        <li>Search</li>
        <li>View Catalog</li>
        <li on:click={publishCardsToCatalog}>Publish Cards to Catalog</li>
      </ul>
    </nav>

    <div class="nine columns" style="padding: 20px;">
      <section>
        <h2>Retailer Catalog List</h2>
        <ul class="card-list">
          {#each cards as card}
            <li role="button" on:click={() => viewCardDetails(card)} on:keydown={(event) => event.key === 'Enter' && viewCardDetails(card)} tabindex="0">
              {card.title}
            </li>
          {/each}
        </ul>
      </section>

      <section class="card-preview">
        <!-- Thumbnails for card preview -->
        <!-- Consider a grid or layout for card preview thumbnails -->
      </section>

      <div class="button-group" style="margin-top: 20px;">
        <button class="button-primary" on:click={viewCardwithGiftsCatalog}>View CardwithGifts Catalog</button>
        <button class="button-primary" on:click={viewCardwithGiftsCatalog}>View Catalog</button>
        <button class="button-primary" on:click={publishCardsToCatalog}>Publish Cards to Catalog</button>
      </div>
    </div>
  </main>
</div>
