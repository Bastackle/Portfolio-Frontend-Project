<template>
  <section class="container pt-3" style="font-family: 'Andalé Mono', monospace;">
  <div class="card">
    <div class="card-body">
      <form @submit.prevent="handleSubmit()">
        <div class="row">
          <div class="col-lg-4 col-md-4 col-sm-6 mt-2">
            <label for="subjID" class="form-label" style="font-weight: bold;">Subject's ID</label>
            <input type="text" id="subjId" class="form-control" v-model.trim="subjs.id" />
          </div>

          <div class="col-lg-8 col-md-8 col-sm-6 mt-2">
            <label for="subjName" class="form-label" style="font-weight: bold;">Subject's Name</label>
            <input type="text" id="subjName" class="form-control" v-model.trim="subjs.name" />
          </div>

          <div class="col-lg-2 col-md-3 col-sm-4 mt-2">
            <label for="subjCredit" class="form-label" style="font-weight: bold;">Credit</label>
            <div class="custom-radio">
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjCreditOne"
                  value="1"
                  v-model="subjs.Credit"
                />
                <label class="form-check-label" for="subjCreditOne">1&nbsp;&nbsp;</label>
              </span>
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjCreditTwo"
                  value="2"
                  v-model="subjs.Credit"
                />
                <label class="form-check-label" for="subjCreditTwo">2&nbsp;&nbsp;</label>
              </span>
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjCreditThree"
                  value="3"
                  v-model="subjs.Credit"
                />
                <label class="form-check-label" for="subjCreditThree">3&nbsp;&nbsp;</label>
              </span>
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjCreditFour"
                  value="4"
                  v-model="subjs.Credit"
                />
                <label class="form-check-label" for="subjCreditThree">4</label>
              </span>
            </div>
          </div>

          <div class="col-lg-2 col-md-3 col-sm-4 mt-2">
            <label for="subjGrade" class="form-label" style="font-weight: bold;">Grade</label>
            <select id="subjGrade" class="form-select" v-model="subjs.Grade">
              <option value="A">A</option>
              <option value="B+">B+</option>
              <option value="B">B</option>
              <option value="C+">C+</option>
              <option value="C">C</option>
              <option value="D+">D+</option>
              <option value="D">D</option>
              <option value="F">F</option>
            </select>
          </div>

          <div class="col-lg-2 col-md-3 col-sm-4 mt-2">
            <label for="subjCredit" class="form-label" style="font-weight: bold;">Semester</label>
            <div class="custom-radio">
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjSemester"
                  value="1"
                  v-model="subjs.Semester"
                />
                <label class="form-check-label" for="subjSemester">1&nbsp;&nbsp;</label>
              </span>
              <span class="option">
                <input
                  class="form-check-input"
                  type="radio"
                  id="subjSemester"
                  value="2"
                  v-model="subjs.Semester"
                />
                <label class="form-check-label" for="subjSemester">2&nbsp;&nbsp;</label>
              </span>
            </div>
          </div>

          <div class="col-lg-6 col-md-5 col-sm-2 mt-2">
            <label for="subjYear" class="form-label" style="font-weight: bold;">Academic Year</label>
            <input type="text" id="subjYear" class="form-control" v-model.trim="subjs.academicYr" />
          </div>

          <div class="col">
            <button type="submit" class="btn btn-primary" style="font-weight: bold;">SAVE</button>
          </div>
        </div>
      </form>
    </div>
    <div class="alert alert-success mt-2" v-show="addSuccess">Add {{ subjs.id }} - {{ subjs.name }}</div>
  </div>
  </section>
</template>

<script>
export default {
  name: "SbjAdd",
  data() {
    return {
      subjs: {
        id: "",
        name: "",
        Credit: null,
        Grade: "",
        academicYr: null,
        Semester: null,
        isShow: false
      },
      addSuccess: false
    };
  },
  methods: {
    handleSubmit() {
      //สร้าง Object เพื่อเตรียมส่งข้อมูล - ค่า properties ที่ v-model กับ form ไว้
      let subjects = {
        id: this.subjs.id,
        name: this.subjs.name,
        Credit: this.subjs.Credit,
        Grade: this.subjs.Grade,
        academicYr: this.subjs.academicYr,
        Semester: this.subjs.Semester,
        isShow: false
      };
      //กำหนดการติดต่อกับ endpoint ระบุ Method POST
      fetch("http://localhost:3000/Subject_Grade", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(subjects)
      })
        .then(() => {
          this.addSuccess = true;
        })
        .catch(err => {
          this.addError = true;
          this.errMessage = err;
        });
    }
  }
};
</script>

<style></style>