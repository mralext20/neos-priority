<template>
  <tr>
    <td>
      <a :href="$props.issue.issueURL">{{ $props.issue.issueNumber }}</a>
    </td>
    <td>
      {{ $props.issue.title }}
    </td>
    <td>
      {{ $props.issue.voteCount }}
    </td>
    <td>
      {{ $props.issue.activePledgeScore.toFixed(3) }}
    </td>
    <td>
      {{ $props.issue.lifetimePledgeScore.toFixed(3) }}
    </td>
  </tr>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    issue: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
