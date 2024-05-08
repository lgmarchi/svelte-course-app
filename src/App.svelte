<script>
	import ContactCard from "./ContactCard.svelte";

	let name = 'Max';
	let age = 30;
	let jobTitle = "";
	let description = "";

	// $: is a reactive statement
	// Don't need to declare upperCaseName
	// It will be updated automatically when name is changed

	$: upperCaseName = name.toUpperCase();

	// Print every time name or age is changed
	$: {
		console.log(`Name: ${name}`);
		console.log(`Age: ${age}`);
	};

	$: if (name = 'Lucas') {
		age = 29;
	}

	function incrementAge() {
		age += 1;
	}

	function changeName() {
		name = 'Lucas';
	}

	function changeNameOnInput(event) {
		const newValue = event.target.value;
		name = newValue;
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {upperCaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<button on:click="{changeName}">Change Name</button>
<!-- <input type="text" value="{name}" on:input={changeNameOnInput}/> -->
<!-- This will automatically change variable name, as a shortcut -->
<input type="text" bind:value="{name}"/>
<input type="text" bind:value="{jobTitle}"/>
<textarea rows="3" type="text" bind:value="{description}"/>



<ContactCard userName="{name}" 
				{jobTitle}
				{description}
				/>


