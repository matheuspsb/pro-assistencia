<template>
  <div class="container">
    <h1>Cadastro</h1>

    <div class="tag-info">
      <span>Identificação da pessoa</span>
    </div>

    <div class="person-identification">
      <div class="input-field">
        <h4>Nome</h4>
        <input type="text" placeholder="Digite o nome" />
        <span>Preenchimento obrigatório</span>
      </div>

      <div class="input-field">
        <h4>Nome social</h4>
        <input placeholder="Digite o nome social" />
      </div>

      <div class="row-field">
        <div class="input-field">
          <h4>Data de nascimento</h4>
          <input type="text" v-model="dateOfBirth" @input="applyDateFormat" placeholder="dd/mm/aaaa" />
          <span>Preenchimento obrigatório</span>
        </div>

        <div class="input-field">
          <h4>Sexo biológico</h4>
          <select>
            <option value="" disabled selected hidden>Selecione</option>
            <option>Masculino</option>
            <option>Feminino</option>
          </select>
          <span>Preenchimento obrigatório</span>
        </div>
      </div>

      <div class="row-field">
        <div class="input-field">
          <h4>Gênero</h4>
          <div class="gender-field">
            <label class="radio-label">
              <input type="radio" name="gender" value="Mulher cisgênero" />
              Mulher cisgênero
            </label>
            <label class="radio-label">
              <input type="radio" name="gender" value="Homem cisgênero" />
              Homem cisgênero
            </label>
            <label class="radio-label">
              <input type="radio" name="gender" value="Mulher transgênero" />
              Mulher transgênero
            </label>
            <label class="radio-label">
              <input type="radio" name="gender" value="Homem transgênero" />
              Homem transgênero
            </label>
            <label class="radio-label">
              <input type="radio" name="gender" value="Travesti" />
              Travesti
            </label>
            <label class="radio-label">
              <input type="radio" name="gender" value="Não binário" />
              Não binário
            </label>
          </div>
        </div>

        <div class="input-field">
          <h4>A pessoa se considera parte do público LGBTQIA+?</h4>
          <div class="belongs-field">
            <label class="radio-label">
              <input type="radio" name="belongs" value="Mulher cisgênero" />
              Sim
            </label>
            <label class="radio-label">
              <input type="radio" name="belongs" value="Homem cisgênero" />
              Não
            </label>
          </div>
        </div>
      </div>

      <div class="input-field">
        <h4>Cor/raça</h4>
        <select>
          <option value="" disabled selected hidden>Selecione</option>
          <option>Branca</option>
          <option>Preta</option>
          <option>Parda</option>
          <option>Indígena</option>
          <option>Amarela</option>
        </select>
        <span>Preenchimento obrigatório</span>
      </div>
    </div>

    <div class="tag-info">
      <span>Documentos</span>
    </div>

    <div class="document">
      <div class="row-field">
        <div class="document-field">
          <h4>RG</h4>
          <input type="text" id="rgInput" v-model="rg" @input="applyRGMask" placeholder="000000000000" />
          <span>Preenchimento obrigatório de RG ou de CPF</span>
        </div>

        <div class="document-field">
          <h4>CPF</h4>
          <input type="text" id="cpfInput" v-model="cpf" @input="applyCPFMask" placeholder="000.000.000-00" />
          <span>Preenchimento obrigatório de RG ou de CPF</span>
        </div>
      </div>
    </div>

    <div class="tag-info">
      <span>Local de residência</span>
    </div>

    <div class="address">
      <div class="row-field">
        <div class="input-field">
          <h4>Bairro</h4>
          <input type="text" placeholder="Digite o bairro" />
          <span>Preenchimento obrigatório</span>
        </div>

        <div class="input-field">
          <h4>Endereço</h4>
          <input type="text" placeholder="Selecione o endereço" />
          <span>Preenchimento obrigatório</span>
        </div>
      </div>

      <div class="row-field">
        <div class="input-field">
          <h4>Número</h4>
          <input placeholder="Digite o número" />
        </div>

        <div class="input-field">
          <h4>Complemento</h4>
          <input placeholder="Ex: apartamento 22" />
        </div>
      </div>
    </div>

    <div class="tag-info">
      <span>Local de residência</span>
    </div>

    <div class="info">
      <div class="row-field">
        <div class="input-field">
          <h4>Celular</h4>
          <input v-model="celular" @input="applyCelularMask" placeholder="(00) 00000-0000" />
        </div>

        <div class="input-field">
          <h4>E-mail</h4>
          <input placeholder="Digite o e-mail" />
        </div>
      </div>
    </div>

    <div>
      <SuccessModal v-show="successModalVisible" />
    </div>

    <div class="button-container">
      <button class="cancel">Cancelar</button>
      <button class="submit" @click="handleSubmit">Cadastrar</button>
    </div>
  </div>
</template>

<script>
import SuccessModal from "./SucessModal/SucessModal.vue";

export default {
  name: "RegistrationForm",
  components: {
    SuccessModal
  },
  data() {
    return {
      successModalVisible: false,
      dateOfBirth: '',
      rg: '',
      cpf: '',
      celular: '',
    };
  },
  methods: {
    applyRGMask(event) {
      let value = event.target.value;
      value = value.replace(/\D/g, '');
      value = value.substring(0, 12);
      this.rg = value;
    },
    applyCPFMask(event) {
      let value = event.target.value;
      value = value.replace(/\D/g, ''); 
      value = value.substring(0, 11); 
      value = value.replace(/(\d{3})(\d)/, '$1.$2'); 
      value = value.replace(/(\d{3})(\d)/, '$1.$2'); 
      value = value.replace(/(\d{3})(\d{1,2})$/, '$1-$2');
      this.cpf = value;
    },
    applyCelularMask(event) {
      let value = event.target.value;
      value = value.replace(/\D/g, '');
      value = value.substring(0, 11);
      value = value.replace(/(\d{2})(\d)/, '($1) $2');
      value = value.replace(/(\d{5})(\d)/, '$1-$2');
      this.celular = value;
    },
    applyDateFormat(event) {
      this.dateOfBirth = this.formatDate(event.target.value);
    },
    formatDate(value) {
      value = value.replace(/\D/g, ''); 
      value = value.substring(0, 8); 
      value = value.replace(/(\d{2})(\d)/, '$1/$2'); 
      value = value.replace(/(\d{2})(\d)/, '$1/$2');
      return value;
    },
    validateFields() {
      let isValid = true;
      const requiredFields = this.$el.querySelectorAll(".input-field");

      const rgInput = document.getElementById("rgInput");
      const cpfInput = document.getElementById("cpfInput");

      if (!rgInput.value.trim() && !cpfInput.value.trim()) {
        const rgSpan = document.querySelector("#rgInput + span");
        const cpfSpan = document.querySelector("#cpfInput + span");

        if (rgSpan && cpfSpan) {
          rgSpan.style.color = "#FF0000";
          cpfSpan.style.color = "#FF0000";
          isValid = false;
        }
      } else {
        const rgSpan = document.querySelector("#rgInput + span");
        const cpfSpan = document.querySelector("#cpfInput + span");

        if (rgSpan && cpfSpan) {
          rgSpan.style.color = "#2E2E2E";
          cpfSpan.style.color = "#2E2E2E";
        }
      }

      requiredFields.forEach((field) => {
        const input = field.querySelector("input[type='text'], select");
        const span = field.querySelector("span");

        if (input && input.value.trim() === "") {
          if (span) {
            span.style.color = "#FF0000";
          }
          isValid = false;
        } else {
          if (span) {
            span.style.color = "#2E2E2E";
          }
        }
      });

      return isValid;
    },
    handleSubmit() {
      if (this.validateFields()) {
        this.successModalVisible = true;
        const formData = {};
        const inputFields = this.$el.querySelectorAll(
          ".input-field input[type='text'], .input-field select"
        );
        inputFields.forEach((field) => {
          formData[field.previousElementSibling.textContent.trim()] =
            field.value;
        });

        const radioFields = this.$el.querySelectorAll(
          ".input-field input[type='radio']:checked"
        );

        radioFields.forEach((field) => {
          const name = field.getAttribute("name");
          formData[name] = field.value;
        });

        console.log("Dados do formulário:", formData);
      } else {
        alert("Preencha todos os campos obrigatórios!");
      }
    },
  },
};
</script>

<style scoped>
h1 {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 24px;
  font-weight: 700;
  line-height: 32px;
  color: #171559;
}

h4 {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 23.17px;
  letter-spacing: 0.01em;
  color: #2e2e2e;
  margin: 0;
}

.container {
  margin-left: 240px;
  padding: 0px 16px;
}

.tag-info {
  display: flex;
  align-items: center;
  width: 100%;
  height: 40px;
  margin-top: 48px;
  padding: 0px 8px;
  border-radius: 8px;
  background-color: #f26363;
}

.tag-info > span {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 600;
  line-height: 23.17px;
  letter-spacing: 0.01em;
  color: #fff;
}

.person-identification {
  display: flex;
  flex-direction: column;
  gap: 36px;
  margin-top: 36px;
}

.row-field {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
  gap: 36px;
}

.input-field {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 8px;
}

.input-field > input {
  padding: 8px 12px;
  border: 1.5px solid #171559;
  border-radius: 8px;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 18px;
  color: #555555;
}

.input-field > span {
  font-family: "Noto Sans JP";
  font-size: 12px;
  font-weight: 500;
  line-height: 16px;
  color: #2e2e2e;
}

.input-field > select {
  padding: 8px 12px;
  border: 1.5px solid #171559;
  border-radius: 8px;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 18px;
  color: #555555;
}

.radio-label {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 20px;
  text-align: left;
  display: flex;
  align-items: center;
}

.radio-label input[type="radio"] {
  all: unset;
  width: 20px;
  height: 20px;
  border: 2px solid #171559;
  border-radius: 50%;
  margin-right: 8px;
}

.radio-label input[type="radio"]:checked {
  background-color: #171559;
}

.gender-field {
  display: grid;
  grid-template-columns: 200px 200px;
  width: 100%;
  gap: 16px;
}

.belongs-field {
  display: flex;
  gap: 32px;
}

.document {
  margin-top: 36px;
}

.document-field {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 8px;
}

.document-field > input {
  padding: 8px 12px;
  border: 1.5px solid #171559;
  border-radius: 8px;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 18px;
  color: #555555;
}

.document-field > span {
  font-family: "Noto Sans JP";
  font-size: 12px;
  font-weight: 500;
  line-height: 16px;
  color: #2e2e2e;
}

.address {
  display: flex;
  flex-direction: column;
  gap: 36px;
  margin-top: 36px;
}

.info {
  display: flex;
  flex-direction: column;
  gap: 36px;
  margin-top: 36px;
}

.button-container {
  display: flex;
  align-items: center;
  gap: 16px;
  justify-content: end;
}

.submit {
  width: 222px;
  border-radius: 8px;
  margin-top: 36px;
  padding: 12px 8px;
  background-color: #171559;
  cursor: pointer;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 20px;
  color: #FEFEFE;
}

.submit:hover {
  background-color: #403E8C;
}

.cancel {
  width: 222px;
  border-radius: 8px;
  margin-top: 36px;
  padding: 12px 8px;
  background-color: #FEFEFE;
  cursor: pointer;

  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 20px;
  color: #171559;
}
</style>
