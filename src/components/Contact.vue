<template>
  <!-- Contact Section START -->
  <section class="container-fluid py-5 px-3" id="contact">
    <!-- Heading Row -->
    <div class="row mb-4 justify-content-center">
      <div class="col-12 col-md-8 col-lg-6 text-center gap-1">
        <h1 class="d-inline-block p-2 fs-4">Contact</h1>
        <p>
          Got a project in mind or just want to chat about web development? Send
          me a message below and I'll get back to you as soon as I can.
        </p>

        <!-- Contact Form  -->
        <div class="text-start">
          <form @submit.prevent="submitForm" class="p-3">
            <div class="mb-3">
              <label for="exampleFormControlInput1" class="form-label"
                >YOUR NAME</label
              >
              <input
                type="text"
                class="form-control"
                id="exampleFormControlInput1"
                placeholder="e.g. Matt Bulaong"
                v-model="name" />
            </div>
            <div class="mb-3">
              <label for="exampleFormControlInput2" class="form-label"
                >EMAIL ADDRESS</label
              >
              <input
                type="email"
                class="form-control"
                id="exampleFormControlInput2"
                placeholder="matt@example.com"
                v-model="email" />
            </div>
            <div class="mb-3">
              <label for="exampleFormControlTextarea1" class="form-label"
                >PROJECT DETAILS / MESSAGE</label
              >
              <textarea
                class="form-control"
                id="exampleFormControlTextarea1"
                rows="5"
                placeholder="Tell me about your timeline, scope, and objectives..."
                v-model="message"></textarea>
            </div>

            <div
              class="d-flex flex-column flex-md-row justify-content-between align-items-md-center">
              <button
                id="contact-btn"
                class="text-center btn p-2"
                type="submit">
                CONTACT ME
              </button>
              <p class="mt-2">
                Direct email: <span>bulaongmatthew55432@gmail.com</span>
              </p>
            </div>
          </form>
        </div>
        <!-- Contact Form END -->
      </div>
    </div>

    <!-- recaptcha checkbox -->
    <div class="d-flex justify-content-center mt-2">
      <div ref="recaptchaContainer"></div>
    </div>
  </section>
  <!-- Contact Section END -->
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Notyf } from "notyf";
import "notyf/notyf.min.css";
import axios from "axios";

const notyf = new Notyf();

const WEB3FORM_ACCESS_KEY = "771b0ace-64c1-406e-90ea-7c675cfc92d4";
const SITE_KEY = "6LcDkBouAAAAAPOBCrvoZrvGEL9aEFl5290PT_VV";

//initial value for the email:

const subject = "New Message from Portfolio Contact Form";

const name = ref("");
const email = ref("");
const message = ref("");

const isLoading = ref(false);

//Function for sending the email:
async function submitForm() {
  if (!recaptchaToken.value) {
    notyf.error("Please verify that you are not a robot.");
    return;
  }

  isLoading.value = true;
  try {
    const response = await axios.post(
      "https://api.web3forms.com/submit",
      {
        access_key: WEB3FORM_ACCESS_KEY,
        subject: subject,
        name: name.value,
        message: message.value,
      },
      {
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json",
        },
      },
    );

    const result = response.data;

    if (result.success) {
      notyf.success("Message Sent!");
      name.value = "";
      email.value = "";
      message.value = "";
    }
  } catch (e) {
    notyf.error("Failed to send email");
  } finally {
    isLoading.value = false;
  }
}

const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref("");

// Callback called by reCAPTCHA when successful
function onRecaptchaSuccess(token) {
  recaptchaToken.value = token;
}

// Callback when expired
function onRecaptchaExpired() {
  recaptchaToken.value = "";
}

// Function to render the reCAPTCHA widget
function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.error("reCAPTCHA not loaded");
    return;
  }

  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: "normal", // or 'compact'
    callback: onRecaptchaSuccess,
    "expired-callback": onRecaptchaExpired,
  });
}

// Function to reset reCAPTCHA
function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = "";
  }
}

onMounted(() => {
  // This code waits for the Google reCAPTCHA library to load, then renders the reCAPTCHA widget using onMounted hook.
  // The widget is rendered with grecaptcha.render(), which requires a sitekey.
  // Callback functions handle success and expiration events.
  // reCAPTCHA is reset upon form submission to clear the token.
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);

  onBeforeUnmount(() => {
    clearInterval(interval);
  });
});
</script>
