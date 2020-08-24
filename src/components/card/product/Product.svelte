<script>
  import { navigate } from "svelte-routing";
  export let item;
  const { image_uri, normal_price, location, total_sold, product_slug, product_name, product_originial, product_warranty } = item
</script>

<style type="text/scss">
  .card-container{
    position: relative;
    width: 185px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 0px 3px;
    border-radius: 5px;
    padding: 10px;
    background: rgb(255, 255, 255);
    margin: 4px;
    min-height: 301px;
    max-height: 301px;
  }
  
  .product-image{
    max-height: 182.5px;
    border-top-left-radius: calc(0.25rem - 1px);
    border-top-right-radius: calc(0.25rem - 1px);
    object-fit: contain;
  }

  .image-container{
    margin-bottom: 11px;
    min-height: 182.5px;
  }

  .title-product{
    position: relative;
    font-size: 14px;
    text-overflow: ellipsis;
    height: 32px;
    margin-bottom: 0px;
    text-transform: capitalize;
    white-space: normal;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    color: rgb(80, 80, 80);
    font-weight: 700;
    overflow: hidden;
  }

  .price-product{
    padding-top: 0px;
    position: relative;
    font-weight: 700;
    color: rgb(237, 48, 44);
    height: 26px;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    margin-top: 8px;
    display: flex;
    justify-content: space-between;
  }
  
  .location{
    text-transform: capitalize;
    flex-grow: 1;
    width: 90px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    margin-right: 1px;
  }

  .sub-container-info-additional{
    color: #505050;
    font-size: 14px;
    position: absolute;
    display: flex;
    background-color: #fff;
    width: 100%;
    font-weight: 400!important;
    transition: opacity .2s linear;
  }

  .container-info-additional{
    position: relative;
  }
  
</style>

<div class="card-container">
  <div on:click={() => navigate(product_slug)} class="image-container" aria-label={product_name}>
    <img alt={product_name} class="product-image" src={`${image_uri}?x-oss-process=image/resize,m_pad,w_250,h_250/format,webp`} />
  </div>
  <div class="body">
    <div on:click={() => navigate(product_slug)} aria-label={product_name}  class="title-product">
      {product_name}
    </div>
    <div on:click={() => navigate(product_slug)} aria-label={product_name} class="price-product">Rp {normal_price.toLocaleString('id')}</div>
    <div class="container-info-additional">
      <div class="sub-container-info-additional" on:click={() => navigate(product_slug)} aria-label={product_name}>
        <span class="location">{location}</span>
        <span>Terjual: {total_sold}</span>
      </div>
    </div>
  </div>
  <div class="container-footer" on:click={() => navigate(product_slug)} aria-label={product_name}>
    {#if product_originial}
      <span>Ori 100%</span>
    {/if}
    {#if product_warranty}
      <span>Garansi</span>
    {/if}
  </div>
</div>