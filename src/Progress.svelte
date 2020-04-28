<script>
  export let percentComplete = 0;
</script>

<style>
  .progress-bar {
    transition: width 0.5s ease-in-out;
  }

  .complete {
    animation: flash 2s;
    animation-iteration-count: infinite;
  }

  @keyframes flash {
    0% {
      @apply bg-orange-300;
    }
    50% {
      @apply bg-indigo-500;
      transform: scale(1.1);
    }
    100% {
      @apply bg-orange-300;
      transform: scale(1);
    }
  }
</style>

<div class="w-2/3 mx-auto mb-10">
  <div
    style={`width: ${percentComplete}%`}
    class={`h-4 rounded-lg bg-orange-300 progress-bar ${percentComplete == 100 ? 'complete' : ''}`} />
</div>
