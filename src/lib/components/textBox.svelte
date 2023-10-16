<script lang="ts">
	import RandomBg from "./randomBg.svelte";
	import Text from "./text.svelte";

    export let title = "title";
    export let value = "";
</script>

<div class=" flex">
    <Text text={title +':'}/>
    <input type="text" class="opacity-0" bind:value/>
</div>
<RandomBg>
    <div class=" h-10">
        <Text text={value}/>
    </div>
</RandomBg>