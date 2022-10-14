<template>
    <div class="container">
      <div class="header">
        <div class="selected">
          <div class="item" v-for="item in userArray" :key="item.id" @click="deleteFromSelected(item)">
            {{ item.name }}
          </div>
        </div>
        <div class="selected" v-if="selectedGoodItem">
          {{selectedGoodItem.name}}
        </div>
      </div>
      <div class="wrapper">
        <div class="sidebar">
          <div class="item" v-for="item in itemsUser" :key="item.id" @click="addToUserArray(item)">{{ item.name }}</div>
        </div>
        <div class="sidebar">
          <div class="item" v-for="item in goodsItems" :key="item.id" @click="selectedGoodItem = item">{{ item.name }}</div>

        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      itemsUser: [
        {
          "id": 1,
          "name": "Shoes 1"
        },
        {
          "id": 2,
          "name": "Shoes 2"
        },
        {
          "id": 3,
          "name": "Shoes 3"
        },
        {
          "id": 4,
          "name": "Shoes 4"
        },
        {
          "id": 5,
          "name": "T-shirt 1"
        },
        {
          "id": 6,
          "name": "T-shirt 2"
        },
        {
          "id": 7,
          "name": "T-shirt 3"
        },
        {
          "id": 8,
          "name": "T-shirt 4"
        }
      ],
      goodsItems: [
            {
              "id": 11,
              "name": "Jacket 1"
            },
            {
              "id": 12,
              "name": "Jacket 2"
            },
            {
              "id": 13,
              "name": "Jacket 3"
            },
            {
              "id": 14,
              "name": "Jacket 4"
            },
            {
              "id": 15,
              "name": "Hoodie 1"
            },
            {
              "id": 16,
              "name": "Hoodie 2"
            },
            {
              "id": 17,
              "name": "Hoodie 3"
            },
            {
              "id": 18,
              "name": "Hoodie 4"
            }
          ],
      userArray: [],
      selectedGoodItem: ''
    }
  },
  methods: {
    addToUserArray(e) {
      if (this.userArray.includes(e)) {
        this.deleteFromSelected(e);
        return;
      } else if (this.userArray.length < 6) {
        this.userArray.push(e);
      }
    },
    deleteFromSelected(e) {
      let index = this.userArray.findIndex(item => item.id === e.id);
      this.userArray.splice(index,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 1280px;
  min-height:800px;
  border: 1px solid #333;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
}

.header, .wrapper, .selected, .item, .sidebar  {
  margin: 10px;
  border: 1px solid #333;
}
.header {
  display: flex;
  justify-content: space-between;
  flex: 1 1 300px;
}
.wrapper {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  flex: 1 1 700px;
}
.selected {
  display: flex;
  flex-flow: row wrap;
  align-content: flex-start;
  width: 400px
}
.sidebar {
  display: flex;
  flex: 1 1 50%;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-content: flex-start;
}
.item {
  width: 70px;
  height: 70px;
}
.item:hover {
  cursor: pointer;
}
.selected {
  min-width: 300px;
}
</style>

