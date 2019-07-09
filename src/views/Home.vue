<template>
   <section>
    <section id="sidebar" class="no-print w-full p-8 bg-red-800">
      <h1 class="text-2xl font-bold text-white">Basic Marketing Idea Outline</h1>
      <p>
        Can be used for planning simple banner ad to simple email. Leave blank and print for handwriting or fill in blanks and print.
      </p>
      <button 
        @click="print"
        class="bg-white hover:bg-gray-200 px-2 py-1 text-xs rounded mr-4"
      >
        Print
      </button>
      <button 
        @click="clearAll"
        class="bg-white hover:bg-gray-200 px-2 py-1 text-xs rounded"
      >
        Clear All
      </button>
    </section>
    <section
      id="main-content"
      class=""
    >
      <section class="bg-gray-200 w-full p-4">
        <Heading text="Target Date" />
        <div class="flex flex-row">
          <div class="w-1/2 mr-4">            
            <TextInput label="Start Date" v-model="startDate"/>
          </div>
          <div class="w-1/2">
            <TextInput label="End Date" v-model="endDate" />
          </div>
        </div>
      </section>
      <section class="p-4">
        <Heading text="Content" />

        <Subheading text="Pain Point" />
        <TextInput fontSize="text-3xl" v-model="painPoint" />

        <Subheading text="Bullet Points" />
        <p class="text-gray-400 text-sm italic">Odd number of bullet points. Either have 1 or 3.</p>
        <ul>
          <li v-for="(i, index) in bullets" :key="index" class="mb-4">
            <TextInput v-model="i.value" />
            <!-- <input 
              type="text"
              v-model="i.value"
              class="bg-white focus:outline-none focus:border focus:border-blue-600 border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal text-base" 
            > -->
          </li>
        </ul>

        <Subheading text="Call to Action" />
        <TextInput label="Goal" />
        <span class="block text-sm text-gray-400">Button Text</span>
        <input 
          type="text"
          class="bg-white focus:outline-none focus:border focus:border-blue-600 border border-gray-300 rounded-lg py-2 px-4 mr-4 w-1/2 appearance-none leading-normal text-base" 
          v-model="btnText"
          >
        <button
          v-show="btnText"
          class="no-print bg-blue-500 hover:bg-blue-700 px-4 py-2 rounded text-white mx-auto uppercase"
        >
          {{ btnText }}
        </button>
      </section>
      <section class="bg-gray-200 p-4">
        <Heading text="Next steps" />
        <div class="flex flex-row">
          <div class="w-1/2 mr-4">
            <Subheading text="What happens next..." />
            <textarea 
              rows="5"
              class="focus:outline-none focus:border focus:border-blue-600 border border-gray-300 rounded-lg py-2 px-4 w-full"
              v-model="nextSteps"
            >
            </textarea>
          </div>
          <div class="w-1/2">
            <Subheading text="Resources Needed" />
            <!-- <div class="no-print flex mb-2">
              <button class="px-2 py-1 bg-white hover:bg-gray-100 rounded mx-2 w-6" @click="resourcesCount = resourcesCount + 1">+</button>
              <button class="px-2 py-1 bg-white hover:bg-gray-100 rounded mx-2 w-6" @click="resourcesCount = resourcesCount - 1">-</button>
            </div> -->
            <ul>
              <li v-for="(i, index) in resources" :key="index" class="mb-4">
                <TextInput fontSize="text-xs" v-model="i.value" />
              </li>
            </ul>
          </div>
        </div>
      </section>
    </section>
    <section class="flex bg-red-800 p-6">
      Copyright 2019 <a href="https://github.com/bmrankin" target="_blank">Bryan Rankin</a>
    </section>
   </section>
</template>

<script>
import Heading from '@/components/Heading'
import Subheading from '@/components/Subheading'
import TextInput from '@/components/TextInput'

export default {
  components: {
    Heading,
    Subheading,
    TextInput
  },
  data: () => ({
    startDate: '',
    endDate: '',
    painPoint: '',
    bullets: [
      { value: '' },
      { value: '' },
      { value: '' },
    ],
    goal: '',
    btnText: '',
    nextSteps: '',
    resources: [
      {value: ''},
      {value: ''},
      {value: ''}
    ]
  }),
  methods: {
    print() {
      this.$nextTick(() => {
        window.print()
      })
    },
    clearAll() {
      this.startDate = '',
      this.endDate = '',
      this.painPoint = '',
      this.bullets = [
        { value: '' },
        { value: '' },
        { value: '' },
      ],
      this.goal = '',
      this.btnText = '',
      this.nextSteps = '',
      this.resources = [
        {value: ''},
        {value: ''},
        {value: ''}
      ]
    }
  }
}
</script>

