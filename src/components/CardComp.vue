<template>
     <div class="row">
        <div class="col-md-6">
            <div class="panel panel-warning">
                <div class="panel-heading">
                    <h4>Card Details</h4>
                </div>

    <div class="panel-body">
        <form>

            <div class="row">
                <div class="col-md-12">

                    <div>
                        <template>
                            <v-file-input small-chips multiple label="File input w/ small chips" v-model="selectedFiles"
                                @change="onFileChange"></v-file-input>
                        </template>
                    </div>

                    <div class="form-group">
                        <label for="email">Title</label>
                        <input type="text" id="title" v-model="title" class="form-control">
                    </div>


                </div>
            </div>
            <div class="row">
                <div class="col-md-12 form-group">
                    <label for="message">Description</label><br>
                    <textarea id="message" rows="3" v-model="message" class="form-control"></textarea>
                </div>
            </div>
            <hr>
            <div class="row">
                <div class="col-md-12">
                    <v-btn rounded color="primary" dark @click="resetForm">Reset Form</v-btn>
                </div>
            </div>
        </form>
    </div>
            </div>
        </div>
   
    <div class="col-md-6">
        <div class="panel panel-warning">
            <div class="panel-heading">
                <h4>Card</h4>
            </div>
            <div class="panel-body">
                <div class="right-panel">
                    <v-img v-for="(file, index) in selectedFiles" :key="index" :src="file.preview"
                        :alt="file.name" class="selected-image"></v-img>
                </div>
                <h3>{{ title }}</h3>
                <v-btn class="mx-2" fab dark color="teal" @click.prevent="submit">
                    <v-icon>mdi-format-list-bulleted-square</v-icon>
                </v-btn>
                <hr>
                <p v-if="isSubmitted">{{ message }} </p>
            </div>
        </div>
    </div>
</div></template>
  
<script>
export default {
    props: {
        initialData: {
            type: Object,
            required: true
        }
    },
    data() {
    return {
      selectedFiles: this.initialData.selectedFiles, // Bu satırı ekledik
      title: this.initialData.title,
      message: this.initialData.message,
      isSubmitted: this.initialData.isSubmitted    
    
    };
  },
    methods: {

        onFileChange(files) {
            // Seçilen resimleri önizleme için döngüye alın
            this.selectedFiles = files.map((file) => ({
                name: file.name,
                preview: URL.createObjectURL(file),
            }));
        },




        resetForm() {

            this.title = "";
            this.message = "";
            this.selectedFiles = [];
            this.isSubmitted = false;

        },

        submit() {
            this.isSubmitted = true;


        }

    }
};
</script>
  
<style scoped>
.selected-image {
    max-width: 100%;
    max-height: 300px;
    margin-top: 10px;
}

.panel-body {
    overflow: hidden;
}

p,
h3 {
    word-wrap: break-word;
}
</style>
  