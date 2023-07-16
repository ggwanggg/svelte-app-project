<script>
	let name = 'leung wang chan';

	//import rounter code
	import { Router, Route, Link } from "svelte-navigator";
	import aboutus from "./aboutus.svelte";
	import contactus from "./contactus.svelte";
	import usefultool from "./usefultool.svelte";

	// waiting finish
	function handleLogin() {
    location.href = '/login';
  }

	//popup function
	export let buttonText = 'Create a post';
  export let popupTitle = 'Create a post';
  export let placeholderText = 'Enter your text here...';
  export let value = '';
	export let title = ''; // new title variable
  export let isPopupVisible = false;

	function togglePopup() {
			isPopupVisible = !isPopupVisible;
	}

	function handleTextareaInput(event) {
		value = event.target.value;
	}

	function handleTitleInput(event) {
		title = event.target.value;
	}

	function PopupMessage() {
		// show message on console
		console.log(`Create a Post's title: ${title}`);
		console.log(`Create a Post's contact: ${value}`);
		//start function
		const newtitleMessage = title.trim();
		if (newtitleMessage !== '') {
			const messageElement = document.createElement('p');
			messageElement.textContent = newtitleMessage;
			document.querySelector('#title-message-container').appendChild(messageElement);
		}
		const newMessage = value.trim();
		if (newMessage !== '') {
			const messageElement = document.createElement('p');
			messageElement.textContent = newMessage;
			document.querySelector('#message-container').appendChild(messageElement);
		}
			value = '' // reset value variable after submitting post
			title = '' // reset title variable after submitting post
			togglePopup()
	}

	//image part
	export let isimageVisible = false;
	let imageUrl = ""; // The initial value of the imageUrl is an empty string
	function handleFileInput(event) {
		const file = event.target.files[0]; // Get the first file selected by the user
		const reader = new FileReader(); // Create a new FileReader object
		reader.onload = () => {
		imageUrl = reader.result; // Set the imageUrl to the base64-encoded image data
	};
	reader.readAsDataURL(file); // Read the file as a Data URL
	}

	function toggleimage() {
		isimageVisible = !isimageVisible;
	}

	// Import necessary dependencies
 	import { onMount } from 'svelte';

	// Define component
	let topQuestions = ["Where can I buy a Scantron from on campus?", "[MATH 170B] How do I set up this problem?", "[CPSC 362] How good is Professor Merin Joseph for anyone who has taken her?", "[GEOL 101] Which professors do you recommend for this class?", "How good is the campus laptop rental system?"];

	onMount(async () => {
		// Fetch top questions on mount
	});

</script>

<!--Router function-->
<Router>
	<header>
	<h1>Welcome to CSUFacts</h1>

	<div class="button-toplogin" style="float: right;">
		<button on:click={handleLogin}>Click Here to Log In</button>
	</div>

	</header>

<div class="flex-container">
	<nav>
		<Link to="/">Home</Link>
		<Link to="aboutus">aboutus</Link>
		<Link to="contactus">contactus</Link>
		<Link to="usefultool">usefultool</Link>
	</nav>

	<main>

		<Route path="/">
		<h3>Home page</h3>

		<h2>Top Questions:</h2>

	  <ul>
	    {#each topQuestions as question}
	      <li>{question}</li>
	    {/each}

	  </ul>


		<!--// the button that create a post-->
		<button on:click={togglePopup}>{buttonText}</button>

		<!-- contain content-->
		<h2>Recently Post (beta1.0)</h2>
		<div id="title-message-container"></div>
		<div id="message-container"></div>
		<div id="image-container"></div>

		<!-- Display the uploaded image using the <img> tag -->
		{#if imageUrl}
		  <img src={imageUrl} alt="Uploaded image">
		{/if}
		<!-- need display no contact-->

		<!--// if isPopupVisible is ture, display the popup box-->
		{#if isPopupVisible}
			<div class="popup-overlay">
				<div class="popup-container">
					<h3>{popupTitle}</h3>
					<label for="title-input">Title:</label>
					<input id="title-input" type="text" value={title} on:input={handleTitleInput}>
					<textarea
						placeholder={placeholderText}
						value={value}
						on:input={handleTextareaInput}
					></textarea>

					{#if isimageVisible}
						<!-- Use the <input> tag with type="file" to allow the user to upload an image -->
						<input type="file" on:change={handleFileInput}>
					{/if}
					<!--image-->
					{#if imageUrl}
					  <img src={imageUrl} alt="Uploaded image">
					{/if}
					<!-- finished there have a bug-->
					<button on:click={toggleimage}>image</button>

					<div class=".button-container">
						<button on:click={PopupMessage}>send</button>
						<button on:click={togglePopup}>Close</button>
					</div>
				</div>
			</div>
		{/if}




		</Route>

		<Route path="aboutus/*aboutusRoute" component={aboutus} />
		<Route path="contactus/*contactusRoute" component={contactus} />
		<Route path="usefultool/*usefultoolRoute" component={usefultool} />
		<Route>
	      <h3>Default</h3>
	      <p>No Route could be matched.</p>
	   </Route>
	</main>
</div>
</Router>



<style>
	header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  nav {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		align-self: flex-start;
  }

	.flex-container {
		display: flex;
		align-items: center;
	}

	main {
		flex: 1;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #22ccbb;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 600;
	}

	h2 {
		color: #aa00bb;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 600;
	}

	button {
    background-color: #000080;
    color: White;
    border: none;
    border-radius: 4px;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }


  button:hover {
    background-color: #FFA500;
  }


	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

/* Set popup value */

	.popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 999;
  }

  .popup-container {
/*other vertically*/
    background-color: white;
    padding: 12rem;
    border-radius: 10.25rem;
    box-shadow: 0 0 10.5rem rgba(0, 0, 0, 10.3);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

	.context-container {
    /* Styles for the context container */
    margin-bottom: 2rem; /* Adds some space between the context and the buttons */
  }

  .button-container {
    /* Styles for the button container */
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }


  .popup-container h3 {
    margin: 0 0 1rem;
  }

  .popup-container textarea {
    width: 200%;
    height: 18rem;
    margin-bottom: 1rem;
    padding: 0.5rem;
    font-size: 1rem;
    border: none;
    border-radius: 0.25rem;
    box-shadow: 0 0 0.25rem rgba(0, 0, 0, 0.2);
  }

  .popup-container button {
		/*display: inline-block;*/
    padding: 0.5rem;
    font-size: 1rem;
    border: none;
    border-radius: 0.25rem;
    background-color: #007aff;
    color: white;
    cursor: pointer;
    box-shadow: 0 0 0.25rem rgba(0, 0, 0, 0.2);
  }


</style>
