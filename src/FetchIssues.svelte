	<script>
	import {onMount, afterUpdate} from 'svelte'
	//import IssueCards from './IssueCards.svelte';
	import Smaristeinar from './smaristeinar.svelte';
	import Anton from './Anton.svelte';
	import Emelie from './Emelie.svelte';
	import Igor from './Igor.svelte';

	// export let name;
	const fetchIssues = (async () => {
		const response = await fetch(
			'https://api.github.com/repos/milo-i/time-estimator/issues'
		);
		return await response.json();
	})();

	export let activeMember;
	
	afterUpdate(() => {
	console.log("active member in fetch:", activeMember);
	})

</script>

{#await fetchIssues}
	<p>...loading</p>
{:then data}
	{#each data as issue}
		{#if issue.assignees.length > 0}
		{#if activeMember === "smaristeinar"}
		<Smaristeinar 
		title={issue.title}
		assignee={issue.assignees[0].login}
		description={issue.body}
		id={issue.number}
		activeMember = {activeMember} 
		/>
		{/if}
		{#if activeMember === "anton"}
		<Anton 
		title={issue.title}
		assignee={issue.assignees[0].login}
		description={issue.body}
		id={issue.number}
		activeMember = {activeMember} 
		/>
		{/if}
		{#if activeMember === "emelie"}
		<Emelie
		title={issue.title}
		assignee={issue.assignees[0].login}
		description={issue.body}
		id={issue.number}
		activeMember = {activeMember} 
		/>
		{/if}
		{#if activeMember === "igor"}
		<Igor
		title={issue.title}
		assignee={issue.assignees[0].login}
		description={issue.body}
		id={issue.number}
		activeMember = {activeMember} 
		/>
		{/if}
		{/if}
	{/each}
{:catch error}
	<p>An error occurred!</p>
{/await}
