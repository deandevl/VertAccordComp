<template>
  <div class='demo_container'>
    <vert-accord-comp
        title="Tool Inventory"
        :slot_names="slot_names"
        :content_height="content_height"
        :css_variables="css_variables">
      <template slot="Hammers">
        <div class="vertAccordComp_itemContent">
          Number: 11 <br>
          Types: ball pein(2), heavy(2), sludge(3), claw(4)
        </div>
      </template>
      <template slot="Screwdrivers">
        <div class="vertAccordComp_itemContent">
          Number: 41 <br>
          Types: blade(10), philips(8), mini(23)
        </div>
      </template>
      <template slot="Knives">
        <div class="vertAccordComp_itemContent">
          Number: 16 <br>
          Types: switch(4), fixed(8), putty(4)
        </div>
      </template>
      <template slot="Wrenches">
        <div class="vertAccordComp_itemContent">
          Number: 23 <br>
          Types: pipe(6), socket(12), crescent(5)
        </div>
      </template>
      <template slot="Saws">
        <div class="vertAccordComp_itemContent">
          Number: 15 <br>
          Types: hack(4), cross(3), rip(5), circular(3)
        </div>
      </template>
    </vert-accord-comp>
  </div>
</template>

<script>
  import VertAccordComp from 'vertaccordcomp';

  export default {
    name: 'App',
    data: function() {
      return {
        slot_names:['Hammers','Screwdrivers','Knives','Wrenches','Saws'],
        content_height: 150,
        css_variables: {
          vertaccord_comp_item_width: '300px'
        }
      };
    },
    components: {
      VertAccordComp
    }
  }
</script>

<style>
  .demo_container {
    padding: 30px;
  }
</style>