<script>
    import { fly, scale } from "svelte/transition";
	import {bounceInOut} from "svelte/easing";
    export let sneaker = {};
	let animate = false;
	const toggleAnimation = () => {
		animate = !animate;
	}
    $: style = `
        text-align: center;
        transform: translateY(${animate ? '-10' : ''}px);
    `
    let sneakerStyle = `
        background-color: ${sneaker.background};
		padding: 20px;
        cursor: pointer;
        position: relative;
        padding-bottom: 50px;
    `
</script>
<div class="col-6 p-0" on:mouseenter="{toggleAnimation}" on:mouseleave="{toggleAnimation}">
    <div style="{sneakerStyle}">
        {#if animate}
            <p transition:scale="{{start: 0, easing: bounceInOut}}" class="price">${sneaker.price}</p>
        {/if}
        <div style="{style}">
            <img src="{sneaker.image}" alt="{sneaker.name}" />
        </div>
        {#if animate}
            <p class="name" transition:fly={{ y: -12 }}>{sneaker.name}</p>
        {/if}
    </div>
</div>
<style>
	.price{
		width: 25px; 
		height: 25px; 
		display: flex; 
		align-items: center; 
		justify-content: center; 
		background-color: rgb(134, 134, 134);
		padding: 20px;
		border-radius: 50%;
		color: #fff;
		position: absolute;
        font-weight: 600;
	}
	.name{
		text-align: center;
		color: rgb(78, 78, 78);
		font-weight: 600;
        position: absolute;
        left: 0;
        right: 0;
	}
</style>