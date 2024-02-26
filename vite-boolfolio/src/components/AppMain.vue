<template lang="">
    <div>
       <ul>
        <li v-for="project in projects" :key='project.id'>
            {{project.title}}
        </li>
       </ul>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            projects: [

            ],
        }
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
                .then((response) => {
                    console.log(response.data.data);
                    this.projects = response.data.data;
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
    },
    created() {
        this.getProjects();
    }
}
</script>
<style lang="">
    
</style>