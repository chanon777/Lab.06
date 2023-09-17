<script setup>
import { ref } from 'vue';

// ตัวแปร
//const travel = ref("");
const money = ref(0);
const nameuser = ref("");
const tel = ref("");
const table = ref("");
const time = ref("");

// const travellist=ref(['Forest Bake','Dong Madame','Chocolate Ville','ร้านชวนพิศมัย','Potpuree'])
 const travellist=ref([
  { name: 'กาแฟโบราณ', price:40 , size: {s:40, m:150, l: 200 }, img: "https://www.funnymandesign.com/2007/wp-content/uploads/2021/09/milk-tea-shop-design_02.jpg" },
  { name: 'cafe milk tea shop', price:50 , size: {s:50, m:160, l: 210 }, img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT9RDMmNi4ZMPgZok8SwGJZBUkxuyY3lPHvWg&usqp=CAU"},
  { name: 'cafe ว้าวุ่น ', price:100 , size: {s:100, m:200, l: 300 }, img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRE02jbqxU2aKW4JJsnIg4TaOljd83Zl0TnuMjq3j2HCm1dkQGnZNl4ioIn5miQAbrk6pk&usqp=CAU"},
  
  
]);
//เก็บข้อมูลการจองร้าน
const bookinglist = ref([

]);

// function
function booking(name){

  bookinglist.value.push(name)

}



</script>


<template>
  
    <div class="text-center">
      <div class="row row-cols-1 row-cols-md-3 g-4">
        <div class="col" v-for="(i, index ) in travellist" :key="index">
                  <div class="card text-bg-secondary n-100" style="width:18rem">
                    <img v-if="i.img" :src="i.img" class="card-img-top" alt="..." />
                      <div class="card-body">
                        <h5 class="card-title">{{ i.name }}</h5>
                        <p class="card-text" >
                          จำนวนโต๊ะ <input  typy="text" v-model="table">
                        </p>
                        <p class="card-text" >
                          ชื่อผู้จอง <input  typy="text" v-model="nameuser">
                        </p>
                        <p class="card-text">
                          เบอร์โทร<input typy="text" v-model="tel">
                        </p>
                        <p class="card-text">
                          วันที่<input typy="text" v-model="date">
                        </p>
                        <p class="card-text">
                          เวลา<input typy="text" v-model="time">
                        </p>
                        <a class="btn btn-danger" @click="booking( i.name )">จองโต๊ะ</a> 
                      </div>
                  </div>
        </div>
      </div>
      
    </div>


    


    
  <div>
    <div class="p-3 m-0 border-0 bd-example m-0 border-0"></div>

    <table class="table table-secondary table-striped" v-if="bookinglist.length > 0">
  <thead>
    <tr>
      <th scope="col">ลำดับ</th>
      <th scope="col">ชื่อผู้จอง</th>
      <th scope="col">เบอร์โทร</th>
      <th scope="col">จำนวนโต๊ะ</th>
      <th scope="col">วันที่</th>
      <th scope="col">เวลา</th>
      <th scope="col">รายชื่อ-ร้านที่จอง</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(item, index, ) in bookinglist" :key="index">
      <td scope="=row">{{ index+1 }}</td>
      <td scope="row">{{ nameuser }}</td>
      <td scope="row">{{ tel }}</td>
      <td scope="row">{{ table }}</td>
      <td scope="row">{{ date }}</td>
      <td scope="row">{{ time }}</td>
      <td>{{ item }}</td>
    </tr>

  </tbody>
</table>

    <button typy="button" class="btn btn-primary">Primary</button>
    <div v-for="(i, index) in travellist" :key="index">
      {{ index+1 }}
      ชื่อ {{ i.name }}
      size s = {{ i.size.s }}
      ราคา {{ i.price }}
      ชื่อผู้จอง{{ i.nameuser }}
      เบอร์โทร {{ i.tel }}
      วันที่{{ i.date }}
      เวลา {{ i.time }}
      จำนวนโต๊ะ {{ i.table }}
  
    </div>




    <h1>ร้านกาแฟ</h1>
      <input type="radio" value="a" v-model="travel" />ร้านกาเเฟใกล้ฉัน
      <input type="radio" value="b" v-model="travel" />ร้านกาแฟเเนะนำ
      <br  />

       จำนวนเงิน
      <input type="number" v-model="money">
      <br  />

      <p v-if="money<100">ไปร้านกาเเฟเเนะนำราคาถูก</p>
      <p v-else-if="money>=100 && money<9999">ไปร้านกาเเฟร้านเเนะนำราคาแพง</p>
      <p v-else>ไปร้านกาเเฟสุดหรู</p>

      <button v-if="money < 50" type="" disabled>เดินทางไปร้านราคาเเพง</button>
      <button v-else type="">เดินทางไปร้านราคาเเพง</button>

      <div v-if="travel == 'a'">ร้านกาเเฟใกล้ฉัน</div>
      <div v-else>ร้านกาแฟเเนะนำ</div>
  </div>

</template>