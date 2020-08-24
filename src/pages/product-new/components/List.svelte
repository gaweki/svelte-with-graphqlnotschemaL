<script>
  import { onMount } from "svelte"
  import Products from "./Products.svelte"

  import { getClient, query } from 'svelte-apollo';
  import { gql } from 'apollo-boost';

  const PRODUCTS = gql`{
  products {

    supplier_code,
      supplier_name,
      location,
      total_sold,
      image_name,
      product_slug,
      product_code,
      product_name,
      variant_id,
      variant_descriptions,
      variant_stock,
      product_stock,
      sku,
      main_menu_id,
      sub_menu_id,
      sub_menucategory_id,
      mainmenu_name,
      submenu_name,
      sub_menucategory_name,
      mainmenu_slug,
      submenu_slug,
      submenu_category_slug,
      normal_price,
      agent_price,
      member_price,
      agent_commision,
      wajib_insurance,
      product_warranty,
      product_condition,
      product_original,
      discount_percentage,
      comission_percentage,
      is_rfc,
      total_view,
      image_uri,
      created,
      updated_at
    }

  }`

  const client = getClient()

  let page = 1;
  const limit = 24;
  let datas = {};
  let loading = {
      loading1: false
    };
  let loadingGlobal = true;
  let arrPage = []

  onMount(async () => {
    loading = {
      ...loading,
      loading1: true
    }
    arrPage.push(page)
    
    try{
      let result
      const raw = await query( client, { query: PRODUCTS })

      raw.result().then(function(res){
        result = res.data.products.slice(0, 24);
        datas = {
          ...datas,
          datas1: res.data.products.slice(0, 24)
        }
        loading = {
          ...loading,
          loading1: false
        }
        loadingGlobal = false
      })

    } catch(e){
      if(e) console.log(e)
    }
  });

  const handleLookMore = async () => {
    let nPage = page+1
    loading = {
        ...loading,
        ["loading"+nPage]: true,
    }
    datas = {
      ...datas,
      ["datas"+(nPage)]: [],
    };
    arrPage.push(nPage)

    loadingGlobal = true

    try{
      let result
      const raw = await query( client, { query: PRODUCTS })

      raw.result().then(function(res){
        result = res.data.products.slice(page*24, (page*24)+24);
        datas = {
          ...datas,
          ["datas"+nPage]: res.data.products.slice(page*24, (page*24)+24)
        }
        loading = {
          ...loading,
          ["loading"+nPage]: false
        }
        loadingGlobal = false
      })

    } catch(e){
      if(e) console.log(e)
    }

    page = nPage;
  };

  // let showMore =
  //   products && meta && products.length < meta.total ? true : false;

</script>

<style type="text/scss">
  .container-list{
    display: flex;
    flex-wrap: wrap;
  }
  button{
    display: inline-block;
    margin-bottom: 0px;
    line-height: 1.42857;
    text-align: center;
    white-space: nowrap;
    vertical-align: middle;
    touch-action: manipulation;
    cursor: pointer;
    user-select: none;
    color: rgb(237, 48, 44);
    font-weight: 700;
    font-size: 16px;
    border-radius: 4px;
    border-width: 2px;
    border-style: solid;
    border-color: rgb(237, 48, 44);
    border-image: initial;
    background: rgb(255, 255, 255);
    padding: 10px 49.5px;
    outline: none;
  }
  .button-container{
    text-align: center;
    width: 100%;
    margin: 20px 0px;
  }
</style>

<div class="container-list">
  {#each arrPage as seq}
    <Products datas={datas["datas"+seq]} />
  {/each}
  <div class="button-container">
    {#if !loadingGlobal}
      <button on:click={handleLookMore}>Lihat Lainnya</button>
    {/if}
  </div>
</div>