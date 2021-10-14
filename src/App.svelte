<script>
	import FetchIssues from "./FetchIssues.svelte";
	let name = "smaristeinar";
</script>


<main>
	<h1 class="title">Hello Team - team planer</h1>
<div class="members-selctor">
  		<label for="members">Choose a member:</label>
		<select name="members" id="members">
			<option value="smaristeinar">Smari</option>
			<option value="anton">Anton</option>
			<option value="emelie">Emelie</option>
			<option value="igor">Igor</option>
			<option value="jin">Jin</option>
		</select>
	</div>
  <FetchIssues name={name}/>
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
.members-selctor > label{
	margin-right: 20px;
	font-size: x-large;
}
select{
	width: 150px;
	background-color: rgb(235, 229, 229);
	border: 1px solid black;
	
}

</style> 

