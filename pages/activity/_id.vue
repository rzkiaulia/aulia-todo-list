<style lang="scss" scoped>

  .page-wraper{
  background-color : #EAEFF3;
}
</style>

<template>
  <div class="page-wraper">
    <div class="container">
      <div class="is-flex is-justify-content-space-between pb-3">
        <div class="is-inline-flex is-align-items-start is-flex-direction-column">
          <n-link class="is-flex is-align-items-justify mt-6" to="/">
          <img class="image brand-image" src="~assets/back.png" />
            <span class="title has-text-black is-size-2">New Activity</span>
        </n-link>
        </div>
      <div class="is-flex is-align-items-justify py-6">
        <section>
         <b-button
          label="Tambah"
          rounded
          type="is-info"
          size="is-medium"
          icon-left="plus"></b-button>
        </section>
      </div>
    </div>
    <div class="is-flex is-justify-content-center">
        <img class="images" src="~/assets/tambahlist.png">
      </div>
    </div>
  </div>
</template>
