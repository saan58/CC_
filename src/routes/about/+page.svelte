 <!-- src/routes/ImageResize.svelte -->
<script>
  let selectedImage;
  let resizePercentage = 50;
  let imageQuality = 70;
  async function handleImageUpload(event) {
    const file = event.target.files[0];
    if (file) {
      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          selectedImage = reader.result;
        };
      };
      reader.readAsDataURL(file);
    }
  }
  function downloadResizedImage() {
    const a = document.createElement('a');
    a.href = selectedImage;
    a.download = 'resized_image.jpeg';
    a.style.display = 'none';
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  }
  function resizeImage() {
    if (selectedImage) {
      const img = new Image();
      img.src = selectedImage;
      img.onload = () => {
        const scaleFactor = resizePercentage / 100;
        const canvas = document.createElement('canvas');
        canvas.width = img.width * scaleFactor;
        canvas.height = img.height * scaleFactor;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
        const resizedImage = canvas.toDataURL('image/jpeg', imageQuality / 100);
        selectedImage = resizedImage;
      };
    }
  }
</script>
<main>
  <h1>Image Resize</h1>
  <input type="file" accept="image/*" on:change={handleImageUpload} />
  <div class="input-row">
    <label>
      Resize Percentage:
      <input type="number" bind:value={resizePercentage} min="1" max="100" />
      <span>{resizePercentage}%</span>
    </label>
    <label>
      Image Quality:
      <input type="range" bind:value={imageQuality} min="1" max="100" step="1" />
      <span>{imageQuality}%</span>
    </label>
    <button on:click={resizeImage}>Resize Image</button>
  </div>
  {#if selectedImage}
    <h2>Resized Image</h2>
    <img src={selectedImage} alt="Resized Image" />
    <button on:click={downloadResizedImage}>Download Resized Image</button>
  {/if}
</main>
<style>
  h1 {
    text-align: center;
  }
  input[type="file"] {
    display: block;
  }
  .input-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }
  span {
    font-weight: bold;
  }
  img {
    max-width: 100%;
  }
</style>