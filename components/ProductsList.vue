<script lang="ts" setup>
	const {
		data: products,
		pending,
		refresh,
		error,
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
			<BCard
				:header="(product as Product).title"
				:img-src="(product as Product).image"
				img-width="75rem"
				img-height="175rem"
				:img-alt="(product as Product).title"
				img-top
				tag="article"
				style="width: 15rem">
				<BButton
					variant="primary"
					href="#"
					style="height: 100%; width: 100%">
					Buy for ${{ (product as Product).price }}
				</BButton>
			</BCard>
		</BListGroupItem>
	</BListGroup>
</template>
