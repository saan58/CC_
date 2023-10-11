<!-- <script>
    let selectedImages = [];
  
    const handleFileChange = (event) => {
      const files = event.target.files;
      for (let i = 0; i < files.length; i++) {
        selectedImages.push(URL.createObjectURL(files[i]));
      }
    };
   
  </script>
  
  <div>
    <input type="file" accept="image/*" multiple on:change={handleFileChange} />
    <div>
      {#each selectedImages as image, index (image)}
        <img src={image} alt={`Image ${index + 1}`} />
      {/each}
    </div>
  </div>

  -->
 

  <!-- <script>
    function openFileDialog() {
      const input = document.createElement("input");
      input.type = "file";
      input.click();
  
      input.addEventListener("change", (event) => {
        const selectedFile = event.target.files[0];
        // You can now work with the selected file
        console.log("Selected file: ", selectedFile);
      });
    }
  </script>
  
  <button on:click={openFileDialog}>Choose File</button> -->
  
  <body> 

  <script>
    let currentImageIndex=0; // To track the currently displayed image index

    // Function to display the selected images
    function displaySelectedImages(input){
        const selectedImagesContainer=document.getElementById('selectedImages');
        selectedImagesContainer.innerHTML=''; // Clear previous selections

        if (input.files && input.files.length > 0) {
            for (let i = 0; i < input.files.length; i++) {
                const reader=new FileReader();
                reader.onload=function(e) {
                    const img=document.createElement('img');
                    img.src=e.target.result;
                    img.classList.add('selected-image');
                    selectedImagesContainer.appendChild(img);
                };
                reader.readAsDataURL(input.files[i]);
            }
            // Show the "Next" button when images are selected
            document.getElementById('nextButton').style.display='block';
        }
    }

    // Function to display the next image
    function nextImage() {
        const images=document.querySelectorAll('.selected-image');
        if (currentImageIndex < images.length-1) {
            images[currentImageIndex].style.display='none';
            currentImageIndex++;
            images[currentImageIndex].style.display='block';
        }
    }
</script>
 


  <!-- Input element for selecting multiple images -->
  <input type="file"  id="imageInput" accept="image/*" multipleonchange="displaySelectedImages(this)">
    
  <!-- Button to trigger image selection -->
  <label id="chooseImageButton" for="imageInput">Choose Images</label>

  <!-- Display the selected images -->
  <div id="selectedImages"></div>

  <!-- Next button -->
  <button id="nextButton" onclick="nextImage()">Next</button>

</body>

<head> 
 
  <style>
 
    /* CSS styles for the button and selected image display */
    #chooseImageButton {
        display: inline-block;
        padding: 10px 20px;
        background-color: #007bff;
        color: #fff;
        cursor: pointer;
    }

    #imageInput {
        display: none;
    }

    #selectedImages {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
    }

    .selected-image {
        max-width: 100px;
        max-height: 100px;
    }

    #nextButton {
        display: none;
        margin-top: 10px;
        padding: 10px 20px;
        background-color: #007bff;
        color: #fff;
        cursor: pointer;
    }

   
   
   
</style>
</head>