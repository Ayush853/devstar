<script>
	import { Button } from 'flowbite-svelte';

	// @ts-ignore
	import sqlFormatterPlus from 'sql-formatter-plus';

	let sqlInput = '';
	let formattedSql = '';

	const formatSql = () => {
		try {
			formattedSql = sqlFormatterPlus.format(sqlInput);
		} catch (error) {
			// @ts-ignore
			formattedSql = `Error formatting SQL: ${error.message}`;
		}
	};
</script>

<main>
	<h1 class="mb-3 text-gray-500 white:text-gray-400">SQL Formatter</h1>

	<label class="mb-3 text-gray-500 white:text-gray-400">Input SQL Script:</label>
	<textarea
		bind:value={sqlInput}
		id="sqlInput"
		rows="10"
		cols="30"
		class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
		placeholder="Enter your sql script here..."
	/>

	<center><Button color="blue" class="mr-1" on:click={formatSql}>Format SQL</Button></center>

	<h1 class="mb-3 text-gray-500 white:text-gray-400" />
	<label class="mb-3 text-gray-500 white:text-gray-400"> Formatted SQL :</label>
	<textarea
		id="formattedSql"
		rows="10"
		cols="30"
		class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
		readonly>{formattedSql}</textarea
	>
</main>

<style>
	main {
		text-align: center;
		margin: 2rem;
	}

	textarea {
		margin: 1rem;
	}
</style>
