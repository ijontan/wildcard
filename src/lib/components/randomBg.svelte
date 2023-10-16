<script>
	import { onMount } from "svelte";

    export let animated = false;
    export let shadowed = false;

    let style = '';
    onMount(() => {
        randomStyle();
        if (!animated) return;
        setInterval(() => {
            randomStyle();
        }, Math.random() * 900 + 100);
    })
    function randomStyle(){
        style = `
            background-color: rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255});
        `;
    }
</script>

    <div class={` transition-all duration-75 ${shadowed ? " shadow-2xl": ""}`} style={style}>
        <slot/>
    </div>