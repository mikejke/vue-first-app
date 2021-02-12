<template>
    <teleport to="body">
      <base-dialog v-if="inputInvalid" title="Неправильный формат" @close="confirmError">
        <template #default>
          <p>Введены неправильные данные!</p>
          <p>Убедитесь что ввели все правильно.</p>
        </template>
        <template #actions>
          <base-button @click="confirmError">
            Хорошо
          </base-button>
        </template>
      </base-dialog>
    </teleport>
  <base-card>
    <form @submit.prevent="submit">
      <div>
        <label for="title">Название</label>
        <input id="title" name="title" type="text" ref="title" />
      </div>
      <div>
        <label for="desc">Описание</label>
        <textarea id="desc" name="desc" rows="3" ref="desc" />
      </div>
      <div>
        <label for="link">Ссылка</label>
        <input id="link" name="link" type="url" ref="link" />
      </div>
      <div>
        <base-button type="submit">Подтвердить</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseDialog from "../UI/BaseDialog.vue";
export default {
  components: { BaseDialog },
  inject: ["addResource"],
  methods: {
    submit() {
      const enteredTitle = this.$refs.title.value;
      const enteredDesc = this.$refs.desc.value;
      const enteredLink = this.$refs.link.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDesc.trim() === "" ||
        enteredLink.trim() === ""
      ) {
        this.inputInvalid = true;
        return;
      }
      // call injected method
      this.addResource(enteredTitle, enteredDesc, enteredLink);
      // clear
      this.$refs.title.value = '';
      this.$refs.desc.value = '';
      this.$refs.link.value = '';
    },
    confirmError() {
      this.inputInvalid = false;
    }
  },
  data() {
    return {
      inputInvalid: false,
    };
  },
};
</script>

<style scoped>
div {
  margin: 0.8rem 0;
}
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}
input:focus,
textarea:focus {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  background: rgba(110, 25, 150, 0.1);
  border: 1px solid rgba(110, 25, 150);
  outline: none;
}
</style>
