 <!-- Page2.svelte -->
<script>
    import { onMount } from 'svelte';
    let imagg = document.getElementById("im");

    
     
  
    let imageUrl;
  
    onMount(() => {
     // const { params } = $page;
      imageUrl = params.imageUrl || 'default.jpg'; // Use a default image URL if none is provided
    });
  </script>
  
  <!-- svelte-ignore a11y-img-redundant-alt -->
  <img src={imagg} alt="Image on Page 2" />
  