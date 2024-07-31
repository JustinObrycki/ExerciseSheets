<script context="module">
        // main navigation for the application
        import Monday from './Monday.svelte';
        import Tuesday from './Tuesday.svelte';
        import Wednesday from './Wednesday.svelte';
        import Thursday from './Thursday.svelte';
        import Friday from './Friday.svelte';
        import Saturday from './Saturday.svelte';
        import Sunday from './Sunday.svelte';


    
        
        // these are our 'pages' to navigate through (in order for this export to work the script tag MUST include context="module")
        export const navOptions = [
                { page: 'Monday',   component: Monday },
                { page: 'Tuesday', component: Tuesday },
                { page: 'Wednesday', component: Wednesday },
                { page: 'Thursday', component: Thursday },
                { page: 'Friday', component: Friday },
                { page: 'Saturday', component: Saturday },
                { page: 'Sunday', component: Sunday }
                // other navigation pages can go here
        ];
        </script>