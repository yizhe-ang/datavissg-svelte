<script>
	export let id = null;
	export let animate = true;
	export let restart = false;
  export let attrs = {}
</script>

<section
	data-auto-animate-id={id}
	data-auto-animate={animate || null}
	data-auto-animate-restart={restart || null}
  data-transition="fade"
  {...attrs}
>
	<slot />
</section>

<style>
  section {
    height: 100%;
    width: 100%;
  }
</style>
