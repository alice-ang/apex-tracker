<template>
    <selection class="search">
        <h1>Track Player Stats</h1>
        <form v-on:submit.prevent="onSubmit">
            <div class="form-group">
                <label for="platform">Platform</label>
                <select name="platform" id="platform" v-model="platform">
                    <option value="psn">Playstation</option>
                    <option value="xbl">Xbox</option>
                    <option value="origin">Origin</option>
                </select>
            </div>
            <div class="form-group"> 
                <label for="gamertag">Gamertag</label>
                <input type="text" name="text" v-model="gamertag" id="gamertag" placeholder="Origin ID, Xbox Live gamertag or PSN ID"/>
            </div>
            <div class="form-group">
                <input type="submit" value="Submit" class="btn">
            </div>
        </form>
    </selection>
</template>
<script>
// JS
export default {
  name: "Search",
  data() {
    return {
      platform: "psn",
      gamertag: ""
    };
  },
  beforeCreate() {
    document.body.className = "body-bg-image";
  },
  methods: {
    onSubmit() {
      if (!this.gamertag) {
        this.$toasted.show("Please enter a gamertag", {
          duration: 3000,
          icon: "exclamation-circle",
          position: 'top-center'
        });
      } else {
        this.$router.push(`/profile/${this.platform}/${this.gamertag}`);
      }
    }
  }
};
</script>
<style >
.form-group > input {
  border: 2px solid #fff;
}


</style>