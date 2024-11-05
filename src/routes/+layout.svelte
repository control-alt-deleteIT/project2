<script>
    import "../app.css";
  
    let navItems = [
      { name: "Home", href: "/project2/home" },
      { name: "Events", href: "/project2/events" },
      { name: "Contacts", href: "/project2/contacts" },
    ];
  </script>
  
  <div class="navbar">
    <h1 class="brand">EventNex</h1>
    <nav>
      {#each navItems as item}
        <a href={item.href} class="nav-link">{item.name}</a>
      {/each}
    </nav>
  </div>
  
  <main>
    <slot />
  </main>
  