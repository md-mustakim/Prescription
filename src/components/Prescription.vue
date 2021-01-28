<template>
  <div class="">
    <div class="row m-0 p-0">
      <div class="col-md-6 col-lg-6 border shadow mx-auto mt-5">
        <div class="row m-3">
          <div class="col-12 border-bottom">
            <PrescriptionHeader />
          </div>
          <div class="col-12 border-bottom p-2 bg-light">
            <div class="d-flex flex-row justify-content-around">
              <div>
                Name: <b>{{ patient.name }}</b>
              </div>
              <div>
                Age: <b>{{ patient.age }}</b>
              </div>
              <div>
                Date:
                <b
                  >{{ new Date().getDate() }}&nbsp;{{
                    monthNames[new Date().getMonth()]
                  }}&nbsp;{{ new Date().getFullYear() }}</b
                >
              </div>
            </div>
          </div>
          <div
            class="col-3 border-right border-bottom"
            style="min-height: 70vh;"
          >
            <u><b>Symptoms of Disease</b></u>
            <table
              class="table table-sm table-borderless border mt-2 p-3 text-left"
            >
              <tr v-for="(item, index) in diseaseList" :key="index">
                <td>
                  {{ index + 1 }}
                </td>
                <td class="text-success">
                  {{ item }}
                </td>
                <td><i class="fa fa-times" @click="removeItem(index)"></i></td>
              </tr>
            </table>

            <label for="disease">
              <input
                type="text"
                id="disease"
                class="form-control"
                v-model="disease"
                @keyup.enter="addToList"
              />
            </label>
          </div>
          <div class="col-9 border-bottom">
            medicine
          </div>
          <div class="col-12">
            <PrescriptionFooter />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import PrescriptionHeader from "@/components/PrescriptionHeader";
import PrescriptionFooter from "@/components/PrescriptionFooter";
export default {
  name: "Prescription",
  components: { PrescriptionFooter, PrescriptionHeader },
  data() {
    return {
      patient: {
        name: "Abdullah",
        age: 46,
        weight: 65,
        bp: "80/120"
      },
      monthNames: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December"
      ],
      disease: null,
      diseaseList: []
    };
  },
  methods: {
    addToList() {
      this.diseaseList.push(this.disease);
      this.disease = null;
    },
    removeItem(index) {
      this.diseaseList.splice(index, 1);
    }
  }
};
</script>
