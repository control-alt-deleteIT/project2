<script>
  import "../app.css";

  let navItems = [
    { name: "Home", href: "/project2/home", icon: "fas fa-home", label: "Home" },
    { name: "Events", href: "/project2/events", icon: "fas fa-calendar", label: "Events" },
  ];
</script>

<div class="header">
<h1 class="brand">EventNex</h1>
<div class="navbar-container">
  <div class="navbar">
    <nav>
      {#each navItems as item}
        <a href={item.href} class="nav-button" aria-label={item.label}>
          <i class={item.icon}></i>
        </a>
      {/each}
    </nav>
  </div>
</div>
</div>

<main>
<slot />
</main>
