<script>
	import { createPageSelector } from "$lib/pageSelector";

	let {pageSelector, nextPage, previousPage} = createPageSelector(25, 4)
</script>

<h1>pageselectorproofofconcept</h1>

<button on:click={previousPage}>Previous</button>
<button on:click={nextPage}>Next</button>

<pre>
	{JSON.stringify($pageSelector, null, 2)}
</pre>