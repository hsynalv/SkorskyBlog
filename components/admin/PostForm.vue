<template>
  <div class="container-fluid mt-5 d-flex flex-wrap justify-content-center align-items-center">
    <form style="width: 500px" @submit.prevent="onSubmit">
      <fieldset>
        <legend v-if="!isUpdate">Yeni Köse Yazısı</legend>
        <legend v-else>Köşe Yazısını Düzenle</legend>
        <div class="form-group">
          <label>Yazar Adı</label>
          <input v-model="post.author" type="text" class="form-control" placeholder="Yazarın adını giriniz..">
        </div>
        <div class="form-group">
          <label>Başlık</label>
          <input v-model="post.title" type="text" class="form-control" placeholder="Yazının baslıgını giriniz..">
        </div>
        <div class="form-group">
          <label>Alt Başlık</label>
          <input v-model="post.subTitle" type="text" class="form-control" placeholder="Yazının alt baslıgını giriniz..">
        </div>
        <div class="form-group">
          <label>Köşe Yazısı</label>
          <textarea v-model="post.text"  class="form-control" rows="5"></textarea>
        </div>
        <button class="btn btn-danger" @click="$router.push('/admin')">İptal</button>
        <button type="submit" class="btn btn-primary">Kaydet</button>
      </fieldset>
    </form>
  </div>
</template>

<script>
export default {
  name: "PostForm",
  data(){
    return{
      post : {
        title : null,
        subTitle : null,
        author : null,
        text : null
      }
    }
  },
  props : {
    isUpdate : {
      type : Boolean,
      required : false,
      default : false
    },
    post : {
      type : Object,
      required: false
    }
  },
  methods : {
    onSubmit(){
      this.$emit("submit",this.post)
      this.post = {}
    }
  },
  created() {
    this.post = this.post ? this.post : {
      id : null,
      title : null,
      subTitle: null,
      text: null,
      author : null
    }
  }
}
</script>

<style scoped>

</style>
