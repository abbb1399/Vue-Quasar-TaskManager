<template>
  <q-page>
      <!-- New -->
        <q-card class="q-ma-lg">
          <q-card-section>
            <div class="text-h4 text-purple">New</div>
         </q-card-section>
          <draggable
            v-bind="dragOptions"
            @start="drag = true"
            @end="drag = false"
          >
            <transition-group
              type="transition"
              :name="!drag ? 'flip-list' : null"
            >
              <q-markup-table class="mb-30 cursor-pointer" v-for="element in list1" :key="element.name" bordered separator="cell">
                <tr>
                  <td>{{ element.name }}</td>
                  <td>{{ element.id }}</td>
                  <td>{{ element.age }}</td>
                </tr>
              </q-markup-table>
            </transition-group>
          </draggable>
        </q-card>

      <!-- Doing -->
        <q-card class="q-ma-lg">
           <q-card-section>
            <div class="text-h4 text-blue">Doing</div>
          </q-card-section>
          <draggable
            v-bind="dragOptions"
            @start="drag = true"
            @end="drag = false"
          >
            <transition-group
              type="transition"
              :name="!drag ? 'flip-list' : null"
            >
              <q-markup-table class="mb-30 cursor-pointer" v-for="element in list2" :key="element.name" bordered separator="cell">
                <tr>
                  <td>{{ element.name }}</td>
                  <td>{{ element.id }}</td>
                  <td>{{ element.age }}</td>
                </tr>
              </q-markup-table>
            </transition-group>
          </draggable>
        </q-card>

      <!-- Done -->
      <q-card class="q-ma-lg">
        <q-card-section>
          <div class="text-h4 text-green">Done</div>
        </q-card-section>

          <draggable
            v-bind="dragOptions"
            @start="drag = true"
            @end="drag = false"
          >
            <transition-group
              type="transition"
              :name="!drag ? 'flip-list' : null"
            >
               <q-markup-table class="mb-30 cursor-pointer" v-for="element in list3" :key="element.name" bordered separator="cell">
                <tr>
                  <td>{{ element.name }}</td>
                  <td>{{ element.id }}</td>
                  <td>{{ element.age }}</td>
                </tr>
              </q-markup-table>
            </transition-group>
          </draggable>
      </q-card>
  </q-page>
</template>

<script>
import draggable from 'vuedraggable'

// transition
export default {
  display: 'Transitions',
  order: 7,
  components: {
    draggable
  },
  data () {
    return {
      list1: [
        { name: '유재석', id: 1, age: 20 },
        { name: '조세호', id: 2, age: 30 },
        { name: '강호동', id: 3, age: 40 }
      ],
      list2: [
        { name: '전인표', id: 4, age: 20 },
        { name: '김개똥', id: 5, age: 30 },
        { name: '홍길동', id: 6, age: 40 }
      ],
      list3: [
        { name: '김김김', id: 7, age: 20 },
        { name: '하하하', id: 8, age: 30 },
        { name: '후후후', id: 9, age: 40 }
      ],
      drag: false
    }
  },
  methods: {},
  computed: {
    dragOptions () {
      return {
        animation: 200,
        group: 'description',
        disabled: false,
        ghostClass: 'ghost'
      }
    }
  }
}
</script>

<style>

.flip-list-move {
  transition: transform 0.5s;
}

.no-move {
  transition: transform 0s;
}

</style>
