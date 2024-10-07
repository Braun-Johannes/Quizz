<script>
export default {
  data() {
    return {
      question: '',
      answers: ['', '', '', ''],
      correctAnswer: '',
      difficulty: '',
      subject: '',
      tags: '',
      hint: '',
      createdCards: []
    }
  },
  methods: {
    addCard() {
      const newCard = {
        question: this.question,
        answers: this.answers,
        correctAnswer: this.correctAnswer,
        difficulty: this.difficulty,
        subject: this.subject,
        tags: this.tags,
        hint: this.hint
      }
      this.createdCards.push(newCard)
      // Clear form inputs
      this.question = ''
      this.answers = ['', '', '', '']
      this.correctAnswer = ''
      this.difficulty = ''
      this.subject = ''
      this.tags = ''
      this.hint = ''
    }
  }
}
</script>

<template>
  <div class="createContainer">
    <span class="logoDot createDot"></span>
    <p class="slogan">Create a card</p>
    <form @submit.prevent="addCard">
      <div class="form-group">
        <label>Question:</label>
        <input v-model="question" type="text" required />
      </div>
      <div class="form-group">
        <label>Answer 1:</label>
        <input v-model="answers[0]" type="text" required />
      </div>
      <div class="form-group">
        <label>Answer 2:</label>
        <input v-model="answers[1]" type="text" required />
      </div>
      <div class="form-group">
        <label>Answer 3:</label>
        <input v-model="answers[2]" type="text" required />
      </div>
      <div class="form-group">
        <label>Answer 4:</label>
        <input v-model="answers[3]" type="text" required />
      </div>
      <div class="form-group">
        <label>Correct Answer:</label>
        <input v-model="correctAnswer" type="text" required />
      </div>
      <div class="form-group">
        <label>Difficulty:</label>
        <input v-model="difficulty" type="text" required />
      </div>
      <div class="form-group">
        <label>Subject:</label>
        <input v-model="subject" type="text" required />
      </div>
      <div class="form-group">
        <label>Tags:</label>
        <input v-model="tags" type="text" required />
      </div>
      <div class="form-group">
        <label>Hint:</label>
        <input v-model="hint" type="text" required />
      </div>
      <button type="submit">Create Card</button>
    </form>

    <div v-for="(card, index) in createdCards" :key="index" class="card">
      <div class="card-front">
        <p>{{ card.question }}</p>
        <ul>
          <li v-for="(answer, idx) in card.answers" :key="idx">{{ answer }}</li>
        </ul>
      </div>
      <div class="card-back">
        <p>Correct Answer: {{ card.correctAnswer }}</p>
        <p>Difficulty: {{ card.difficulty }}</p>
        <p>Subject: {{ card.subject }}</p>
        <p>Tags: {{ card.tags }}</p>
        <p>Hint: {{ card.hint }}</p>
      </div>
    </div>
  </div>
</template>

<style>
.createContainer {
  display: flex;
  flex-direction: column;
  align-items: center;

  padding: 10px;
}

.form-group {
  display: flex;
  align-items: center;

  margin-bottom: 5px;
  text-align: left;
}

.form-group label {
  width: 200px; /* Adjust this width as needed */
  margin-right: 100px;
}

.createDot {
  height: 50px;
  width: 50px;
}
</style>
