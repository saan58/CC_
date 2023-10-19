<head>
    <title>Multiple Image Upload</title>
    <style>
        /* CSS styles for the button and selected image display */
        #chooseImageButton {
            display: inline-block;
            padding: 10px 20px;
            background-color:  #181717;
            color: #fff;
            border-radius: 5px;
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
            margin-top: 50px;
            padding: 10px 20px;
            background-color:  #181717;
            color: #fff;
            border-radius: 5px;
            cursor: pointer;

        }
    </style>
</head>
<body>
    <!-- Input element for selecting multiple images -->
    <input type="file" id="imageInput" accept="image/*" multiple onchange="displaySelectedImages(this)">
    <!-- Button to trigger image selection -->
    <label id="chooseImageButton" for="imageInput">Choose Images</label>
    <!-- Display the selected images -->
    <div id="selectedImages"></div>
    <!-- Next button -->
    <button id="nextButton" onclick="nextImage()">Next</button>
    <script>

// let imageInput; 
           
 
 

        let currentImageIndex = 0;
    // To track the currently displayed image index
        // Function to display the selected images
        function displaySelectedImages(input) {
            const selectedImagesContainer = document.getElementById('selectedImages');
            selectedImagesContainer.innerHTML = ''; // Clear previous selections
            if (input.files && input.files.length > 0) {
                for (let i = 0; i < input.files.length; i++) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const img = document.createElement('img');
                        img.src = e.target.result;
                        img.classList.add('selected-image');
                        selectedImagesContainer.appendChild(img);
                    };
                    reader.readAsDataURL(input.files[i]);
                }
                // Show the "Next" button when images are selected
                document.getElementById('nextButton').style.display = 'block';
            }
        }
        // Function to display the next image
        function nextImage() {
          //  window.open("http://localhost:5173/width");
            const images = document.querySelectorAll('.selected-image');
            if (currentImageIndex < images.length - 1) {
                images[currentImageIndex].style.display = 'none';
                const currentImageDataURL = images[currentImageIndex].src;
                currentImageIndex++;
                images[currentImageIndex].style.display = 'block';

                localStorage.setItem("key", imageInput);
        
        // Construct the URL for the next page with the image data as a query parameter
       // const nextPageURL = "http://localhost:5173/width?image=" + encodeURIComponent(currentImageDataURL);
        const nextPageURL = "http://localhost:5173/width";
        // Open the next page in a new window
        window.open(nextPageURL);
                 
            }
        }
    </script>
</body>