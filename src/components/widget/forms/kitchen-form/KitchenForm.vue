<script setup></script>

<template>
  <section id="post-order">
    <h2 class="kitchen-form__title">Сделать заявку</h2>
    <form class="kitchen-form" enctype="multipart/form-data">
      <div class="kitchen-form__content">
        <div class="kitchen-form__content-left">
          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">1. Форма кухни?</legend>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="kitchenShape"
                value="угловая"
                class="kitchen-form__radio"
              />
              Угловая
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="kitchenShape"
                value="прямая"
                class="kitchen-form__radio"
              />
              Прямая
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="kitchenShape"
                value="п-образная"
                class="kitchen-form__radio"
              />
              П-образная
            </label>
          </fieldset>

          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">
              2. Материал из которого будет изготовлена кухня?
            </legend>
            <label class="kitchen-form__option">
              <input
                type="checkbox"
                name="material"
                value="пластик"
                class="kitchen-form__checkbox"
              />
              Пластик
            </label>
            <label class="kitchen-form__option">
              <input
                type="checkbox"
                name="material"
                value="лдсп"
                class="kitchen-form__checkbox"
              />
              ЛДСП
            </label>
            <label class="kitchen-form__option">
              <input
                type="checkbox"
                name="material"
                value="пленка"
                class="kitchen-form__checkbox"
              />
              Плёнка
            </label>
            <label class="kitchen-form__option">
              <input
                type="checkbox"
                name="material"
                value="консультация"
                class="kitchen-form__checkbox"
              />
              Нужна консультация
            </label>
          </fieldset>

          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">3. Срок изготовления?</legend>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="deadline"
                value="1 месяц"
                class="kitchen-form__radio"
              />
              В течение месяца
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="deadline"
                value="3 месяца"
                class="kitchen-form__radio"
              />
              В течение 3 месяцев
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="deadline"
                value="от полугода"
                class="kitchen-form__radio"
              />
              От полугода
            </label>
          </fieldset>

          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">4. Бюджет?</legend>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="budget"
                value="150-300"
                class="kitchen-form__radio"
              />
              150–300 тысяч
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="budget"
                value="300-500"
                class="kitchen-form__radio"
              />
              300–500 тысяч
            </label>
            <label class="kitchen-form__option">
              <input
                type="radio"
                name="budget"
                value="500+"
                class="kitchen-form__radio"
              />
              От 500 и выше
            </label>
          </fieldset>
        </div>

        <div class="kitchen-form__content-right">
          <fieldset class="kitchen-form__section">
            <legend class="kitchen-form__legend">Контактные данные:</legend>
            <input
              type="text"
              name="firstName"
              placeholder="Имя*"
              class="kitchen-form__input"
              required
            />
            <input
              type="text"
              name="lastName"
              placeholder="Фамилия*"
              class="kitchen-form__input"
              required
            />
            <input
              type="tel"
              name="phone"
              placeholder="Телефон*"
              class="kitchen-form__input"
              required
            />
          </fieldset>

          <div class="kitchen-form__section">
            <label class="kitchen-form__file-label">
              Прикрепить свой проект:
              <input
                type="file"
                name="projectFile"
                class="kitchen-form__file"
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
