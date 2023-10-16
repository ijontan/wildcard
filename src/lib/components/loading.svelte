<script>
	import { onMount } from "svelte";
	import Dialog from "./dialog.svelte";
	import RandomBg from "./randomBg.svelte";
	import Text from "./text.svelte";

    let text = ""
    let show = true;
    onMount(() => {
        setInterval(() => {
            text += "."
        }, 100)
    })
</script>

<Dialog show={show}>
    <RandomBg>
        <div class="w-screen h-screen grid justify-center items-center relative">
            <div class="flex">
                <Text text="loading" center/>
                <Text {text}/>
            </div>
            <button  class=" absolute top-0 right-0 opacity-10" on:click={()=>{show = false}}>
                <span>
                    stop loading
                </span>
            </button>
        </div>
    </RandomBg>
</Dialog>