<script>
  //java script code
  //var slider = document.getElementById("myRange");
  //var output = document.getElementById("demo");
  //output.innerHTML = slider.value;

  // slider.oninput = function() {
  //   output.innerHTML = this.value;
  // }
</script>

<!-- for Heading container Box  -->
<center>
  <div class="Heading_container">
    <center>
      <h2>Bulk Resize Images</h2>
    </center>
  </div>
</center>
<h1 class="percentage"><u>Longest Side</u></h1>

<div class="row">
  <div class="column">
    <nav>
      <ul>
        <li class="Choose_file"><a href="./home">Percentage</a></li>
        <li class="Choose_file"><a href="./file_size">File Size</a></li>
        <li class="Choose_file"><a href="./image_dim">Image Dimensions</a></li>
        <li class="Choose_file"><a href="./width">Width</a></li>
        <li class="Choose_file"><a href="./height">Height</a></li>
        <li class="Choose_file"><a href="./longest">Longest Side</a></li>
        <div class = "row">
          <div class="column2">
            <li class="Choose_file1"><a href="./longest">Back</a></li>
          </div>
          <div class ="column2">
            <li class="Choose_file1"><a href="./longest">Delete</a></li>

          </div>
        </div>
      </ul>
    </nav>
  </div>
  <div class="column1">
    <p class="p1">
      Make the longest side of images  <input class="input1" /> pixels..
    </p>

    <div class="row">
      <div class="column">
        <p class="p2">Image Format</p>
        <form>
          <select class="select">
            <option value="JPEG">JPEG</option>
            <option value="PNG">PNG</option>
            <option value="WEBP">WEBP</option>
          </select>
        </form>
      </div>
      <div>
        <p class="p3">Image Quali</p>

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

<center>
  <button type="button" class="bn">Start</button>
</center>

<style>
  /* choose button style */
  .bn {
    height: 20%;
    width: 80%;
    font-size: 20px;
    color: white;
    font-weight: 700;
    margin-top: 50px;
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
    padding-left: 200px;
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
  }

  .p2 {
    font-size: 30px;
    margin-left: 50px;
  }
  .p3 {
    font-size: 30px;
    padding-left: 200px;
  }

  .input1 {
    height: 30px;
    width: 40px;
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
    height: 400px; /* Should be removed. Only for demonstration */
  }

  .column2{
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
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 200px;
  }

  li a {
    display: block;
    color: #000;
    padding: 8px 16px;
    text-decoration: none;
  }

  /* Change the link color on hover */
  li a:hover {
    color: white;
  }
</style>
