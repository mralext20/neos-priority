<template>
  <table border="1">
    <thead>
      <tr>
        <th
          @click="sort('issueNumber')"
          v-bind:class="[sortBy === 'issueNumber' ? sortDirection : '']"
        >
          Number
        </th>

        <th
          @click="sort('title')"
          v-bind:class="[sortBy === 'title' ? sortDirection : '']"
        >
          Name
        </th>
        <th
          @click="sort('voteCount')"
          v-bind:class="[sortBy === 'voteCount' ? sortDirection : '']"
        >
          Votes
        </th>

        <th
          @click="sort('activePledgeScore')"
          v-bind:class="[sortBy === 'activePledgeScore' ? sortDirection : '']"
        >
          Active Pledge Score
        </th>
        <th
          @click="sort('lifetimePledgeScore')"
          v-bind:class="[sortBy === 'lifetimePledgeScore' ? sortDirection : '']"
        >
          Lifetime Pledge Score
        </th>
      </tr>
    </thead>
    <tbody>
      <Issue
        v-for="issue in this.sortedData"
        :key="issue.issueNumber"
        :issue="issue"
      />
    </tbody>
  </table>
</template>

<script>
import Issue from "./components/Issue.vue";

export default {
  name: "App",
  components: {
    Issue,
  },
  data() {
    return {
      issues: [],
      sortDirection: "desc",
      sortBy: "voteCount",
    };
  },
  computed: {
    sortedData: function () {
      let z = [...this.issues];
      return z.sort((p1, p2) => {
        let modifier = 1;
        if (this.sortDirection === "desc") modifier = -1;
        if (p1[this.sortBy] < p2[this.sortBy]) return -1 * modifier;
        if (p1[this.sortBy] > p2[this.sortBy]) return 1 * modifier;
        return 0;
      });
    },
  },
  methods: {
    sort: function (s) {
      if (s === this.sortBy) {
        this.sortDirection = this.sortDirection === "asc" ? "desc" : "asc";
      }
      this.sortBy = s;
    },
  },

  async mounted() {
    let res = await fetch("https://neos.alext.duckdns.org/videos/prioritys");
    let data = await res.json();
    data.forEach((e) => {
      this.$data.issues.push(e);
    });
  },
};
</script>

<style>
.asc:after {
  content: "\25B2";
}

.desc:after {
  content: "\25BC";
}

th:hover {
  cursor: pointer;
}
</style>
