<script>
	import IssueCards from './IssueCards.svelte';
	// export let name;
	const fetchIssues = (async () => {
		const response = await fetch(
			'https://api.github.com/repos/milo-i/time-estimator/issues'
		);
		return await response.json();
	})();
</script>

{#await fetchIssues}
	<p>...loading</p>
{:then data}
	{#each data as issue}
		{#if issue.assignees.length > 0}
			<IssueCards
				title={issue.title}
				assignee={issue.assignees[0].login}
				description={issue.body}
				id="{issue.number}}"
			/>
		{/if}
	{/each}
{:catch error}
	<p>An error occurred!</p>
{/await}
