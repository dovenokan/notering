<script>
	window.onload = function() {
		new Audio('https://res.cloudinary.com/odcloud/video/upload/v1625930644/notal.mp3_ycwskc.mp3').play()
		document.querySelector("textarea").value = localStorage.getItem("note")
	}
</script>

<main>
	<nav>
		<li>Noter</li>
	</nav>
	<textarea name="" id="" 
	on:change={(event) => localStorage.setItem("note", event.target.value)}
	></textarea>
</main>


<style>
	main {
		text-align: center;
		font-size: 5vh;
	}

	li{
		list-style: none;
		margin: 15px;
		color: blue;
	}

	nav{
		background-color: rgba(6, 17, 75, 0.98);
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
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}
</style>