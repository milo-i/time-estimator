<script>
	import FetchIssues from './FetchIssues.svelte';
	let name = 'smaristeinar';
	let activeMember;

	function reloadCards() {
        console.log("the name has been changed");
        let chooseMember =  document.querySelector('#members');
        activeMember = chooseMember.value;
        console.log(activeMember)
        //localStorage.setItem("Active Member", activeMember)
        
    }
	

</script>

<main>
	<h1>Hello Team</h1>
	<p>List of team members</p>

	<label for="members">Choose a member:</label>

	<select on:change={reloadCards} name="members" id="members">
		<option value=""></option>
		<option value="smaristeinar">Smari</option>
		<option value="anton">Anton</option>
		<option value="emelie">Emelie</option>
		<option value="igor">Igor</option>
		<option value="jin">Jin</option>
	</select>

	<FetchIssues {name} activeMember = {activeMember} />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
