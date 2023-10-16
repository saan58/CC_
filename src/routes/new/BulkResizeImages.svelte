<script>
    import { session } from '@sveltejs/kit';
    let selectedImages = $session.selectedImages;
  </script>
  <main>
    <h2>Bulk Resize Images</h2>
    <div class="drop_image">
      <p>Drop images here</p>
      <section>
        {#each selectedImages as image (image)}
          <img src={image} alt="Selected Image" />
        {/each}
      </section>
    </div>
  </main>