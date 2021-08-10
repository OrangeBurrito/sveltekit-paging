<script>
	import '../style.css'
	import Pager from "$lib/components/Pager.svelte";
	import { posts } from "$lib/data";

	let selectedPosts = [];

	function onPageSelected(e) {
		const {startIndex, endIndex} = e.detail
		console.log(e.detail)
			selectedPosts = posts.slice(startIndex, endIndex)
	}
</script>

<h1>Page Selector Proof of Concept</h1>

<Pager total={posts.length} limit={4} on:page-selected={onPageSelected}/>

<pre>
	{JSON.stringify(selectedPosts, null, 2)}
</pre>