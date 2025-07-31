<script setup>
import { computed, ref } from "vue";


import question from "@/json/ask-question.json";
import CustomDropDown from "@/components/shared/drop-down/custom-drop-down/CustomDropDown.vue";

const importQuestion = ref(question);
const questionData = ref({});

const handleAnswer = (question, answer) => {
  questionData.value[question] = answer;
};

const contactData = ref({
  firstName: "",
  lastName: "",
  phone: "",
  projectFile: null,
});

const phoneTouched = ref(false);

const formatPhone = () => {
  let digits = contactData.value.phone.replace(/\D/g, "");

  // Если начинается с 8, заменяем на +7
  if (digits.startsWith("8")) {
    digits = "7" + digits.slice(1);
  }

  // Если не начинается с 7, добавляем
  if (!digits.startsWith("7")) {
    digits = "7" + digits;
  }

  // Обрезаем до 11 цифр (без +)
  digits = digits.slice(0, 11);

  // Форматируем как +7 (XXX) XXX-XX-XX
  let formatted = "+7";
  if (digits.length > 1) formatted += " (" + digits.slice(1, 4);
  if (digits.length >= 4) formatted += ") " + digits.slice(4, 7);
  if (digits.length >= 7) formatted += "-" + digits.slice(7, 9);
  if (digits.length >= 9) formatted += "-" + digits.slice(9, 11);

  contactData.value.phone = formatted;
};

// Проверка на правильный формат: +7 и 10 цифр
// const isValid = computed(() => {
//   return /^\+7\d{10}$/.test(contactData.value.phone);
// });

// Проверка: номер должен быть в формате +7 (XXX) XXX-XX-XX
const isValid = computed(() => {
  return /^\+7 \(\d{3}\) \d{3}-\d{2}-\d{2}$/.test(contactData.value.phone);
});

const handleFileUpload = (e) => {
  contactData.value.projectFile = e.target.files[0];
};

const submitForm = async () => {
  try {
    // if (!/^[\d\+][\d\(\)\ -]{10,11}\d$/.test(contactData.value.phone)) {
    //   alert("Введите корректный номер телефона 8 (900) 000 00 00*");
    //   return;
    // }

    const formData = new FormData();

    const formKitchen = [];

    formData.append("firstName", contactData.value.firstName);
    formData.append("lastName", contactData.value.lastName);
    formData.append("phone", contactData.value.phone);

    if (contactData.value.projectFile) {
      formData.append("projectFile", contactData.value.projectFile);
    }

    // console.log(questionData.value);
    for (const value of Object.values(questionData.value)) {
      formKitchen.push(value);
    }

    formData.append("formKitchen", JSON.stringify(formKitchen));

    const response = await fetch("http://localhost:4000/api/data", {
      method: "POST",
      body: formData,
    });

    if (!response.ok) {
      const errData = await response.json().catch(() => ({}));
      throw new Error(
        errData.message || `HTTP error! status: ${response.status}`
      );
    }

    const data = await response.json();
    console.log("Сервер получил данные:", data.message);
  } catch (error) {
    console.error("Ошибка при отправке формы:", error.message);
  } finally {
    contactData.value = {
      firstName: "",
      lastName: "",
      phone: "",
      projectFile: null,
    };
  }
};
</script>

<template>
  <section class="kitchen-form-section">
    <h2 class="kitchen-form-section__hidden-anchor" id="post-order"></h2>
    <form
      class="kitchen-form"
      enctype="multipart/form-data"
      @submit.prevent="submitForm"
    >
      <div class="kitchen-form__content">
        <div class="kitchen-form__content-left">
          <legend class="kitchen-form__legend">Выберите данные кухни:</legend>
          <CustomDropDown
            v-for="item in importQuestion"
            :question="item.question"
            :list="item.ask"
            :key="item.question"
            :modelValue="item.answer"
            @update:modelValue="(value) => handleAnswer(item.question, value)"
          />
        </div>

        <div class="kitchen-form__content-right">
          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">Контактные данные:</legend>
            <input
              type="text"
              @input="
                contactData.firstName = $event.target.value.replace(
                  /[^A-Za-zА-Яа-яЁё]/g,
                  ''
                )
              "
              name="firstName"
              placeholder="Имя*"
              class="kitchen-form__input"
              v-model="contactData.firstName"
              required
            />
            <input
              type="text"
              @input="
                contactData.lastName = $event.target.value.replace(
                  /[^A-Za-zА-Яа-яЁё]/g,
                  ''
                )
              "
              name="lastName"
              placeholder="Фамилия*"
              class="kitchen-form__input"
              v-model="contactData.lastName"
              required
            />
            <input
              @input="formatPhone"
              @blur="phoneTouched = true"
              @focus="phoneTouched = false"
              type="tel"
              name="phone"
              placeholder="+7 (___) ___-__-__"
              class="kitchen-form__input"
              v-model="contactData.phone"
              required
            />
            <p
              v-if="phoneTouched && !isValid"
              class="kitchen-form__number-error"
            >
              ❌ Неверно введен номер
            </p>
          </fieldset>

          <div class="kitchen-form__section">
            <label class="kitchen-form__file-label">
              <input
                type="file"
                name="projectFile"
                class="kitchen-form__file"
                @change="handleFileUpload"
                accept="image/*,.pdf,.doc,.docx,.png,.jpg,.jpeg"
              />
            </label>
          </div>
        </div>
      </div>

      <button type="submit" class="kitchen-form__submit">Отправить</button>
    </form>
  </section>
</template>

<style src="./style.scss"></style>