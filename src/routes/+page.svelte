<script>
  // import Counter from './Counter.svelte';
  let activeDiv = "div1";
  let selectedImage;
  let file;
  let imageSelected = true;
  let selectedFormat = "jpeg";
  let resizedImage;
  let resizePercentage = 50;
  let imageQuality = 70;
  let isvlue = false;
  let resizeWidth = 500;
  let resizeHeight = 500;
  let resizeLongSide = 500;
  let resizeDimensionsWidth = 500;
  let resizeDimensionsHeight = 500;
  let state1 = false;
  let isDownload = false;
  const formats = ["jpeg", "png", "webp"];

  //====================
  function handleChange(event) {
    selectedFormat = event.target.value;
  }

  //===========choose image function==========
  const handleImageSelect = (event) => {
    imageSelected = false;
    isvlue = true;

    file = event.target.files[0];
    selectedImage = URL.createObjectURL(file);
  };

  //======= Function to switch the active div================
  function switchDiv(divId) {
    activeDiv = divId;
  }
  //=========== percenta Function logic =========

  const percentaFunction = async () => {
    isDownload = true;
    if (file) {
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
          const resizedImage = canvas.toDataURL(
            "image/jpeg",
            imageQuality / 100
          );
          selectedImage = resizedImage;
        };
      };
      reader.readAsDataURL(file);
    }

    //console.log(selectedImage);
    // Send selectedImage to the backend for resizing
    // Receive the resized image URL from the backend
    // Set resizedImage to the URL of the resized image
  };

  //=========== Image Dimensions function =========

  const imageDimFunctioin = async () => {
    isDownload = true;

    if (file) {
      console.log("file res");
      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          console.log(img.width);
          console.log(img.height);

          console.log(resizeDimensionsWidth);
          const scaleFactor = resizeDimensionsWidth / img.width;
          console.log(scaleFactor);
          const canvas = document.createElement("canvas");
          canvas.width = resizeDimensionsWidth;
          canvas.height = resizeDimensionsHeight;

        
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
         
          const resizedImage = canvas.toDataURL(
            "image/jpeg",
            imageQuality / 100
          );
       
          selectedImage = resizedImage;
        };
      };
      reader.readAsDataURL(file);
    }

    //console.log(selectedImage);
    // Send selectedImage to the backend for resizing
    // Receive the resized image URL from the backend
    // Set resizedImage to the URL of the resized image
  };

  //============Width functjion =============

  const widthFunction = async () => {
    isDownload = true;

    if (file) {
    
      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          const scaleFactor = resizeWidth / img.width;
          const canvas = document.createElement("canvas");
          canvas.width = resizeWidth;
          canvas.height = img.height * scaleFactor;
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
          
          const resizedImage = canvas.toDataURL(
            "image/jpeg",
            imageQuality / 100
          );
         
          selectedImage = resizedImage;
        };
      };
      reader.readAsDataURL(file);
    }

    //console.log(selectedImage);
    // Send selectedImage to the backend for resizing
    // Receive the resized image URL from the backend
    // Set resizedImage to the URL of the resized image
  };

  //================Height Function=============

  const heightFunction = async () => {
    isDownload = true;

    if (file) {
      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          const scaleFactor = resizeHeight / img.height;
          const canvas = document.createElement("canvas");
          canvas.width = img.width * scaleFactor;
          canvas.height = resizeHeight;
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
          const resizedImage = canvas.toDataURL(
            "image/jpeg",
            imageQuality / 100
          );

          selectedImage = resizedImage;
        };
      };
      reader.readAsDataURL(file);
    }

    //console.log(selectedImage);
    // Send selectedImage to the backend for resizing
    // Receive the resized image URL from the backend
    // Set resizedImage to the URL of the resized image
  };

  // ===========longest Side function ===========
  const longSideFunction = async () => {
    isDownload = true;

    if (file) {
      const reader = new FileReader();
      reader.onload = () => {
        const img = new Image();
        img.src = reader.result;
        img.onload = () => {
          const scaleFactorW = resizeLongSide / img.width;
          const scaleFactorH = resizeLongSide / img.height;
          const canvas = document.createElement("canvas");

          if (img.width > img.height) {
            canvas.width = resizeLongSide;
            canvas.height = scaleFactorW * img.height;
          } else {
            canvas.height = resizeLongSide;
            canvas.width = scaleFactorH * img.width;
          }

          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
          const resizedImage = canvas.toDataURL(
            "image/jpeg",
            imageQuality / 100
          );

          selectedImage = resizedImage;
        };
      };
      reader.readAsDataURL(file);
    }

    //console.log(selectedImage);
    // Send selectedImage to the backend for resizing
    // Receive the resized image URL from the backend
    // Set resizedImage to the URL of the resized image
  };

  const downloadImage = () => {
    isDownload = false;
    const a = document.createElement("a");
    a.href = selectedImage;
    a.download = "resized_image." + selectedFormat; // You can customize the filename here
    a.style.display = "none";

    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  };

  const deltetImage = ()=>{
    imageSelected = true;
    isvlue = false;
  };

</script>

{#if imageSelected}
  <div>
    <!-- for Heading container Box  -->
    <center>
      <div class="Heading_container">
        <center>
          <h2>Bulk Resize Images</h2>
        </center>
      </div>

      <!-- for get a padding  -->
      <br /><br />
      <br /><br />
      <br /><br />

      <!-- Drop image here or image choose  -->
      <div class="drop_image">
        <p>Drop images here <br /> or</p>

        <div>
          <input
            class="inputValue"
            type="file"
          
            accept="image/*"
            on:change={handleImageSelect}
          />
        </div>

        <!-- <section>
                  
                 <Counter/>
             </section> -->
      </div>
    </center>
  </div>
{/if}

{#if isvlue}
  <!-- for Heading container Box  -->
  <center>
    <div class="Heading_container">
      <center>
        <h2>Bulk Resize Images</h2>
      </center>
    </div>
  </center>

  <div class="row">
    <div class="column">
      <!-- Navigation bar for controlling all page  -->
      <nav>
        <ul>
          <button class="Choose_file" on:click={() => switchDiv("div1")}
            >Percentage</button
          ><br />
          <button class="Choose_file" on:click={() => switchDiv("div2")}
            >File Size</button
          ><br />
          <button class="Choose_file" on:click={() => switchDiv("div3")}
            >Image Dimensions</button
          ><br />
          <button class="Choose_file" on:click={() => switchDiv("div4")}
            >Width</button
          ><br />
          <button class="Choose_file" on:click={() => switchDiv("div5")}>
            Height</button
          ><br />
          <button class="Choose_file" on:click={() => switchDiv("div6")}
            >Longest Side</button
          >
          <div class="row">
            <div class="column2">
              <button class="Choose_file1" on:click={() => deltetImage()}
                >Back</button>
            </div>
            <div class="column2">
              <button class="Choose_file1" on:click={() => deltetImage()}
                >Delete</button>
            </div>
          </div>
        </ul>
      </nav>
    </div>

    {#if activeDiv == "div1"}
      <div id="div1">
        <!-- Name of page  -->
        <h1 class="percentage"><u>Percentage</u></h1>

        <div class="column1">
          <p class="p1">
            Scale images to <input
              class="input1"
              type="number"
              bind:value={resizePercentage}
              min="1"
              max="100"
            /> % of the original dimensions.
          </p>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <select
                class="select"
                bind:value={selectedFormat}
                on:change={handleChange}
              >
                {#each formats as format}
                  <option value={format}>{format}</option>
                {/each}
              </select>
            </div>

            {#if selectedFormat !== "png"}
              <div>
                <p class="p3">Image Quality</p>
                <div class="slidecontainer">
                  <input
                    class="slider"
                    type="range"
                    bind:value={imageQuality}
                    min="1"
                    max="100"
                    step="1"
                  />
                  <span>{imageQuality}%</span>
                </div>
              </div>
            {/if}
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>

          {#if selectedImage}
            <center>
              <!-- <img   src={selectedImage} alt="Selected Image" /> -->
              <button type="button" class="bn" on:click={percentaFunction}
                >Start</button
              >
            </center>
          {/if}

          {#if isDownload}
            <center>
              <a href={resizedImage} download="resized_image.jpg">
                <button type="button" class="bn" on:click={downloadImage}
                  >Download</button
                >
              </a>
            </center>
          {/if}
        </div>
      </div>
    {/if}

    {#if activeDiv == "div2"}
      <div id="div2">
        <h1 class="percentage"><u>File Size</u></h1>

        <div class="column1">
          <p class="p4">Images will be resized to 97.7 kB or less.</p>

          <div class="slidecontainerfilesize">
            <input
              type="range"
              min="1"
              max="100"
              value="50"
              class="slider"
              id="myRange"
            />
            <p>Value: <span id="demo" /></p>
          </div>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <!-- select image formate  -->
              <form>
                <select class="select">
                  <option value="JPEG">JPEG</option>
                  <option value="PNG">PNG</option>
                  <option value="WEBP">WEBP</option>
                </select>
              </form>
            </div>
            <div>
              <p class="p3">Image Quality</p>

              <div class="slidecontainer">
                <input
                  type="range"
                  min="1"
                  max="100"
                  value="50"
                  class="slider"
                  id="myRange"
                />
                <p>Value: <span id="demo" /></p>
              </div>
            </div>
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>
        </div>
      </div>
    {/if}

    {#if activeDiv == "div3"}
      <div id="div3">
        <h1 class="percentage"><u> Image Dimensions</u></h1>

        <div class="column1">
          <p class="p1">
            Make images <input
              class="input1"
              type="number"
              bind:value={resizeDimensionsWidth}
              min="1"
            />
            x
            <input
              class="input1"
              type="number"
              bind:value={resizeDimensionsHeight}
              min="1"
            /> (Width × Height)
          </p>

          <label style="margin-left: 50px ; font-size: 21px;">
            <input type="checkbox" bind:checked={state1} />
            Use padding to avoid stretching or squashing images.
          </label>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <select
                class="select"
                bind:value={selectedFormat}
                on:change={handleChange}
              >
                {#each formats as format}
                  <option value={format}>{format}</option>
                {/each}
              </select>
            </div>
            {#if selectedFormat !== "png"}
              <div>
                <p class="p3">Image Quality</p>
                <div class="slidecontainer">
                  <input
                    class="slider"
                    type="range"
                    bind:value={imageQuality}
                    min="1"
                    max="100"
                    step="1"
                  />
                  <span>{imageQuality}%</span>
                </div>
              </div>
            {/if}
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>

          {#if selectedImage}
            <center>
              <!-- <img   src={selectedImage} alt="Selected Image" /> -->
              <button type="button" class="bn" on:click={imageDimFunctioin}
                >Start</button
              >
            </center>
          {/if}

          {#if isDownload}
            <center>
              <a href={resizedImage} download="resized_image.jpg">
                <button type="button" class="bn" on:click={downloadImage}
                  >Download</button
                >
              </a>
            </center>
          {/if}
        </div>
      </div>
    {/if}

    {#if activeDiv == "div4"}
      <div id="div4">
        <h1 class="percentage"><u>Width</u></h1>
        <div class="column1">
          <p class="p1">
            Make the width of images <input
              class="input1"
              type="number"
              bind:value={resizeWidth}
              min="1"
            /> pixels.
          </p>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <select
                class="select"
                bind:value={selectedFormat}
                on:change={handleChange}
              >
                {#each formats as format}
                  <option value={format}>{format}</option>
                {/each}
              </select>
            </div>
            {#if selectedFormat !== "png"}
              <div>
                <p class="p3">Image Quality</p>
                <div class="slidecontainer">
                  <input
                    class="slider"
                    type="range"
                    bind:value={imageQuality}
                    min="1"
                    max="100"
                    step="1"
                  />
                  <span>{imageQuality}%</span>
                </div>
              </div>
            {/if}
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>

          {#if selectedImage}
            <center>
              <!-- <img   src={selectedImage} alt="Selected Image" /> -->
              <button type="button" class="bn" on:click={widthFunction}
                >Start</button
              >
            </center>
          {/if}

          {#if isDownload}
            <center>
              <a href={resizedImage} download="resized_image.jpg">
                <button type="button" class="bn" on:click={downloadImage}
                  >Download</button
                >
              </a>
            </center>
          {/if}
        </div>
      </div>
    {/if}

    {#if activeDiv == "div5"}
      <div id="div5">
        <h1 class="percentage"><u>Height</u></h1>

        <div class="column1">
          <p class="p1">
            Make the height of images <input
              class="input1"
              type="number"
              bind:value={resizeHeight}
              min="1"
            /> pixels.
          </p>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <select
                class="select"
                bind:value={selectedFormat}
                on:change={handleChange}
              >
                {#each formats as format}
                  <option value={format}>{format}</option>
                {/each}
              </select>
            </div>
            {#if selectedFormat !== "png"}
              <div>
                <p class="p3">Image Quality</p>
                <div class="slidecontainer">
                  <input
                    class="slider"
                    type="range"
                    bind:value={imageQuality}
                    min="1"
                    max="100"
                    step="1"
                  />
                  <span>{imageQuality}%</span>
                </div>
              </div>
            {/if}
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>

          {#if selectedImage}
            <center>
              <!-- <img   src={selectedImage} alt="Selected Image" /> -->
              <button type="button" class="bn" on:click={heightFunction}
                >Start</button
              >
            </center>
          {/if}

          {#if isDownload}
            <center>
              <a href={resizedImage} download="resized_image.jpg">
                <button type="button" class="bn" on:click={downloadImage}
                  >Download</button
                >
              </a>
            </center>
          {/if}
        </div>
      </div>
    {/if}

    {#if activeDiv == "div6"}
      <div id="div6">
        <h1 class="percentage"><u>Longest Side</u></h1>

        <div class="column1">
          <p class="p1">
            Make the longest side of images <input
              class="input1"
              type="number"
              bind:value={resizeLongSide}
              min="1"
            /> pixels.
          </p>

          <div class="row">
            <div class="column">
              <p class="p2">Image Format</p>
              <select
                class="select"
                bind:value={selectedFormat}
                on:change={handleChange}
              >
                {#each formats as format}
                  <option value={format}>{format}</option>
                {/each}
              </select>
            </div>
            {#if selectedFormat !== "png"}
              <div>
                <p class="p3">Image Quality</p>
                <div class="slidecontainer">
                  <input
                    class="slider"
                    type="range"
                    bind:value={imageQuality}
                    min="1"
                    max="100"
                    step="1"
                  />
                  <span>{imageQuality}%</span>
                </div>
              </div>
            {/if}
          </div>

          <p class="p2">Image Background</p>
          <form style="margin-left: 50px;">
            <input type="color" id="favcolor" name="favcolor" value="#ff0000" />
            <label for="favcolor" style="font-size: 20px;">color</label>
          </form>

          {#if selectedImage}
            <center>
              <!-- <img   src={selectedImage} alt="Selected Image" /> -->
              <button type="button" class="bn" on:click={longSideFunction}
                >Start</button
              >
            </center>
          {/if}

          {#if isDownload}
            <center>
              <a href={resizedImage} download="resized_image.jpg">
                <button type="button" class="bn" on:click={downloadImage}
                  >Download</button
                >
              </a>
            </center>
          {/if}
        </div>
      </div>
    {/if}
  </div>
{/if}

<!-- CSS style section -->

<head>
  <title>File Choose </title>
</head>

<style>
  h1 {
    width: 100%;
  }

  /* heading Style */
  .Heading_container {
    /* border: 2px solid red; */
    height: 40opx;
    width: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: flex-end;
    background-color: #aebdca;
    border-radius: 8px;

    /* box-shadow: 0px 20px 50px grey  ; */
    box-shadow: 0 8px 6px -6px rgb(36, 35, 35);
    /* object-fit: ; */
  }
  h2 {
    font-size: 30px;
  }

  /* drop image container style */
  .drop_image {
    pointer-events: auto;
    height: 300px;
    width: 1200px;
    background-color: #aebdca;
    border-radius: 8px;
    box-shadow: 0 8px 6px -6px rgb(36, 35, 35);
    align-content: flex-end;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    padding-top: 1%;
  }

  /* choose button style */
  .inputValue {
    height: 20%;
    width: 20%;
    font-size: medium;
    color: white;
    font-weight: 700;

    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 15px;
    gap: 15px;
    background-color: #181717;
    outline: 3px #181717 solid;
    outline-offset: -3px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    transition: 400ms;
  }

  .bn {
    height: 20%;
    width: 80%;
    font-size: 20px;
    color: white;
    font-weight: 700;
    margin-top: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 15px;
    gap: 15px;
    background-color: #181717;
    outline: 3px #181717 solid;
    outline-offset: -3px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    transition: 400ms;
  }

  .slidecontainer {
    padding-left: 70px;
    width: 100%;
  }

  .slider {
    width: 100%;
    height: 10px;
    border-radius: 5px;
    background: #d3d3d3;
    outline: none;
    opacity: 0.7;
    -webkit-transition: 0.2s;
    transition: opacity 0.2s;
  }

  .slider:hover {
    opacity: 1;
  }

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 23px;
    height: 24px;
    border: 0;
    background: url("contrasticon.png");
    cursor: pointer;
  }

  .slider::-moz-range-thumb {
    width: 23px;
    height: 24px;
    border: 0;
    background: url("contrasticon.png");
    cursor: pointer;
  }

  .select {
    height: 40px;
    width: 300px;
    margin-left: 50px;
    font-size: 20px;
    border-radius: 5px;
  }

  .p2 {
    font-size: 30px;
    margin-left: 50px;
  }
  .p3 {
    font-size: 30px;
    padding-left: 70px;
  }

  .input1 {
    height: 23px;
    width: 50px;
    border-radius: 5px;
  }

  .p1 {
    font-size: 30px;
    margin-left: 50px;
  }

  .row {
    display: flex;
  }

  /* Create two equal columns that sits next to each other */
  .column {
    font-size: 0;
    padding: 10px;
    height: 100px; /* Should be removed. Only for demonstration */
  }

  .column1 {
    flex: 50%;
    padding: 10px;
    padding-left: 100px;
    height: 400px; /* Should be removed. Only for demonstration */
  }

  .column2 {
    flex: 50%;
    padding: 3px;
    height: 400px; /* Should be removed. Only for demonstration */
  }
  /* heading Style */
  .Heading_container {
    /* border: 2px solid red; */
    height: 60px;
    width: 400px;

    display: flex;
    justify-content: center;
    align-items: center;
    align-content: flex-end;
    background-color: #aebdca;
    border-radius: 8px;
    /* box-shadow: 0px 20px 50px grey  ; */
    box-shadow: 0 8px 6px -6px rgb(36, 35, 35);
    /* object-fit: ; */
    font-size: 20px;
  }

  .percentage {
    padding-left: 300px;
  }

  .Choose_file1 {
    height: 50px;
    width: 100px;
    margin-bottom: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* align-content: flex-end; */
    background-color: #d1d7dc;
    border-radius: 8px;
    /* box-shadow: 0px 20px 50px grey  ; */

    /* object-fit: ; */
    font-size: 20px;
  }

  /* Change the link color on hover */
  .Choose_file1 :hover {
    height: 50px;
    width: 100px;
    margin-bottom: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* align-content: flex-end; */
    background-color: #000000;
    border-radius: 8px;
    /* box-shadow: 0px 20px 50px grey  ; */

    /* object-fit: ; */
    font-size: 20px;
  }

  .Choose_file {
    height: 50px;
    width: 200px;
    margin-bottom: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* align-content: flex-end; */
    background-color: #d1d7dc;
    border-radius: 8px;
    /* box-shadow: 0px 20px 50px grey  ; */

    /* object-fit: ; */
    font-size: 20px;
  }

  /* Change the link color on hover */
  .Choose_file :hover {
    height: 50px;
    width: 200px;
    margin-bottom: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* align-content: flex-end; */
    background-color: #000000;
    border-radius: 8px;
    /* box-shadow: 0px 20px 50px grey  ; */

    /* object-fit: ; */
    font-size: 20px;
  }

  ul {
    margin: 0;
    padding: 0;
    margin-top: 90px;
    width: 200px;
  }
</style>
