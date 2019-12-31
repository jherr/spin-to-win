<script>
let options = [
	'Option 1'
];
let selected = null;

const newItem = () => {
	options = [...options, `Option ${options.length + 1}`];
};

const run = () => {
	let rate = 1.2 + (Math.random() * 0.4);
	let speed = 10;
	selected = 0;
	const runIteration = () => {
		speed = speed * rate;
		window.setTimeout(() => {
			selected = ( selected + 1 ) % options.length;
			if (speed < 1000) {
				runIteration();
			}
		}, speed);
	}
	runIteration();
}
</script>

<div class="container">
	{#each options as option, i}
		<div class="option {selected === i ? 'selected' : ''}">
			<input
				type="text"
				value={option}
			/>
		</div>
	{/each}
	<div class="option new" on:click={newItem}>
		<button>
			+
		</button>
	</div>
</div>
<button on:click={run} class="run">
	Run
</button>

<style>
.container {
	font-family: Arial, Helvetica, sans-serif;
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	grid-gap: 0.25em;
}

.option {
	padding: 3em 0em 3em 0em;
	background: lightseagreen;
}

.selected {
	background: darkgreen;
}

.new {
	background: white;
	text-align: center;
}

.new > button {
	border-width: 0px;
	font-size: 3em;
	background: white;
	margin: 0px;
	padding: 0px;
}

.option > input {
	background: #00000000;
	color: white;
	font-size: xx-large;
	border-width: 0px;
	text-align: center;
	width: 100%;
	margin: 0px;
	padding: 0px;
}

.run {
	font-size: xx-large;
	font-weight: bold;
	width: 100%;
	padding: 1em;
	border-radius: 1em;
	margin-top: 2em;
	border-width: 0px;
	color: white;
	background-color: darkblue;
}
</style>