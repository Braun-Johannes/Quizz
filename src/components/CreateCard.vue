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

    <div class="card-container">
      <div class="card-content">
        <div class="card-front">
          <div class="form-group">
            <label>Question:</label>
            <input v-model="question" type="text" required />
          </div>

          <div class="form-group" v-for="(answer, index) in answers" :key="index">
            <label>Answer {{ index + 1 }}:</label>
            <input v-model="answers[index]" type="text" required />
          </div>
        </div>
        <div class="card-back">
          <div class="form-group">
            <label>Correct Answer:</label>
            <select v-model="correctAnswer" required>
              <option v-for="(answer, index) in answers" :key="answer" :value="answer">
                Answer {{ index + 1 }}
              </option>
            </select>
          </div>
        </div>
      </div>
      <div class="additional-info">
        <div class="form-group">
          <label>Difficulty:</label>
          <select v-model="difficulty" required>
            <option value="1">1 Star</option>
            <option value="2">2 Stars</option>
            <option value="3">3 Stars</option>
            <option value="4">4 Stars</option>
          </select>
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
      </div>
      <button type="submit" @click="addCard">Create Card</button>
    </div>

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

<style scoped>
.createDot {
  height: 50px;
  width: 50px;
}

.card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-content {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.card-front,
.card-back {
  background-color: grey;
  padding: 20px;
  margin: 10px;
  border-radius: 10px;
  width: 300px;
}

.additional-info {
  margin-top: 20px;
  display: flex;
}

.form-group {
  margin-bottom: 15px;
}

button {
  margin-top: 20px;
}
</style>
