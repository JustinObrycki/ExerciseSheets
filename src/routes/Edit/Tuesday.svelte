<style>
    div.Exercise_sheet {
    overflow: scroll;
    height: 680px;
    overflow-x: hidden;
    padding-bottom: 58px;
	min-height: 82vh;

    
}
exercise-card {
    display: grid;
    
    
}

button.add_exercise {
    height: 40px;
}


</style>
<script>
    import { onMount } from 'svelte';
    import ExerciseCard from "./ExerciseCard.svelte";

 

    let exercise_list = []

    let save = function(){
        localStorage.setItem('Exercises_Tuesday', JSON.stringify(exercise_list))
    }

    let add_exercise = function(){
        exercise_list = [...exercise_list, {}]
        save()
    }

    let delete_exercise = function(event){
        let exercise_to_delete = event.detail.exercise_to_delete
        exercise_list = exercise_list.filter((e) => e !== exercise_to_delete)
        save()
    }

    onMount(() => {
        exercise_list = JSON.parse(localStorage.getItem('Exercises_Tuesday')) || []

    })

</script>



    <hr/>
    <div class="Exercise_sheet">
        <exercise-card>
            {#each exercise_list as exercise }
                <ExerciseCard exercise={exercise} on:delete={delete_exercise} on:change={save}></ExerciseCard>
            {/each}
    
            <button class="add_exercise" on:click={add_exercise}>+ Add Exercise</button>
        </exercise-card>
    </div>
    
    