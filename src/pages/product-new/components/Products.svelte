<script>
  import Product from "@/components/card/product"
  export let datas 
</script>

{#each datas as data}
  <Product item={data} />
{/each}