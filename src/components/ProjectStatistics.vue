<template>
  <div>
    <Card>
      <h2>Projects</h2>
    </Card>
    <Card>
      <h3>Project Statistics</h3>
      <p>
        Statistics are limited until extended statistic endpoints are published to
        the Modrinth API.
      </p>
      <div class="grid-display">
        <div class="grid-display__item">
          <div class="label">Total Downloads</div>
          <div class="value">
            {{ formatCount(store.total_downloads) }}
          </div>
          <span class="smaller-value"
            >from {{ store.projects.length }} project{{
              store.projects.length === 1 ? "" : "s"
            }}
          </span>
        </div>
        <div class="grid-display__item">
          <div class="label">Total Follows</div>
          <div class="value">{{ formatCount(store.total_followers) }}</div>
          <span class="smaller-value"
            >from {{ store.projects.length }} project{{
              store.projects.length === 1 ? "" : "s"
            }}</span
          >
        </div>
      </div>
    </Card>
  </div>
</template>

<script>
import { store } from "@/store";

export default {
  data: () => {
    return {
      store,
    };
  },
  props: ["settings"],
  methods: {
    formatCount(amount) {
      return this.settings.abreviate_downloads
        ? Intl.NumberFormat("en-US", {
            notation: "compact",
            maximumFractionDigits: 1,
          }).format(amount)
        : amount;
    },
  },
};
</script>
