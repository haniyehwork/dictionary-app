<template>
<div class="meaningcard">
    <label>
            Meanings
      <div class="card mb-3" style="width: 18rem;">
        <ul class="list-group hey">
          <li class="list-group-item" v-for="meaning in meanings" :key="meaning">{{meaning.definition}}</li>
        </ul>
      </div>
    </label>
</div>
</template>

<script>
export default {
    name: 'Meanings',
    props: ['wordd' , 'meanings', 'meaning'],
}
</script>