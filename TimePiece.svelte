<svelte:options tag="time-piece" />

<script>

  let timezone = $$props["time-zone"] || $$props["timezone"];
  let secondHand = $$props["second-hand"] || true;

  const getLocaleTime = () => new Date(new Date(new Date().toUTCString()).toLocaleString("en-US", {
      timeZone: timezone,
    }));

  const getSystemTime = () => new Date();
  const getTime = timezone ? getLocaleTime : getSystemTime;

  let time = getTime();

  const interval = setInterval(() => {
    time = getTime();
  }, 1000);

  $: hours = time.getHours();
  $: minutes = time.getMinutes();
  $: seconds = time.getSeconds();

</script>

<svg class="clock" viewBox="-50 -50 100 100">
  <circle class="clock-face" r="48" />

  {#if secondHand}
    <g transform="rotate({6 * seconds})">
      <line class="seconds-hand" y1="4" y2="-40" />
    </g>
  {/if}

  <line
    class="hours-hand"
    y1="4"
    y2="-24"
    transform="rotate({30 * hours + minutes / 2})"
  />

  <line
    class="minutes-hand"
    y1="4"
    y2="-40"
    transform="rotate({6 * minutes + seconds / 10})"
  />
</svg>

<style>

  svg.clock {
    width: var(--clock-size, 100%);
    height: var(--clock-size, 100%);
  }

  .clock-face {
    fill: var(--clock-face-fill, none);
    stroke: var(--clock-face-stroke, currentColor);
  }

  .clock-face,
  .hours-hand,
  .minutes-hand,
  .seconds-hand {
    stroke-width: var(--clock-stroke-width, 1.5);
  }

  .hours-hand,
  .minutes-hand {
    stroke: var(--clock-hand-stroke, currentColor);
  }

  .seconds-hand {
    stroke: var(--clock-seconds-color, orange);
  }

</style>