<script>
    import { quintOut } from 'svelte/easing';
	import { crossfade } from 'svelte/transition';

	const [send, receive] = crossfade({
		fallback(node, params) {
			const style = getComputedStyle(node);
			const transform = style.transform === 'none' ? '' : style.transform;

			return {
				duration: 600,
				easing: quintOut,
				css: t => `
					transform: ${transform} scale(${t});
					opacity: ${t}
				`
			};
		}
	});

    export let todo
    export let todos
    let isEdit = false
    let title = ''
    function onEdit(){
        isEdit = true
        title = todo.title
    }
    function deleteTodo(){
        $todos = $todos.filter(t=> t.id !== todo.id)
    }
    function updateTodo(){
        todo.title = title
        offEdit()
    }
    function offEdit(){
        isEdit = false
    }
    function refreshTodos(){
        $todos = $todos
    }
</script>

{#if isEdit}
    <div>
        <input type="text" bind:value={title}
               on:keydown={(e)=>{e.key === 'Enter' && updateTodo()}}/>
        <button on:click={updateTodo}>OK</button>
        <button on:click={offEdit}>Cancel</button>
    </div>
{:else}
    <div>
        <label in:receive="{{key: todo.id}}"
                out:send="{{key: todo.id}}"
        >
        <input type=checkbox bind:checked={todo.done} on:change={refreshTodos}/>
        {todo.title}
        <button on:click={onEdit}>Edit</button>
        <button on:click={deleteTodo}>Delete</button>
        </label>
    </div>
{/if}
