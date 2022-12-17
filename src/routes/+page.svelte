<script>
	import images from '$lib/data/image_data.json';
	import PicturesViewer from '$lib/Components/PicturesViewer/PicturesViewer.svelte';
</script>

<!-- <h1>This text needs to replaced with a component showing Airbnb style image grid</h1>
<p>
	See <a href="https://www.airbnb.com/rooms/20238974">the link</a> for an example. The ideal component
	will make use of Flowbite-Svelte and Tailwind CSS
</p>
<p>
	The grid should be dynamic and interactive and work for multiple screen sizes similiar to the one
	on Airbnb
</p>
<p>Example images can be found in image_data.json</p> -->

<div class="max-w-[80%] mx-auto">
  {#each images as imagesPack} 
	<PicturesViewer images={imagesPack.images} />
  {/each}
</div>
