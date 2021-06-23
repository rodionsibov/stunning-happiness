<template>
  <main
    class="
      antialiased
      flex
      items-center
      justify-center
      min-h-screen
      p-4
      bg-green-100
    "
  >
    <div
      class="
        w-full
        bg-white
        flex-none
        shadow-lg
        rounded-lg
        p-4
        md:px-12
        md:py-6
        max-w-md
        relative
        overflow-hidden
      "
    >
      <svg
        viewBox="0 0 200 200"
        xmlns="http://www.w3.org/2000/svg"
        class="text-blue-100 absolute -left-24 -top-12 w-60 h-60"
      >
        <path
          fill="currentColor"
          d="M37.7,-68.4C48.5,-59,56.7,-48.2,63.3,-36.6C69.9,-25,74.8,-12.5,78.3,2C81.8,16.5,83.9,33.1,76.2,42.8C68.5,52.4,51,55.2,36.7,62.4C22.3,69.5,11.2,81.1,-2.2,84.9C-15.6,88.7,-31.1,84.8,-41.8,75.5C-52.6,66.3,-58.4,51.7,-66.2,38.2C-74,24.8,-83.8,12.4,-84.7,-0.5C-85.6,-13.5,-77.8,-26.9,-67.6,-36.2C-57.3,-45.5,-44.8,-50.6,-33.1,-59.6C-21.5,-68.6,-10.7,-81.4,1.3,-83.7C13.4,-86.1,26.8,-77.9,37.7,-68.4Z"
          transform="translate(100 100)"
        />
      </svg>
      <svg
        viewBox="0 0 200 200"
        xmlns="http://www.w3.org/2000/svg"
        class="text-yellow-100 absolute -right-24 -top-18 w-52 h-52"
      >
        <path
          fill="currentColor"
          d="M32.7,-57C44.5,-49.8,57.6,-45.3,64.7,-36.3C71.7,-27.2,72.7,-13.6,72.8,0.1C73,13.8,72.3,27.5,67.3,40.1C62.3,52.8,53,64.2,41,70.9C29.1,77.7,14.6,79.7,0,79.7C-14.5,79.6,-28.9,77.4,-39.1,69.6C-49.3,61.9,-55.2,48.6,-60.7,36C-66.2,23.5,-71.3,11.8,-71.5,-0.1C-71.7,-12,-67,-24,-62.2,-37.6C-57.3,-51.2,-52.1,-66.3,-41.7,-74.3C-31.3,-82.4,-15.7,-83.4,-2.6,-78.8C10.4,-74.3,20.9,-64.3,32.7,-57Z"
          transform="translate(100 100)"
        />
      </svg>
      <div class="relative">
        <div class="text-right text-gray-800">
          <p class="text-xm leading-3">Score</p>
          <p class="font-bold">60</p>
        </div>
        <div class="bg-white shadow-lg p-1 rounded-full w-full h-5 mt-4">
          <div class="bg-blue-700 rounded-full w-11/12 h-full"></div>
        </div>
        <div
          class="
            bg-gray-100
            rounded-lg
            p-2
            neumorph-1
            text-center
            font-bold
            text-gray-800
            mt-8
          "
        >
          <div class="bg-white p-5">
            {{ currentQuestion.question }}
          </div>
        </div>
        <div v-for="(choice, index) in currentQuestion.choices" :key="index">
          <div class="mt-8">
            <div
              class="
                neumorph-1
                option-default
                bg-gray-100
                p-2
                rounded-lg
                mb-3
                relative
              "
            >
              <div
                class="
                  absolute
                  right-0
                  top-0
                  shadow-md
                  bg-blue-700
                  p-1
                  transform
                  rotate-45
                  rounded-md
                  h-10
                  w-10
                  text-white
                  font-bold
                "
              >
                <p class="transform -rotate-45">+10</p>
              </div>
              <div class="rounded-lg font-bold flex p-2">
                <div class="p-3 rounded-lg">
                  {{ index }}
                </div>
                <div class="flex items-center pl-6">
                  {{ choice }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-8 text-center">
          <div class="h-1 w-12 bg-gray-800 rounded-full mx-auto"></div>
          <p class="font-bold text-gray-800">2/10</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";

export default {
  setup() {
    let questionCounter = ref(0);
    const currentQuestion = ref({
      question: "",
      answer: 1,
      choices: [],
    });

    const questions = [
      {
        question: "Which programming...",
        answer: 1,
        choices: ["Java", "Python", "C", "Jakarta"],
      },
      {
        question: "On Twitter...",
        answer: 3,
        choices: ["120", "260", "100"],
      },
    ];

    const onQuizStart = () => {
      currentQuestion.value = questions[questionCounter.value];
    };

    onMounted(() => {
      onQuizStart();
    });

    return { currentQuestion, questions, questionCounter, onQuizStart };
  },
};
</script>

<style scoped>
.neumorph-1 {
  box-shadow: 6px 6px 18px rgba(0, 0, 0, 0.09), -6px -6px 18px #fff;
}
</style>