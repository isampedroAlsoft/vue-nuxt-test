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
		:img-alt="product.title"
		img-top
		tag="article"
		style="width: 15rem">
	</BCard>
</template>
