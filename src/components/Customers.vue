<template>
<div class="main">
      <div class="addButton">
         <button type="button" class="btn btn-primary" v-on:click="show = false" >รายงาน</button>
         <button type="button" class="btn btn-primary" v-on:click="show = true" >เพิ่มข้อมูลใหม่</button>
      </div>
      <div class="card" >
        <div class="card-body" >
            <div v-if="show">
              <label >
                <h5>เพิ่ม/แก้ไข  ข้อมูลลูกค้า</h5>
              </label>
              <hr>
              <form class="form-horizontal " autocomplete = "off"  >
                <div >
                  <div class="form-group">
                    <label class="control-label col-sm-4" for="name">ชื่อ:</label>
                    <div class="col-sm-10">
                      <input type="text" class="form-control" id="name" v-model="name">
                    </div>
                  </div>
                  <div class="form-group" >
                    <label class="control-label col-sm-4" for="sex">เพศ:</label>
                    <div class="col-sm-10" >
                      <input type="radio" name="sex" value="male"   v-model="sex">ชาย
                      <input type="radio" name="sex" value="female" v-model="sex">หญิง
                    </div>
                  </div>
                  <div class="form-group">
                    <label class="control-label col-sm-4" for="address">ที่อยู่</label>
                    <div class="col-sm-10">
                        <textarea class="form-control" rows="5" id="address"></textarea>
                    </div>
                  </div>
                  <div class="form-group">
                    <label class="control-label col-sm-4" for="email" >อีเมล:</label>
                    <div class="col-sm-10">
                        <input type="text" class="form-control" id="email" v-model="email">
                    </div>
                  </div>
                  <div class="form-group">
                    <label class="control-label col-sm-4" for="tel">เบอร์โทร:</label>
                    <div class="col-sm-10">
                      <input type="text" class="form-control" id="tel" v-model="tel">
                    </div>
                  </div>
                </div>
                <div style="margin-top:10px">
                     <button type="button" class="btn btn-primary " v-on:click="save()" >บันทึก</button>
                     <button type="button" class="btn btn-success " v-on:click="edit()" >แก้ไข</button>
                     <button type="button" class="btn btn-info" v-on:click="reset()" >ล้าง</button>
                </div>
              </form>
            </div>
            <div class="table-responsive " style="margin-top: 2%" v-if="!show">
              <div class="row">
                <div class="col-sm-5">
                  <h5>รายงานข้อมูลลูกค้า</h5>
                </div>
                <div  class="col-sm-7 input-group">
                    <select class="form-control" >
                      <option>ค้นหาจาก</option>
                      <option>ID</option>
                      <option>Name</option>
                    </select>
                    <input type="text" class="form-control " style="margin-left:5px;">
                    <button class="btn btn-success" style="margin-left:5px;">ค้นหา</button>
                </div>
              </div>
              <table class="table table-sm" style="margin-top:15px;" >
                <thead>
                  <tr>
                      <th>#</th>
                      <th>ชื่อ-นามสกุล</th>
                      <th>ที่อยู่</th>
                      <th>เพศ</th>
                      <th>อีเมล</th>
                      <th>เบอร์โทร</th>
                      <th>แก้ไข/ลบ</th>
                  </tr>
                </thead>
                <tbody v-if="dataTable !== null">
                    <tr v-for="i in dataTable">
                      <td> {{i.id}}</td>
                      <td> {{i.name}}</td>
                      <td> {{i.address}} </td>
                      <td> {{i.sex}} </td>
                      <td> {{i.email}} </td>
                      <td> {{i.tel}} </td>
                      <td>
                        <button type="button" class="btn btn-warning" v-on:click="setForm()" >แก้ไข</button>
                        <button type="button" class="btn btn-danger" v-on:click="deleteUser(i.id)" >ลบ</button>
                      </td>
                    </tr>
                </tbody>
              </table>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      dataTable: null,
      id: '',
      name: '',
      sex: '',
      address: '',
      email: '',
      tel: '',
      show: false
    }
  },
  methods: {
    laodData: function () {
      axios.get('http://127.0.0.1:3000/customers/')
        .then(response => {
          this.dataTable = response.data.data
          console.log(response.data.data)
        })
    }
  },
  computed: {
  },
  created: function () {
    this.laodData ()
  }
}
</script>

<style scoped>
.addButton {
    margin:20px;
    float: right;
}
</style>
