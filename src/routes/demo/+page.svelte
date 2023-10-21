<script>
  import JSZip from 'jszip';

  let selectedImages = [];
  let zip = new JSZip();

  const handleImageSelect = (event) => {
    const files = event.target.files;
    for (let i = 0; i < files.length; i++) {
      selectedImages.push(files[i]);
    }
  };

  const createAndDownloadZipFile = async () => {
    for (let i = 0; i < selectedImages.length; i++) {
      const file = selectedImages[i];
      const img = new Image();
      img.src = URL.createObjectURL(file);

      const scaleFactor = resizePercentage / 100;
      const canvas = document.createElement('canvas');
      canvas.width = img.width * scaleFactor;
      canvas.height = img.height * scaleFactor;
      const ctx = canvas.getContext('2d');
      ctx.drawImage(img, 0, 0, canvas.width, canvas.height);

      const blob = await new Promise((resolve) => canvas.toBlob(resolve, 'image/jpeg', imageQuality / 100));
      const fileName = `image_${i}.jpeg`;

      zip.file(fileName, blob);
    }

    zip.generateAsync({ type: 'blob' }).then((content) => {
      const url = URL.createObjectURL(content);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'images.zip';
      a.style.display = 'none';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    });
  };
</script>

<input type="file" accept="image/*" multiple on:change={handleImageSelect} />
{#if selectedImages.length > 0}
  <button type="button" on:click={createAndDownloadZipFile}>Download Zip</button>
{/if}
