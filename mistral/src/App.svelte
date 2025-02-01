<script>
	import { onDestroy } from "svelte";
	import { writable } from "svelte/store";
		
	export let name;
	let scalerond = 0;
	let t = 0;
	const inputValue = writable("");
	const storedValue = writable("");
	const showPopup = writable(false);

	let popupX = 50;
	let popupY = 50;
	let isDragging = false;
	let offsetX, offsetY;

	const interval = setInterval(() => {
		t += 0.01;
		scalerond = Math.cos(t);
	}, 16);

	onDestroy(() => clearInterval(interval));

	function handleSubmit() {
		storedValue.set($inputValue);
		showPopup.set(true);
	}

	function closePopup() {
		showPopup.set(false);
	}

	function startDrag(event) {
		isDragging = true;
		offsetX = event.clientX - popupX;
		offsetY = event.clientY - popupY;
	}

	function onDrag(event) {
		if (isDragging) {
			popupX = event.clientX - offsetX;
			popupY = event.clientY - offsetY;
		}
	}

	function stopDrag() {
		isDragging = false;
	}
	


</script>

<body>
	<div id="hero">
<main on:mousemove={onDrag} on:mouseup={stopDrag}>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<input type="text" id="test" name="test" bind:value={$inputValue} required minlength="4" size="10">
	<button id="submit" name="submit" on:click={handleSubmit}>Submit</button>
	
	{#if $showPopup}
		<div id="popup" class="popup" style="top: {popupY}px; left: {popupX}px;" >
			<div class="popup-header" on:mousedown={startDrag} on:mouseup={stopDrag}>
				<p></p>
			</div>
			<p>Vous avez écrit : {$storedValue}</p>
			<button on:click={closePopup}>Fermer</button>
		</div>
	{/if}
</main>
	</div>
</body>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0;

	}


	body {
		padding: 0px;
	}

	#hero {
    background-image: url("/img/background.png");
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	user-select: none;
}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.popup {
		position: absolute;
		background: white;
		padding: 20px;
		box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
		border-radius: 10px;
		z-index: 1000;
	}

	.popup-header {
		background: #ccc;
		padding: 10px;
		cursor: grab;
		border-top-left-radius: 10px;
		border-top-right-radius: 10px;
	}
</style>