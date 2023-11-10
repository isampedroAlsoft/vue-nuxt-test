<template class="container">
	<div>
		<BNavbar
			variant="info"
			toggleable="lg">
			<BNavbarBrand href="/">Product Store</BNavbarBrand>
			<BNavbarToggle target="nav-collapse" />
			<BCollapse
				id="nav-collapse"
				is-nav>
				<BNavbarNav>
					<BNavItem href="/">Home</BNavItem>
					<BNavItem
						href="/cart"
						>Cart</BNavItem
					>
				</BNavbarNav>
				<!-- Right aligned nav items -->
				<BNavbarNav class="ms-auto mb-2 mb-lg-0">
					<BNavItemDropdown right>
						<!-- Using 'button-content' slot -->
						<template #button-content>
							<em>Ignacio</em>
						</template>
						<BDropdownItem href="#">Profile</BDropdownItem>
						<BDropdownItem href="#">Sign Out</BDropdownItem>
					</BNavItemDropdown>
				</BNavbarNav>
				<BNavForm class="d-flex">
					<BFormInput
						class="me-2"
						placeholder="Search" />
					<BButton
						type="submit"
						variant="outline-success"
						>Search</BButton
					>
				</BNavForm>
			</BCollapse>
		</BNavbar>
	</div>
</template>
