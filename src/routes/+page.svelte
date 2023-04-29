<script>
	let final = 0
	let console = ""
	let current = null
	function resolveState() {
	  switch (current) {
		case "add":
		  final += parseFloat(console)
		  console
		  break;
		case "subtract":
		  final -= parseFloat(console)
		  console
		  break
		case "multiply":
		  final *= parseFloat(console)
		  console
		  break
		case "divide":
		  final /= parseFloat(console)
		  console
		  break
		default:
		  final = parseFloat(console)
		  console = ""
		  break
	  }
	}
	function setOperation(operation) {
	  resolveState()
	  current = operation
	}
	function setValue(value) {
	  if (console.toString() == "0" || current == "equal") {
		console = ""
	  }
	  if (current == "equal") {
		current = ""
	  }
	  if (value == "C") {
		final = 0
		current = null
		console = ""
		return
	  }
	  console = console + value
	}
	function equal() {
	  resolveState()
	  console = final
	  current = "equal"
	}
  </script>
  
  <svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
  </svelte:head>
  
  <section>
	<div class="calculator__container">
	  <div class="result__box">
		<input type="text" class="result" bind:value={console} readonly={true} />
	  </div>
	  <div class="buttons__box">
		<button
		  on:click={() => {
			setValue("1")
		  }}>1</button
		>
		<button
		  on:click={() => {
			setValue("2")
		  }}>2</button
		>
		<button
		  on:click={() => {
			setValue("3")
		  }}>3</button
		>
		<button
		  on:click={() => {
			setOperation("add")
		  }}>+</button
		>
		<button
		  on:click={() => {
			setValue("4")
		  }}>4</button
		>
		<button
		  on:click={() => {
			setValue("5")
		  }}>5</button
		>
		<button
		  on:click={() => {
			setValue("6")
		  }}>6</button
		>
		<button
		  on:click={() => {
			setOperation("subtract")
		  }}>-</button
		>
		<button
		  on:click={() => {
			setValue("7")
		  }}>7</button
		>
		<button
		  on:click={() => {
			setValue("8")
		  }}>8</button
		>
		<button
		  on:click={() => {
			setValue("9")
		  }}>9</button
		>
		<button
		  on:click={() => {
			setOperation("multiply")
		  }}>*</button
		>
		<button on:click={()=>{setValue('C');}}>C</button>
		<button
		  on:click={() => {
			setValue("0")
		  }}>0</button
		>
		<button on:click={equal}>=</button>
		<button
		  on:click={() => {
			setOperation("divide")
		  }}>/</button
		>
	  </div>
	</div>
  </section>
  
  <style>
	section {
	  display: flex;
	  flex-direction: column;
	  justify-content: center;
	  align-items: center;
	  flex: 0.6;
	}
  
	* {
	  margin: 0;
	  padding: 0;
	  box-sizing: border-box;
	}
  
	.calculator__container {
	  width: 400px;
	  height: 100%;
	  border: 1px solid black;
	}
  
	.result__box {
	  width: 100%;
	  padding: 10px;
	}
  
	.result {
	  width: 100%;
	  padding: 20px;
	  border: 1px solid black;
	  text-align: start;
	  font-size: 32px;
	}
  
	.buttons__box {
	  width: 100%;
	  height: 100%;
	  display: grid;
	  grid-template-columns: repeat(4, 1fr);
	  grid-gap: 10px;
	  padding: 20px 10px;
	}
  
	button {
	  width: 100%;
	  padding: 25px;
	  border: 1px solid black;
	  border-radius: unset;
	  font-size: 32px;
	  background-color: rgb(231, 231, 231);
	}
  </style>
  