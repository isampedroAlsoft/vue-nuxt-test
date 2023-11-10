<script lang="ts" setup>
	const route = useRoute();
	const { id } = route.params;
	let product: Product;
	let pendingRequest = true;
	if (/^\d+$/.test(id as string)) {
		const { data, pending } = (await useLazyFetch(
			`https://fakestoreapi.com/products/${id}`,
		)) as unknown as { data: Product; pending: boolean };
		product = data;
		pendingRequest = pending;
	}
</script>

<template class="container">
	<div
		class="d-flex flex-column align-items-center justify-content-center"
		v-if="/^\d+$/.test(id as string)">
		<div
			v-if="pendingRequest"
			class="d-flex justify-content-center align-items-center border-0">
			<BSpinner style="height: 10rem; width: 10rem" />
		</div>
		<div v-else>
			<div
				class="container-fluid py-.25 bg-secondary d-flex justify-content-center">
				<h2>Product: {{ product.title }}</h2>
			</div>
			<BCard
				:img-src="product.image"
				:img-alt="product.title"
				img-top
				tag="article">
				<BButton
					variant="primary"
					href="#"
					style="height: 100%; width: 100%">
					Buy for ${{ product.price }}
				</BButton>
			</BCard>
		</div>
	</div>
</template>
