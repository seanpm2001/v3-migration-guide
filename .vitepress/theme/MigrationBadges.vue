<script>
const validBadges = {
  new: 'new',
  breaking: 'breaking',
  removed: 'removed',
  updated: 'updated'
}

export default {
  props: {
    badges: {
      type: Array,
      default: () => [],
      validator(value) {
        return value.every((badge) => Object.keys(validBadges).includes(badge))
      }
    }
  },
  data() {
    return {
      validBadges
    }
  }
}
</script>

<template>
  <div class="migration-badge-wrapper">
    <span
      v-for="badgeType in badges"
      :class="`migration-badge is-${badgeType}`"
      :key="`badge-type-${badgeType}`"
    >
      {{ validBadges[badgeType] }}
    </span>
  </div>
</template>

<style scoped>
.migration-badge {
  background-color: #ccc;
  font-size: 0.8rem;
  border: 2px solid #ccc;
  border-radius: 5px;
  margin-right: 0.5rem;
  margin-top: 0.5rem;
  color: #222;
  padding: 0.25rem 0.25rem;
  font-weight: bold;
}

.migration-badge:first-child {
  margin-left: 1rem;
}

.migration-badge.is-new {
  background-color: #228740;
  border-color: #228740;
  color: #fff;
}

.migration-badge.is-breaking {
  background-color: #b00000;
  border-color: #b00000;
  color: #fff;
}

.migration-badge.is-removed {
  background-color: #cf8700;
  border-color: #cf8700;
  color: #fff;
}

.migration-badge.is-updated {
  background-color: #fcff44;
  border-color: #fcff44;
  color: #222;
}

.migration-badge-wrapper {
  display: inline-block;
  position: relative;
  top: -0.5rem;
}
</style>
