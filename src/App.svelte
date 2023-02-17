<script>
	import Sneaker from "./components/Sneaker.svelte";
	let sneakers = [
		{
			name: "Fashion Shoe Sneakers",
			price: 20,
			image: "/1.png",
			background: "rgb(211, 211, 211)",

		},
	];

</script>

<div class="body">
	<div class="main">
		<div class="row justify-content-center align-items-center vh-100 vw-100">
			<div class="col-6">
				<div class="row justify-content-center align-items-center w-100 h-100">
					{#each sneakers as sneaker, i}
						<Sneaker sneaker="{sneaker}" />
					{/each}
				</div>
			</div>
		</div>
	</div>
</div>


