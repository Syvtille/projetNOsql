<script>
    import { getProducts } from "../utils";

	let name = "";
	let price;
	let quantite;

	const createProducts = async () => {
		try {
			const response = await fetch("http://localhost:3000/products", {
				method: "POST",
				headers: {
					"Content-Type": "application/json",
				},
				body: JSON.stringify({ name, price, quantite }),
			});
		} catch (error) {
			console.error("Error:", error);
		}
	};

	const handleSubmit = async () => {
		await createProducts();
		name = ''
		price = ''
		quantite = ''
		getProducts();
	};
</script>

<form on:submit|preventDefault={async () => await handleSubmit()}>
	<h2>Créer un article de sport :)</h2>
	<div>
		<input bind:value={name} placeholder="Libellé" type="text" />
		<input bind:value={price} placeholder="Prix" type="text" />
		<input bind:value={quantite} placeholder="Quantité" type="text" />
	</div>
	<button type="submit">Valider</button>
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 2rem 0;
		row-gap: 1rem;
	}
	div {
		display: flex;
		flex-direction: column;
		align-items: center;
		row-gap: 1rem;
	}
</style>
