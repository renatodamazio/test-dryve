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
                                    <span class="md-error" v-if="!$v.form.firstName.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.firstName.minlength">Invalid first name</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('lastName')">
                                    <label for="last-name">Sobrenome</label>
                                    <md-input name="last-name" id="last-name" autocomplete="given-lastName" v-model="form.lastName" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.lastName.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.lastName.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>
                        
                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-50">
                                <md-field :class="getValidationClass('email')">
                                    <label for="email">E-mail</label>
                                    <md-input name="email" id="email" autocomplete="given-email" v-model="form.email" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.email.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.email.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-25">
                                <md-field :class="getValidationClass('phone')">
                                    <label for="phone">Telefone</label>
                                    <md-input name="phone" id="phone" autocomplete="given-phone" v-model="form.phone" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.phone.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.phone.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-25">
                                <md-field :class="getValidationClass('zipcode')">
                                    <label for="zipcode">CEP</label>
                                    <md-input name="zipcode" id="zipcode" autocomplete="given-zipcode" v-model="form.zipcode" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.zipcode.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.zipcode.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-layout-item md-size-50">
                                <md-field :class="getValidationClass('address')">
                                    <label for="address">Endereço</label>
                                    <md-input name="address" id="address" autocomplete="given-address" v-model="form.address" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.address.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.address.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('number')">
                                    <label for="number">Número</label>
                                    <md-input name="number" id="number" autocomplete="given-name" v-model="form.number" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.number.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.number.minlength">Invalid first name</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('complement')">
                                    <label for="complement">Complemento</label>
                                    <md-input name="complement" id="complement" autocomplete="given-name" v-model="form.complement" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.complement.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.complement.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div  class="md-size-50 md-layout-item">
                                <md-field :class="getValidationClass('neighbor')">
                                    <label for="neighbor">Bairro</label>
                                    <md-input name="neighbor" id="neighbor" autocomplete="given-name" v-model="form.neighbor" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.neighbor.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.neighbor.minlength">Invalid first name</span>
                                </md-field>
                            </div>
                        </div>

                        <div class="md-small-size-100 md-layout md-gutter">
                            <div  class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('city')">
                                    <label for="city">Cidade</label>
                                    <md-input name="city" id="city" autocomplete="given-name" v-model="form.city" :disabled="sending" />
                                    <span class="md-error" v-if="!$v.form.city.required">The first name is required</span>
                                    <span class="md-error" v-else-if="!$v.form.city.minlength">Invalid first name</span>
                                </md-field>
                            </div>

                            <div class="md-size-25 md-layout-item">
                                <md-field :class="getValidationClass('lastName')">
                                    <md-select v-model="country" name="country" id="country" placeholder="Country">
                                        <md-option value="australia">Australia</md-option>
                                        <md-option value="brazil">Brazil</md-option>
                                        <md-option value="japan">Japan</md-option>
                                        <md-option value="united-states">United States</md-option>
                                    </md-select>
                                </md-field>
                            </div>
                        </div>

                    </md-card-content>
                </md-card-area>
                 <md-card-actions md-alignment="left">
                    <md-button>Action</md-button>
                    <md-button>Action</md-button>
                </md-card-actions>
            </md-card>
        </form>
      </md-step>

      <md-step id="second" md-label="Second Step">
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
      </md-step>

      <md-step id="third" md-label="Third Step">
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
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
    }
    .md-stepper-header .md-button-content:after {
        display: none !important;
    }
    
</style>
<script>
import { validationMixin } from 'vuelidate'
  import {
    required,
    email,
    minLength,
    maxLength
  } from 'vuelidate/lib/validators'

  export default {
    name: 'FormValidation',
    mixins: [validationMixin],
    data: () => ({
      country: null,
      form: {
        firstName: null,
        lastName: null,
        phone: null,
        zipcode: null,
        email: null,
        address: null,
        neighbor: null,
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