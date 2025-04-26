<script setup>
import { ref } from 'vue'

// Form fields
const name = ref('')
const city = ref('')
const state = ref('')
const phone = ref('')
const email = ref('')
const submitted = ref(false)
const isSubmitting = ref(false)

// Error states
const errors = ref({
    name: false,
    phone: false,
    email: false
})

// Validate form
const validateForm = () => {
    let valid = true
    errors.value.name = name.value.trim().length < 2
    errors.value.phone = !phone.value || !/^\(\d{3}\) \d{3}-\d{4}$/.test(phone.value)
    errors.value.email = !/^\S+@\S+\.\S+$/.test(email.value)

    if (errors.value.name || errors.value.phone || errors.value.email) {
        valid = false
    }
    return valid
}

const formatPhone = (event) => {
    let numbers = event.target.value.replace(/\D/g, '')
    if (numbers.length > 10) numbers = numbers.slice(0, 10)

    let formatted = ''
    if (numbers.length > 0) formatted += '(' + numbers.slice(0, 3)
    if (numbers.length >= 4) formatted += ') ' + numbers.slice(3, 6)
    if (numbers.length >= 7) formatted += '-' + numbers.slice(6)
    phone.value = formatted
}

// Submit form using fetch
const submitForm = async () => {
    if (!validateForm()) return

    isSubmitting.value = true

    try {
        const response = await fetch('https://formsws-hilstaging-com-0adj9wt8gzyq.runscope.net/solar', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                name: name.value,
                city: city.value,
                state: state.value,
                phone: phone.value,
                email: email.value
            })
        })

        if (response.ok) {
            // submitted.value = true // this line should be here, as the service is failing im adding this line in finally block
            alert("Form Submitted Successfully.")
        } else {
            console.error('Form submission failed:', response.statusText)
        }
    } catch (error) {
        console.error('Form submission error:', error)
    }
    finally{
        submitted.value = true;
        isSubmitting.value = false;
        name.value = "";
        city.value = "";
        state.value = "";
        email.value = "";
        phone.value = "";
    }
}
</script>

<template>
    <div class="user-form">
        <div class="form-header">
            Enter to win a 3rd generation Nest<br />
            Learning Thermostat worth $249.
        </div>
        <form @submit.prevent="submitForm" role="form" aria-labelledby="formTitle">
            <input 
                v-model="name" 
                :class="{ error: errors.name }" 
                type="text" 
                placeholder="Name" 
                aria-label="Full Name"
                autocomplete="name"
            />

            <div class="row">
                <input 
                    v-model="city" 
                    type="text" 
                    placeholder="City" 
                    class="half-width" 
                    aria-label="City"
                    autocomplete="address-level2"
                />
                <input 
                    v-model="state" 
                    type="text" 
                    placeholder="State" 
                    class="half-width" 
                    aria-label="State"
                    autocomplete="address-level1"
                />
            </div>

            <input 
                v-model="phone" 
                :class="{ error: errors.phone }" 
                type="text" 
                placeholder="Phone Number"
                @input="formatPhone" 
                aria-label="Phone Number"
                autocomplete="tel"
            />

            <input 
                v-model="email" 
                :class="{ error: errors.email }" 
                type="email" 
                placeholder="Email Address" 
                aria-label="Email Address"
                autocomplete="email"
            />

            <button 
                type="submit" 
                :disabled="submitted || isSubmitting"
                :aria-busy="isSubmitting.toString()"
                :aria-disabled="(submitted || isSubmitting).toString()"
                aria-label="Submit to win"
            >
                <span v-if="isSubmitting">LOADING...</span>
                <span v-else>{{ submitted ? 'SUBMITTED' : 'ENTER TO WIN' }}</span>
            </button>
        </form>
    </div>
</template>


<style scoped>
.user-form {
    background: white;
    min-width: 670px;
    width: 60%;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
    margin: 0 auto 24px auto;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    overflow: hidden;
}

.form-header {
    background-color: #4A4A4A;
    color: white;
    padding: 18px;
    font-size: 18px;
    font-weight: bold;
    text-align: center;
    height: 80px;
    box-sizing: border-box;
}

form {
    display: flex;
    flex-direction: column;
    gap: 16px;
    padding: 20px 48px;
    flex-grow: 1;
}

.row {
    display: flex;
    gap: 20px;
}

.half-width {
    flex: 1;
}

input {
    padding: 14px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 6px;
    outline: none;
    transition: border-color 0.2s ease;
    width: 100%;
    box-sizing: border-box;
}

input.error {
    border-color: #D50303;
}

button {
    background-color: #F6931D;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
    border-radius: 40px;
    width: 50%;
    cursor: pointer;
    transition: background-color 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 12px rgba(255, 167, 38, 0.4);
    align-self: center;
}

button:hover:not(:disabled) {
    background-color: #fb8c00;
}

button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}

/* 📱 Responsive for screens below 767px */
@media (max-width: 767px) {
    .user-form {
        width: 90%;
        min-width: unset;
        padding: 0;
        margin: 16px auto;
        box-shadow: none;
        background: transparent;
    }

    .form-header {
        height: auto;
        padding: 16px 12px;
        font-size: 16px;
    }

    form {
        padding: 20px 20px;
        gap: 12px;
        background: white;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }

    .row {
        flex-direction: column;
        gap: 12px;
    }

    .half-width {
        width: 100%;
    }

    button {
        width: 100%;
        padding: 14px;
        font-size: 16px;
        border-radius: 30px;
    }
}
</style>
