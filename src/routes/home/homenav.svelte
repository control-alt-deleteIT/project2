<script>
    import "/src/app.css";
  
    let navItems = [
      { name: "Home", href: "/home", icon: "fas fa-home", label: "Home" },
      { name: "Events", href: "/events", icon: "fas fa-calendar", label: "Events" },
    ];
  </script>
  
  <div class="flex items-center justify-between bg-pink-600 shadow-md p-4">
    <h1 class="text-4xl font-bold text-white uppercase transform transition-transform duration-300 hover:scale-105">EventNex</h1>
    <div class="flex gap-4">
      {#each navItems as item}
        <a href={item.href} class="text-white text-2xl transition-all duration-300 hover:text-pink-200 p-3 rounded-full" aria-label={item.label}>
          <i class={item.icon}></i>
        </a>
      {/each}
    </div>
  </div>
  
  