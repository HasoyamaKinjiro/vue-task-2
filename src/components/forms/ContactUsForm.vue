<script setup lang="ts">
import { object, string } from "yup";
import { useForm } from "vee-validate";
import { reactive, ref } from "vue";
import { RouterLink } from "vue-router";
import UiInput from "@/components/UI/UiInput.vue";

interface ContactForm {
  first_name: string;
  last_name: string;
  email: string;
  question: string;
}

const contactFormSection = ref<HTMLElement | null>(null);
const isSuccess = ref(false);

const initialContactForm: ContactForm = {
  first_name: "",
  last_name: "",
  email: "",
  question: "",
};

const schema = object().shape({
  first_name: string().required("First name is required"),
  last_name: string().required("Last name is required"),
  email: string().email("Invalid email").required("Email is required"),
  question: string().min(8, "Question must be at least 8 characters").required("Question is required"),
});

const contactForm = reactive(
  JSON.parse(JSON.stringify(initialContactForm)),
) as ContactForm;

const {
  handleSubmit: handleSubmitContactUs,
  resetForm,
  setErrors,
  isSubmitting,
} = useForm({
  initialValues: initialContactForm,
  validationSchema: schema,
});

const onSubmit = handleSubmitContactUs(async (values) => {
  try {
    const params: ContactForm = {
      first_name: values.first_name,
      last_name: values.last_name,
      email: values.email,
      question: values.question,
    };
    await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(params),
    });
    resetForm();
    isSuccess.value = true;
    contactFormSection.value?.scrollIntoView({
      block: "center",
      behavior: "smooth",
    });
  } catch (error) {
    setErrors(error);
  }
});
</script>

<template>
  <div ref="contactFormSection" class="contact-form-section">
    <div class="container">
      <h2 class="form-title">
        Send us a message
      </h2>

      <div class="form-wrapper">
        <div v-if="isSuccess" class="success-message">
          <div class="success-text">
            Your message has been sent, our team will reach back shortly!
          </div>
          <RouterLink to="/" class="submit-button">
            <span style="color: #fff;">Home</span>
          </RouterLink>
        </div>
        <form
          v-else
          class="form"
          @submit.prevent="onSubmit"
        >
          <div class="form-fields">
            <div class="form-row">
              <div class="form-col">
                <label>
                  First Name
                  <UiInput
                    v-model="contactForm.first_name"
                    name="first_name"
                    placeholder="First Name"
                  />
                </label>
              </div>
              <div class="form-col">
                <label>
                  Last Name
                  <UiInput
                    v-model="contactForm.last_name"
                    name="last_name"
                    placeholder="Last Name"
                  />
                </label>
              </div>
            </div>
            <div class="form-group">
              <label>
                Email
                <UiInput
                  v-model="contactForm.email"
                  name="email"
                  placeholder="Email"
                />
              </label>
            </div>
            <div class="form-group">
              <label>
                Question
                <UiInput
                  v-model="contactForm.question"
                  name="question"
                  placeholder="Question"
                  :text-area="true"
                />
              </label>
            </div>
          </div>

          <button
            :disabled="isSubmitting"
            type="submit"
            class="submit-button"
          >
            Send
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.contact-form-section {
  padding: 32px 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

.form-title {
  margin-bottom: 36px;
  text-align: center;
}

.form-wrapper {
  min-height: 100%;
  display: flex;
  justify-content: center;
}

.success-message {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px 38px;
}

.success-text {
  padding: 10px 100px;
  text-align: center;
  font-weight: 500;
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 580px;
}

.form-fields {
  width: 100%;
  gap: 16px;
}

.form-row {
  display: flex;
  gap: 16px;
}

.form-col {
  width: 50%;
}

.submit-button {
  margin-top: 24px;
  padding: 12px 60px;
  font-size: 16px;
  background-color: var(--green-bg-1);
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}

.submit-button:hover:not(:disabled) {
  background-color: hsla(160, 100%, 37%, 0.55);
}
</style>
