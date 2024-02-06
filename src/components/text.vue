<template>

    <div  class="flex flex-col justify-center items-center gap-y-5 lg:gap-y-10 p-7">
      <div>
        <h2 class="text-xl text-[#059669] font-bold">{{userVl}}</h2>
      </div>
      <div class="text-center px-6 lg:px-14">
        
        <p class="text-2xl text-white font-bold">{{userDataVal.advice}}</p>
       -
      </div>
    </div>

</template>

<script>
export default {
    name:'text',
    props:{
        userVl:String,
        userDataVal:Object,
    }
}
</script>

<style>

</style>