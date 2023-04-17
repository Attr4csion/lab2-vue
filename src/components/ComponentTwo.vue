<template>
  <div>
    <div class="input">
        <label>Наименование
        <input 
          type="text" 
          v-model="newName"></label>
        <label>Количество
        <input 
          type="text" 
          v-model="newCount"></label>
        <label>Цена
        <input 
          type="text" 
          v-model="newPrice"></label>
        <button @click="addRow">Добавить</button>
      </div>
      <table>
        <tr>
          <th @click="sortList('name')">Наименование</th>
          <th @click="sortList('count')">Количество</th>
          <th @click="sortList('price')">Цена</th>
        </tr>
        <tr v-for="(data, index) in sortedData" :key="index">
          <td>{{ data.name }}</td>
          <td>{{ data.count }}</td>
          <td>{{ data.price }}</td>
          <td>
            <button class="del_btn" @click="deleteRow(index)">Удалить</button>
        </td>
        </tr>
        <td colspan="3">ИТОГО</td>
        <td colspan="2">{{ CalcFullPrice() }}</td>
      </table>
    </div>
  </template>

<script>
export default {
  data() {
    return {
        newName:'',
        newCount:0,
        newPrice:0,
        fullprice:0,
      sortedData: [
        { name: 'Огурец', count: 12, price: 150},
        { name: 'Помидор', count: 5, price: 100},
      ],
      sortedbysome: true,
    };
  },
 
  methods: {
    sortList(sortBy) {
      if (this.sortedbysome) {
        this.sortedData.sort((x, y) => (x[sortBy] > y[sortBy] ? -1 : 1));
        this.sortedbysome = false;
      } else {
        this.sortedData.sort((x, y) => (x[sortBy] < y[sortBy] ? -1 : 1));
        this.sortedbysome = true;
      }
    },
    addRow(){
        this.sortedData.push({
            name:this.newName,
            count:this.newCount,
            price:this.newPrice
        })
        this.newName='',
        this.newCount=0,
        this.newPrice=0
    },
    deleteRow(index){
        this.sortedData.splice(index,1)
    },
    CalcFullPrice(){
      let tFullPrice = 0;
            for (let i = 0;i < this.sortedData.length;i++){
                this.fullprice = this.sortedData[i].count*this.sortedData[i].price;
                tFullPrice += this.fullprice;
            }
            return tFullPrice
    }
  },
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

th:hover {
  cursor: pointer;
  background: rgb(229, 255, 211);
}

tr:nth-child(even) {
  background-color: #f3f3f3;
}
.input{
    display: flex;
    flex-direction: column;
    width: 100%;
    padding: 10px 18px ;
    font-size: 18px;
    margin-bottom: 16px;
}
.input button{
  margin: 0 auto;
  appearance: none;
  border: 0;
  border-radius: 5px;
  background: #2dfab3;
  color: #000000;
  padding: 8px 16px;
  font-size: 16px;
  cursor:pointer;
}
label{
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}
.del_btn{
  cursor:pointer;
  appearance: none;
  border: 0;
  border-radius: 5px;
  background: #fa2d2d;
  color: #000000;
  padding: 8px 16px;
  font-size: 16px;
}

</style>