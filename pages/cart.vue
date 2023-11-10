<script lang="ts" setup>
	const productList: Product[] = [];
	const cart = useState('cart', () => productList);
    console.log(cart);
</script>

<template>
	<div class="container">
		<div class="d-flex flex-column align-items-center justify-content-center">
			<div
				class="container-fluid py-.25 bg-secondary d-flex justify-content-center">
				<h2>Cart</h2>
			</div>
			<div class="d-flex justify-content-center align-items-center border-0">
				<BButton
					variant="primary"
					@click="cart.pop()"
					href="#"
					style="height: 100%; width: 100%">
					Pop element
				</BButton>
				<BListGroup
					style="flex-wrap: wrap"
					horizontal>
					<BListGroupItem
						v-for="product in cart"
						:key="(product as Product).id"
						class="d-flex justify-content-center align-items-center border-0">
						<CartCard :product="product" />
					</BListGroupItem>
				</BListGroup>
			</div>
		</div>
	</div>
</template>
