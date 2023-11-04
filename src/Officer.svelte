<script>
  import { Card } from "spaper";
  import { Github} from "@icons-pack/svelte-simple-icons";
  import Icon from "@iconify/svelte";

  export let image;
  export let name;
  export let title;
  export let mail, website, github, linkedin;
  export let description;
</script>


<Card {image} imageAlt="{name}'s pic" width="15em" style="z-index:1">
  
  <span slot="title" class="text-warning">
    {name}
  </span>
  
  <span slot="subTitle" class="text-danger">
    {title}
  </span>

  <p style="color: whitesmoke">{description}</p>
  <p slot="bottom" class="links">
    
    {#if github}
      <a href={github} target="_blank">
        <span class="icon"><Github/></span>
      </a>
    {/if}

    {#if mail}
      <a href={"mailto:" + mail}>
        <span class="icon"><Icon icon="ci:mail" /></span>
      </a>
    {/if}

    {#if website}
      <a href={website} target="_blank">
        <span class="icon"><Icon icon="ci:window-code-block" /></span>
      </a>
    {/if}

    {#if linkedin}
        <a href={linkedin} target="_blank">
            <span class="icon"><Icon icon="mdi:linkedin"/></span>
        </a>
    {/if}  
  </p>
</Card>


<style>

  .links {
    margin-top: 2rem;
    display: flex;
    text-decoration: none;
    gap: 0.75rem;
  }

  a {
    background-image: none;
    margin: 0 !important;
  }

  .icon {
    /* font-size: 30px; */
    color: whitesmoke;
  }
  .icon:hover {
    color: #e74b36 ;
  }
  .links,

  :global(svg) {
    height: 30px;
    width: 30px;
  }
  .text-warning {
    color: whitesmoke;
  }
  
  .text-danger {
    color: #e74b36;
  }
</style>
