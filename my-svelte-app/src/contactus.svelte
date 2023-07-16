<script>
	import { Router, Route, Link } from "svelte-navigator";

	export let contactusRo;

	let title = '';
	let content = '';

	function handleSubmit() {
		// Handle form submission here
		console.log(`Title: ${title}, Content: ${content}`);
	}
</script>




	<main>
		<h1>Contact Us</h1>
			<div class="contactus">

			<table>
			  <tr>
			    <th>Title:</th>
			    <td><input type="text" bind:value={title} /></td>
			  </tr>
			  <tr>
			    <th>Content:</th>
			    <td><textarea rows="5" bind:value={content}></textarea></td>
			  </tr>
			</table>

			<button type="submit" on:click={handleSubmit}>Submit</button>

		  <nav>
		    <Link to="../">Go back home page</Link>
		  </nav>
		</div>
	</main>


	<style>
	  * {
	    box-sizing: border-box;
	  }

	  body {
	    margin: 0;
	    font-family: Arial, sans-serif;
	    font-size: 16px;
	    line-height: 1.5;
	  }

	  main {
	    max-width: 800px;
	    margin: 0 auto;
	    padding: 20px;
	  }

	  h1 {
	    text-align: center;
	    font-size: 2.5rem;
	    margin-top: 0;
	  }

	  .contactus {
	    background-color: #f9f9f9;
	    padding: 20px;
	    border-radius: 5px;
	    box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
	    margin-bottom: 20px;
	  }

	  table {
	    border-collapse: collapse;
	    margin: 20px;
	    width: 100%;
	  }

	  th, td {
	    border: 1px solid black;
	    padding: 10px;
	  }

	  th {
	    text-align: left;
	    width: 20%;
	    background-color: #f2f2f2;
	  }

	  td {
	    width: 80%;
	  }

	  input[type="text"], textarea {
	    width: 100%;
	    padding: 10px;
	    box-sizing: border-box;
	    margin: 10px 0;
	    border: none;
	    border-radius: 5px;
	    font-size: 1rem;
	  }

	  textarea {
	    height: 150px;
	    resize: none;
	  }

	  button[type="submit"] {
	    background-color: #4CAF50;
	    color: white;
	    padding: 10px 20px;
	    border: none;
	    border-radius: 5px;
	    cursor: pointer;
	    font-size: 1rem;
	    margin-top: 20px;
	  }

	  button[type="submit"]:hover {
	    background-color: #3e8e41;
	  }

	  nav {
	    text-align: center;
	    margin-top: 20px;
	  }

	  nav a {
	    color: #000;
	    text-decoration: none;
	    padding: 10px;
	    border-radius: 5px;
	    background-color: #f2f2f2;
	    margin: 0 10px;
	  }

	  nav a:hover {
	    background-color: #ddd;
	  }
	</style>
