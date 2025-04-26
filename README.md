# Form Project - Quinstreet Assignment

A responsive, pixel-perfect form page built with Vue 3, designed to meet the provided requirements including animation, validation, and AJAX form submission.

---

## 📋 Overview

This project features:

- Pixel-perfect design based on mockups
- Cross-browser compatibility (Chrome, Firefox, Safari, Edge)
- Fully responsive layout (mobile breakpoint: 767px)
- Smooth background color transition between `#ECF8FB` and `#EFEFEF` every 5 seconds
- Form validation with dynamic error handling
- AJAX form submission to a specified endpoint
- Accessibility best practices implemented

---

## 🌐 Live Demo

👉 [View Hosted Project Here](https://spectre8498.github.io/quinstreet_assgn/)

---

## 📑 Features

### General Design

- **Pixel Perfect Layout**: Built precisely according to provided mockups.
- **Cross-Browser Compatibility**: Tested on Chrome, Firefox, Safari, Edge.
- **Responsive Design**: Mobile optimization with breakpoint at 767px.
- **Smooth Background Transition**: 
  - Transitions between `#ECF8FB` and `#EFEFEF` every 5 seconds continuously.
- **Performance Optimized**: 
  - Minimal assets, optimized loading speed.

### Form Features

- **Input Masking**:
  - Phone field accepts only U.S. phone numbers: `(XXX) XXX-XXXX`
- **Mobile UX Optimization**: 
  - Form is highly usable on mobile devices.
- **Field Validation**:
  - `Name`: Required, minimum 2 characters.
  - `Phone`: Required, with input mask validation.
  - `Email`: Required, valid email format.
  - `City` and `State`: Optional.
- **Error Indication**:
  - Input fields with validation errors change their border color to `#D50303`.
- **AJAX Submission**:
  - Data is sent to:
    ```
    https://formsws-hilstaging-com-0adj9wt8gzyq.runscope.net/solar
    ```
  - No page reload.
  - Upon success, submit button text changes to `"Submitted"`, disabling further submissions.

### Additional Features

- **"Read More" Link**:
  - Opens [Google](https://www.google.com) in a new tab (`_blank`).

- **Accessibility**:
  - Alt text for images and proper ARIA attributes used where necessary.

---

## 🛠 How to Run Locally

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/spectre8498/quinstreet_assgn.git
   cd quinstreet_assgn
   npm install
   npm run dev
```

### Project Structure
quinstreet_assgn/
├── public/
│   └── index.html
├── src/
│   ├── assets/
│   │   ├── logo.png
│   │   └── background.svg     
│   ├── components/
│   │   ├── Form.vue
│   │   └── BackgroundAnimation.vue
│   ├── App.vue
│   └── main.js
├── package.json
├── vite.config.js
└── README.md