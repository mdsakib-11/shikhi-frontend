<template>
  <div class="">
    <Header/>

    <section class="pt-4 pb-4">
      <div class="container">
        <h3 class="fw-bolder">Courses</h3>
        
        <div class="row" v-if="courses">
   
            <CourseItem v-for="course in courses" :key="course.id" :course="course"></CourseItem>
           
        
        </div>
        <div class="spenner" v-else>
          loading...
        </div>
      </div>
    </section>

    <Footer/>
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import CourseItem from '../components/CourseItem.vue'
import http from 'axios'
export default {
  components: { Header, Footer, CourseItem },
  data(){
    return {
      courses: []
    }
  },
 methods: {
   async getCourses(){
      await http.get('http://shikhi.test/api/courses').then((res)=>{
          this.courses = res.data.courses;
          // console.log(res.data.courses);
      });
    }
 },
 mounted() {
    this.getCourses();
 },
}
</script>

<style>

</style>