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



</style>
<script>
    import { onMount } from 'svelte';
    import ExerciseCard from "./ExerciseCard.svelte";

 

    let exercise_list = []

    let save = function(){
        localStorage.setItem('Exercises_Monday', JSON.stringify(exercise_list))
    }

    let add_exercise = function(){
        exercise_list = [...exercise_list, {}]
        save()
    }

    let delete_exercise = function(event){
        let exercise_to_delete = event.detail.exercise_to_delete
        exercise_list = exercise_list.filter((t) => t !== exercise_to_delete)
        save()
    }

    onMount(() => {
        exercise_list = JSON.parse(localStorage.getItem('Exercises_Monday')) || []

    })

</script>



    <hr/>
    <div class="Exercise_sheet">
        <exercise-card>
            {#each exercise_list as exercise }
                <ExerciseCard exercise={exercise} on:delete={delete_exercise} on:change={save}></ExerciseCard>
            {/each}
        </exercise-card>
    </div>