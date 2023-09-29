<script>
import { userStore } from "../store/store.js";

export default {
  emits: ["close-modal"],
  data() {
    return {
      userStore,
      inputName: "",
      inputDeadline: "",
      inputPriority: "",
    };
  },
  methods: {
    addUser() {
      if (
        this.inputName === "" ||
        this.inputDeadline === "" ||
        this.inputPriority === ""
      )
        return;
      const newUser = {
        id: Date.now().toString(),
        name: this.inputName,
        Deadline: this.inputDeadline,
        Priority: this.inputPriority,
        status: "1",
      };
      userStore.createUser(newUser);
      this.inputName = "";
      this.inputDeadline = "";
      this.inputPriority = "";
      this.$emit("close-modal");
    },
  },
};
</script>

<template>
  <span class="text-gray-700 font-bold text-2xl">Create User</span>
  <div class="flex flex-col gap-3"
  >
    <div class="flex flex-col gap-1">
      <label class="text-gray-700 font-semibold">Name</label>
      <input
        v-model="inputName"
        class="border-2 py-1 border-gray-400 rounded-md"
      />
    </div>
    <div class="flex flex-col gap-1">
      <label class="text-gray-700 font-semibold">Deadline</label>
      <input
        type="date"
        v-model="inputDeadline"
        class="border-2 py-1 border-gray-400 rounded-md"
      />
    </div>
    <div class="flex flex-col gap-1">
      <label class="text-gray-700 font-semibold">Priority</label>
      <select v-model="inputPriority" class="border-2 py-1 border-gray-400 rounded-md">
        <option value="Low">Low</option>
        <option value="Medium">Medium</option>
        <option value="High">High</option>
      </select>
    </div>
  </div>
  
  <button
    @click="addUser"
    class="px-4 py-2 mt-1 bg-gray-700 w-fit h-fit text-gray-100 font-bold text-sm rounded-xl hover:scale-110 transition-all hover:ease-in-out hover:duration-300"
  >
    Submit
  </button>
</template>
