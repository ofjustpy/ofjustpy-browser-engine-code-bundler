<script>
    export let jp_props;
    import Htmlcomponent from './Htmlcomponents.svelte';
    import FlowBiteComponent from './FlowBiteComponent.svelte';

  const descriptionObject = {
    ...jp_props.attrs,
    class: jp_props.classes, 
  };
  


  let components = {'html_component': Htmlcomponent,
                    'flowbite_component': FlowBiteComponent
                    };
		    
</script>
<svelte:options namespace='svg'/>


<svelte:element  this={jp_props.html_tag} {...descriptionObject}>
{#each jp_props.object_props as cobj_props}
  {#if cobj_props.vue_type === "svg_component"}
    <svelte:self  jp_props={cobj_props}/>
  {:else}
    <svelte:component this={components[cobj_props.vue_type]} jp_props={cobj_props} />
  {/if}
{/each}

</svelte:element>


