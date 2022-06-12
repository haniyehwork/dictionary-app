<template>
    <div class="maincard">
        <h2 class="card-title">{{wordd}} <span>({{partOfSpeech}})</span></h2>
        <p class="card-text">{{phoneticc}}</p>
        <label>
            <span style="padding: 0px;" class="btn" @click.prevent="playSound(audiosrc)"><svg
                    style="transform: scale(0.8);" id="playicon" xmlns="http://www.w3.org/2000/svg" width="35"
                    height="35" viewBox="0 0 35 35">
                    <circle cx="17.5" cy="17.5" r="17.5" fill="#1c88b7" />
                    <path
                        d="M8.8,9.2V26.3a2.1,2.1,0,0,0,3.3,1.9l15.6-9.3a2.2,2.2,0,0,0-.2-3.9L12,7.2A2.2,2.2,0,0,0,8.8,9.2Z"
                        transform="translate(0 0)" fill="#fff" />
                </svg>
            </span>
            <span style="padding: 0px;" class="btn" @click.prevent="playSound(audiosrc1)"><svg
                    style="transform: scale(0.8);" id="playicon" xmlns="http://www.w3.org/2000/svg" width="35"
                    height="35" viewBox="0 0 35 35">
                    <circle cx="17.5" cy="17.5" r="17.5" fill="#ffc400" />
                    <path
                        d="M8.8,9.2V26.3a2.1,2.1,0,0,0,3.3,1.9l15.6-9.3a2.2,2.2,0,0,0-.2-3.9L12,7.2A2.2,2.2,0,0,0,8.8,9.2Z"
                        transform="translate(0 0)" fill="#fff" />
                </svg>
            </span>
            Play the sound
        </label>
        <p class="card-text"><strong>Synonyms:</strong> {{synonyms}}</p>
    </div>
</template>

<script>
export default {
    props: ['wordd', 'partOfSpeech', 'phoneticc', 'synonyms', 'audiosrc'],
    methods:{
        playSound (sound) {
        if(sound) {
          var audio = new Audio(sound);
          audio.play();
        }
      }
    }

    
}
</script>