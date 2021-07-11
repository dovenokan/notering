<script>
	window.onload = function() {
		new Audio('https://res.cloudinary.com/odcloud/video/upload/v1625930644/notal.mp3_ycwskc.mp3').play()
		document.querySelector("textarea").value = localStorage.getItem("note")
		document.querySelector("textarea").removeAttribute("disabled")
	}

	function clear() {
			document.querySelector("textarea").value = ""
			localStorage.setItem("note", "")
	}

	function download() {
		var data = document.querySelector("textarea").value.toString()
		var a = document.querySelector("a#save");
		var file = new Blob([data], {type: 'text/plain'});
		a.href = URL.createObjectURL(file);
		a.download = new Date().valueOf()+"_noter_notes.txt";
	}

</script>

<main>
	<nav>
		<li on:click={clear} class="func clear">Clear</li>
		<li><h1>Notering</h1></li>
		<!-- svelte-ignore a11y-invalid-attribute -->
		<li on:click={download} class="func download"><a href="" id="save">Download</a></li>
	</nav>
	<textarea disabled name="" id="" 
	on:change={(event) => localStorage.setItem("note", event.target.value)}
	></textarea>
</main>


<style>
	main {
		text-align: center;
		font-size: 4.2vh;
	}

	li{
		list-style: none;
		margin: 15px;
		color: rgb(19, 19, 143);
		font-weight: 500;
	}

	a, a:hover, a:visited{
		text-decoration: none;
		color: inherit;
	}	


	.clear{
		color: rgb(119, 18, 18);
	}

	.download{
		color: rgb(6, 134, 25);
	}

	nav{
		background-color: rgba(4, 10, 41, 0.98);
		height: 8vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	textarea{
		resize: none;
		border: transparent;
		width: 200vh;
		height: 90vh;
		background-color: rgb(11 4 37);
		color: whitesmoke;
		font-size: 3vh;
		font-weight: 400;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}
</style>