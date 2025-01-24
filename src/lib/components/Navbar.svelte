<script>
    // Optional: Define your navigation links
    export let links = [];
  </script>
  
  <nav>
    <p id="title">CodingTree</p>
    <ul id="navBar">
      {#each links as { href, text }}
        <li >
          <a class="navBarLink" href={href}>{text}</a>
        </li>
      {/each}
    </ul>
  </nav>
  
  <style>
    nav {
      height: 10vh;
      background: #333;
      color: #fff;
      padding: 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
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
        margin-left: 1rem;
        font-size: 2rem;
        color: greenyellow;
    }
    #navBar{
        margin-right: 2rem;
    }
    .navBarLink{
        text-decoration: none;
    }
    .navBarLink:hover{
        font-weight: bold;
        color: greenyellow;
        text-decoration: none;
    }
  </style>
  