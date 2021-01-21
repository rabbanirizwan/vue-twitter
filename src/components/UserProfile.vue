<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <h1 class="user-profile__username">@{{ user.username }}</h1>
      <div class="user-profile__admin" v-if="user.isAdmin">Admin</div>
      <div><strong>Followers:</strong> {{ followers }}</div>
      <form class="form" @submit.prevent="createNewTwoot">
        <label for="newTwoot">
          <strong>New Twoot</strong>
        </label>
        <textarea id="newTwoot" rows="4" v-model="newTwootContent" />
        <div class="twoot_type">
          <label for="newTwootType"><strong>Type: </strong> </label>
          <select id="newTwootType" v-model="selectedTwootType">
            <option
              :value="option.value"
              v-for="(option, index) in twootTypes"
              :key="index"
            >
              {{ option.name }}
            </option>
          </select>
        </div>
        <button>Twoot</button>
      </form>
    </div>
    <div class="tweet-wrapper">
      <TwootItem
        v-for="(twoot, index) in user.twoots"
        :key="index"
        :username="user.username"
        :twoot="twoot"
        @favourite="toggleFavourite"
      />
    </div>
  </div>
</template>
<script>
import TwootItem from "./TwootItem";
export default {
  name: "UserProfile",
  components: { TwootItem },
  data() {
    return {
      newTwootContent: "",
      selectedTwootType: "instant",
      twootTypes: [
        { value: "draft", name: "Draft" },
        { value: "instant", name: "Instant" },
      ],
      followers: 0,
      user: {
        id: 1,
        username: "__Rizwand",
        firstName: "Rizwan",
        lastName: "Rabbani",
        email: "abx@gmail.com",
        isAdmin: false,
        twoots: [
          { id: 1, content: "Twotter is amazing" },
          { id: 2, content: "Don't forget subscribe" },
        ],
      },
    };
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
    toggleFavourite(id) {
      console.log(`Favourite twoot ${id}`);
    },
    createNewTwoot() {
      if (this.newTwootContent && this.selectedTwootType !== "draft") {
        this.user.twoots.unshift({
          id: this.user.twoots.length + 1,
          content: this.newTwootContent,
        });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid gray;
}
h1 {
  margin: 0;
}
.user-profile__admin {
  background: palevioletred;
  color: white;
  border-radius: 5px;
  margin-right: auto;
  padding: 0 10px;
  font-weight: bold;
}
.form {
  padding-top: 20px;

  display: flex;
  flex-direction: column;
}
</style>

