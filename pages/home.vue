<script setup lang="ts">
definePageMeta({
  title: "Home",
  layout: "home",
});

interface Card {
  title: string;
  description: string;
  linkCaption: string;
  linkPath: string;
  icon: string;
}

const cards: Card[] = [
  {
    title: "LatestContentTitle",
    description: "LatestContentDesc",
    linkCaption: "LatestContentLink",
    linkPath: "demo",
    icon: "arrow-up-right-from-square",
  },

  {
    title: "ConnectWithOthersTitle",
    description: "ConnectWithOthersDesc",
    linkCaption: "CommingSoon",
    linkPath: "demo",
    icon: "comments",
  },
  {
    title: "JoinDiscussionsTitle",
    description: "JoinDiscussionsDesc",
    linkCaption: "CommingSoon",
    linkPath: "demo",
    icon: "users",
  },
];
</script>

<template>
  <main class="container py-8">
    <!-- Header -->
    <div class="text-center mb-16">
      <h1 class="text-5xl font-bold text-primary-500">
        {{ "WelcomeHeader" }}
      </h1>
      <p class="text-xl text-gray-600 max-w-2xl mx-auto mb-8">
        {{ "WelcomeDescription" }}
      </p>
      <NuxtLink :to="{ name: 'demo' }">
        <BaseButton class="flex mx-auto gap-2 items-center">
          <span>{{ "ExploreFeeds" }}</span>
          <FontAwesomeIcon icon="fars fa-square-up-right" class="w-5 h-5" />
        </BaseButton>
      </NuxtLink>
    </div>

    <!-- Feature Cards  -->
    <div
      class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 mb-8 justify-center"
      data-aos="fade-up"
      data-aos-duration="800"
    >
      <HomeCard
        v-for="(card, index) in cards"
        :key="index"
        :icon="card.icon"
        :title="card.title"
        :description="card.description"
        :linkCaption="card.linkCaption"
        :linkPath="card.linkPath"
      />
    </div>
  </main>
</template>
