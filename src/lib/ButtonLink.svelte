<script lang='ts'>
  export let href: string = ''
  export let target: string = '_blank'
</script>

<a {href} {target} class='px-6 py-3 bg-orange-100 rounded-md text-orange-900'><slot /></a>