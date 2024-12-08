<template>
    <div style="font-family: 'Andalé Mono', monospace;">
        <div class="card my-2">
            <div class="card-body bg-info bg-opacity-10">
                <h5 class="card-title" style="font-weight: bold;">Subject's ID: {{ Subject_Grade.id }}</h5>
                <div class="card-sub-title">Subject's Name: {{ Subject_Grade.name }}</div>
                <div class="card-text">Credits: {{ Subject_Grade.Credit }}</div>
                <div class="card-text">Grade: {{ Subject_Grade.Grade }}</div>
                <div class="card-text">Semester: {{ Subject_Grade.Semester }}/{{ Subject_Grade.academicYr }}</div>
            </div>
        </div>
        <button class="btn btn-sm btn-danger"  @click="delDetail(sbjID)">
            <i class="bi bi-trash"></i>
            Delete
        </button>
    </div>
  
</template>

<script>
export default {
    name: "SubjectDetail",
    props: ['sbjID'],
    data() {
        return {
            Subject_Grade: [],
        };
    },
    mounted() {
        fetch('http://localhost:3000/Subject_Grade/'+this.sbjID)
        .then(res => res.json())
        .then(data => (this.Subject_Grade = data))
        .catch(err => console.log(err.message));
    },
    methods: {
        delDetail(theID) {
            fetch('http://localhost:3000/Subject_Grade/'+theID, {
                method:'DELETE'
            })
            .then(this.$emit('delete'))
            .catch()
        }
    }
}
</script>

<style>
</style>