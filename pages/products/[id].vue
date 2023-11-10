<script lang="ts" setup>
	const productList: Product[] = []
	const cart = useState('cart',() => productList);
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
		v-if="/^\d+$/.test(id as string) && !pendingRequest">
		<div
			class="container-fluid py-.25 bg-secondary d-flex justify-content-center">
			<h2>Product: {{ product.title }}</h2>
		</div>
		<BCard
			:img-src="product.image"
			:img-alt="product.title"
			img-top
			style="width: 25em"
			tag="article">
			<BButton
				variant="primary"
				@click="cart.push(product)"
				href="#"
				style="height: 100%; width: 100%">
				${{ product.price }} - Add to carti
			</BButton>
		</BCard>
	</div>
	<div
		v-else
		class="d-flex justify-content-center align-items-center border-0">
		<BSpinner style="height: 10rem; width: 10rem" />
	</div>
</template>
