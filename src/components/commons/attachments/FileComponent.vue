<template>
  <div class="file-type">
     <a :href="data.fileUrl" :download="data.fileName">
        <p class="file-name">{{ data.fileName }}</p>
        <p class="file-size">{{ data.fileSize }}</p>
     </a>
  </div>
</template>

<script>
export default {
    name:'FileComponent',
    props:{
        data:[],
    }
}
</script>

<style lang="scss" scoped>
.file-type{
    border-radius: 5px;
    line-height: 4px;
    padding: 20px;
    align-items: center;
    width: fit-content;
    height: 61px;
    display: flex;
    flex-direction: column;
    background-color: $background-color;

    .file-name{
        font-size: 0.9rem;
        font-weight: 800;
    }
    .file-size{ font-size: 0.8rem; color: $gray; align-self: normal; }
    a{ text-decoration: none; color: $black; }
    }
</style>