<script>
    // Optional: Define your navigation links
    export let links = [];
  </script>
  
  <nav>
    <p>Coding Tree</p>
    <ul>
      {#each links as { href, text }}
        <li>
          <a href={href}>{text}</a>
        </li>
      {/each}
    </ul>
  </nav>
  
  <style>
    nav {
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
    p{
        display: inline;
        margin-right: 2rem;
    }
  </style>
  