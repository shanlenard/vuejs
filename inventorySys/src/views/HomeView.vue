<template>
  <div class="Home">

    <h2>{{ appTitle }}</h2>

    <h3>{{ counterData.title }}</h3>
    <div>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1)" class="btn">+</button>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" v-autofocus>
    </div>

  </div>
</template>

<script setup>
/*
  imports
*/

  import { ref, reactive, computed, watch, onMounted, onBeforeMount, onBeforeUnmount, onUnmounted, onDeactivated, onActivated, onBeforeUpdate, onUpdated } from 'vue'
  import { vAutofocus } from '@/directives/vAutofocus';

/* 
  app title
*/
//Non Reactive data
const appTitle = 'My Amazing Counter App'

onMounted(() => {
  console.log('Do stuff related to App Title')
})

/*
  counter
*/

//Reactive data
const counterData = reactive({
  count: 0,
  title: 'My Counter'
})

//watchers
watch(() => counterData.count, (newCount, oldCount) => {
  if (newCount === 20) {
    alert('Way to go! You made it to 20!!')
  }
})

//computed property
const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return 'even'
  return 'odd'
})

//function
const increaseCounter = amount => {
  counterData.count += amount
}
//function
const decreaseCounter = amount => {
  counterData.count -= amount
}

onMounted(() => {
  console.log('Do stuff related to Counter')
})


// //onBefore mount hooks
// onBeforeMount(() => {
//   console.log('onBeforeMount')
// })

// //onMounted hooks
// onMounted(() => {
//   console.log('onMounted')
// })

// //onBeforeUnmount hooks
// onBeforeUnmount(() => {
//   console.log('onBeforeUnmount')
// })

// //onUnmounted hooks
// onUnmounted(() => {
//   console.log('onUnmounted')
// })

// //onActivated hooks
// onActivated(() => {
//   console.log('onActivated')
// })

// //onDeactivated hooks
// onDeactivated(() => {
//   console.log('onDeactivated')
// })

// //onBeforeUpdate
// onBeforeUpdate(() => {
//   console.log('onBeforeUpdate')
// })

// //onUpdated
// onUpdated(() => {
//   console.log('onUpdated')
// })

</script>


<!-- <script>
export default {
  data() {
    return {
      count: 0
    }
  },
  computed: {
    myComputedProperty() {
      // perform logic based on a data property
      return 'my result'
    }
  },
  watch: {
    count(newCount, oldCount) {
      if(newCount == 20) alert('asdasd')
    }
  }
}
</script> -->



<!-- <script>
  ## REF
import { ref } from 'vue'
export default {
  setup() {
    const counter = ref(0)

    const increaseCounter = () => {
      counter.value++
    }

    const decreaseCounter = () => {
      counter.value--
    }

    return {
      counter,
      increaseCounter,
      decreaseCounter
    }
  }
}
</script> -->

<!-- <script>
  ## OLD OPTION API - 
export default {
  data() {
    return {
      counter: 10 
    }
  },
  methods: {
    increaseCounter() {
      this.counter++
    },
    decreaseCounter() {
      this.counter--
    }
  }
}
</script> -->

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>