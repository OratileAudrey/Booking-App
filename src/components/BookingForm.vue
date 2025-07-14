<template>
  <div class="booking-container">
    <div class="header-section">
      <div class="brand-title">
        <h1>Fun Travels</h1>
        <span class="tagline">Your Trip, Your Own Way!</span>
      </div>
      <div class="logo-container">
        <img src="/logo.png" alt="Oratile Audrey Logo" class="logo" />
      </div>
    </div>

    <form @submit.prevent="submitForm" class="booking-form">
      <div class="form-grid">
        <div class="input-group">
          <label for="name">Your Name</label>
          <input id="name" name="name" v-model="form.name" type="text" required placeholder="Enter your full name" />
        </div>

        <div class="input-group">
          <label for="destination">Destination</label>
          <input id="destination" name="destination" v-model="form.destination" type="text" required
            placeholder="Where do you want to go?" />
        </div>

        <div class="input-group">
          <label for="people">Number of Travelers</label>
          <input id="people" name="people" v-model="form.people" type="number" min="1" required />
        </div>

        <div class="input-group">
          <label for="dates">Travel Dates</label>
          <input id="dates" name="dates" v-model="form.dates" type="text" placeholder="e.g. 10 Dec - 15 Dec" required />
        </div>

        <div class="input-group">
          <label for="duration">Duration (Days)</label>
          <input id="duration" name="duration" v-model="form.duration" type="number" min="1" required />
        </div>
      </div>

      <div class="input-group">
        <label for="budget">Budget Range</label>
        <input id="budget" name="budget" v-model="form.budget" type="text" required
          placeholder="e.g. R3,000 - R12,000" />
      </div>

      <div class="input-group">
        <label for="help">What can I help you with?</label>
        <select id="help" v-model="form.help" required>
          <option disabled value="">-- Choose your needs --</option>
          <option>🏨 Accommodation</option>
          <option>🚗 Transport</option>
          <option>🎯 Activities & Experiences</option>
          <option>✈️ Planning the whole trip</option>
          <option>🤔 Not sure, let's discuss</option>
        </select>
      </div>

      <div class="input-group">
        <label for="extra">Tell me more about your dream trip</label>
        <textarea id="extra" v-model="form.extra" rows="4"
          placeholder="Any special requirements, preferences, or things you'd love to do?" />
      </div>

      <button type="submit" class="submit-btn">
        <span class="btn-icon">💬</span>
        Let's Chat on WhatsApp
      </button>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { reactive } from 'vue'

const form = reactive({
  name: '',
  destination: '',
  people: 1,
  dates: '',
  duration: 1,
  budget: '',
  help: '',
  extra: ''
})

const submitForm = () => {
  const message = `Hi Fun Travels team! 🌍

My name is ${form.name} !

My Trip Details:
• Destination: ${form.destination}
• Travelers: ${form.people}
• Dates: ${form.dates}
• Duration: ${form.duration} day(s)
• Budget: ${form.budget}

I need help with: ${form.help}

Additional info: ${form.extra || 'Nothing specific!'}

Thank you! `

  const encodedMessage = encodeURIComponent(message)
  const phone = '27790618994'
  const url = `https://wa.me/${phone}?text=${encodedMessage}`
  window.open(url, '_blank')
}
</script>

<style scoped>
.booking-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 20px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.header-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 2px solid rgba(255, 255, 255, 0.2);
}

.brand-title {
  display: flex;
  flex-direction: column;
  color: white;
}

.brand-title h1 {
  font-size: 2rem;
  font-weight: 700;
  margin: 0;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  letter-spacing: 1px;
}

.tagline {
  font-size: 0.9rem;
  opacity: 0.9;
  font-weight: 300;
  margin-top: 0.2rem;
  font-style: italic;
}

.logo-container {
  display: flex;
  align-items: center;
}

.logo {
  height: 70px;
  width: auto;
  border-radius: 50%;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  border: 3px solid rgba(255, 255, 255, 0.3);
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}


.booking-form {
  background: white;
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.form-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.input-group label {
  font-weight: 600;
  color: #2c3e50;
  font-size: 0.95rem;
  letter-spacing: 0.5px;
}

.input-group input,
.input-group select,
.input-group textarea {
  padding: 1rem;
  font-size: 1rem;
  border: 2px solid #e1e8ed;
  border-radius: 12px;
  background: #f8fafc;
  transition: all 0.3s ease;
  font-family: inherit;
}

.input-group input:focus,
.input-group select:focus,
.input-group textarea:focus {
  outline: none;
  border-color: #667eea;
  background: white;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  transform: translateY(-2px);
}

.input-group input::placeholder,
.input-group textarea::placeholder {
  color: #94a3b8;
  font-style: italic;
}

.input-group select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
  background-position: right 1rem center;
  background-repeat: no-repeat;
  background-size: 1.5em 1.5em;
  padding-right: 3rem;
}

.input-group textarea {
  resize: vertical;
  min-height: 100px;
  line-height: 1.5;
}

.submit-btn {
  width: 100%;
  padding: 1.2rem 2rem;
  background: linear-gradient(135deg, #25d366 0%, #128c7e 100%);
  color: white;
  border: none;
  border-radius: 12px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  margin-top: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.submit-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(37, 211, 102, 0.4);
}

.submit-btn:active {
  transform: translateY(-1px);
}

.btn-icon {
  font-size: 1.2rem;
}

/* Responsive design */
@media (max-width: 768px) {
  .booking-container {
    margin: 1rem;
    padding: 1.5rem;
  }

  .header-section {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }

  .brand-title h1 {
    font-size: 1.8rem;
  }

  .logo {
    height: 50px;
  }

  .booking-form {
    padding: 1.5rem;
  }

  .form-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
}

/* Smooth animations */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.booking-container {
  animation: fadeIn 0.6s ease-out;
}
</style>
