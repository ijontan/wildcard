<script>
	import Text from "./text.svelte";
    import Button from "./button.svelte";
    let day = 1;
    let month = 1;
    let year = 2000;
    export let value = "1-1-2000";

    $: value = `${day}-${month}-${year}`;

    function resetValue(){
        day = 1;
        month = 1;
        year = 2000;
    }
</script>

<div class="flex flex-col">
    <div class="flex">
        <Text text="choose Date" center/>
        <Text text={value}/>
    </div>
    <div class="flex">
        <Button text="day -" clickAction={() => {day--;}} didntClickAction={resetValue} />
        <Button text="day +" clickAction={() => {day++;}} didntClickAction={resetValue} />
    </div>
    <div class="flex">
        <Button text="month -" clickAction={() => {month--;}} didntClickAction={resetValue} />
        <Button text="month +" clickAction={() => {month++;}} didntClickAction={resetValue} />
    </div>
    <div class="flex">
        <Button text="year -" clickAction={() => {year--;}} didntClickAction={resetValue} />
        <Button text="year +" clickAction={() => {year++;}} didntClickAction={resetValue} />
    </div>
</div>