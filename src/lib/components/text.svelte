<script>
	import { onMount } from "svelte";

    export let text = "Hello World!";
    export let animated = false;
    export let minSize = 1;
    export let center = false;
    let count = 0;

    $: chars = text.split("");

    onMount(() => {
        if (!animated) return;
        setInterval(() => {
            count++;
        }, 300);
    })

    function randomStyle() {
        return `color: rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255});
                font-size: ${Math.random() * 2 *minSize + minSize}rem;
                font-weight: ${Math.random() * 900 + 100};
        `;
    }

    function onClick() {
        text = text.split("").reverse().join("");
    }
</script>

<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
{#key count}
<p
    class={`flex ${center?"items-center": ""}`}
on:click={onClick}
>
{#each chars as char}
<span class=" tracking-tighter whitespace-pre" style={randomStyle()}>{char}</span>
{/each}
</p>
{/key}