<template>
  <div class="card mr-3 mb-3 card-success" style="width: 18rem;">
    <div class="card-body">
      <h5 class="card-title">{{post.title}}</h5>
      <h6 class="card-subtitle mb-2 text-muted">{{post.subTitle}}</h6>
      <p class="card-text">{{post.text}}</p>
      <div class="admin-button-container" v-if="isAdmin">
        <a href="#"  @click.prevent="$router.push('admin/' + post.id)" class="btn btn-outline-warning btn-sm">Düzenle</a>
        <a href="#" class="btn btn-outline-danger btn-sm">Sil</a>
      </div>
      <a v-else href="#"  @click.prevent="$router.push('/posts/' + post.id)" class="btn btn-outline-info btn-sm">Görüntüle</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "post",
  props : {
    isAdmin : {
      required : true,
      type : Boolean
    },
    post : {
      required: true,
      type : Object
    }
  }
}
</script>

<style scoped>
  .card-body{
    height: 225px;
  }
  .card-text{
    height: 70px;
    overflow: hidden;
    text-overflow: ellipsis ;
  }
</style>
