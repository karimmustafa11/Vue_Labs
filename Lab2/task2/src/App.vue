<template>
  <div>
    <HeaderComponent />
    <div style="display: flex;">
      <SidebarComponent />
      <ContentComponent />
    </div>
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import FooterComponent from './components/FooterComponent.vue'
import SidebarComponent from './components/SidebarComponent.vue'
import ContentComponent from './components/ContentComponent.vue'

export default {
  components: {
    HeaderComponent,
    FooterComponent,
    SidebarComponent,
    ContentComponent
  }
}
</script>
