<script lang="ts" setup>
	const {
		data: products,
		pending,
	} = await useLazyFetch('https://fakestoreapi.com/products');
</script>

<template class="container">
	<div
		v-if="pending"
		class="d-flex justify-content-center align-items-center border-0">
		<BSpinner style="height: 10rem; width: 10rem" />
	</div>
	<BListGroup
		class="d-flex"
		style="flex-wrap: wrap"
		horizontal>
		<BListGroupItem
			v-for="product in products"
			:key="(product as Product).id"
			class="d-flex justify-content-center align-items-center border-0">
			<ProductsCard :product="product"/>
		</BListGroupItem>
	</BListGroup>
</template>
