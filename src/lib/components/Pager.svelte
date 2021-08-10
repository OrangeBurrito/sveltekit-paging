<script>
import { createPageSelector } from "$lib/pageSelector";
import { createEventDispatcher, onMount } from "svelte";

	export let total = 0
	export let limit = 0

	const {pageSelector, nextPage, previousPage} = createPageSelector(total, limit)

	const dispatch = createEventDispatcher()

	function dispatchPageSelected() {
		dispatch('page-selected', {
			page: $pageSelector.page,
			startIndex:	($pageSelector.page - 1) * limit,
			endIndex: $pageSelector.startIndex + $pageSelector.limit
		})
	}

	function onPreviousPage() {
		previousPage()
		dispatchPageSelected()
	}
	
	function onNextPage() {
		nextPage()
		dispatchPageSelected()
	}

	onMount(() => dispatchPageSelected())
</script>

<button on:click={onPreviousPage}>Previous</button>
<button on:click={onNextPage}>Next</button>