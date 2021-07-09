<script>
	export let patientName;
	export let patientId;
	export let comment = "";
	export let readonly;
	export let dirtyDocument = false;

	const keyPress = () => {
		dirtyDocument = true;
		window.chrome.webview.postMessage("DocumentStatus:dirty");
	}

</script>

<main>
	<div class:hide={readonly}>
		
		<label>Navn</label>
		<input disabled value={patientName} id="name" />

		<label>Personnummer</label>
		<input disabled value={patientId} id="patientId" />

		<input type="text" placeholder="Kommentar" id="commentBox" value="{comment}" on:input={keyPress}/>		
		
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.hide button {
		display: none;
	}

	.inactive {
		opacity: 0.5;
	}
</style>
