<script>
  import FetchIssues from './FetchIssues.svelte';
  let name = 'smaristeinar';
  let activeMember;

  function reloadCards() {
    console.log('the name has been changed');
    let chooseMember = document.querySelector('#members');
    activeMember = chooseMember.value;
    console.log(activeMember);
    //localStorage.setItem("Active Member", activeMember)
  }

  const generateReport = () => {
    document.getElementById('report-section').innerHTML = '';

    const reducer = (previousValue, currentValue) =>
      previousValue + currentValue;

    const getMax = (a, b) => {
      return Math.max(a, b);
    };

    const getMin = (a, b) => {
      return Math.min(a, b);
    };

    // const getAverage = (arr) => arr.reduce((a, b) => a + b) / arr.length;

    const keys = Object.keys(localStorage);
    for (let key of keys) {
      console.log(`${key}: ${localStorage.getItem(key)}`); // localStorage.getItem(key) är av typen string, INTE number

      console.log(JSON.parse(localStorage.getItem(key)).length);
      document.getElementById('report-section').insertAdjacentHTML(
        'beforeend',
        `<div class="time-est"><p>Issue id: ${key} total time estimation: ${JSON.parse(
          localStorage.getItem(key)
        ).reduce(reducer)}</p>
          <p>Max estimation time: ${JSON.parse(
            localStorage.getItem(key)
          ).reduce(getMax)}</p>
          <p>Min estimation time: ${JSON.parse(
            localStorage.getItem(key)
          ).reduce(getMin)}</p>
          <p>Average: ${
            JSON.parse(localStorage.getItem(key)).reduce((a, b) => a + b) /
            JSON.parse(localStorage.getItem(key)).length
          }

          </p></div>`
      );
    }
  };
</script>

<main>
  <h1 class="title">Hello Team</h1>

  <div class="members-selctor" />
  <label for="members">Choose a member:</label>

  <select on:change={reloadCards} name="members" id="members">
    <option value="" />
    <option value="smaristeinar">Smari</option>
    <option value="anton">Anton</option>
    <option value="emelie">Emelie</option>
    <option value="igor">Igor</option>
    <option value="jin">Jin</option>
  </select>

  <button on:click={generateReport}>Generate time report</button><br />
  <div id="report-section" />

  <FetchIssues {name} {activeMember} />
</main>

<style>
  .title {
    margin-top: 0px;
    margin: 0px;
    padding: 0px;
    color: white;
    font-size: large;
    background-image: linear-gradient(
      to right,
      rgb(0, 28, 151),
      rgb(90, 129, 214)
    );
  }

  main {
    height: 100%;
    width: 100%;
  }

  .members-selctor {
    margin-top: 10px;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  label {
    margin-right: 20px;
    font-size: x-large;
  }
  select {
    width: 150px;
    background-color: rgb(235, 229, 229);
    border: 1px solid black;
  }
  .report-btn {
    background-color: aqua;
  }
  #report-section {
    background-color: bisque;
    /* border: 1px solid black; */
  }
  div.time-est {
    border: 1px solid black;
  }
</style>
