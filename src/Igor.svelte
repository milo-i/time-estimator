<script>
	import {onMount, afterUpdate} from 'svelte'
	

	export let title;
	export let assignee;
	export let description;
	export let id;

	let inputValue;

	function handleClick(buttonid) {
		let arry = [];
		console.log("Issue:", id, "estimated time:", inputValue);
		if (!window.localStorage.getItem(`${id}`) && inputValue) {
			arry.push(inputValue)
			window.localStorage.setItem(`${id}`,JSON.stringify(arry));
		}
		else if(inputValue){
			arry = JSON.parse(localStorage.getItem(`${id}`));
			arry.push(inputValue);
			window.localStorage.setItem(`${id}`,JSON.stringify(arry));
		}
		if (inputValue) {
		document.getElementById(buttonid).classList.add("disable-button");
		}
		//inputValue = "";
	}
	export let activeMember;


</script>

<div>
	<div class="">
		<div class="issueCard">
			<h2 class="title">{title}</h2>
			<h3 class="id">{'Id: ' + id}</h3>
			<h3 class="assignee">{'Assignee: ' + assignee}</h3>
			<div class="description">
				<p>{description}</p>
			</div>
			<div class="inputWrapper">
				<label>
					Estimate hours
					<input bind:value={inputValue} placeholder={activeMember} type="number" pattern="[0-9]" id="inputField" />
				</label>
				<button id="{assignee + id}" on:click={handleClick(assignee + id)}>Save</button>
			</div>
		</div>
	</div>
</div>

<style>
	.issueCards {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		row-gap: 40px;
	}

	.issueCard {
		border: 1px solid black;
		background-color: rgb(243, 167, 154);
		width: 300px;
		height: 350px;
		text-align: left;
		padding-left: 10px;
		box-shadow: 10px 10px rgb(43, 17, 13);
	}

	.title {
		text-decoration: underline;
		margin-bottom: 0px;
	}

	.description {
		padding: 2px;
		background-color: rgb(243, 217, 217);
		width: 280px;
		padding-left: 5px;
		padding-top: 0px;
	}

	.assignee {
		margin-top: 0px;
	}
	.id {
		margin-top: 0px;
		margin-bottom: 0px;
	}
</style>
