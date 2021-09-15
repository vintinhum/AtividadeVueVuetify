<template>    
    <v-app-bar color="#18FFFF" fixed bottom height="70" outlined>
      <v-text-field @keyup.enter="send()" v-model="field" solo hide-details label="Diga alguma coisa!"></v-text-field>
      
      <v-btn @click="send()" icon color="black">
        <v-icon right>mdi-send</v-icon>
      </v-btn>  
    </v-app-bar>
</template>

<script>
export default {
    data() {
        return {
            field: '',
            timeStamp: '',
            editedTimeStamp: '',
            index: 0,
            edited: false
        }
    },
    methods: {
        send() {
            if (this.field != '') {

                this.getNow()
                

                let post = {
                    name: 'Vítor Bárrios',
                    text: this.field,
                    date: this.timeStamp,
                    editedDate: this.editedTimeStamp,
                    index: this.index,
                    edited: this.edited
                }

                console.log(this.index)
                this.$emit('send-message', post)
                this.field = ''
                this.index += 1
            }
            
        },
        getNow() {
            const today = new Date();
            const date = String(today.getDate()).padStart(2,"0") + '/' + String((today.getMonth()+1)).padStart(2,"0") + '/' + today.getFullYear();
            const time = String(today.getHours()).padStart(2,"0") + ":" + String(today.getMinutes()).padStart(2,"0");
            const dateTime = "Publicado em " + date + ", às " + time;
            const editedPostDateTime = "Publicado em " + date + ", às " + time + " (editado)";
            this.timeStamp = dateTime
            this.editedTimeStamp = editedPostDateTime
        }
    }
}
</script>

