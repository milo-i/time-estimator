<script>

    /*let issues = [
    {
    title: "Issue Card Component",
    description: "make component that prints the fetched issues as cards",
    assignee: "Anton",
    id: "1"
    },
    {
    title: "Member 'login'",
    description: "make component that handles which member who is active",
    assignee: "Igor",
    id: "2"
    },
    {
    title:"Fetch data",
    description: "make a fetch from githubg to get issues",
    assignee: "Smari",
    id:"3"
    },
    {
    title:"Generate Report",
    description: "Make a report with estimated time vs actual time",
    assignee: "Emelie",
    id:"4"
    },
    {
    title:"User time estimation",
    description: "make input field and function for the users estimated time on the issue",
    assignee: "Jin",
    id:"5"
    },
    {
    title:"Close Issue Function",
    description: "create function to close issue and report actual time",
    assignee: "Anton",
    id:"5"
    },
    {
    title:"Some other Issue",
    description: "create something ",
    assignee: "Igor",
    id:"5"
    },
    {
    title:"Another unidentified Issue",
    description: "build something, not sure 'bout what ",
    assignee: "Smari",
    id:"5"
    }

]*/



export let title;
export let assignee;
export let description
export let id


</script>

<style>

.issueCards {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    row-gap: 40px;
 

}

.issueCard {
    border: 1px solid black;
    background-color: rgb(243, 167, 154);
    width:300px;
    height: 250px;
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
    
}

.assignee {
    margin-top: 0px;
}
.id {
    margin-top: 0px;
    margin-bottom: 0px;
}


</style>

<div>
    <div class = "issueCards">
       <div class="issueCard">
           <h2 class="title">{title}</h2>
           <h3 class="id">{"Id: " + id}</h3>
           <h3 class="assignee">{"Assignee: " + assignee}</h3>
           <div class="description">
           <p>{description}</p>
           </div>
       </div>
    </div>
</div>