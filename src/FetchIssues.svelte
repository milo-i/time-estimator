<script>
	import IssueCards from "./issueCards.svelte"
	const fetchIssues = (async () => {
		const response = await fetch('https://api.github.com/repos/milo-i/time-estimator/issues');
    return await response.json()
	})()
</script>

{#await fetchIssues}
	<p>...loading</p>
{:then data}
	<div class="issueWrapper">
	<div class="issueCards">
	{#each data as issue}
        {#if issue.assignees.length > 0}
			<IssueCards title={issue.title} assignee={issue.assignees[0].login} description={issue.body} id={issue.number} />
        {/if}
    {/each}
	</div>
	</div>
{:catch error}
	<p>An error occurred!</p>
{/await}

<style>
.issueCards {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    row-gap: 40px;
	justify-items: center;
}


</style>