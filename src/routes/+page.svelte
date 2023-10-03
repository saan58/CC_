 

<script>
 
 

</script>

<!-- <BackgroundImage/> -->

<div class="background-container">
    <!-- Your content goes here -->
    <slot> 
        </slot>
</div>
  
<center>
    <div class="coun">
        <center>
            <h2>Bulk Resize Images</h2>
        </center>
    </div>
    <br /><br />
    <br /><br />
    <br /><br />
    <div class="b">
        <p>Drop images here <br /> or</p>
        <button type="button" class="bn" on:click={print}>Choose Images</button>
    </div>
</center>


    <div class="horizontal">
          
        <div> Super-fast</div>
       
        <div>100% free</div>
       
        <div> Batch processing</div>
        <div> Works in your web browser</div>
        
    </div>



    <div class="horizontal1">
        <div>Easy to use</div>
        <div>No sign-up</div>
        <div>Private — no uploading</div>
        <div>Compress Images</div>
         
    </div>


    <div class="horizontal2">
       
        <div>Reduce file size of images</div>
    </div>
 

<style>
    .coun {
        /* border: 2px solid red; */
        height: 40opx;
        width: 400px;
      
        display: flex;
        justify-content: center;
        align-items: center;
        align-content: flex-end;
        background-color:#AEBDCA;
       border-radius: 8px;
        /* box-shadow: 0px 20px 50px grey  ; */
        box-shadow: 0 8px 6px -6px rgb(36, 35, 35);
        /* object-fit: ; */
    }
    h2 {
        font-size: 30px;
    }
    .b {
        height: 200px;
        width: 1200px;
        background-color:#AEBDCA;
        border-radius: 8px;
        box-shadow: 0 8px 6px -6px rgb(36, 35, 35);
        align-content: flex-end;
        justify-content: center;
        align-items: center;
        font-size: 28px;
        padding-top: 1%;
        
    }
    .bn {
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

    .horizontal div {
        display: inline-block;
        padding-top: 7%;
        padding-left: 12%;
         
        
    }
    .horizontal1 div {
        display: inline-block;
        padding-top: 3%;

        padding-left: 12%;
        
    }
    .horizontal2 div {
        display: inline-block;
        padding-top: 3%;

        padding-left: 12%;
       
    }


    .background-container {
      width: 100%;
      height: 100%;
     
      background-size: cover;
    
    
      position: absolute;
    
      background-color:#AEBDCA;
    background-repeat: no-repeat;
    background-attachment: fixed;
   opacity: 40%;
   /* text-align: start; */
       
    }

    img{
        width: 7%;
        
        color: black;
    }
    

</style>
