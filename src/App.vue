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
      sortDirection: "asc",
      sortBy: "title",
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
    // let data = await fetch("https://api.neos.com/api/stats/priorityIssues");
    let data = [
      {
        title: "LogiX Collections System",
        issueNumber: 256,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/256",
        voteCount: 21,
        activePledgeScore: 22.336920711618713,
        lifetimePledgeScore: 11.953422783880288,
      },
      {
        title: "Tweaking the Hip Tracking of the FBT",
        issueNumber: 1120,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1120",
        voteCount: 30,
        activePledgeScore: 21.414452009663957,
        lifetimePledgeScore: 21.852286107688002,
      },
      {
        title: "Upgrade to BEPU physics v2",
        issueNumber: 232,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/232",
        voteCount: 25,
        activePledgeScore: 11.530858774434439,
        lifetimePledgeScore: 11.151542145267534,
      },
      {
        title:
          "Feature Request: Official support for YouTube live chat integration",
        issueNumber: 921,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/921",
        voteCount: 12,
        activePledgeScore: 7.511530858774434,
        lifetimePledgeScore: 8.55477841918996,
      },
      {
        title: "Stuck Gather Jobs for Certain Users",
        issueNumber: 2062,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/2062",
        voteCount: 2,
        activePledgeScore: 5.754447616955853,
        lifetimePledgeScore: 11.569101752420808,
      },
      {
        title: "FFT analyzer",
        issueNumber: 1207,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1207",
        voteCount: 9,
        activePledgeScore: 4.788051833955634,
        lifetimePledgeScore: 3.6998689569153274,
      },
      {
        title:
          "Headless client can produce anomalous command output due to console logging",
        issueNumber: 2436,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/2436",
        voteCount: 4,
        activePledgeScore: 3.6898748078190207,
        lifetimePledgeScore: 2.268532791101369,
      },
      {
        title:
          "[For DynamicBorn]Inside/Outside range type collider like in Unity.",
        issueNumber: 1724,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1724",
        voteCount: 7,
        activePledgeScore: 3.0529321326597847,
        lifetimePledgeScore: 2.1148043785175763,
      },
      {
        title: "Physics Rigidbody simulation",
        issueNumber: 22,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/22",
        voteCount: 6,
        activePledgeScore: 2.899187349000659,
        lifetimePledgeScore: 3.6624755592598106,
      },
      {
        title: "Neos Store, Neos Jobs, Neos Workshop",
        issueNumber: 145,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/145",
        voteCount: 4,
        activePledgeScore: 2.899187349000659,
        lifetimePledgeScore: 3.465121516077915,
      },
      {
        title: "[Feature Request] Ability to adjust/disable post processing",
        issueNumber: 322,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/322",
        voteCount: 3,
        activePledgeScore: 1.8669009444322426,
        lifetimePledgeScore: 4.543297815145324,
      },
      {
        title: "Desktop mode for Leap Motion",
        issueNumber: 1178,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1178",
        voteCount: 2,
        activePledgeScore: 1.8449374039095103,
        lifetimePledgeScore: 1.296304452057925,
      },
      {
        title: "Grabbing after implicit cast node breaks tool + ribbon",
        issueNumber: 918,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/918",
        voteCount: 1,
        activePledgeScore: 1.581374917636723,
        lifetimePledgeScore: 2.7172535629675734,
      },
      {
        title:
          "Cascading asset dependency tracking + dynamic loading/unloading from components",
        issueNumber: 183,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/183",
        voteCount: 5,
        activePledgeScore: 1.1860311882275423,
        lifetimePledgeScore: 3.8764488902886023,
      },
      {
        title: "User Blocking Functionality",
        issueNumber: 557,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/557",
        voteCount: 3,
        activePledgeScore: 0.9224687019547552,
        lifetimePledgeScore: 0.6730811577993072,
      },
      {
        title: "Video Encoder",
        issueNumber: 142,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/142",
        voteCount: 1,
        activePledgeScore: 0.7906874588183616,
        lifetimePledgeScore: 0.4026853445303016,
      },
      {
        title: "(Custom Shaders) Way to Import Shaders",
        issueNumber: 63,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/63",
        voteCount: 1,
        activePledgeScore: 0.7906874588183616,
        lifetimePledgeScore: 0.29914718124413653,
      },
      {
        title: "Switch to universal rendering pipeline",
        issueNumber: 335,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/335",
        voteCount: 1,
        activePledgeScore: 0.7906874588183616,
        lifetimePledgeScore: 1.4708069744503378,
      },
      {
        title: "Quest 2 No-Longer Detected via Virtual Desktop",
        issueNumber: 1520,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1520",
        voteCount: 1,
        activePledgeScore: 0.7906874588183616,
        lifetimePledgeScore: 0.5858298966031007,
      },
      {
        title: "Add 2-Step Verification for account login",
        issueNumber: 206,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/206",
        voteCount: 3,
        activePledgeScore: 0.5271249725455743,
        lifetimePledgeScore: 0.6377651711246521,
      },
      {
        title: 'Filter for "Random Worlds" In the World Browser',
        issueNumber: 2566,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/2566",
        voteCount: 1,
        activePledgeScore: 0.5271249725455743,
        lifetimePledgeScore: 0.6751585687801692,
      },
      {
        title: "Screen Share",
        issueNumber: 144,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/144",
        voteCount: 3,
        activePledgeScore: 0.5271249725455743,
        lifetimePledgeScore: 0.29914718124413653,
      },
      {
        title: "Object ID / License System",
        issueNumber: 21,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/21",
        voteCount: 2,
        activePledgeScore: 0.3953437294091808,
        lifetimePledgeScore: 0.37393397655517063,
      },
      {
        title: '"Linear Lighting" or Gamma Correction',
        issueNumber: 1819,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1819",
        voteCount: 1,
        activePledgeScore: 0.26356248627278717,
        lifetimePledgeScore: 0.3365405788996536,
      },
      {
        title: "Linux / OS X Support (SteamVR & Desktop)",
        issueNumber: 149,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/149",
        voteCount: 1,
        activePledgeScore: 0.26356248627278717,
        lifetimePledgeScore: 0.07478679531103413,
      },
      {
        title: "LogiX Access to Components",
        issueNumber: 243,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/243",
        voteCount: 1,
        activePledgeScore: 0.26356248627278717,
        lifetimePledgeScore: 0.17450252239241298,
      },
      {
        title: "Webcam Face tracking for Desktop Users",
        issueNumber: 1555,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1555",
        voteCount: 1,
        activePledgeScore: 0.26356248627278717,
        lifetimePledgeScore: 0.7354034872251689,
      },
      {
        title:
          'Prompt never returns after running "restart" command in headless client',
        issueNumber: 1841,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/1841",
        voteCount: 1,
        activePledgeScore: 0.26356248627278717,
        lifetimePledgeScore: 0.24928931770344712,
      },
      {
        title: "Add ability to reconfigure save and cache locations",
        issueNumber: 58,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/58",
        voteCount: 1,
        activePledgeScore: 0.13178124313639358,
        lifetimePledgeScore: 0.24928931770344712,
      },
      {
        title: "Neos Activities",
        issueNumber: 152,
        issueURL: "https://github.com/Neos-Metaverse/NeosPublic/issues/152",
        voteCount: 1,
        activePledgeScore: 0.13178124313639358,
        lifetimePledgeScore: 0.037393397655517066,
      },
    ];
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
</style>
