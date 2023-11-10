<script lang="ts" setup>
	const props = defineProps({
		product: {
			type: Object as () => Product,
			required: true,
		},
	});
	const product: Product = props.product;
</script>

<template>
	<BCard
		:header="product.title"
		:img-src="product.image"
		img-width="75rem"
		img-height="175rem"
		:img-alt="product.title"
		img-top
		tag="article"
		style="width: 15rem">
		<BButton
			variant="primary"
			href="#" 
			style="height: 100%; width: 100%">
			Buy for ${{ product.price }}
		</BButton>
	</BCard>
</template>
