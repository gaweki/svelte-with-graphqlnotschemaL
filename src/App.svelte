<script>
	import { Router, Link, Route } from "svelte-routing";
	import NavLink from "@/components/navlink";
	import ProductNew from "@/pages/product-new";
	import Homepage from "@/pages/homepage";

	import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  const client = new ApolloClient({
    uri: __apps__.env.baseUrl
  })
  setClient(client)

	export let url = "";
</script>

<style global>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>

<Router url="{url}">
  <div>
    <Route path="product-new" component="{ProductNew}" />
    <Route path="/"><ProductNew /></Route>
  </div>
</Router>
