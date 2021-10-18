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
	<h1 class="title">Hello Team</h1>

<div class="members-selctor"></div>
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
.title{
	margin-top: 0px;
	margin: 0px;
	padding: 0px;
	color: white;
	font-size: large;
	background-image: linear-gradient(to right, rgb(0, 28, 151), rgb(90, 129, 214));
}
	
main{
	height: 100%;
	width: 100%;

}

.members-selctor{
	margin-top: 10px;
	display: flex;
	flex-direction: row;
	justify-content: center;
}
 label{
	margin-right: 20px;
	font-size: x-large;
}
select{
	width: 150px;
	background-color: rgb(235, 229, 229);
	border: 1px solid black;
	
}


</style>
