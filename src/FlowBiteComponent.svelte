<script>
    export let jp_props;

  import { AccordionItem } from 'flowbite-svelte';
  import { Accordion } from 'flowbite-svelte';
  
  import { Alert }	from 'flowbite-svelte';
  import { Avatar } from 'flowbite-svelte';
import { Badge } from 'flowbite-svelte';
import { Banner } from 'flowbite-svelte';

import { Breadcrumb } from 'flowbite-svelte';
import { Button } from 'flowbite-svelte';
import { ButtonGroup } from 'flowbite-svelte';
import { Card } from 'flowbite-svelte';
import { Dropdown } from 'flowbite-svelte';



  import { InfoCircleSolid } from 'flowbite-svelte-icons';
  import Htmlcomponent from './Htmlcomponents.svelte';
  import SVGComponent from './SVGComponent.svelte';
  console.log("in FlowBiteComponent with jp_props");
  console.log(jp_props);

  const fb_components = {
   'AccordionItem': AccordionItem,
   'Accordion': Accordion,
   'Avatar': Avatar,
    'Alert': Alert,
    'Badge': Badge,
    'Banner': Banner,
    'Breadcrumb': Breadcrumb,
    'Button': Button,
    'ButtonGroup': ButtonGroup,
    'Card': Card,
    'Dropdown': Dropdown,

  };
  const descriptionObject = {
    ...jp_props.attrs,
    class: jp_props.classes, 
  };
  
  console.log("Flowbite description object");
  console.log(jp_props.attrs);
   console.log(jp_props.classes);
  console.log(descriptionObject)

  let components = {'html_component': Htmlcomponent,
                    'svg_component': SVGComponent
                    
                    };
		    
</script>



<svelte:component  this={fb_components[jp_props.html_tag]} {...descriptionObject}>
{#each jp_props.object_props as cobj_props}
  {#if cobj_props.vue_type === "html_component"}
    <svelte:component this={Htmlcomponent} jp_props={cobj_props}/>
  {:else if jp_props.vue_type === "flowbite_component"}
  <svelte:self jp_props={cobj_props}/>
  {:else}
    <svelte:component this={components[cobj_props.vue_type]} jp_props={cobj_props} />
  {/if}
{/each}

</svelte:component>


