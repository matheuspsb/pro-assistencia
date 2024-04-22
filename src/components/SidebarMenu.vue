<template>
  <div class="sidebar">
    <div class="logo">
      <img alt="pro assistencia logo" src="../assets/pro-logo.png" />
      <div>
        <span class="pro">Pro</span>
        <span class="assistencia">Assistência</span>
      </div>
    </div>

    <div class="nav">
      <span class="tag">Viçosa</span>
      <div class="nav-option">
        <PhCaretLeft :size="12" color="#4B4B4B" />
        <span>Coordenação</span>
      </div>
    </div>

    <div class="menu">
      <div
        v-for="(option, index) in menuOptions"
        :key="index"
        :class="{ 'menu-option': true, selected: option.selected }"
        @click="selectOption(index)"
      >
        <component
          :is="option.icon"
          :size="22"
          :color="option.selected ? '#FFF' : '#4B4B4B'"
          :weight="option.selected ? 'fill' : 'regular'"
        />
        <span>{{ option.label }}</span>
      </div>
    </div>

    <div class="footer">
      <div class="profile">
        <img alt="profile image" src="../assets/image 94.png" />
        <p>Felipe Domingues</p>
      </div> 
    </div>
  </div>
</template>

<script>
import {
  PhHouseLine,
  PhCaretLeft,
  PhClipboardText,
  PhCalendarDots,
  PhUser,
  PhCheckSquareOffset,
} from "@phosphor-icons/vue";

export default {
  name: "SidebarMenu",
  components: {
    PhHouseLine,
    PhCaretLeft,
    PhClipboardText,
    PhCalendarDots,
    PhUser,
    PhCheckSquareOffset,
  },
  data() {
    return {
      menuOptions: [
        { label: "Início", icon: "PhHouseLine", selected: false },
        { label: "Cadastro", icon: "PhClipboardText", selected: true },
        { label: "Agenda", icon: "PhCalendarDots", selected: false },
        { label: "Perfil", icon: "PhUser", selected: false },
        { label: "Relatórios", icon: "PhCheckSquareOffset", selected: false },
      ],
    };
  },
  methods: {
    selectOption(index) {
      this.menuOptions.forEach((option, i) => {
        option.selected = i === index;
      });
    },
  },
};
</script>

<style>
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  width: 240px;
  height: 100%;
  border: 1px solid #d8d8d8;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 16px 32px;
  border-bottom: 1px solid #d8d8d8;
}

.nav {
  display: flex;
  flex-direction: column;
  align-items: baseline;
  padding: 16px 8px;
  border-bottom: 1px solid #d8d8d8;
  gap: 4px;
}

.nav-option {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 4px;
}

.nav-option > span {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 20.27px;
  color: #4b4b4b;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding-top: 16px;
}

.menu-option {
  display: flex;
  align-items: center;
  gap: 12px;
  height: 40px;
  padding: 0px 16px;
  cursor: pointer;
}

.menu-option.selected {
  background-color: #f26363;
}

.menu-option > span {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 500;
  line-height: 20.27px;
  letter-spacing: 0.5px;
  color: #4b4b4b;
}

.pro {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 23.17px;
}

.assistencia {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 16px;
  font-weight: 700;
  line-height: 23.17px;
  color: #f26363;
}

.tag {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 12px;
  font-weight: 600;
  line-height: 17.38px;
  color: #5f5f5f;
}

.footer {
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  border-top: 1px solid #D8D8D8
}

.profile {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 16px;
  gap: 8px;
}

.profile > img {
  width: 48px;
  height: 48px;
  border-radius: 100%;
  border: 1px solid #F26363;
}

.profile > span {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 14px;
  font-weight: 600;
  color: #4B4B4B;
}
</style>
