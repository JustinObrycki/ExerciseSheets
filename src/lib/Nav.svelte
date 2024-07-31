<script context="module">
    // main navigation for the application
    import Sunday from './Monday.svelte';

    
    // these are our 'pages' to navigate through (in order for this export to work the script tag MUST include context="module")
    export const navOptions = [
            { page: 'Monday',   component: Sunday }
            // other navigation pages can go here
    ];
    </script>