<script>
  export let name;
  //Now using svelte.store https://svelte.dev/tutorial/writable-stores
  //export let justpyComponents;
  import { justpyComponents } from "./store.js";
  $: console.log('Store value:', $justpyComponents);
  var btncolor = "bg-green-200/50";

  import Htmlcomponent from './Htmlcomponents.svelte';
  import FlowBiteComponent from './FlowBiteComponent.svelte';
  import SVGComponent from './SVGComponent.svelte';  


  
//   let uno = false;
//   let dummy_props = {};
  let selected_component = Htmlcomponent;
  let components = {'html_component': Htmlcomponent,
  		    'flowbite_component': FlowBiteComponent,
		    'svg_component': SVGComponent
                    
                    };
</script>
  
{#each $justpyComponents as jpcomp}
  {#if jpcomp.vue_type === "html_component"}
    <svelte:component this={Htmlcomponent} jp_props={jpcomp}/>
  {:else}
    <svelte:component this={components[jpcomp.vue_type]} jp_props={jpcomp} />
  {/if}
  
  
{/each}



