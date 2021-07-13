<script>
	window.onload = function() {
		new Audio('https://res.cloudinary.com/odcloud/video/upload/v1625930644/notal.mp3_ycwskc.mp3').play()
		document.querySelector("textarea").removeAttribute("disabled")
		if (localStorage.getItem("note").length > 0) {
			document.querySelector("textarea").value = localStorage.getItem("note")
		}
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
	<div class="container">
		<nav>
			<li on:click={clear} class="func clear">Clear</li>
			<li><h1>{"<Notering>"}</h1></li>
			<!-- svelte-ignore a11y-invalid-attribute -->
			<li on:click={download} class="func download"><a href="" id="save">Download</a></li>
		</nav>
		<textarea disabled name="" id="" 
			on:keyup={() => localStorage.setItem("note", document.querySelector("textarea").value)}
		></textarea>
	</div>
</main>


<style>
	@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css')
	
	main {
		text-align: center;
		font-size: 4.2vh;
	}

	li{
		list-style: none;
		margin: 15px;
		color: rgb(19, 19, 143);
		font-weight: 500;
		font-size: 4.2vh;
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
		background-color: rgba(0, 0, 0, 0.844);
		height: 7.346vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	textarea{
		margin-left: 18vh;
		resize: none;
		border: transparent;
		width: 150vh;
		height: 92vh;
		background-color: rgb(6, 4, 24);
		color: whitesmoke;
		font-size: 3vh;
		font-weight: 400;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}
</style>