<script>
	import { CarouselTransition, Button, Modal } from 'flowbite-svelte';
	import { Squares2x2 } from 'svelte-heros-v2';

	export let images = [
		{
			image_url: '1',
			tags: ''
		}
	];
	const imgPositionClass =
		'aspect-video object-cover w-full h-full object-bottom hover:brightness-75 transition-all ease-in';
	const visibleImages = [...images].slice(0, 5);
	const carouselImages = images.map((i, idx) => {
		return { id: idx, name: 'image', imgurl: i.image_url, attribution: 'view' };
	});
	$: isModal = false;
</script>

<div class="rounded-md overflow-hidden mb-4">
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div class="hidden sm:block relative cursor-pointer" on:click={() => (isModal = true)}>
		<div class="grid grid-rows-2 grid-cols-4 grid-flow-col gap-1 ">
			<img
				src={visibleImages[0].image_url}
				alt="view"
				class="row-span-2 col-span-2 {imgPositionClass}"
			/>
			<img
				src={visibleImages[1].image_url}
				alt="view"
				class="row-span-1 col-span-1 {imgPositionClass}	"
			/>
			<img
				src={visibleImages[2].image_url}
				alt="view"
				class="row-span-1 col-span-1 {imgPositionClass}"
			/>
			<img
				src={visibleImages[3].image_url}
				alt="view"
				class="row-span-1 col-span-1 {imgPositionClass}	"
			/>
			<img
				src={visibleImages[4].image_url}
				alt="view"
				class="row-span-1 col-span-1 {imgPositionClass}	"
			/>
		</div>
		<Button outline color="light" size="xs" class="absolute bottom-3 right-3 flex"
			><Squares2x2 size="15" class="mr-2" /> <span class="text-md">Show all photos</span></Button
		>
	</div>
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div class="sm:hidden block relative">
		<CarouselTransition
			images={carouselImages}
			transitionType="fly"
			transitionParams={{ delay: 250, duration: 300 }}
			showCaptions={false}
			showThumbs={false}
			showIndicators
		/>
		<div class="absolute top-0 left-[10%] w-[80%] h-[85%]"on:click|capture={() => (isModal = true)}/>
	</div>
</div>

<Modal size="xl" autoclose bind:open={isModal} class="w-full">
	<div class="w-[90%] mx-auto py-[40px]">
		{#each images as image}
			<img src={image.image_url} alt="view" class="w-full mb-3" />
		{/each}
	</div>
</Modal>
