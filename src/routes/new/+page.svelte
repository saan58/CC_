<script>
    let selectedImages = [];
    // Function to handle image selection
    function displaySelectedImages(event) {
      const files = event.target.files;
      if (files && files.length > 0) {
        for (let i = 0; i < files.length; i++) {
          const reader = new FileReader();
          reader.onload = function(e) {
            selectedImages = [...selectedImages, e.target.result];
          };
          reader.readAsDataURL(files[i]);
        }
      }
    }
    // Function to navigate to the Bulk Resize Images page
    function navigateToBulkResize() {
      $session.selectedImages = selectedImages;
      $page.goto('/bulk-resize');
    }
  </script>
  <main>
    <input type="file" accept="image/*" multiple on:change={displaySelectedImages} />
    <div>
      {#each selectedImages as image (image)}
        <img src={image} alt="Selected Image" />
      {/each}
    </div>
    <button on:click={navigateToBulkResize}>Next</button>
  </main>