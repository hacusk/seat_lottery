<script>
	let column = 2;
	let input = "輿水,星,姫川,白坂,小早川";
	let table = [];

	const draw = () => {
		table = [];
		const member = input.split(',');
		const len = member.length;

		if (column > 1) {
			for(let i = 0; i < Math.ceil(len / column); i++){
				table[i] = [];
				for(let j = 0; j < column; j++){
					table[i][j] = '';
				}
			}
			let c = 0
			for(let i = 0; i < len; i++) {
				const person = member.splice(Math.floor(Math.random() * member.length), 1)[0];
				if(i % column === 0) {
					table[c][i%column] = person;
				} else {
					table[c][i%column] = person;
				}
				if (i % column === column - 1) {
					c++;
				}
			}
		} else {
			for(let i = 0; i < len; i++) {
				const person = member.splice(Math.floor(Math.random() * member.length), 1);
				table[i] = person;
			}
		}
		console.log(table);
	}
</script>

<main>
	<div>
		<p>列数</p>
		<input type=number bind:value={column} min=1>
	</div>
	<div>
		<p>メンバー(カンマくぎり)</p>
		<input bind:value={input} />
	</div>
	<button on:click={draw}>抽選</button>
	<table border=1>
		<tbody>
			{#each table as tr}
				<tr>
					{#each tr as td}
						<td>{td}</td>
					{/each}
				</tr>
			{/each}
		</tbody>
	</table>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		justify-content: center;
		display: flex;
		flex-direction: column;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>