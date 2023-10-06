<script>
//java script code 
</script>

<!-- for Heading container Box  -->
<center>
    <div class="Heading_container">
        <center>
            <h2>Bulk Resize Images</h2>
        </center>
    </div>
</center>
<h1 class="percentage"><u>Percentage</u> </h1>

 
 <div class="row">
  <div class="column">
    <nav>       
      <ul>
          <li class="Choose_file" ><a href="./home">Percentage</a></li>
          <li class="Choose_file" ><a href="./file_size">File Size</a></li>
          <li class="Choose_file" ><a href="./image_dim">Image Dimensions</a></li>
          <li class="Choose_file"><a href="./width">Width</a></li>
          <li class="Choose_file"><a href="./height">Height</a></li>
          <li class="Choose_file"><a href="./longest">Longest Side</a></li>
        </ul>
       </nav>
    
  </div>
  <div class="column1" style="background-color:#bbb;">
 <p>Scale images to <input> % of the original dimensions.</p>

  </div>
</div>
 

  
 

<style>

 

.row {
  display: flex;
}

/* Create two equal columns that sits next to each other */
.column {
 
  padding: 10px;
  height: 300px; /* Should be removed. Only for demonstration */
}

.column1 {
  flex: 50%;
  padding: 10px;
  height: 550px; /* Should be removed. Only for demonstration */
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

    .percentage{
      padding-left: 300px;
    }

    .Choose_file{
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
    .Choose_file :hover{
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