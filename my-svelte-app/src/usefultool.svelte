<script>
	import { Router, Route, Link } from "svelte-navigator";


	export let usefultool;

	// Define an array of tool objects with name and URL properties
	const tools = [
		{ name: "Math Tool 1", url: "https://mathsolver.microsoft.com/zh-Hant/calculus-calculator" },
		{ name: "Math Tool 2", url: "https://homepage.divms.uiowa.edu/~mbognar/applets/bin.html" },
		{ name: "Math Tool 3", url: "https://www.emathhelp.net/calculators/linear-algebra/reduced-row-echelon-form-rref-calculator/?i=%5B%5B1%2C-3%2C-1%2C17%5D%2C%5B-2%2C6%2C4%2C-40%5D%2C%5B3%2C-8%2C-6%2C56%5D%5D&reduced=on" },
		// Add more tools as needed
	];
</script>

<main>
  <h1>Welcome to Useful Tool</h1>

  <div class="catalog">
		<h2>Math Tool</h2>
		<!-- Display links to each tool in the catalog -->
    {#each tools as tool}
      <a href={tool.url}>{tool.name}</a>
    {/each}
  </div>
</main>

<div class="usefultool">


  <span>You're at usefultool/{usefultool}</span>

  <nav>
    <Link to="../">Go back to home page</Link>
  </nav>
</div>

<style>
  /* Add styles for the catalog links and headings */
  .catalog {
    margin-top: 20px;
  }

  .catalog h2 {
    font-size: 24px;
    margin-bottom: 10px;
  }

  .catalog a {
    display: block;
    font-size: 18px;
    margin-bottom: 10px;
    text-decoration: none;
    color: #333;
    transition: all 0.3s ease-in-out;
  }

  .catalog a:hover {
    color: #007acc;
    transform: scale(1.05);
  }

  /* Add styles for the Useful Tool section */
  .usefultool {
    margin-top: 50px;
    text-align: center;
  }

  .usefultool span {
    display: block;
    font-size: 18px;
    margin-bottom: 20px;
  }

  .usefultool nav {
    display: flex;
    justify-content: center;
  }

  .usefultool nav a {
    font-size: 16px;
    margin: 0 10px;
    text-decoration: none;
    color: #333;
    transition: all 0.3s ease-in-out;
  }

  .usefultool nav a:hover {
    color: #007acc;
    transform: scale(1.05);
  }
</style>
