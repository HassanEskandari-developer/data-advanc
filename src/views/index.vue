<template>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Manrope:wght@200..800&display=swap"
    rel="stylesheet"
  />
  <main class="w-full h-screen overflow-y-auto bg-[#1f2937] p-8 lg:px-0">
    <Overlay v-if="isRequest"></Overlay>
    <section
      class="w-[700px] lg:w-[700px] h-auto bg-[#475569] rounded-[20px] mx-auto flex flex-col justify-center items-center gap-y-5 lg:gap-y-10"
    >
      ,<Input @userVal="funUser($event)"></Input>
      <template v-if="posts.length > 0">
        <Text
          v-for="(slid, index) in posts"
          :userVl="varuser"
          :userDataVal="slid"
          :key="index"
        ></Text>
      </template>

      <div
        v-else-if="posts.length == 0 && varuser"
        class="border bg-red-500 w-[80%] flex justify-center items-center m-10 p-2 l rounded-[10px]"
      >
        <p class="text-[25px] font-bold text-white">
          لطفا کلمه مورد نظر را صحیح وارد کنید
        </p>
      </div>
      <!-- <div
        class="w-[80%] lg:w-full flex justify-center items-center relative lg:px-20"
      >
        
        <img
          src="/public/images/pattern-divider-desktop.svg"
          alt=""
          class="h-5"
        />

        <div
          class="w-24 h-24 border absolute top-[50%] translate-y-[50%] bg-green-400 rounded-full flex justify-center items-center cursor-pointer hover:scale-125 hover:transition duration-200"
          @click="dataHandel"
        >
          <img src="/public/images/icon-dice.svg" alt="" class="w-12 h-12" />
        </div>
      </div> -->
    </section>
  </main>
</template>

<script>
import axios from "axios";
import Overlay from "../components/overlay.vue";
import Text from "../components/text.vue";
import Input from "../components/input.vue";
export default {
  components: {
    Overlay,
    Text,
    Input,
  },
  data() {
    return {
      posts: [],
      isRequest: false,
      varuser: "",
    };
  },
  mounted() {
    this.getAdvise();
  },

  methods: {
    getAdvise() {
      // let myQueryString = `https://digikala.com/product?pageNumber=1&count=10&categoryId=10` => pass this in params object
      // let myQueryParam = 'https://api.expoyab.com/explore-service/api/v1/Company/22'
      // let myRequestBody = {
      //     title:'string',
      //     decription:'string',
      //     productId:1
      // }
      this.isRequest;
      axios
        .get(`https://api.adviceslip.com/advice/search/${this.varuser}`, null, {
          // params:{
          //     pageNumber:1,
          //     count:10,
          //     isShow:true
          // }
          // 'Authorization':'jwt token'
          // 'Content-Type':''
        })
        .then((response) => {
          console.log(response.data);
          if (response.data.slips) {
            this.posts = response.data.slips;
          } else {
            this.posts = [];
            setTimeout(() => {
              this.isRequest = true;
            }, 0.5);
            setTimeout(() => {
              this.isRequest = false;
            }, 2000);
          }
        });
      // .then((Response) => console.log(Response));
      console.log(this.posts);
    },
    funUser(event) {
      this.varuser = event;
      this.getAdvise();
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body,
main {
  font-family: "Manrope", sans-serif;
  font-optical-sizing: auto;
  font-weight: weight;
  font-style: normal;
}
</style>