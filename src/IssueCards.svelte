
<style>

.issueCard {
    border: 1px solid black;
    background-color: rgb(243, 167, 154);
    width:300px;

    text-align: left;
    padding-left: 10px;
    box-shadow: 10px 10px rgb(43, 17, 13);

}

.title {
    text-decoration: underline;
    margin-bottom: 0px;
}

.description {
    padding:2px;
    background-color: rgb(243, 217, 217);
    width: 280px;
    padding-left: 5px;
    padding-top: 0px;
    font-size: large;
    font-weight: bold;
    
}

.assignee {
    margin-top: 0px;
}
.id {
    margin-top: 0px;
    margin-bottom: 0px;
}
</style>
<script>
	export let title;
	export let assignee;
	export let description;
	export let id;

	let inputValue;

	function handleClick() {
		console.log(inputValue);
	}
</script>

<div>
	<div class="issueCards">
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
					<input bind:value={inputValue} type="number" pattern="[0-9]" />
				</label>
				<button on:click={handleClick}>Save</button>
			</div>
		</div>
	</div>
</div>

