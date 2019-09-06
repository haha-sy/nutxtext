<template>
  <div class="about">
    <div>
      <h2>我是about关于页面</h2>
      <p>ID是: {{$route.params.id}}</p>
      <ul>
        <li>
          <nuxt-link to="/">Home页面</nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
      transitions: 'test'
  }
</script>

<style>

</style>
