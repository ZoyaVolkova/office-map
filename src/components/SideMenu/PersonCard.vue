<template>
  <div class="person">
    <div class="person__photo">
      <img :src="person.picture" alt="photo" />
    </div>
    <div class="person__info">
      <div class="person__info-name">
        <span class="bold">{{ person.name }} ({{ person.age }})</span>
      </div>

      <div class="person__info-email">
        <span class="bold">Почта: </span><br />
        {{ person.email }}
      </div>
      <div class="person__info-email">
        <span class="bold">Дата регистрации:</span> <br />
        {{ formatedDate }}
      </div>
      <div class="person__info-about">
        <span class="bold">О себе:</span> <br />
        {{ person.about }}
      </div>
    </div>
  </div>
</template>

<script>
import { format } from 'date-fns'

export default {
  props: {
    person: {
      type: Object,
      default: null,
    },
  },
  computed: {
    formatedDate() {
      return format(new Date(this.person.registered), 'dd.MM.yyyy HH:mm')
    },
  },
}
</script>

<style scoped>
.person {
  display: grid;
  grid-template-columns: 50px 1fr;
  grid-gap: 8px;
  line-height: 150%;
}

.person__photo img {
  height: 50px;
  width: 50px;
  border-radius: 50%;
}

.person__info {
  display: grid;
  grid-gap: 8px;
  font-size: 18px;
}

.person__info-name {
  margin-bottom: 10px;
  color: rgb(20, 82, 216);
  font-size: 22px;
}
.bold {
  font-weight: bold;
}
</style>
