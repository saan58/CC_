 
<script>
  import { onMount } from 'svelte';

  let imageUrl = '';

  onMount(() => {
    // Get the image URL from the form data
    const urlParams = new URLSearchParams(new URL(window.location.href).search);
    imageUrl = urlParams.get("image");
  });
</script>

<h1>Image on the Next Page</h1>
<!-- <img {src}={imageUrl}> -->
