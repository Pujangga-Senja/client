<template>
  <div class="container">
    <b-form v-on:submit.prevent="submitAudio">
    <!-- Styled -->
      <b-form-file
        v-model="file"
        :state="Boolean(file)"
        placeholder="Choose a file or drop it here..."
        drop-placeholder="Drop file here..."
      ></b-form-file>
      <b-button variant="primary" class="my-3" type="submit">Submit Audio</b-button>
    </b-form>
    <div>
      <p></p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Swal from 'sweetalert2';
export default {
  name: 'AudioForm',
  data () {
    return {
      file: null,
      textResult: ''
    }
  },
  methods: {
    submitAudio () {
      let fd = new FormData()
      console.log(this.file, '{{{')
      fd.append('fileName', this.file)
      axios({
        method: 'post',
        url: 'http://35.192.129.227/audio',
        headers: {
          'Content-Type': 'multipart/form-data',
          access_token: localStorage.getItem('access_token')
        },
        data: fd
      })
        .then(({ data }) => {
          console.log(data)
          Swal.fire({
            icon: 'success',
            text: "Submitted!"
          })
          this.textResult = data
          return this.$emit('textResult', this.textResult)
        })
        .catch(err => {
          Swal.fire({
            icon: 'error',
            title: 'Oops...',
            text: err
          })
        })
    },
    // watch: {
    //   textResult(n, o) {
    //     console.log(o)
    //     this.textResult = n
    //   }
    // }
  }
}
</script>

<style scoped>
  .container {
    margin-top: 3vh
  }

</style>