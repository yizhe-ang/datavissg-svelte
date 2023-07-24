<script>
  export let id = null;
  export let context;
  export let linkText;
  export let linkUrl;
</script>

<div data-id={id}>
  {context}
  <a href={linkUrl} target="_blank" rel="noopener noreferrer">
    {linkText}
  </a>
</div>

<style>
  div {
    padding: 2px 12px;
    border-radius: 5px;
    display: inline-block;
    /* transform: translate(0, 30em); */
    position: absolute;
    bottom: 0;
    left: 0;
    font-size: 0.5em;
    background-color: var(--r-background-color);
  }

  a {
    font-weight: 600;
  }
</style>
