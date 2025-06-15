<template>
  <div>
    <HeaderComponent />
    <div style="display: flex;">
      <SidebarComponent />
      <router-view style="flex: 1;" />
    </div>
    <FooterComponent />
  </div>
</template>
