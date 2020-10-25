<script>
  import { createEventDispatcher } from 'svelte';

  let dispatch = createEventDispatcher();
  let name;
  let level;
  let age;
  let skills = [];

  const handleSubmit = () => {
    const person = {
      name, 
      level,
      age, 
      skills,
      id: Math.random()  
    }
    dispatch('addPerson', person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder='name' bind:value={name}>
  <input type="number" placeholder='age' bind:value={age}>
  <label>Skills:</label>
  <!-- <input type="checkbox" bind:checked={fighting}>fighting<br>
  <input type="checkbox" bind:checked={sneaking}>sneaking<br>
  <input type="checkbox" bind:checked={running}>running<br> -->
  <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
  <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
  <input type="checkbox" bind:group={skills} value="running">running<br>
  <label>Belt colour:</label>
  <select bind:value={level}>
    <option value="Master">Master</option>
    <option value="Pro">Pro</option>
    <option value="Moderate">Moderate</option>
    <option value="Beginner">Beginner</option>
  </select>
  <button>Add Player</button>
</form>