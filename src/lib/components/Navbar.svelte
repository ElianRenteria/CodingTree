<script>
    // Optional: Define your navigation links
    export let links = [];
  </script>
  
  <nav>
    <div class="navBarLogo">
      <img src="/coding_tree_logo.png" alt="CodingTree Logo" id="logo"/>
      <p id="title">CodingTree </p>
    </div>
    <ul id="navBar">
      {#each links as { href, text }}
        <li >
          <a class="navBarLink dynamic-text" href={href}>{text}</a>
        </li>
      {/each}
    </ul>
  </nav>
  
  <style>
    nav {
      height: 10vh;
      background: var(--dynamic-bg-color);
      padding: 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: inset 0 -1px 0 0 var(--dynamic-shadow-color);
    }
  
    ul {
      list-style: none;
      display: flex;
      gap: 1rem;
      margin: 0;
      padding: 0;
      align-items: center;
    }
  
    a {
      color: inherit;
      text-decoration: none;
    }
  
    a:hover {
      text-decoration: underline;
    }
    #title{
        display: inline;
        padding: 0;
        margin: 0;
        font-size: 2rem;
        color: var(--pico-color-lime-250);
    }
    #navBar{
        margin-right: 2rem;
    }
    .navBarLink{
        font-size: 1.1rem;
        text-decoration: none;
        font-weight: 500;
    }
    .navBarLink:hover{
        color: var(--pico-color-lime-250);
        text-decoration: none;
    }
    #logo {
      width: 3rem;
      height: auto;
      display: inline;
      margin: 0;
      margin-left: 1rem;
      padding: 0;
      padding-bottom: .6rem;
    }
    .navBarLogo{
      display: flex;
      align-items: end;
    }
  </style>
  