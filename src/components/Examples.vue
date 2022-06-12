<template>
<div class="examplecard">
    <label>
            Examples
         <div class="card mb-3" style="width: 18rem;">
               <ul class="list-group hey">
                  <li class="list-group-item" v-for="example in examples" :key="example">{{example.example}}</li>
               </ul>
            </div>
         </label>
</div>
</template>

<script>
export default {
    name: 'Examples',
    props: ['wordd' , 'examples'],
}
</script>