<template>
    <div>
        <v-dialog v-model="dialog" >
            <template v-slot:activator="{on, attrs}">
                <v-card class="ma-3" :class="messageProp.name != 'Eu' ? 'cyan accent-2' : 'purple'">
            
                    <v-card-subtitle class="font-weight-bold black--text">{{ messageProp.name == 'Eu' ? 'Eu' : messageProp.name }}</v-card-subtitle>
                    <v-card-text class="font-weight-normal grey--text text--darken-4 editme">{{ messageProp.text }}</v-card-text>
                    <v-card-actions>
                        <v-row justify="start">
                            <v-card-text class="font-weight-light grey--text text--darken-4">{{ messageProp.edited ? messageProp.editedDate : messageProp.date }}</v-card-text>

                        </v-row>
                        <v-spacer></v-spacer>
                        <v-btn v-bind="attrs" v-on="on" icon color ="black">
                            <v-icon>mdi-pencil</v-icon>
                        </v-btn>
                        <v-btn @click="removePost()" icon color="black">
                            <v-icon>mdi-delete</v-icon>
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </template>
            <v-card>
        <v-card-title class="text-h5 cyan accent-2">
          Editar publicação
        </v-card-title>

        <v-text-field v-model="messageProp.text" solo flat @input="messageProp.edited = true">
        </v-text-field>

        <v-divider></v-divider>

        <v-card-actions class="cyan accent-2">
          <v-spacer></v-spacer>
          <v-btn
            color="black"
            text
            outlined
            @click="dialog = false, messageProp.edited = true"
          >
            Confirmar
          </v-btn>
        </v-card-actions>
      </v-card>
        </v-dialog>
    </div>
    
</template>

<script>


export default {
    data() {
        return {
            index: 0,
            dialog: false
            
        }
    },
    props: {
        messageProp: {
            type: Object,
            required: true
        }
        
    },
    methods: {
        
        removePost() {
            let post = {
                    name: 'Vítor Bárrios',
                    text: this.field,
                    date: this.timeStamp,
                    index: this.messageProp.index
                }

            console.log(post)
            this.$emit('remove-post', this.messageProp)
        }
    }
}


</script>


