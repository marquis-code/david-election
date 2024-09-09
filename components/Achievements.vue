<!-- <template>
    <section class="bg-white dark:bg-gray-900">
      <div class="container px-6 py-10 mx-auto">
        <div class="mt-6 md:flex md:items-center md:justify-between">
          <div>
            <h1 data-aos="flip-left"
                class="text-2xl font-semibold text-gray-800 capitalize lg:text-3xl dark:text-white">
              My Achievements
            </h1>
            <div class="flex mx-auto mt-6" data-aos="flip-left">
              <span class="inline-block w-40 h-1 bg-blue-500 rounded-full"></span>
              <span class="inline-block w-3 h-1 mx-1 bg-blue-500 rounded-full"></span>
              <span class="inline-block w-1 h-1 bg-blue-500 rounded-full"></span>
            </div>
          </div>
  
          <div class="flex justify-between mt-8 md:mt-0">
            <button @click="prev" title="left arrow" data-aos="flip-left"
                class="p-2 mx-3 text-gray-800 transition-colors duration-300 border rounded-full rtl:-scale-x-100 dark:text-gray-200 dark:hover:bg-gray-800 dark:border-gray-700 hover:bg-gray-100">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
              </svg>
            </button>
  
            <button @click="next" title="right arrow" data-aos="flip-left"
                class="p-2 text-gray-800 transition-colors duration-300 border rounded-full rtl:-scale-x-100 dark:text-gray-200 dark:hover:bg-gray-800 dark:border-gray-700 hover:bg-gray-100">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
              </svg>
            </button>
          </div>
        </div>
        <section class="lg:flex overflow-hidden space-y-6 lg:space-y-0 lg:space-x-8 mt-8 xl:mt-12">
          <div v-for="(item, idx) in visibleItems" :key="idx" class="lg:w-1/3 relative block p-8 border rounded-lg dark:border-gray-700 group" @click="stopCarousel">
            <img
              alt="Achievement image"
              :src="dynamicImage(item.image)"
              class="absolute inset-0 h-full w-full object-cover opacity-75 transition-opacity group-hover:opacity-30"
            />
            <div class="relative p-4 sm:p-6 lg:p-8">
              <p class="text-sm font-medium uppercase tracking-widest text-pink-500">Achievement</p>
              <p class="text-xl font-bold text-white sm:text-2xl">David Gyang</p>
              <div class="mt-32 sm:mt-48 lg:mt-64">
                <div class="translate-y-8 transform opacity-0 transition-all group-hover:translate-y-0 group-hover:opacity-100">
                  <p class="text- text-white leading-relaxed">{{ item.desc }}</p>
                </div>
              </div>
            </div>
          </div>
        </section>
        <div class="flex justify-center mt-6">
          <span v-for="(dot, index) in totalGroups" :key="index" class="w-3 h-3 mx-2 bg-gray-300 rounded-full cursor-pointer" 
            :class="{ 'bg-blue-500': currentGroup === index }" @click="goToGroup(index)">
          </span>
        </div>
      </div>
    </section>
  </template>
  
  <script setup lang="ts">
  import { ref, computed } from 'vue'
  import { dynamicImage } from '@/utils/assets'
  
  const itemsPerPage = 3
  const currentGroup = ref(0)
  const achievements = ref([
    {
      desc: `This Iconic photograph got a lot of attention and made my friends and I little celebrities at the time. It was taken for the ULAPS fashion week on "Alté/Vintage" day.
Interestingly, we just recently won "Clique of the year at the ULAPS Awards night.`,
      image: 'campaign14.jpeg'
    },
    {
      desc: `Still from the ULAPS Fashion week`,
       image: 'campaign2.jpeg'
    },
    {
      desc: `The ULAPS variety night themed "THE WEDDING PARTY" I acted as the father of the groom Mr Kolawole Coker. I remember that my biggest problem at the time was how to match Mrs Coker's energy🤣`,
       image: 'campaign4.jpeg'
    },
    {
      desc: `In my very first year in this college, I co-hosted the ULAPS Symposium together with the eloquent Eniola Ajayi and I was very nervous but of course nobody knew. I can conceal these things pretty well.`,
       image: 'campaign3.jpeg'
    },
    {
      desc: `Me receiving an award at the COMPSSA JADE Dinner and Awards Night. 
Looking back at this picture, I realized that the presenters are one of the two ULAPSites I admire the most.
Adejayi Blessing (COMPSSA'S Minister of Power and my personal mentor) and Akinsanmi Zeenat (The Speaker of the House of Representatives to whom I was privileged to serve as Clerk)`,
       image: 'campaign6.jpeg'
    },
    {
      desc: `The Award winning David Gyang😌`,
       image: 'campaign7.jpeg'
    },
    {
      desc: `On this day, I was elected as the General Secretary of the Board of Lectors, Divine Physician and St. Luke's Catholic Chaplaincy. As you may have observed, I was a tad overdressed because I thought it was a formal event. I wanted the ground to swallow me😭`,
       image: 'campaign5.jpeg'
    },
    {
        desc: `My friend John BaBby and I both work at this company called HealthBetter.ng and on this day at work, he was really hyping me up to take this picture and I'm really glad I did, it turned out to be my favorite picture of the year.`,
       image: 'campaign8.jpeg'
    },
    {
      desc: `Some of the members of HealthBetter.ng at a meeting.`,
       image: 'campaign9.jpeg'
    },
    {
      desc: `The team of Erranders.ng after the NIMELSSA Skill up workshop where we pitched our Startup company to them`,
       image: 'campaign17.jpeg'
    },
    {
        desc: `Me and my welfare team at the children's care centre Idi Araba for the COMPSSA Charity Drive 1.0
We had packed drugs, foodstuff and so many provision and yet they were all smiles. These beautiful people made leadership so easy`,
        image: 'campaign10.jpeg'
    },
    {
        desc: 'The beautiful Abigail Moejoh was probably very confused as to what I was saying but she held herself well. I remember how eloquently and effortlessly she spoke to the children at the hospice. I was highly impressed.',
        image: 'desc1.jpeg'
    },
    {
        desc: 'I was a Special Invited guest as a member of Erranders.ng at the Shuttlers end of the year party',
        image: 'campaign23.jpeg'
    },
    {
        desc: 'The CEO and members of Erranders.ng',
        image: 'campaign25.jpeg'
    },
    {
        desc: `At the COMPSSA International Women's Day Celebration Lecture held at the Old Great Hall, I remember the Guest Speaker Pharm. Mrs. Clare Omatseye celebrating the few men that were there to celebrate the women on their day and it strengthened my resolve to always stand by and support women, cheering them on as they achieve great things.`,
        image: 'iwd-group.jpeg'
    },
    {
        desc: 'With my dear friend and classmate Akinnola Temiloluwa after the International Women\'s Day lecture.',
        image: 'iwd.jpeg'
    }, {
        desc: 'Here I was elected President, Board of Lectors, Divine Physician and St. Luke\'s Catholic Chaplaincy after my Tenure as General secretary',
        image: 'lector.jpeg'
    },
    {
        desc: 'Served as "bannerboy" for the COMPSSA SYNERGY WEEK banner representing the University of Lagos Association of Physiotherapy Students (ULAPS)',
        image: 'banner.jpeg'
    },
    {
        desc: `I headed the Awareness day of COMPSSA WEEK: SYNERGY and it was no joke. Conceiving and Actualizing the idea of a mobile carnival were two different things, thankfully my Amazing committee members came through and I'm glad everyone had fun.
This event saw the birth of the COMPSSA Cheerleading Squad and the rebirth of the COMPSSA Dance Commune`,
image: 'camp.jpeg'
    },
    {
        image: 'campaign1.jpeg',
        desc: `This was me at my stand at Electrofest/COMPSSA Trade fair. I was serving as Head of Protocol for Electrofest and at the same time I was running my footwear stand at the trade fair. It took a lot of effort but my committee as usual lessened the burden.`
    },
    {
        image: 'dance.jpeg',
        desc: `Members of The COMPSSA Dance Commune performing at Electrofest. I was so proud of my girls.`
    },
    {
        image: 'fola.jpeg',
        desc: `I also served as Head of Protocol at the Mr. and Miss Unilag Pageant and In this Picture, I am welcoming Guinness world Record Holder Dr. Fola David to the show.`
    },
    {
        image: 'campaign19.jpeg',
        desc: `This was the COMPSSA president's Interview with Owolabi Rhoda. I saw this and I was so happy because I received the commendation that I deserved and never got.`
    },
    {
        image: 'campaign12.jpeg',
        desc: `My second year hosting the ULAPS Symposium with the beautiful Temitope Alugo.`
    },
    {
        image: 'campaign11.jpeg',
        desc: `This picture shows the me together with the ULAPS EDITOR IN-CHIEF Tolulope Kalejaiye of the ULAPS Editorial Board at the official Magazine Launch. I was so proud because I had published an article in this magazine as a member of the Editorial Board.`
    },
    {
         image: 'campaign10.jpeg',
        desc: `The 300lvl class representatives of the ULAPS HOUSE OF REPRESENTATIVES.`
    },
    {
         image: 'campaign13.jpeg',
        desc: `The ULAPS "Clique of the year"`
    },
    {
         image: 'campaign18.jpeg',
        desc: `John BaBby and I were so engrossed designing the "Time of Our Lives" signing banner for COMPSSA's LOUD 2.0. I was so pissed and disappointed when I heard that it had been defaced, thankfully it was repaired.`
    },
    {
         image: 'campaign27.jpeg',
        desc: 'I was privileged to speak to the Students of Ogunlade schools on "Physiotherapy as a Career path" at the ULAPS Health Week Outreach.'
    }
  ])
  
  // Calculate total groups for carousel dots
  const totalGroups = computed(() => Math.ceil(achievements.value.length / itemsPerPage))
  
  // Get visible items for the current group
  const visibleItems = computed(() => {
    return achievements.value.slice(currentGroup.value * itemsPerPage, (currentGroup.value + 1) * itemsPerPage)
  })
  
  // Function to go to the next group of items
  const next = () => {
    if (currentGroup.value < totalGroups.value - 1) {
      currentGroup.value++
    }
  }
  
  // Function to go to the previous group of items
  const prev = () => {
    if (currentGroup.value > 0) {
      currentGroup.value--
    }
  }
  
  // Function to go to a specific group when clicking on dots
  const goToGroup = (index: number) => {
    currentGroup.value = index
  }
  
  // Function to stop the carousel when an item is clicked
  const stopCarousel = () => {
    console.log('Carousel movement stopped.')
  }
  </script>
  
  <style scoped>
  /* Add custom styles for carousel dots and transitions if needed */
  </style>
   -->

   <template>
    <section class="bg-white dark:bg-gray-900">
        <div class="container px-6 py-10 mx-auto">
            <div class="mt-6 md:flex md:items-center md:justify-between">
                <div>
                    <h1 data-aos="flip-left"
                        class="text-2xl font-semibold text-gray-800 capitalize lg:text-3xl dark:text-white">
                        My Achievements
                    </h1>
                    <div class="flex mx-auto mt-6" data-aos="flip-left">
                        <span class="inline-block w-40 h-1 bg-blue-500 rounded-full"></span>
                        <span class="inline-block w-3 h-1 mx-1 bg-blue-500 rounded-full"></span>
                        <span class="inline-block w-1 h-1 bg-blue-500 rounded-full"></span>
                    </div>
                </div>

                <div class="flex justify-between mt-8 md:mt-0">
                    <button @click="prev" title="left arrow" data-aos="flip-left"
                        class="p-2 mx-3 text-gray-800 transition-colors duration-300 border rounded-full rtl:-scale-x-100 dark:text-gray-200 dark:hover:bg-gray-800 dark:border-gray-700 hover:bg-gray-100">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
                            stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
                        </svg>
                    </button>

                    <button @click="next" title="right arrow" data-aos="flip-left"
                        class="p-2 text-gray-800 transition-colors duration-300 border rounded-full rtl:-scale-x-100 dark:text-gray-200 dark:hover:bg-gray-800 dark:border-gray-700 hover:bg-gray-100">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24"
                            stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
                        </svg>
                    </button>
                </div>
            </div>
            <section class="lg:flex overflow-hidden space-y-6 lg:space-y-0 lg:space-x-8 mt-8 xl:mt-12">
                <div v-for="(item, idx) in visibleItems" :key="idx"
                class="lg:w-1/3 relative block p-8 border rounded-lg dark:border-gray-700 group"
                    @click="stopCarousel">
                    <img alt="Achievement image" :src="dynamicImage(item.image)"
                        class="absolute inset-0 h-full w-full object-cover opacity-75 transition-opacity group-hover:opacity-30" />
                    <div class="relative p-4 sm:p-6 lg:p-8">
                        <p class="text-sm font-medium uppercase tracking-widest text-pink-500">Achievement</p>
                        <p class="text-xl font-bold text-white sm:text-2xl">David Gyang</p>
                        <div class="mt-32 sm:mt-48 lg:mt-64">
                            <div
                                class="translate-y-8 transform opacity-0 transition-all group-hover:translate-y-0 group-hover:opacity-100">
                                <p class="text- text-white leading-relaxed">{{ item.desc }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <div class="flex justify-center mt-6">
                <span v-for="(dot, index) in totalGroups" :key="index"
                    class="w-3 h-3 mx-2 bg-gray-300 rounded-full cursor-pointer"
                    :class="{ 'bg-blue-500': currentGroup === index }" @click="goToGroup(index)">
                </span>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { dynamicImage } from '@/utils/assets'
const itemsPerPage = 3;
const currentGroup = ref(0);
const autoSlideInterval = ref(null); // to hold the interval reference
const achievements = ref([
    {
      desc: `This Iconic photograph got a lot of attention and made my friends and I little celebrities at the time. It was taken for the ULAPS fashion week on "Alté/Vintage" day.
Interestingly, we just recently won "Clique of the year at the ULAPS Awards night.`,
      image: 'campaign14.jpeg'
    },
    {
      desc: `Still from the ULAPS Fashion week`,
       image: 'campaign2.jpeg'
    },
    {
      desc: `The ULAPS variety night themed "THE WEDDING PARTY" I acted as the father of the groom Mr Kolawole Coker. I remember that my biggest problem at the time was how to match Mrs Coker's energy🤣`,
       image: 'campaign4.jpeg'
    },
    {
      desc: `In my very first year in this college, I co-hosted the ULAPS Symposium together with the eloquent Eniola Ajayi and I was very nervous but of course nobody knew. I can conceal these things pretty well.`,
       image: 'campaign3.jpeg'
    },
    {
      desc: `Me receiving an award at the COMPSSA JADE Dinner and Awards Night. 
Looking back at this picture, I realized that the presenters are one of the two ULAPSites I admire the most.
Adejayi Blessing (COMPSSA'S Minister of Power and my personal mentor) and Akinsanmi Zeenat (The Speaker of the House of Representatives to whom I was privileged to serve as Clerk)`,
       image: 'campaign6.jpeg'
    },
    {
      desc: `The Award winning David Gyang😌`,
       image: 'campaign7.jpeg'
    },
    {
      desc: `On this day, I was elected as the General Secretary of the Board of Lectors, Divine Physician and St. Luke's Catholic Chaplaincy. As you may have observed, I was a tad overdressed because I thought it was a formal event. I wanted the ground to swallow me😭`,
       image: 'campaign5.jpeg'
    },
    {
        desc: `My friend John BaBby and I both work at this company called HealthBetter.ng and on this day at work, he was really hyping me up to take this picture and I'm really glad I did, it turned out to be my favorite picture of the year.`,
       image: 'campaign8.jpeg'
    },
    {
      desc: `Some of the members of HealthBetter.ng at a meeting.`,
       image: 'campaign9.jpeg'
    },
    {
      desc: `The team of Erranders.ng after the NIMELSSA Skill up workshop where we pitched our Startup company to them`,
       image: 'campaign17.jpeg'
    },
    {
        desc: `Me and my welfare team at the children's care centre Idi Araba for the COMPSSA Charity Drive 1.0
We had packed drugs, foodstuff and so many provision and yet they were all smiles. These beautiful people made leadership so easy`,
        image: 'campaign10.jpeg'
    },
    {
        desc: 'The beautiful Abigail Moejoh was probably very confused as to what I was saying but she held herself well. I remember how eloquently and effortlessly she spoke to the children at the hospice. I was highly impressed.',
        image: 'desc1.jpeg'
    },
    {
        desc: 'I was a Special Invited guest as a member of Erranders.ng at the Shuttlers end of the year party',
        image: 'campaign23.jpeg'
    },
    {
        desc: 'The CEO and members of Erranders.ng',
        image: 'campaign25.jpeg'
    },
    {
        desc: `At the COMPSSA International Women's Day Celebration Lecture held at the Old Great Hall, I remember the Guest Speaker Pharm. Mrs. Clare Omatseye celebrating the few men that were there to celebrate the women on their day and it strengthened my resolve to always stand by and support women, cheering them on as they achieve great things.`,
        image: 'iwd-group.jpeg'
    },
    {
        desc: 'With my dear friend and classmate Akinnola Temiloluwa after the International Women\'s Day lecture.',
        image: 'iwd.jpeg'
    }, {
        desc: 'Here I was elected President, Board of Lectors, Divine Physician and St. Luke\'s Catholic Chaplaincy after my Tenure as General secretary',
        image: 'lector.jpeg'
    },
    {
        desc: 'Served as "bannerboy" for the COMPSSA SYNERGY WEEK banner representing the University of Lagos Association of Physiotherapy Students (ULAPS)',
        image: 'banner.jpeg'
    },
    {
        desc: `I headed the Awareness day of COMPSSA WEEK: SYNERGY and it was no joke. Conceiving and Actualizing the idea of a mobile carnival were two different things, thankfully my Amazing committee members came through and I'm glad everyone had fun.
This event saw the birth of the COMPSSA Cheerleading Squad and the rebirth of the COMPSSA Dance Commune`,
image: 'camp.jpeg'
    },
    {
        image: 'campaign1.jpeg',
        desc: `This was me at my stand at Electrofest/COMPSSA Trade fair. I was serving as Head of Protocol for Electrofest and at the same time I was running my footwear stand at the trade fair. It took a lot of effort but my committee as usual lessened the burden.`
    },
    {
        image: 'dance.jpeg',
        desc: `Members of The COMPSSA Dance Commune performing at Electrofest. I was so proud of my girls.`
    },
    {
        image: 'fola.jpeg',
        desc: `I also served as Head of Protocol at the Mr. and Miss Unilag Pageant and In this Picture, I am welcoming Guinness world Record Holder Dr. Fola David to the show.`
    },
    {
        image: 'campaign19.jpeg',
        desc: `This was the COMPSSA president's Interview with Owolabi Rhoda. I saw this and I was so happy because I received the commendation that I deserved and never got.`
    },
    {
        image: 'campaign12.jpeg',
        desc: `My second year hosting the ULAPS Symposium with the beautiful Temitope Alugo.`
    },
    {
        image: 'campaign11.jpeg',
        desc: `This picture shows the me together with the ULAPS EDITOR IN-CHIEF Tolulope Kalejaiye of the ULAPS Editorial Board at the official Magazine Launch. I was so proud because I had published an article in this magazine as a member of the Editorial Board.`
    },
    {
         image: 'campaign10.jpeg',
        desc: `The 300lvl class representatives of the ULAPS HOUSE OF REPRESENTATIVES.`
    },
    {
         image: 'campaign13.jpeg',
        desc: `The ULAPS "Clique of the year"`
    },
    {
         image: 'campaign18.jpeg',
        desc: `John BaBby and I were so engrossed designing the "Time of Our Lives" signing banner for COMPSSA's LOUD 2.0. I was so pissed and disappointed when I heard that it had been defaced, thankfully it was repaired.`
    },
    {
         image: 'campaign27.jpeg',
        desc: 'I was privileged to speak to the Students of Ogunlade schools on "Physiotherapy as a Career path" at the ULAPS Health Week Outreach.'
    }
  ])

// Calculate total groups for carousel dots
const totalGroups = computed(() => Math.ceil(achievements.value.length / itemsPerPage));

// Get visible items for the current group
const visibleItems = computed(() => {
  return achievements.value.slice(currentGroup.value * itemsPerPage, (currentGroup.value + 1) * itemsPerPage);
});

// Function to go to the next group of items
const next = () => {
  if (currentGroup.value < totalGroups.value - 1) {
    currentGroup.value++;
  } else {
    currentGroup.value = 0; // Reset to the first group when reaching the end
  }
};

// Function to go to the previous group of items
const prev = () => {
  if (currentGroup.value > 0) {
    currentGroup.value--;
  } else {
    currentGroup.value = totalGroups.value - 1; // Go to the last group when reaching the start
  }
};

// Function to go to a specific group when clicking on dots
const goToGroup = (index: number) => {
  currentGroup.value = index;
  resetAutoSlide(); // Reset the auto-slide after a manual action
};

// Function to stop the carousel when an item is clicked
const stopCarousel = () => {
  console.log('Carousel movement stopped.');
};

// // Function to handle dynamic image fetching
// const dynamicImage = (image) => {
//   return image; // Modify this to handle dynamic images if needed
// };

// Auto-slide function
const autoSlide = () => {
  autoSlideInterval.value = setInterval(() => {
    next();
  }, 10000); // Auto-slide every 3 seconds
};

// Reset auto-slide interval after user interaction
const resetAutoSlide = () => {
  clearInterval(autoSlideInterval.value); // Clear the previous interval
  autoSlide(); // Restart the auto-slide
};

// Start the auto-slide on mount
onMounted(() => {
  autoSlide();
});

// Clean up the interval when the component is unmounted
onUnmounted(() => {
  clearInterval(autoSlideInterval.value);
});
</script>

<style scoped>
/* Add custom styles for carousel dots and transitions if needed */
</style>
