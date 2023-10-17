<script lang="ts">
	import { onMount } from "svelte";


    export let char = "k";
    export let animated = false;
    
    function randomStyle() {
        return `color: rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255});
                font-size: ${Math.random() * 5 +2}rem;
                font-weight: ${Math.random() * 900 + 100};
        `;
    }

    let rect: DOMRectReadOnly | null = null;
    let x = 0;
    let y = 0;

    let  vy = 0;
    let vx = 0;
    let gravity = 10;
    let prevTime = 0;
    let frame: number;
    
    onMount(() => {
        let frame = requestAnimationFrame(tick);
        return () => {
            cancelAnimationFrame(frame);
        }
    })

    function tick(){
        if (!rect) return;
        prevTime = Date.now();
        const now = Date.now();
        const dif = now - prevTime;
        const delta = dif / 1000;
        prevTime = now;

        vy += gravity * delta;
        y += vy * delta;
        x += vx * delta;
        // if (rect.bottom < window.innerHeight) {
        //     vy = -vy;
        //     y = window.innerHeight - rect.height;
        // }
        if (!animated) return;
        requestAnimationFrame(tick);
    }
</script>
<span bind:contentRect={rect}
    class={animated ? "fixed" : ""}
    style={`top: ${y}px; left: ${x}px; ${randomStyle()}`}
>
    {char}
</span>
