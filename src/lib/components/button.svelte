<script lang="ts">
	import { page } from "$app/stores";
	import RandomBg from "./randomBg.svelte";
    import Text from "./text.svelte";

    export let text = "click_me!";
    export let clickAction = () => {console.log("clicked!");};
    export let didntClickAction = () => {console.log("didn't click!");};
    function onClick(e: MouseEvent) {
        e.preventDefault();
        
        if (window.confirm("are you sure you clicking me?")) {
            window.open($page.url.origin)
            alert("you clicked me!");
            clickAction();
        } else {
            window.open($page.url.origin)
            alert("you didn't click me!");
            didntClickAction();
        }
    }

    function prank(e: KeyboardEvent) {
        e.preventDefault();
        if (e.key !== "Enter") return;
        alert("you've been pranked! this is not the real button!");
    }

    let x = 0;
    let y = 0;
    let running = false;

    function mousemove(e: MouseEvent) {
        x += e.movementX;
        y += e.movementY;
    }
</script>
<button class="relative"
    on:click={(e)=>{e.preventDefault();}}
    on:keypress={prank}
>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class={`${running ? " absolute" : ""} py-5 -my-5 mx-10`}
        style={`top: ${y}px; left: ${x}px;`}
        on:mousemove={mousemove}
        on:mouseenter={() => running = true}
        on:mouseleave={() => {running = false; x = 0; y = 0;}}
    >
        <RandomBg animated shadowed>
            <button on:click={onClick} class="  outline-none -mx-10">
                <Text {text} animated/>
            </button>
        </RandomBg>
    </div>
</button>