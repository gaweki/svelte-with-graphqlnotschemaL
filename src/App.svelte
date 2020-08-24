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

<Router url="{url}">
  <div>
    <Route path="product-new" component="{ProductNew}" />
    <Route path="/"><Homepage /></Route>
  </div>
</Router>
