<style>
    exercise-card {
    display: grid;
    max-height: 100%;
    max-width: 100%;
    margin: 20px;
    padding: 20px;
    grid-template:
    "Exercise Exercise Completion" 40px
    "Sets Reps Reps" 40px
    "Warmup Max Max" 40px
    "delete delete delete" 40px
    ;
    justify-items: start;
    box-shadow: 1px 1px 10px 0px #b2b2b2;
    border-radius: 10px;
    align-items: center;
    justify-content: space-between;
    background-color: white;

}
exercise-card .Exercise {
    grid-area: Exercise;

}

exercise-card .Sets {
    grid-area: Sets;

}

exercise-card .Reps {
    grid-area: Reps;

}

exercise-card .Warmup {
    grid-area: Warmup;
}

exercise-card .Max {
    grid-area: Max;
  
}

exercise-card .Completion {
    grid-area: Completion;
    width: 50px;
    height: 50px;
}

exercise-card .delete {
    grid-area: delete;
    margin: auto;
    
}

</style>

<script>
    import { createEventDispatcher } from 'svelte';
    let send_event = createEventDispatcher()

    export let exercise

    let delete_exercise = function(){
        send_event("delete", {exercise_to_delete: exercise})
    }

    let notifyOfChange = function(){
        send_event("change",{exercise_to_delete: exercise})
    }

</script>

<exercise-card class:completed={exercise.done}>
    <p class="Exercise">Exercise: <input type="text" bind:value={exercise.text} on:change={notifyOfChange}/></p>
    <input type="checkbox" class="Completion" bind:checked={exercise.done} on:change={notifyOfChange}/>
    <p class="Sets">Sets: <input type="number" bind:value={exercise.number} on:input={notifyOfChange}/></p>
    <p class="Reps">Reps: <input type="number" bind:value={exercise.number} on:input={notifyOfChange}/></p>
    <p class="Warmup">Warmup: <input type="number" bind:value={exercise.number} on:input={notifyOfChange}/></p>
    <p class="Max">Max: <input type="number" bind:value={exercise.number} on:input={notifyOfChange}/></p>
    <button class="delete" on:click={delete_exercise}>X</button>
</exercise-card>
