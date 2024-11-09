<script lang="ts">
  import Homenav from './homenav.svelte';

  let currentEvents = [
    {
      name: "Annual Charity Gala",
      startDate: "2024-11-15",
      endDate: "2024-11-16",
      time: "6:00 PM",
      description: "A charitable event gathering for a good cause, featuring live performances, auctions, and more.",
      image: "https://images2.unation.com/event-images/ow-event-1718338518-45006039.jpg",
      attendees: 450
    },
    {
      name: "Tech Conference 2024",
      startDate: "2024-12-01",
      endDate: "2024-12-02",
      time: "9:00 AM",
      description: "A two-day event with industry leaders sharing insights on the latest trends in technology and innovation.",
      image: "https://img.freepik.com/free-vector/technology-conference-flyer-template_1361-1613.jpg",
      attendees: 1500
    },
    {
      name: "Art Exhibition",
      startDate: "2024-11-22",
      endDate: "2024-11-23",
      time: "5:00 PM",
      description: "An exhibition featuring local artists, showcasing diverse styles and mediums of art.",
      image: "https://thehaatofart.com/wp-content/uploads/2024/07/photo-vibrant-art-gallery-contemporary-artwork_1600x897-1024x574.jpg",
      attendees: 350
    },
    {
      name: "Coding Bootcamp",
      startDate: "2024-12-10",
      endDate: "2024-12-15",
      time: "10:00 AM",
      description: "A week-long coding bootcamp where participants can learn full-stack development from industry professionals.",
      image: "https://tholispane.co.za/wp-content/uploads/2024/05/Coding-Bootcamps-1024x576.jpg",
      attendees: 120
    },
    {
      name: "Music Festival",
      startDate: "2024-11-25",
      endDate: "2024-11-26",
      time: "4:00 PM",
      description: "A vibrant music festival celebrating various genres, with performances from both local and international artists.",
      image: "https://i0.wp.com/mnlconcertscene.com/wp-content/uploads/2022/05/tugatog1.jpg?resize=672%2C372&ssl=1",
      attendees: 800
    },
    {
      name: "Leadership Summit 2024",
      startDate: "2024-12-05",
      endDate: "2024-12-06",
      time: "8:00 AM",
      description: "A two-day summit focused on leadership skills, bringing together renowned speakers and thought leaders.",
      image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQrkFnz3CTutjflcHtqswBvCgehojchQ6maMQ&s",
      attendees: 500
    }
  ];

  let topEvents = [
    {
      name: "Victoria's Secret Fashion Show 2024",
      startDate: "2024-12-06",
      endDate: "2024-12-12",
      time: "7:00 PM",
      description: "The runway is returning in 2024 and we have your backstage pass. Stay tuned for show sneak peeks and more.",
      attendees: 15000,
      videoLink: "/vs2024.mp4" 
    },
    {
      name: "World Music Awards 2024",
      startDate: "2024-12-08",
      endDate: "2024-12-08",
      time: "9:00 PM",
      description: "The prestigious World Music Awards recognizing the achievements of global music stars, with live performances from top artists.",
      attendees: 10000,
      videoLink: "/award.mp4"
    }
  ];
  function unmuteVideo(event: MouseEvent | FocusEvent) {
  const video = event.currentTarget as HTMLVideoElement;
  video.muted = false;
}


  function muteVideo(event: MouseEvent | FocusEvent) {
  const video = event.currentTarget as HTMLVideoElement;
  video.muted = true;
}


</script>

<style>
  /* Add custom glowing effect */
  .glowing-text {
    text-shadow: 0 0 6px rgba(102, 252, 241, 0.8), 0 0 9px rgba(102, 252, 241, 0.8), 0 0 30px rgba(102, 252, 241, 0.8);
  }
</style>

<Homenav />

<div class="p-6 mt-11 min-h-screen text-[#C5C6C7]">
  <h2 class="text-3xl font-bold mt-6 text-center text-[#66FCF1] mb-11 glowing-text">
    Top Events Worldwide
  </h2>

  <div class="grid gap-8 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-2 xl:grid-cols-2 mb-11">
    {#each topEvents as event}
      <div class="bg-[#1F2833] rounded-lg shadow-lg p-6 flex flex-col justify-between">
        <!-- Video that loops and plays automatically -->
        <video 
        autoplay 
        loop 
        muted 
        class="w-full h-80 object-cover rounded-md mb-4"
        id="video-{event.name}"
        onmouseover={unmuteVideo}
        onmouseout={muteVideo}
        onfocus={unmuteVideo}
        onblur={muteVideo}>
        <source src={event.videoLink} type="video/mp4" />
        Your browser does not support the video tag.
      </video>
        
        <h4 class="text-2xl font-semibold text-[#66FCF1] mb-2">{event.name}</h4>
        
        <div class="text-sm text-[#C5C6C7] mb-2">
          <p><strong>Start Date:</strong> {event.startDate}</p>
          <p><strong>End Date:</strong> {event.endDate}</p>
          <p><strong>Time:</strong> {event.time}</p>
          <p><strong>Attendees:</strong> {event.attendees}</p>
        </div>
        
        <p class="text-[#C5C6C7] mb-4">{event.description}</p>

        <div class="mt-4 text-center">
          <button class="bg-transparent text-[#f7941d] px-8 py-3 rounded-lg hover: hover:text-[#ffffff] transition-all duration-300">
            Register Now
          </button>
          
        </div>
      </div>
    {/each}
  </div>





  <!-- Page Title for Current Events -->
  <h1 class="text-4xl font-bold mb-8 mt-12 text-center text-[#66FCF1]">Current Events</h1>

  <!-- Event Cards Grid -->
  <div class="grid gap-8 sm:grid-cols-1 lg:grid-cols-3">
    {#each currentEvents as event}
      <div class="bg-[#1F2833] rounded-lg shadow-lg transition-transform transform hover:scale-105 hover:shadow-xl p-6 flex flex-col justify-between space-y-4">
        <!-- Event Image -->
        <img src={event.image} alt={event.name} class="w-full h-48 object-cover rounded-md mb-4" />

        <h4 class="text-2xl font-semibold text-[#66FCF1]">{event.name}</h4>
        <div class="text-md text-[#C5C6C7]">
          <p><strong>Start Date:</strong> {event.startDate}</p>
          <p><strong>End Date:</strong> {event.endDate}</p>
          <p><strong>Time:</strong> {event.time}</p>
        </div>
        <p class="text-sm italic text-[#C5C6C7]">{event.description}</p>

        <!-- RSVP Button -->
        <div class="mt-4 text-center">
          <button class="bg-transparent text-[#f7941d] px-8 py-3 rounded-lg hover: hover:text-[#ffffff] transition-all duration-300">
            Register Now
          </button>
          
        </div>
      </div>
    {/each}
  </div>

  <!-- Call to Action Section -->
  <section class="mt-16 text-center">
    <h2 class="text-2xl font-semibold text-[#66FCF1] mb-6">Join Us for More Events</h2>
    <p class="text-lg text-[#C5C6C7] mb-4">Stay connected and be part of the most exciting events happening in our community.</p>
    <button class="bg-[#66FCF1] text-[#1F2833] px-8 py-3 rounded-lg shadow-lg hover:bg-[#45A29E] transition-all duration-300">
      Explore More Events
    </button>
  </section>
</div>