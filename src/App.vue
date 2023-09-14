<template>
  <div class="main-container">
    <transition name="fade" mode="out-in">
    <Questions v-if="questionsAnswered < questions.length" :questions="questions" :questionsAnswered="questionsAnswered" @question-answered="questionAnswered" />
    <Result v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>
    
    <button type="button" class="reset-btn" @click.prevent="reset" v-if="questionsAnswered === questions.length">Reset</button>
  </div>
</template>

<script>
import Questions from './components/Questions.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components:{
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "What is the colour of Raichu's cheeks",
          answers: [
            {
              text: 'Yellow',
              is_correct: true
            },
            {
              text: 'Red',
              is_correct: false
            },
            {
              text: 'Orange',
              is_correct: false
            },
            {
              text: 'Brown',
              is_correct: false
            }
          ]
        },
        {
          q: 'Which Pokemon Professor in the series is considered to be the best scientist about Pokemon"?',
          answers: [
            {
              text: 'Professor Agatha',
              is_correct: false
            },
            {
              text: 'Professor Elm',
              is_correct: false
            },
            {
              text: 'Professor Oak',
              is_correct: true
            },
            {
              text: 'Professor Rowan',
              is_correct: false
            }
          ]
        },
        {
          q: 'Which type of Pokemon is Gyarados?',
          answers: [
            {
              text: 'Water and Dragon',
              is_correct: false
            },
            {
              text: 'Water and Flying',
              is_correct: true
            },
            {
              text: 'Flying and Dragon',
              is_correct: false
            },
            {
              text: 'Dragon and Ice',
              is_correct: false
            }
          ]
        },
        {
          q: 'Which year was Pokemon Red and Green released?',
          answers: [
            {
              text: '1995',
              is_correct: false
            },
            {
              text: '1994',
              is_correct: false
            },
            {
              text: '1998',
              is_correct: false
            },
            {
              text: '1996',
              is_correct: true
            }
          ]
        },
        {
          q: 'What is the number of Pokemon in the original Pokedex?',
          answers: [
            {
              text: '148',
              is_correct: false
            },
            {
              text: '150',
              is_correct: false
            },
            {
              text: '145',
              is_correct: false
            },
            {
              text: '151',
              is_correct: true
            }
          ]
        },
        {
          q: 'What is the slogan of the Pokemon franchise?',
          answers: [
            {
              text: 'Gotta catch ‘em all',
              is_correct: true
            },
            {
              text: 'Catch ‘em all',
              is_correct: false
            },
            {
              text: 'Catch ‘em if you can',
              is_correct: false
            },
            {
              text: 'Gotta catch all',
              is_correct: false
            }
          ]
        },
        {
          q: 'What does the name Pokemon really mean?',
          answers: [
            {
              text: 'It is the name of a gaming company',
              is_correct: false
            },
            {
              text: 'It is a combination of pocket and monster',
              is_correct: true
            },
            {
              text: 'It is the hometown of the creator',
              is_correct: false
            },
            {
              text: 'No real meaning behind it',
              is_correct: false
            }
          ]
        },
        {
          q: 'What is the difference between a female and a male Pikachu?',
          answers: [
            {
              text: 'The colour of the cheeks',
              is_correct: false
            },
            {
              text: 'The shape of the tail',
              is_correct: true
            },
            {
              text: 'The weight of the body',
              is_correct: false
            },
            {
              text: 'No difference between the genders',
              is_correct: false
            }
          ]
        },
      ],
      results: [
        {
          min: 0,
          max: 5,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!"
        },
        {
          min: 6,
          max: 7,
          title: "Close!",
          desc: "You are almost a Pokemon master!"
        },
        {
          min: 8,
          max: 8,
          title: "Wow, you're a genius!",
          desc: "You are a Pokemon master!"
        }
      ]
    }
  },
  methods:{
    questionAnswered(is_correct){
      if(is_correct){
        this.totalCorrect++;
      }

      this.questionsAnswered++;
    },
    reset(){
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  }
}
</script>

<style></style>