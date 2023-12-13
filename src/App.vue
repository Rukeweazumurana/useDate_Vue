<template>
<div>
   <p>Current Date: {{ currentDate.toLocaleDateString() }}</p>
   <button @click="getCurrentDate">Get Current Date</button>
   <br />
   <button @click="getDayAndMonth">Get Day and Month</button>
   <br />
   <label>Add Days: </label>
   <input
     type="number"
     v-model="daysToAdd"
   />
   <button @click="addDays">Add Days</button>
   <br />
   <label>Add Months: </label>
   <input
     type="number"
     v-model="monthsToAdd"
   />
   <button @click="addMonths">Add Months</button>
   <br />
   <p v-if="resultDate">Result Date: {{ resultDate.toLocaleDateString() }}</p>
</div>
</template>

<script>
export default {
data() {
   return {
     currentDate: new Date(),
     daysToAdd: 0,
     monthsToAdd: 0,
     resultDate: null,
   };
},
methods: {
   getCurrentDate() {
     this.currentDate = new Date();
   },
   getDayAndMonth() {
     const day = this.currentDate.getDate();
     const month = this.currentDate.getMonth() + 1; // Months are 0-based
     alert(`Day: ${day}, Month: ${month}`);
   },
   addDays() {
     const newDate = new Date(this.currentDate);
     newDate.setDate(this.currentDate.getDate() + this.daysToAdd);
     this.resultDate = newDate;
   },
   addMonths() {
     const newDate = new Date(this.currentDate);
     newDate.setMonth(this.currentDate.getMonth() + this.monthsToAdd);
     this.resultDate = newDate;
   },
},
};
</script>