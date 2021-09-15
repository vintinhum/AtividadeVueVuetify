<template>
    <v-card class="ma-3" :class="postProp.name != 'Eu' ? 'teal accent-3' : 'purple'">
        
      <v-card-subtitle class="font-weight-bold black--text">{{ postProp.name == 'Eu' ? 'Eu' : postProp.name }}</v-card-subtitle>
      <v-card-text>{{ postProp.text }}</v-card-text>
      
      
      <v-card-actions>
          <v-card-text class="font-weight-light white--text">timeStamp</v-card-text>
          <v-spacer></v-spacer>
          <v-btn icon color ="black">
              <v-icon>mdi-pencil</v-icon>
          </v-btn>
          <v-btn icon color="black">
                <v-icon>mdi-delete</v-icon>
            </v-btn>
        
      </v-card-actions>
        

    </v-card>
</template>

<script>
export default {
    data() {
        return {
            timeStamp: " "
        }
        
    },
    props: {
        postProp: {
            type: Object,
            required: true
        }
    }
}