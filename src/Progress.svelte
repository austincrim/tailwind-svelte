<script>
    export let percentComplete = 0;
  </script>

<style>
    .progress-bar {
        transition: width .5s ease-in-out;
    }
</style>

<div class="w-2/3 mx-auto mb-10">
  <div style={`width: ${percentComplete}%`} class="h-4 rounded-lg bg-orange-300 progress-bar" />
</div>
