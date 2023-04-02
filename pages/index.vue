<template>
  <div>
    <v-btn @click="loadAccounts" :disabled="loading">Load Characters...</v-btn>
    <br />
    <span v-if="loading">Loading...</span>
    <v-progress-linear
      v-if="loading"
      indeterminate
      color="cyan"
    ></v-progress-linear>

    <v-item-group multiple>
      <v-container>
        <v-row>
          <v-col
            v-for="character in characters"
            :key="character.id"
            class="d-flex child-flex"
            cols="4"
          >
            <v-card class="mx-auto" max-width="370">
              <v-img
                class="align-end text-white"
                height="200"
                :src="
                  character.thumbnail.path + '.' + character.thumbnail.extension
                "
                cover
              >
                <v-card-title>
                  <v-btn color="yellow">
                    {{ character.name }}
                  </v-btn>
                </v-card-title>
              </v-img>

              <v-card-text>
                <div>
                  {{
                    character.description
                      ? character.description
                      : 'The information about this character is not founded or is empty.'
                  }}
                </div>
              </v-card-text>

              <v-card-actions>
                <v-btn color="#e92428" class="text-none" dark v-bind="attrs">
                  Explore
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-item-group>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      characters: [],
      loading: false,
    }
  },
  methods: {
    loadAccounts() {
      console.log('Cargar cuentas')
      const ts = 20
      const hash = '73505b649dce69cb8d6ace5b28ce5148'
      const apikey = '8b29bc630dd53f8cbe2ddb63722ffff0'

      const url =
        'https://gateway.marvel.com:443/v1/public/characters?ts=' +
        ts +
        '&apikey=' +
        apikey +
        '&hash=' +
        hash

      this.loading = true
      this.$axios
        .get(url)
        .then((response) => {
          const results = response.data.data.results
          this.characters = results
          console.log(results)
        })
        .catch((error) => {
          alert('Ha ocurrido un error al cargar las cuentas')
          console.log(error)
        })
        .finally(() => {
          this.loading = false
        })
    }
  },
}
</script>

<style></style>
