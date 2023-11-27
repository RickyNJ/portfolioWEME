<script lang="ts">
    import { createEventDispatcher } from "svelte";

	export let src: string;
    export let position: string;
    
    const dispatch = createEventDispatcher();

    function handleClick(){
        dispatch('clicked',{
            text: position
        });       
    }
</script>

<img {src} alt="person" on:click={handleClick}/>

<style>
	img {
		aspect-ratio: 3/4;
		width: 50vh;
		border-radius: 5%;
	}

	img:hover {
		transition: transform 0.3s ease;
        animation-delay: 150ms;
		transform: scale(1.05);
	}

    img:not(:hover){
        transition: transform 0.3s ease;
        
		transform: scale(1);
    }
</style>
