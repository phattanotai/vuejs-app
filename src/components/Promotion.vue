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
                <h3 >เพิ่ม/แก้ไข  ข้อมูลส่วนลด</h3>
              </label>
              <hr>
              <form class="form-horizontal " autocomplete = "off"  >
                <div >
                  <div class="form-group">
                      <label class="control-label col-sm-4" for="id">รหัสส่วนลด:</label>
                      <div class="col-sm-10">
                        <input type="text" class="form-control" id="id" v-model="id">
                      </div>
                    </div>
                    <div class="form-group">
                      <label class="control-label col-sm-4" for="name">รหัสกล่องสินค้า:</label>
                      <div class="col-sm-10">
                        <input type="text" class="form-control" id="name" v-model="name">
                      </div>
                    </div>
                  <div class="form-group">
                    <label class="control-label col-sm-4" for="address">รายละเอียด</label>
                    <div class="col-sm-10">
                        <textarea class="form-control" rows="5" id="address"></textarea>
                    </div>
                  </div>
                  <div class="form-group row">
                    <div class="col-sm-6">
                      <label class="control-label col-sm-4" for="email" >ส่วนลด:</label>
                      <div class="col-sm-10">
                          <input type="text" class="form-control" id="email" v-model="email">
                      </div>
                    </div>
                    <div class="col-sm-6">
                      <label class="control-label col-sm-4" for="tel">จำนวนเดือน:</label>
                      <div class="col-sm-10">
                        <input type="text" class="form-control" id="tel" v-model="tel">
                      </div>
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
            <div class="table-responsive " style="margin: auto;margin-top: 2%" v-if="!show">
              <table class="table" >
                <thead>
                  <tr>
                      <th>#</th>
                      <th>กล่องสินค้า</th>
                      <th>รายละเอียด</th>
                      <th>ส่วนลด</th>
                      <th>แก้ไข/ลบ</th>
                  </tr>
                </thead>
                <tbody>
                    <tr v-for="i in userData">
                      <td> {{i.id}}</td>
                      <td> {{i.name}}</td>
                      <td> {{i.detail}} </td>
                      <td> {{i.price}} </td>
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
export default {
  data () {
    return {
      dataTable: null,
      id: '',
      name: '',
      type: '',
      sex: '',
      address: '',
      email: '',
      tel: '',
      show: true
    }
  },
  methods: {

  },
  computed: {

  }
}
</script>

<style scoped>
.addButton{
    margin:20px;
    float: right;
}

</style>
