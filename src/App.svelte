<script>
	window.onload = function() {
		// new Audio('https://res.cloudinary.com/odcloud/video/upload/v1625930644/notal.mp3_ycwskc.mp3').play()
		document.querySelector("textarea").removeAttribute("disabled")
		let update_w = parseInt(localStorage.getItem("box_width").slice(0,-2))
		document.querySelector("textarea").style.width = update_w > window.innerWidth ? `${window.innerWidth}px` : localStorage.getItem("box_width")
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
		<div class="xxxpx-4 xxxpy-1 my-2 text-primary">
			<h1 class="display-6 fw-bold text-gray">Notering</h1>
			<div class="buttons-area xxxcol-lg-6 mx-auto">
			  <div class="xxxd-grid gap-2 xxxd-sm-flex justify-content-sm-center">
				<button on:click={clear} type="button" class="btn btn-danger btn-lg xxxpx-4 gap-3">Clear</button>
				<!-- svelte-ignore a11y-invalid-attribute -->
				<button on:click={download} type="button" class="btn btn-success btn-lg px-4"><a href="#" id="save">Download</a></button>
			  </div>
			</div>
			<textarea class="my-2" name="" id="" 
			on:keyup={() => localStorage.setItem("note", document.querySelector("textarea").value) }
			on:mouseup={() => localStorage.setItem("box_width", document.querySelector("textarea").style.width)} 
			></textarea>
		</div>
</main>

<style>
	main {
		text-align: center;
		font-size: 3.2vh;
	}
	
	a, a:hover, a:visited{
		text-decoration: none;
		color: inherit;
	}	

	.buttons-area{
		/* background-color: red; */
	}

	textarea{
		resize: horizontal;
		border: transparent;
		width: 20rem;
		height: 25em;
		margin: 0ch;
		background-color: rgb(6, 4, 24);
		color: whitesmoke;
		border-radius: 5px;
		font-size: 3vh;
		font-weight: 400;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}

</style>