<template>
  <div>
    <v-btn :disabled="loading">Load Characters...</v-btn>
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
            class="d-flex child-flex"
            cols="4"
          >
            <v-card class="mx-auto" max-width="370">
              <v-img
                class="align-end text-white"
                height="200"
                cover
              >
                <v-card-title>
                  <v-btn color="yellow">
                  </v-btn>
                </v-card-title>
              </v-img>

              <v-card-text>
                
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
  }
}
</script>

<style></style>
