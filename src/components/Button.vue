<template>
    <button class="button" :class="{pink: isPink, purple: !isPink}">
      Lorem ipsum
    </button>
</template>

<script>
export default {
    name: 'ButtonDefault',
    props:{
      isPink: Boolean
    }

}
</script>

<style lang="scss" scoped>
.button {
  display: flex;
  justify-content: center;
  align-items: center;
    transform: scale(1);
    transition: 0.5s;
    border-radius: 50px;
    width: 150px;
    height: 50px;
    border: solid 1px #999999;
    background-color: #f5f5f5;
    color: #999999;
    &:hover,
    &hover {
      transform: scale(1.4);
      transition: 0.5s;
      border: solid 1.3px #3e007d;
      cursor: pointer;
    }
  }
  
  .pink:hover{
    color: #a74482;
  }

  .purple:hover{
    color: #693668;
  }
</style>