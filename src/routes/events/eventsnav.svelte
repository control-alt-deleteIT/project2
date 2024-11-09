<script>
  import logo from '/logo.png';
  let navItems = [
    { name: "Home", href: "/home", icon: "fas fa-home", label: "Home" },
    { name: "Events", href: "/events", icon: "fas fa-calendar", label: "Events" },
  ];
</script>

<div class="fixed w-full h-20 top-0 px-8 flex items-center justify-between bg-transparent z-10 py-2 transition-all duration-300">
  <!-- Logo on the Left with Link to Home -->
  <div class="logo">
    <a href="/">
       <img src={logo} alt="EventNex Logo" class="w-24 h-auto" /> <!-- Reduced logo size -->
    </a>
  </div>

  <!-- Buttons on the Right -->
  <div class="flex space-x-3">
    <!-- Dashboard Button -->
    <a href="/home" class="flex items-center text-[#FFFFFF] font-semibold text-base px-3 py-1.5 rounded-lg hover:text-white transition">
       <i class="fas fa-home mr-2 text-[#f7941d]"></i>
       <span>Dashboard</span>
    </a>

    <!-- Events Button -->
    <a href="/events" class="flex items-center text-[#FFFFFF] font-semibold text-base px-3 py-1.5 rounded-lg hover:text-white transition">
       <i class="fas fa-calendar-alt mr-2 text-[#f7941d]"></i>
       <span>Events</span>
    </a>
  </div>
</div>