<template>
  <div class="wrapper">
    
    <div class="wrapper-content">
      <section>
        <div class="container">

          <h1>{{title}}</h1>
        
          <div class="message" v-if="message">
              <p>{{message}}</p>
          </div>

          <!-- new note -->
          <div class="new-note">
              <input v-model="note.title" type="text">
              <textarea v-model="note.descr"></textarea>
              <button @click="addNote">New note</button>
          </div>
          <!-- note list -->
          <div class="notes">
              <div class="note" v-for="(note, index) in notes" :key="index">
                  <div class="note-header">
                      <p>{{note.title}}</p>
                  </div>
                  <div class="note-body">
                      <p>{{note.descr}}</p>
                      <span>{{note.date}}</span>
                  </div>
              </div>
          </div>
        </div>
      </section>
    </div>
    
  </div>
</template>

<script>


export default {
  data () {
    return {
      title: 'notes App',
      message: null,
      note: {
          title: '',
          descr: '',
      },
      notes: [
          {
              title: 'First Note',
              descr: 'Description for first note',
              date: new Date(Date.now()).toLocaleString()
          },
          {
              title: 'Second Note',
              descr: 'Description for second note',
              date: new Date(Date.now()).toLocaleString()
          },
          {
              title: 'Third Note',
              descr: 'Description for third note',
              date: new Date(Date.now()).toLocaleString()
          }
      ]
    }
  },
  methods: {
    addNote(){
        let {title, descr} = this.note;

        if(title === ''){
            this.message = 'title can`t be blank!'
            return false
        }

        this.notes.push({
            title,
            descr,
            date: new Date(Date.now()).toLocaleString()
        })

        this.message = null
        this.note.title = ''
        this.note.descr = ''
    }
  },
}
</script>

<style>
</style>
