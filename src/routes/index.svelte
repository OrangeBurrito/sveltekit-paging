<script>
import { posts } from "$lib/data";

	import { createPageSelector } from "$lib/pageSelector";

	const {pageSelector, nextPage, previousPage} = createPageSelector(posts.length, 4)

	let selectedPosts = []

	$: {
		selectedPosts = posts.slice($pageSelector.startIndex, $pageSelector.startIndex + $pageSelector.limit)
	}
</script>

<h1>pageselectorproofofconcept</h1>

<button on:click={previousPage}>Previous</button>
<button on:click={nextPage}>Next</button>

<pre>{JSON.stringify($pageSelector, null, 2)}</pre>

<pre>
	{JSON.stringify(selectedPosts, null, 2)}
</pre>