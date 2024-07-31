<style>
    div.Exercise_sheet {
    overflow: scroll;
    height: 680px;
    overflow-x: hidden;
    
}

div.Exercises_for_today_box {
    margin-top: 10%;
    border: solid 2px black;
    text-align: center;
    font-size: 30px;
    width: 12%;
    margin-left: 43%;
    background-color: white;
}

week-header {
    display: grid;
    grid-template:
    "Day Day Day Day Day Day Day"
    ;
    justify-items: center;
}

week-header .Day {
    width: 100px;
    height: 100px;
    border: solid 2px black;
    border-radius: 50%;
    display: flex;
    text-align: center;
    align-items: center;
    justify-content: center;
    background-color: white;
}

current-day {
    text-align: center;
    font-size: 30px;
}
exercise-card {
    display: grid;
    
}

button.add_exercise {
    height: 40px;
}

footer-card {
    height: 100px;
    width: 100%;
    position: fixed;
    bottom: 0;
    display: grid;
    grid-template:
    "Exercises Home Schedule"
    ;
    font-size: 30px;
    
}

save-card {
    height: 100px;
    width: 100%;
    position: fixed;
    bottom: 0;
    display: block;
    font-size: 30px;
    background-color: white;
    border: 1px solid;
    text-align: center;
    align-items: center;
    justify-content: center;
    margin: 0;

}
</style>
<script>
    import { onMount } from 'svelte';
    import ExerciseCard from "../lib/ExerciseCard.svelte";

    let save = function(){
        localStorage.setItem('exercises', JSON.stringify(exercise_list))
    }

    let exercise_list = []

    let add_exercise = function(){
        exercise_list = [...exercise_list, {done: false, text: ""}]
        save()
    }

    let delete_exercise = function(event){
        let exercise_to_delete = event.detail.exercise_to_delete
        exercise_list = exercise_list.filter((e) => e !== exercise_to_delete)
        save()
    }

    onMount(() => {
    task_list = JSON.parse(localStorage.getItem('exercises')) || []

    })

    let change_day_to = function(event){
        let current_day = event.detail.current_day
        
    }
</script>



<body>
    <week-header>
        <button class="Day" on:click={change_day_to}>Sunday</button>
        <button class="Day" on:click={change_day_to}>Monday</button>
        <button class="Day" on:click={change_day_to}>Tuesday</button>
        <button class="Day" on:click={change_day_to}>Wednesday</button>
        <button class="Day" on:click={change_day_to}>Thursday</button>
        <button class="Day" on:click={change_day_to}>Friday</button>
        <button class="Day" on:click={change_day_to}>Saturday</button>
    </week-header>
    <hr/>
    <current-day>
        <p>Exercises for Monday</p>
    </current-day>
    <hr/>
    <div class="Exercise_sheet">
        <exercise-card>
            {#each exercise_list as exercise }
                <ExerciseCard exercise={exercise} on:delete={delete_exercise} on:change{save}></ExerciseCard>
            {/each}
    
            <button class="add_exercise" on:click={add_exercise}>+ Add Exercise</button>
        </exercise-card>
    </div>
    
    
    <save-card>
        <p class="Exercises">Save Exercises</p>
    </save-card>
    </body>