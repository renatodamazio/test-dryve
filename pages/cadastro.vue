<template>
  <div>
    <md-steppers>
      <md-step id="first" md-label="DADOS DO CLIENTE">
        <form novalidate class="md-layout" @submit.prevent="validateUser">
            <md-card class="md-layout-item md-size-100 md-small-size-100">
                <md-card-area>
                    <md-card-content>
                        <div class="md-small-size-100 md-layout md-gutter">
                            <div  class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('firstName')">
                                    <label for="first-name">Nome</label>
                                    <md-input name="first-name" id="first-name" autocomplete="given-name" v-model="form.firstName" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.firstName.required">Digite seu primeiro nome</span>
                                    <span class="md-error" v-else-if="!$v.form.firstName.minlength">Campo inválido</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('lastName')">
                                    <label for="last-name">Sobrenome</label>
                                    <md-input name="last-name" id="last-name" autocomplete="given-lastName" v-model="form.lastName" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.lastName.required">Sobrenome é obrigatório</span>
                                    <span class="md-error" v-else-if="!$v.form.lastName.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>
                        
                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-50">
                                <md-field :class="getValidationClass('email')">
                                    <label for="email">E-mail</label>
                                    <md-input name="email" id="email" autocomplete="given-email" v-model="form.email" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.email.required">E-mail é obrigatório</span>
                                    <span class="md-error" v-else-if="!$v.form.email.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-25">
                                <md-field :class="getValidationClass('phone')">
                                    <label for="phone">Telefone</label>
                                    <md-input name="phone" id="phone" autocomplete="given-phone" v-model="form.phone" :disabled="sending" v-mask="['(##) ####-####', '(##) #####-####']"/>
                                    <span class="md-error" v-if="!$v.form.phone.required">Telefone é obrigatório</span>
                                    <span class="md-error" v-else-if="!$v.form.phone.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                            <div class="md-layout-item md-size-25">
                              <md-button class="md-primary is-small">+ adicionar outro</md-button>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-25">
                                <md-field :class="getValidationClass('zipcode')">
                                    <label for="zipcode">CEP</label>
                                    <md-input name="zipcode" id="zipcode" autocomplete="given-zipcode" v-model="form.zipcode" :disabled="sending"  @blur="getCep" v-mask="'##.###-###'"/>
                                    <span class="md-error" v-if="!$v.form.zipcode.required">Cep é Obrigatório</span>
                                    <span class="md-error" v-else-if="!$v.form.zipcode.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-50">
                                <md-field :class="getValidationClass('address')">
                                    <label for="address">Endereço</label>
                                    <md-input name="address" id="address" autocomplete="given-address" v-model="form.address" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.address.required">Endereço é Obrigatório</span>
                                    <span class="md-error" v-else-if="!$v.form.address.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('number')">
                                    <label for="number">Número</label>
                                    <md-input name="number" id="number" autocomplete="given-name" v-model="form.number" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.number.required">Número</span>
                                    <span class="md-error" v-else-if="!$v.form.number.minlength">Campo inválido</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('complement')">
                                    <label for="complement">Complemento</label>
                                    <md-input name="complement" id="complement" autocomplete="given-name" v-model="form.complement" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.complement.required">Complemento</span>
                                    <span class="md-error" v-else-if="!$v.form.complement.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div  class="md-size-50 md-layout-item">
                                <md-field :class="getValidationClass('neighbor')">
                                    <label for="neighbor">Bairro</label>
                                    <md-input name="neighbor" id="neighbor" autocomplete="given-name" v-model="form.neighbor" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.neighbor.required">Bairro</span>
                                    <span class="md-error" v-else-if="!$v.form.neighbor.minlength">Campo inválido</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div  class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('city')">
                                    <label for="city">Cidade</label>
                                    <md-input name="city" id="city" autocomplete="given-name" v-model="form.city" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.city.required">Cidade</span>
                                    <span class="md-error" v-else-if="!$v.form.city.minlength">Campo inválido</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('state')" class="pt-0">
                                    <md-select v-model="state" name="state" id="state" placeholder="Estado">
                                        <md-option :value="state.sigla" v-for="state in states">{{ state.nome }}</md-option>
                                    </md-select>
                                </md-field>
                            </div>
                        </div>

                    </md-card-content>
                </md-card-area>
                 <md-card-actions md-alignment="left">
                    <md-button type="submit" class="md-raised md-purple">Salvar</md-button>
                    &nbsp;&nbsp;
                    <md-button @click="clearForm()" class="md-purple">Cancelar</md-button>
                </md-card-actions>
            </md-card>
        </form>
      </md-step>

      <md-step id="second" md-label="Dados do veículo" md-disabled>
        <h1>Em breve</h1>
      </md-step>

      <md-step id="third" md-label="Intençao de compra" md-disabled>
        <h1>Em breve</h1>
      </md-step>
    </md-steppers>
  </div>
</template>
<style lang="scss">
    .md-stepper-header {
        height: 48px;
        .md-stepper-number {
            display: none;
            .md-button-content {
                &:after {
                    display: none !important;
                }
            }
        }
        .md-button-content {
            margin: 0 auto;
            text-transform: uppercase;
        }

        .md-stepper-text {
          .md-stepper-label {
            font-size: 14px;
          }
        }

        &.md-active {
          .md-stepper-text {
            color: #6200ee;
          }
          border-bottom: 1px solid #6200ee;
        }
    }

    .md-steppers-navigation {
      box-shadow: none;
      border-bottom: solid 1px rgba(0, 0, 0, 0.12);
    }

    .md-stepper-header .md-button-content:after {
        display: none !important;
    }

    .md-stepper-content {
      .md-card {
        border: none;
        padding: 0;
      }
    }
    
    .md-field {
      height: 56px;
      opacity: 0.7;
      border-radius: 4px;
      border: 1px solid rgba(0, 0, 0, 0.38);
      label {
        left: 16px;
        top: 17px;
        font-size: 16px;

      }
      .md-input {
        padding-left: 16px;
        padding-right: 16px;
        font-size: 16px;
      }
    }

    .md-menu.md-select {
      input {
        height: 54px;
      }
    }

    .is-small {
      .md-button-content {
        font-size: 14px;
        text-transform: none;
      }
    }
</style>
<script>
  import axios from 'axios';
  import { validationMixin } from 'vuelidate';
  import {mask} from 'vue-the-mask'

  import {
    required,
    email,
    minLength,
    maxLength
  } from 'vuelidate/lib/validators'

  export default {
    name: 'FormValidation',
    mixins: [validationMixin],
    directives: { mask },

    data: () => ({
      state: 'SP',
      states: [
          {
            "id_uf": 1,
            "sigla": "AC",
            "nome": "Acre",
            "codigo": 12,
            "id_pais": 1
          },
          {
            "id_uf": 2,
            "sigla": "AL",
            "nome": "Alagoas",
            "codigo": 27,
            "id_pais": 1
          },
          {
            "id_uf": 3,
            "sigla": "AM",
            "nome": "Amazonas",
            "codigo": 13,
            "id_pais": 1
          },
          {
            "id_uf": 4,
            "sigla": "AP",
            "nome": "Amapá",
            "codigo": 16,
            "id_pais": 1
          },
          {
            "id_uf": 5,
            "sigla": "BA",
            "nome": "Bahia",
            "codigo": 29,
            "id_pais": 1
          },
          {
            "id_uf": 6,
            "sigla": "CE",
            "nome": "Ceará",
            "codigo": 23,
            "id_pais": 1
          },
          {
            "id_uf": 7,
            "sigla": "DF",
            "nome": "Distrito Federal",
            "codigo": 53,
            "id_pais": 1
          },
          {
            "id_uf": 8,
            "sigla": "ES",
            "nome": "Espírito Santo",
            "codigo": 32,
            "id_pais": 1
          },
          {
            "id_uf": 9,
            "sigla": "GO",
            "nome": "Goiás",
            "codigo": 52,
            "id_pais": 1
          },
          {
            "id_uf": 10,
            "sigla": "MA",
            "nome": "Maranhão",
            "codigo": 21,
            "id_pais": 1
          },
          {
            "id_uf": 11,
            "sigla": "MG",
            "nome": "Minas Gerais",
            "codigo": 31,
            "id_pais": 1
          },
          {
            "id_uf": 12,
            "sigla": "MS",
            "nome": "Mato Grosso do Sul",
            "codigo": 50,
            "id_pais": 1
          },
          {
            "id_uf": 13,
            "sigla": "MT",
            "nome": "Mato Grosso",
            "codigo": 51,
            "id_pais": 1
          },
          {
            "id_uf": 14,
            "sigla": "PA",
            "nome": "Pará",
            "codigo": 15,
            "id_pais": 1
          },
          {
            "id_uf": 15,
            "sigla": "PB",
            "nome": "Paraíba",
            "codigo": 25,
            "id_pais": 1
          },
          {
            "id_uf": 16,
            "sigla": "PE",
            "nome": "Pernambuco",
            "codigo": 26,
            "id_pais": 1
          },
          {
            "id_uf": 17,
            "sigla": "PI",
            "nome": "Piauí",
            "codigo": 22,
            "id_pais": 1
          },
          {
            "id_uf": 18,
            "sigla": "PR",
            "nome": "Paraná",
            "codigo": 41,
            "id_pais": 1
          },
          {
            "id_uf": 19,
            "sigla": "RJ",
            "nome": "Rio de Janeiro",
            "codigo": 33,
            "id_pais": 1
          },
          {
            "id_uf": 20,
            "sigla": "RN",
            "nome": "Rio Grande do Norte",
            "codigo": 24,
            "id_pais": 1
          },
          {
            "id_uf": 21,
            "sigla": "RO",
            "nome": "Rondônia",
            "codigo": 11,
            "id_pais": 1
          },
          {
            "id_uf": 22,
            "sigla": "RR",
            "nome": "Roraima",
            "codigo": 14,
            "id_pais": 1
          },
          {
            "id_uf": 23,
            "sigla": "RS",
            "nome": "Rio Grande do Sul",
            "codigo": 43,
            "id_pais": 1
          },
          {
            "id_uf": 24,
            "sigla": "SC",
            "nome": "Santa Catarina",
            "codigo": 42,
            "id_pais": 1
          },
          {
            "id_uf": 25,
            "sigla": "SE",
            "nome": "Sergipe",
            "codigo": 28,
            "id_pais": 1
          },
          {
            "id_uf": 26,
            "sigla": "SP",
            "nome": "São Paulo",
            "codigo": 35,
            "id_pais": 1
          },
          {
            "id_uf": 27,
            "sigla": "TO",
            "nome": "Tocantins",
            "codigo": 17,
            "id_pais": 1
          }
        ],
      form: {
        firstName: null,
        lastName: null,
        phone: null,
        zipcode: null,
        email: null,
        address: null,
        neighbor: null,
        complement: null,
        city: null
      },
      userSaved: false,
      sending: false,
      lastUser: null
    }),
    validations: {
      form: {
        firstName: {
          required,
          minLength: minLength(3)
        },
        address: {
            required,
            minLength: minLength(3)
        },
        lastName: {
          required,
          minLength: minLength(3)
        },
        number: {
            required,
            minLength: minLength(1)
        },
        zipcode: {
          required,
          maxLength: maxLength(3)
        },
        phone: {
          required
        },
        complement: {
          required
        },
        email: {
          required,
          email
        },
        neighbor: {
          required,
          email
        },
        city: {
          required,
          email
        },
      }
    },
    methods: {
      getCep() {
        var zipcode = this.form.zipcode.replace(/[^a-zA-Z0-9 ]/g, '');
        
        if (zipcode.length < 8) return false;

        axios.get(`https://viacep.com.br/ws/${zipcode}/json/`)
        .then((resp) => {
          let res = (resp.data);
          this.form.city = res.localidade;
          this.form.neighbor = res.bairro;
          this.form.complement = res.complemento;
          this.state = res.uf;
        })
      },

      getValidationClass (fieldName) {
        const field = this.$v.form[fieldName]

        if (field) {
          return {
            'md-invalid': field.$invalid && field.$dirty
          }
        }
      },
      clearForm () {
        this.$v.$reset()
        this.form.firstName = null
        this.form.lastName = null
        this.form.zipcode = null
        this.form.phone = null
        this.form.email = null
        this.form.number = null
        this.form.address = null
        this.form.complement = null
        this.form.city = null
      },
      saveUser () {
        this.sending = true

        // Instead of this timeout, here you can call your API
        window.setTimeout(() => {
          this.lastUser = `${this.form.firstName} ${this.form.lastName}`
          this.userSaved = true
          this.sending = false
          this.clearForm()
        }, 1500)
      },
      validateUser () {
        this.$v.$touch()

        if (!this.$v.$invalid) {
          this.saveUser()
        }
      }
    }
  }
</script>