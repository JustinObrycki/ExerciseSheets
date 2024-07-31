<style>
	.nav {
		justify-content: space-evenly;
	}
	.nav-tabs .nav-link{
		width: 100px;
		height: 100px;
		border: solid 1px black;
		border-radius: 10%;
		display: flex;
		text-align: center;
		align-items: center;
		justify-content: center;
		background-color: white;
		box-shadow: 1px 1px 10px 0px #b2b2b2;
	}
	.nav-link.active {
		width: 100px;
		height: 100px;
		border-radius: 10%;
		display: flex;
		text-align: center;
		align-items: center;
		justify-content: center;
		background-color: rgba(207, 207, 207, 0.541);
	}
	.nav-tabs .nav-link:hover {
		border: solid 3px black;
	}
</style>

<script>
    
import { navOptions } from  './NavEdit.svelte';	
let selected = navOptions[0];	
let intSelected = 0;	

function changeComponent(event) {
	selected = navOptions[event.srcElement.id];
	intSelected = event.srcElement.id;
}
</script>
<link rel='stylesheet' href='https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css'>
<div class="container">
	<ul class="nav nav-tabs">
		{#each navOptions as option, i}
		<li class="nav-item">
			<button class={intSelected==i ? "nav-link active p-2 ml-1" : "p-2 ml-1 nav-link"} on:click={changeComponent} id={i} role="tab">{option.page}</button>
		</li>
		{/each}
	</ul>
	<!-- content wrapper -->
	<div class="row">
		<div class="col-sm-12">
			<div class="p-2">
				<h1 style="text-align: center; font-size: 30px;">Exercises for {selected.page}</h1>
				<a class="btn btn-primary" href="/"> View Exercises</a>
				<!--  main content  -->
				<svelte:component this={selected.component}/>
			</div>
		</div>
	</div>
</div>