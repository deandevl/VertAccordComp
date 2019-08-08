<template>
  <div class="vertAccordComp">
    <div class="vertAccordComp_titleBox" v-show="title">{{title}}</div>
    <ul class="vertAccordComp_uList">
      <li class="vertAccordComp_li" v-for="(name,index) in slot_names" :key="index">
        <div class="vertAccordComp_itemTitle" v-on:mouseover="tit_mouseover($event)" v-on:mouseout="tit_mouseout($event)">
          {{name}}
        </div>
        <slot :name="name" class="vertAccordComp_itemContent">Fallback Content</slot>
      </li>

    </ul>
  </div>
</template>

<script>
  export default {
    name: 'VertAccordComp',
    props: {
      slot_names: {
        type: Array,
        default: null
      },
      title: {
        type: String,
        default: null
      },
      content_height: {
        type: Number,
        default: 200
      },
      css_variables: {
        type: Object,
        default: () => {
          return null;
        }
      }
    },
    methods: {
      tit_mouseover: function(e){
        const item_content_box = e.currentTarget.nextElementSibling;
        item_content_box.style = `height: ${this.content_height}px`;
      },
      tit_mouseout: function(e){
        const item_content_box = e.currentTarget.nextElementSibling;
        item_content_box.style = 'height: 0;';
      }
    },
    mounted(){
      if(this.css_variables !== null){
        for(let key of Object.keys(this.css_variables)){
          this.$el.style.setProperty(`--${key}`, this.css_variables[key]);
        }
      }
    }
  }
</script>

<style lang="less">
  :root {
    --vertaccord_comp_font_family: Verdana,serif;

    --vertaccord_comp_title_color: black;
    --vertaccord_comp_title_font_size: 1rem;
    --vertaccord_comp_title_font_weight: bold;

    --vertaccord_comp_item_color: black;
    --vertaccord_comp_item_background: white;
    --vertaccord_comp_item_width: 12rem;

    --vertaccord_comp_item_title_hover_color: white;
    --vertaccord_comp_item_title_hover_background: linear-gradient(to bottom, #454545 0%, #cccccc 100%);
  }

  .vertAccordComp {
    font-family: var(--vertaccord_comp_font_family);

    &_titleBox {
      color: var(--vertaccord_comp_title_color);
      font-size: var(--vertaccord_comp_title_font_size);
      font-weight: var(--vertaccord_comp_title_font_weight);
    }

    &_uList {
      margin: 0;
      padding: 0;
      list-style: none;
    }

    &_li {
      display: block;
      margin: 0;
      padding: 0;
      list-style: none;
      color: var(--vertaccord_comp_item_color);
      background: var(--vertaccord_comp_item_background);

      &:hover {
        transition: all 2s ease-in-out;
      }
    }

    &_itemTitle {
      font-size: 1rem;
      height: 1.25rem;
      font-weight: bold;
      margin-top: .625rem;
      text-align: center;
      width: var(--vertaccord_comp_item_width);

      &:hover {
        cursor: pointer;
        color: var(--vertaccord_comp_item_title_hover_color);
        background: var(--vertaccord_comp_item_title_hover_background);
      }
    }

    &_itemContent {
      overflow-x: hidden;
      overflow-y: hidden;
      transition: all 1s ease-in-out;
      width: var(--vertaccord_comp_item_width);
      height: 0;
      border-bottom: 1px solid black;
    }
  }
</style>