<template>
    <section class="container pt-5" style="font-family: 'Andalé Mono', monospace;">
        <div class="Container">
            <div class="display-2" style="font-weight: bold;">Academic Record</div>
            <br>
            <button class="btn btn-outline-primary btn-sm mx-1" @click="toggleList()" style="font-weight: bold; border-radius: 5px; background-color: #f0f0f0; color: #333; border-color: #ccc; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); transition: background-color 0.3s ease;">
                <i class="bi bi-list-ul"></i>
                Show Academic Record
            </button>

            <button class="btn btn-outline-primary btn-sm mx-1" @click="toggleAdd()" style="font-weight: bold; border-radius: 5px; background-color: #f0f0f0; color: #333; border-color: #ccc; box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); transition: background-color 0.3s ease;">
                <i class="bi bi-plus-lg"></i>
                Add Subject
            </button>
            <div class="m-2" v-if="showSbjList">
                <Record/>
            </div>
            <div class="m-2" v-if="showSbjAdd">
                <SbjAdd />
            </div>
            <br><br>
        </div>
    </section>
</template>

<script>
import Record from "./Record.vue";
import SbjAdd from "./SbjAdd.vue";

export default {
    name: 'RecordPage',
    components: {
        Record,
        SbjAdd
    },
    data() {
    return {
        showSbjList: false,
        showSbjAdd: false
    }
  },
  methods: {
    toggleList(){
        this.showSbjList=!this.showSbjList,
        this.showSbjAdd=false
    },
    toggleAdd(){
        this.showSbjAdd=!this.showSbjAdd
        this.showSbjList=false
    }
  }
}
</script>

<style>

</style>
