<template>
<div style="cursor:pointer">
    <v-card
    class="ma-3"
    color="blue accent-3"
    dark
    width="380"
    height="284"
  >

    <v-card-actions @click="overlay = !overlay">
          <div class=" ma-auto my-16">
            <v-icon size="128" class="mt-1"> mdi-plus-circle </v-icon>
          </div>
    </v-card-actions>
  </v-card>

  <v-overlay :value="overlay">


    <v-card light>
      <v-card-title>Adicionar nova Turma
          <div class="px-2 ml-auto">
            <v-icon @click="overlay = !overlay"> mdi-close-circle-outline </v-icon>
          </div>
      </v-card-title>
      <v-card-text>
      <v-form class="px-3"     
      ref="form"
      v-model="valid"
      lazy-validation>
    <v-text-field
      v-model="name"
      :counter="10"
      :rules="nameRules"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-select
      v-model="select"
      :items="items"
      :rules="[v => !!v || 'Item is required']"
      label="Item"
      required
    ></v-select>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'You must agree to continue!']"
      label="Do you agree?"
      required
    ></v-checkbox>

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Validate
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>

    <v-btn
      color="warning"
      @click="resetValidation"
    >
      Reset Validation
    </v-btn>
    </v-form>
    </v-card-text>
    </v-card>


  </v-overlay>


</div>
</template>
<script>
  export default {
    data: () => ({
        overlay:false,
        valid: true,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) || 'Name must be less than 10 characters',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ],
      checkbox: false,
    }),

    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
  }

</script>