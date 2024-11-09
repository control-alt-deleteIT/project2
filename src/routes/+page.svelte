

<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>EventNex</title>
   <script src="https://cdn.tailwindcss.com"></script>
   <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</head>
 
 <body class="bg-gradient-to-r from-black via-[#0A1E3A] to-black min-h-screen m-0 p-0">
  <!-- Navbar -->
 <div class="fixed w-full h-20 top-0 px-8 flex items-center justify-between bg-transparent z-10 py-2 transition-all duration-300">
   <!-- Logo on the Left with Link to Home -->
   <div class="logo">
     <a href="/">
        <img src="/logo.png" alt="EventNex Logo" class="w-24 h-auto" /> <!-- Reduced logo size -->
     </a>
   </div>
 
   <!-- Buttons on the Right -->
   <div class="flex space-x-3">
     <!-- Dashboard Button -->
     <a href="/home" aria-label="Go to Dashboard" class="flex items-center text-[#FFFFFF] font-semibold text-base px-3 py-1.5 rounded-lg hover:text-white transition">
        <i class="fas fa-home mr-2 text-[#f7941d]"></i>
        <span>Dashboard</span>
     </a>
 
     <!-- Events Button -->
     <a href="/events" aria-label="View Events" class="flex items-center text-[#FFFFFF] font-semibold text-base px-3 py-1.5 rounded-lg hover:text-white transition">
        <i class="fas fa-calendar-alt mr-2 text-[#f7941d]"></i>
        <span>Events</span>
     </a>
   </div>
 </div>
 
 
   <!-- Main content container -->
   <div class="flex items-center justify-center min-h-screen text-[#C5C6C7] text-center px-4 mt-5"> <!-- Reduced top margin -->
     <div>
       <h1 class="text-4xl font-extrabold text-[#66FCF1] uppercase leading-tight mb-2">
          Transform Your Ideas
       </h1>
       <h1 class="text-4xl font-extrabold uppercase leading-tight mb-4">
          Into Reality with <span class="text-[#66FCF1] drop-shadow-[0_0_10px_#66FCF1]">EventNex</span>
       </h1>
       <p class="text-lg">Your Event Scheduling Platform</p>
     </div>
   </div>
 
  <!-- New Section: Introducing Our Website -->
 <section class="py-16 bg-[#1F2833] text-center text-[#C5C6C7]">
    <div class="max-w-4xl mx-auto">
      <h2 class="text-3xl font-semibold mb-6 text-[#66FCF1]">Introducing EventNex</h2>
      
  
      <!-- Short, Eye-Catching Caption -->
      <p class="text-xl mb-8">
        EventNex is your all-in-one event planning platform to create, manage, and track your events effortlessly.
      </p>
  
      <!-- Icon-Based Feature Highlights -->
      <div class="grid grid-cols-3 gap-12 mt-10">
        <!-- Feature 1 -->
        <div class="flex flex-col items-center">
          <i class="fas fa-calendar-alt text-5xl mb-3 text-[#f7941d]"></i>
          <h3 class="text-xl font-semibold text-[#66FCF1]">Easy Event Scheduling</h3>
          <p class="text-lg">Create events in minutes</p>
        </div>
 
        <!-- Feature 3 -->
        <div class="flex flex-col items-center">
          <i class="fas fa-check-circle text-5xl mb-3 text-[#f7941d]"></i>
          <h3 class="text-xl font-semibold text-[#66FCF1]">Seamless Event Management</h3>
          <p class="text-lg">Manage invites and RSVP effortlessly</p>
        </div>
  
        <!-- Feature 2 -->
        <div class="flex flex-col items-center">
          <i class="fas fa-users text-5xl mb-3 text-[#f7941d]"></i>
          <h3 class="text-xl font-semibold text-[#66FCF1]">Collaborate with Ease</h3>
          <p class="text-lg">Share event details & track attendees</p>
        </div>
  
      </div>
 
  </section>
  
   <!-- Contact Section -->
 <section class="bg-gradient-to-r from-black via-[#0A1E3A] to-black text-[#C5C6C7] py-16 text-center">
    <div class="max-w-3xl mx-auto">
      <h2 class="text-3xl font-semibold mb-6 text-[#66FCF1]">Get in Touch</h2>
      <p class="text-lg mb-8">Have questions or want to collaborate with us? We'd love to hear from you. Reach out to us through the contact methods below.</p>
      
      <!-- Contact Information and Icons -->
      <div class="flex justify-center space-x-16">
        <!-- Phone -->
        <div class="flex flex-col items-center">
            <a href="tel:+1234567890" aria-label="Call us" class="text-[#f7941d] text-4xl mb-2 hover:text-[#66FCF1]">
                <i class="fas fa-phone-alt"></i>
             </a>
          <span class="text-lg">Phone: +1 234 567 890</span>
        </div>
  
        <!-- Email -->
        <div class="flex flex-col items-center">
            <a href="mailto:support@eventnex.com" aria-label="Send an email" class="text-[#f7941d] text-4xl mb-2 hover:text-[#66FCF1]">
                <i class="fas fa-envelope"></i>
             </a>
          <span class="text-lg">Email: <a href="mailto:support@eventnex.com" class="hover:text-[#66FCF1]">support@eventnex.com</a></span>
        </div>
  
        <!-- Social Media -->
        <div class="flex flex-col items-center">
            <a href="https://www.facebook.com/EventNex" target="_blank" aria-label="Visit our Facebook page" class="text-[#f7941d] text-4xl mb-2 hover:text-[#66FCF1]">
                <i class="fab fa-facebook"></i>
             </a>
          <span class="text-lg">Facebook: <a href="https://www.facebook.com/EventNex" target="_blank" class="hover:text-[#66FCF1]">/EventNex</a></span>
        </div>
      </div>
  
      <p class="mt-10 text-lg font-semibold">We look forward to connecting with you!</p>
    </div>
  </section>
  
 </body>