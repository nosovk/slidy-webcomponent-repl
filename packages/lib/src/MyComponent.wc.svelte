<svelte:options tag="my-component"/>

<script lang="ts">
  import { slidy } from "@slidy/core";
  let items = [],
          index = 4,
          length = 9,
          position = 0,
          snap = 'center', flow = 'row', axis = 'x',
          played = false,
          timer = 0,
          duration = 375,
          loop = false;

  function onMove(e) {
    index = e.detail.index
    position = e.detail.position
  }
  function reload() {
    page = Math.trunc((Math.random()*100))
  }
  function play() {
    played = !played
    if (timer) clearInterval(timer)
    timer = played ? setInterval(() => {
      if(!loop && index === length -1) {
        clearInterval(timer)
        played = !played
      }
      index++
    }, duration) : 0
  }
  function looping() {
    loop = !loop
  }
  console.log("slidy")
</script>

<p>index: [<b>{index}</b>] position: <b>{Math.trunc(position)}</b>px</p>

<section style:--flow={flow}>
  <ul tabindex="0"
      role="listbox"
      use:slidy={{
				index,
				clamp: 0,
				indent: 1,
				sensity: 5,
				gravity: 1.2,
				duration,
				axis,
				snap,
				loop,
			}} on:move={onMove}>
    <slot></slot>
  </ul>
</section>

<nav>
  <button on:click={looping} class:active={loop}>loop</button>
  <button on:click={reload}>reload</button>
  <button on:click={play} class:active={played}>{played ? 'pause' : 'play'}</button>
</nav>

<style>
  section {
    overflow: hidden;
    height: 300px;
  }
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-flow: var(--flow) nowrap;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    width: 100%;
    height: 100%;
  }
  ul li {
    flex: 1 0 auto;
    width: auto;
    max-width: 100%;
    max-height: calc(100% - 2rem);
    height: 100%;
    position: relative;
    background: whitesmoke;
  }
  ul li:before {
    content: attr(id);
    position: absolute;
    bottom: 0;
    padding: 0.75rem 1rem;
    z-index: 1;
  }
  ul li img {
    width: 100%;
    width: auto;
    height: 100%;
    display: flex;
    object-fit: cover;
    max-width: 100%;
  }
  :global(nav) {
    display: flex;
    justify-content: center;
    margin: 1rem 0;
    flex-wrap: wrap;
    align-items: center;
    gap: 1rem
  }
  .active, b {color: red;}
  h1, p {
    text-align: center;
  }
  :global(body) {
    padding: 0;
  }
</style>
