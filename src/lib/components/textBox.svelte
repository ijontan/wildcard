<script lang="ts">
	import RandomBg from "./randomBg.svelte";
	import Text from "./text.svelte";

    export let title = "title";
    export let value = "";

    function onClick(e: MouseEvent) {
        e.preventDefault();
        alert("you clicked me!");
        if (!confirm('are you sure you want to change the value?')) return;
        if (!confirm('are you really sure you want to change the value?')) return;
        if (!confirm('are you really really sure you want to change the value?')) return;
        value = prompt("enter new value", value) ?? value;
        alert("too bad this is not the real way to change the value!");
        value = '';
    }

    function onType(e: KeyboardEvent) {
        if (Math.random() < 0.8) return;
        value += e.key;
    }
</script>

<div class=" flex gap-5">
    <Text text={title +':'}/>
    <input type="text" class=" bg-transparent outline-none text-transparent placeholder:text-white/5" placeholder="click me to type" bind:value
        on:keypress={onType}
    />
</div>
<RandomBg>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class=" h-10" on:click={onClick}>
        <Text text={value}/>
    </div>
</RandomBg>