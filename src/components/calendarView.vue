<template>
  <div id="calendar-view">
    <h1 id="title"> Calendar View </h1>
    <button @click="visible = 'month'" >Month</button>
    <button @click="visible = 'week'" >Week</button>
    <button @click="visible = 'day'" >Day</button>
    <div id="views">
    <div id="views">
    <transition name="fade">
      <div  class='calview weekView' v-if="visible == 'week'" >
        <week></week>
      </div>
      </transition>
      <transition name="fade">
      <div  class='calview monthView' v-if="visible == 'month'">
        <month></month>
      </div>
      </transition>
      <transition name="fade">
      <div  class='calview dayView' v-if="visible == 'day'">
        <day></day>
      </div>
      </transition>
    </div>
  </div>
</template>
<script>
  import Week from './week'
  import Month from './month'
  import Day from './day'
  export default {
    data: function () { 
    return { visible: 'month' } 
    },
    components: {
      Week,
      Month,
      Day
    },
    methods: {
      viewCalendar: function (calendar) {
        $('.calview').addClass('calendar-hidden'); 
        $('.' + calendar).removeClass('calendar-hidden');
      }
    } 
  }
</script>
<style>
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }
  .fade-enter, .fade-leave-active {
      opacity: 0
    }
</style>
