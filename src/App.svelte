<script>
 import Product from "./Product.svelte";
 import Button from "./Button.svelte";

 let title = "";
 let price = 0;
 let description = "";

 let products = [];
 let cartItems = [];

 function setTitle(event) {
	title = event.target.value;
 }

function createProduct() {
	const newProduct = {
	title: title,
	price: price,
	description: description
};

  products = products.concat(newProduct)
};

</script>

<style>
 section {
 		width: 30rem;
		margin: auto;
 }
 label,
 input,
 textarea {
 	width: 100%;
 }
</style>


<section>
<div>
	<label for="title">title</label>
	<input type="text" id="title" value="{title}" on:blur ="{setTitle}" />
</div>
<div>
	<label for="price">Price</label>
	<input type="number" id="price" bind:value=  "{price}" />
</div>
<div>
	<label for="description">Desc</label>
	<textarea rows="3" id="description" bind:value="{description}" />
</div>

<Button on:click{createProduct}>Create Product</Button>

</section>

{#if products.length === 0}
	<p>No products added yet</p>
	{:else}
	{#each products as product}
<Product
	productTitle={product.title}
	productPrice={product.price}
	productDescription={product.description} />
	{/each}
{/if}
