<script>
  import { fade } from 'svelte/transition';
  import Style from '../../internal/Style';

  let klass = '';
  export { klass as class };
  export let width = '256px';
  export let active = true;
  export let fixed = false;
  export let absolute = false;
  export let right = false;
  export let mini = false;
  export let clipped = false;
  export let noBorder = false;
  export let miniWidth = '56px';
  export let clippedHeight = '56px';
  export let transition = fade;
  export let transitionOpts = {};
  export let style = null;

  if (mini) width = miniWidth;
</script>

<style lang="scss" src="./NavigationDrawer.scss">
</style>

<aside
  class="s-navigation-drawer {klass}"
  transition:transition={transitionOpts}
  class:active
  class:fixed
  class:absolute
  class:right
  class:mini
  class:clipped
  on:hover
  use:Style={{ 'nav-width': width, 'nav-clipped-height': clippedHeight }}
  {style}>
  <slot name="prepend" />
  <div class="s-navigation-drawer__content">
    <slot />
  </div>
  <slot name="append" />
  {#if !noBorder}
    <div class="s-navigation-drawer__border" />
  {/if}
</aside>
