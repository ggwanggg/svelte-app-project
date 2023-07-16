<script>
	import { Router, Route, Link } from "svelte-navigator";

	export let aboutus;
</script>

<main>
	<h1>About US</h1>
	<div class="aboutus">

	  <span>You're at blog/{aboutus}</span>
		<h2>Hi professor Merin Joseph</h2>
		<h3>There is group info:</h3>
		<p>Name: Leung Wang Chan Email:lchan2021@csu.fullerton.edu</p>
		<p>Name: Aidan Castillo Email:</p>
		<p>Name: Emma Jauregui Email:</p>
		<p>Name: Jordan Muir Email:</p>
		<p>Name: Ismail Peracha Email:</p>
	  <nav>
	    <Link to="../">Go back home page</Link>
	  </nav>
	</div>
</main>



<style>
  /* Set background color and font family */
  body {
    background-color: #f2f2f2;
    font-family: Arial, sans-serif;
  }

  /* Style the header */
  h1 {
    text-align: center;
    font-size: 2.5rem;
    margin-top: 2rem;
  }

  /* Style the blog container */
  .Blog {
    background-color: white;
    padding: 2rem;
    border-radius: 1rem;
    box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
    margin-top: 2rem;
  }

  /* Style the blog title */
  h2 {
    color: #3e3e3e;
    font-size: 2rem;
    margin-top: 1rem;
  }

  /* Style the group info section */
  h3 {
    color: #666666;
    font-size: 1.5rem;
    margin-top: 2rem;
  }

  /* Style the individual names and emails */
  p {
    color: #666666;
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
  }

  /* Style the navigation link */
  nav {
    margin-top: 2rem;
    text-align: center;
  }

  /* Style the link itself */
  a {
    color: #0077cc;
    font-weight: bold;
    text-decoration: none;
    padding: 0.5rem;
    border-radius: 0.5rem;
    background-color: #e6f3ff;
    box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
  }

  /* Style the link on hover */
  a:hover {
    background-color: #0077cc;
    color: white;
  }
</style>
