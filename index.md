<template>
  <div class="container" @scroll="handleScroll">
    <!-- display the banner on the page -->
    <section class="banner"
      :class="{ active: isActive }"
      v-if="pageConfig && !pageConfig.tiles"
      :data-name="pageConfig.name">
      <h2 class="banner__title heading-1">{{pageConfig.name }}</h2>
      <h4 class="banner__title heading-4">{{pageConfig.description}}
      </h4>
      <p class="banner__text banner__text--timestamp">
        {{ lastModified }}
      </p>
    </section>
    <!-- render the markdown when content is available -->
    <vue-markdown class="content" :source="markdown"></vue-markdown>
    <-- display the tiles, when children are available -->
    <ul class="cards" v-if="pageConfig.tiles">
      <li class="card" @click="switchPage(tile)" 
       v-for="tile in pageConfig.tiles" 
       v-bind:style="{ backgroundColor: tile.bgColor }">
        <font-awesome-icon class="card__icon" 
         size="2x" 
         :icon="tile.icon"/>
        <h4 class="card__title">{{tile.name}}</h4>
        <p class="card__text">{{tile.description}}</p>
      </li>
    </ul>
  </div>
</template>
