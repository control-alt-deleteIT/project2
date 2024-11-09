<script>
  import "/src/app.css";

  let navItems = [
    { name: "Dashboard", href: "/project2/home", icon: "fas fa-home", label: "Dashboard" },
    { name: "Events", href: "/project2/events", icon: "fas fa-calendar-alt", label: "Events" },
  ];
</script>

<div class="fixed w-full h-20 top-0 px-8 flex items-center justify-between bg-transparent z-10 py-2 transition-all duration-300">

  <div class="logo">
    <a href="/">
      <img src="/logo.png" alt="EventNex Logo" class="w-24 h-auto" />
    </a>
  </div>

  <div class="flex gap-4">
    {#each navItems as item}
      <a
        href={item.href}
        class="flex items-center text-[#FFFFFF] text-xl font-semibold px-3 py-2 rounded-lg transition-all duration-300 hover:text-[#f7941d] hover:bg-[#ffffff22]"
        aria-label={item.label}
      >
        <i class={`${item.icon} mr-2 text-[#f7941d]`}></i>
        <span>{item.name}</span>
      </a>
    {/each}
  </div>
</div>