<script>
	import {writable} from 'svelte/store'
	import Todo from './Todo.svelte'
	let title = ''
	let todos = writable([])
	let id = 0
	function createTodo() {
		if(!title.trim()){
			return
		}
		$todos.push({
			id,
			title
		})
		// 할당을 통해 반응성을 유지하기 위해 svelte는 자기 자신을 할당하는 경우가 많다.
		$todos = $todos  
		title = ''
		id += 1
	}
</script>

<h1>Svelte Todo List</h1>
<input bind:value={title} type="text"
	   on:keydown={(e)=> {e.key === 'Enter' && createTodo() }} /> 
<button on:click={createTodo}> 
	Create Todo 
</button>
	{#each $todos as todo}
	<!-- bind로 props도 양방향 데이터 바인딩 가능! -->
	<!-- <Todo bind:todos={todos} todo={todo} /> -->

	<!-- todos 객체를 통체로 넘겨줘야 writable! -->
	<Todo todos={todos} todo={todo} />

	{/each}
