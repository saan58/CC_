<script>
  let selectedImages = [];
  let resizedImages = [];
  let resizePercentage = 50;
  let imageQuality = 70;
 
  let selectedFormat = "jpeg";
   

  // Handle image selection and display
  const handleImageSelect = (event) => {
    const files = event.target.files;
    const imageList = document.getElementById("imageList");
    imageList.innerHTML = "";

    for (let i = 0; i < files.length; i++) {
      const file = files[i];
      const imageUrl = URL.createObjectURL(file);

      // // Display the selected images
      // const listItem = document.createElement("li");
      // listItem.textContent = file.name;
      // imageList.appendChild(listItem);

      selectedImages.push({ file, imageUrl });
    }
  };

  // Bulk image resizing function
  const bulkResize = async () => {
   
    const resizedImagesContainer = document.getElementById("resizedImages");
    resizedImagesContainer.innerHTML = "";

    for (let i = 0; i < selectedImages.length; i++) {
      const { file, imageUrl } = selectedImages[i];

      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          const scaleFactor = resizePercentage / 100;
          const canvas = document.createElement("canvas");
          canvas.width = img.width * scaleFactor;
          canvas.height = img.height * scaleFactor;
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
          const resizedImage = canvas.toDataURL(`image/${selectedFormat}`, imageQuality / 100);

          // Store the resized images
          resizedImages.push({ file, resizedImage });

          // Display the resized images and provide download links
          const imgElement = document.createElement("img");
          imgElement.src = resizedImage;
           resizedImagesContainer.appendChild(imgElement);

          const downloadLink = document.createElement("a");
          downloadLink.href = resizedImage;
          downloadLink.download = `resized_image_${i}.${selectedFormat}`;
          downloadLink.textContent = "Downfdggload";
          resizedImagesContainer.appendChild(downloadLink);
        };
      };
      reader.readAsDataURL(file);
    }
  };

  // Rest of your code remains the same
</script>


<!-- Add a file input for multiple image selection -->
<input type="file" accept="image/*" multiple on:change={handleImageSelect} />

<!-- Display the list of selected images -->
<div id="output">
  <h3>Selected Images:</h3>
  <ul id="imageList"></ul>
</div>

<!-- Add a button to start bulk resizing -->
<button type="button" class="bn" on:click={bulkResize}>Bulk Resize</button>

<!-- Display the resized images and provide download links -->
<div id="resizedImages"></div>
