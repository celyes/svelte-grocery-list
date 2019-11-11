<script>
	
	let items = [
		{id: 1, name: "milk", done: false},
		{id: 2, name: "bread", done: false},
		{id: 3, name: "eggs", done: false}
	];
	let name = '';

	const remove = item => {
		items = items.filter(i => i !==item);
	}

	const complete = item => {
		item.done = true;
	}

	const addItem = ()=>{
		items = [
			...items,
			{id: Math.floor(Math.random() * 100), name, done: false}
		];
		name = '';
	}
</script>

<style>
	h1 {
		color: purple;
		text-align: center;
	}
	ul{
		list-style-type: none;
		margin: 0 auto;
		padding: 0;
	}
	li{
		border-bottom: 1px solid #dedede;
		padding: 15px 5px;
	}
	.completeLabel{
		display: inline-block;
	}
	.id{
		color: #999;
		font-size: 12px;
		padding-right: 15px;
	}
	.name{
		font-size: 38px;
		color: #00f;
		font-weight: 100;
	}
	.remove{
		font-size: 12px;
		float: right;
		margin-left: 10px;
	}
	.btn-transparent{
		border: none;
		background: none;
  		transition: transform .2s; 
	}
	.btn-transparent:hover{
		transform: scale(1.5);
	}
	.done{
		pointer-events:none; 
    	opacity:0.4;
	}
	.key{
		background-color: #dcdcdc;
		color: #000;
		padding: 0 3px;
		font-size: 14px;
		font-family: monospace;
	}
	
</style>

	<div class="row">
		<div class="col my-4">
			<h1>Grocery List 🗒️</h1>
		</div>
	</div>
	<div class="row">
		<div class="col-md-6 offset-md-3">
			<ul>
				<form on:submit|preventDefault={addItem}>
					<label for="name" class="text-muted">Hit <span class="key">Enter</span> to add item</label>
					<input class="form-control" id="name" type="text" bind:value={name} placeholder="Ex: juice" />
				</form>
				{#each items as item}
					<li>
						<div class="row">
							<div class="col-12">
								<input name="completeBox" id="completeBox{item.id}" type="checkbox" bind:checked={item.done}>	
								<label for="completeBox{item.id}" class="completeLabel">
									<small class="text-muted">{item.done ? '' : 'in'}complete</small>
								</label>
								</div>
							<div class="col-8 {item.done ? 'done' : ''}">
								<span class="name">{item.name}</span>
							</div>
							<div class="col-4">				
								<button class="remove btn-transparent" on:click={()=> remove(item)}>❌</button>
							</div>
						</div>
					</li>
				{/each}
			</ul>
		</div>
	</div>

