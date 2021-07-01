<template>
  <!-- le composant est alimenté par  -->
  <div>
    <nav
      id="cmp-nav-left"
      @mouseover="openNavbar()"
      @mouseleave="closeNavbar()"
      :class="navStyle"
    >
      <!-- Element central du menu -->
      <ul class="nav-elements">
        <!-- elements -->
        <li
          v-for="(menu, index) in navElements"
          :key="'middle' + index"
          class="elements"
          :class="
            menu.topElement
              ? 'firstElement'
              : '' || menu.bottomElement
              ? 'lastElement'
              : ''
          "
        >
          <!-- logique avec des sous-elements -->
          <div v-if="menu.childElement">
              <div
                :id="'heading' + menu.id"
                class="pt-3 pb-3 collapsed d-flex align-items-center myA"
                type="button"
                data-bs-toggle="collapse"
                :data-bs-target="'#' + menu.id"
                aria-expanded="false"
                :aria-controls="menu.id"
              >
                <a class="myA">
                  <font-awesome-icon :icon="menu.icon" class="nav-icon" />
                  {{ menu.name }}
                  </a
                >
                 <span class="accordion-state">&#9658;</span>
              </div>
              <ul
                :id="menu.id"
                class="collapse"
                :aria-labelledby="'heading' + menu.id"
                :data-bs-parent="menu.dataBsParent"
              >
                <!-- Sous-menus -->
                <li
                  class="sousmenu"
                  v-for="(sousMenu, index) in menu.sousMenu"
                  :key="'sub1' + index"
                  @click="closeNavbar()"
                >
                  <router-link
                    :to="sousMenu.subPath"
                    class="myA"
                  >
                    <font-awesome-icon
                      :icon="sousMenu.subIcon"
                      class="nav-submenu-icon"
                    />
                    {{ sousMenu.subName }}
                  </router-link>
                </li>
              </ul>
          </div>
          <!-- logique sans sous-elements -->
          <div v-if="!menu.childElement" @click="closeNavbar()">
              <router-link
                :to="menu.path"
                class="pt-3 pb-3 d-flex align-items-center myA"
                :id="menu.id"
              >
                <font-awesome-icon :icon="menu.icon" class="nav-icon" />
                {{ menu.name }}
              </router-link>
          </div>
          <!-- barre sous le premier élément -->
          <hr v-if="index === 0" class="top-hr" />
        </li>
      </ul>
    </nav>

    <!-- buttons pour screenTouch -->
    <div>
      <!-- Button Wrap -->
      <div class="toggle-btn" :class="toggled ? 'btn-is-close' : 'btn-is-open'" @click="toggled ? openNavbar() : closeNavbar()">
        <font-awesome-icon
          :icon="buttonIcon"
          aria-hidden="true"
          class="toggle-btn-icon"
        />
      </div>

      <!-- lower btn vient se placer derriere le menu afin de creer un clic de fermeture dans la fenetre. activé uniquement sur les ecrans tactiles  -->
      <div :class="toggled ? '' : 'lowerBtn'" @click="closeNavbar()"></div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { Menu } from '@/components/interfaceMenu'

@Component({
  computed: {
  }
})
export default class SideBarLeft extends Vue {
  navElements: Menu[] = [
  ]

  /* gestion de l'icone du toggle btn */
  toggleBtnOpenIt = 'align-justify';
  toggleBtnCloseBtn = 'times';
  buttonIcon = this.toggleBtnOpenIt;

  /* état de la barre
    navStyle change la classe 'is-close'/'is-open'
  */

  toggled = true;
  navStyle = 'is-close'; // change la classe du menu (is-close / is-open)

  /** controle toggled et change la classe du menu pour fermer la barre */
  closeNavbar (): void {
    if (!this.toggled) {
      this.navStyle = 'is-close'
      this.toggled = !this.toggled
      this.buttonIcon = this.toggleBtnOpenIt
    }
  }

  /** controle toggled et change la classe du menu pour ouvrir la barre */
  openNavbar (): void {
    if (this.toggled) {
      this.navStyle = 'is-open'
      this.toggled = !this.toggled
      this.buttonIcon = this.toggleBtnCloseBtn
    }
  }
}
</script>
<style scoped lang="scss">
@import "./src/style";
</style>
