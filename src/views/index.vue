<template>
  <main class="w-full h-screen bg-[#1f2937] flex justify-center items-center px-5 lg:px-0"> 
    <section class="w-[700px] lg:w-[700px]  h-[400px]  bg-[#475569] rounded-[20px] flex flex-col justify-center items-center gap-y-5 lg:gap-y-10 ">

        <div>
            <h2 class="text-xl text-[#059669] font-bold">Lorem, ipsum dolor. #</h2>
        </div>
        <div class="text-center px-6 lg:px-14">
            <p class="text-2xl text-white font-bold">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nobis odio animi magnam quam iusto placeat accusantium accusamus unde culpa optio!</p>
        </div>
        <div class="w-[80%] lg:w-full flex justify-center items-center relative lg:px-20">
            <!-- <span class="border w-[80%] h-[1px]"></span> -->
            <img src="/public/images/pattern-divider-desktop.svg" alt="" class="h-5 ">

            <div class="w-24 h-24 border absolute top-[45px] left-[95px] lg:top-[65px] lg:left-[305px] bg-green-400 rounded-full flex justify-center items-center">
            <img src="/public/images/icon-dice.svg" alt="" class=" w-12 h-12 ">
                
                </div>            
        </div>
    </section>
  </main>
</template>

<script>
export default {

}
</script>

<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>