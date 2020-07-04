<script>
    export let percentComplete = 0;
</script>


<div class="w-2/3 mx-auto mb-10">
    <div
        style={`width: ${percentComplete}%`}
        class={`h-4 rounded bg-orange-300 transition-all duration-300 ease-in-out ${percentComplete === 100 && `bg-green-500`}`} 
    />
</div>
