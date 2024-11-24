<script lang="ts">
  import { onMount } from "svelte";
  import { atUriToPostUri, getUserPosts, getLikes, getPost } from "./utils";
  import { cn } from "src/utils";

  const { uri, likesCount, likesData, user } = $props();

  let postUri = $state(uri);
  let postLikesCount = $state(likesCount);
  let postLikesData = $state(likesData.filter((like) => like.actor.avatar));

  onMount(async () => {
    if (!uri && user) {
      let posts = await getUserPosts(user);

      const url = window.location.href;

      // @ts-expect-error: weird type fuckery
      const post = posts.find((post) => post.post.embed?.external?.uri === url);

      if (post) {
        postUri = post.post.uri;
        postLikesCount = post.post.likeCount;

        postLikesData = (await getLikes(post.post.uri)).filter(
          (like) => like.actor.avatar
        );
      }
    } else if (uri) {
      postLikesData = (await getLikes(uri)).filter((like) => like.actor.avatar);

      const post = await getPost(uri);

      if (post) {
        postUri = post.uri;
        postLikesCount = post.likeCount;
      }
    }
  });
</script>

{#if postUri}
  <div class="not-prose flex flex-col mt-16 gap-4">
    <div class="text-sm text-base-950 dark:text-base-100 font-semibold">
      {postLikesCount} like{postLikesCount === 1 ? "" : "s"} on bluesky
    </div>

    <div class="isolate flex -space-x-2 overflow-hidden px-4 flex-wrap">
      {#each postLikesData as user, index}
        <a
          href={`https://bsky.app/profile/${user.actor.handle}`}
          class={cn(
            "relative inline-block size-12 rounded-full overflow-hidden ring-2 ring-base-50 dark:ring-base-900  bg-base-950",
            index === 0 ? "-ml-2" : ""
          )}
          target="_blank"
        >
          <img
            title={user.actor.handle}
            loading="lazy"
            src={user.actor.avatar.replace('avatar', 'avatar_thumbnail')}
            alt={"liked by " + user.actor.displayName}
          />
        </a>
      {/each}

      {#if postLikesData.length < postLikesCount}
        <div
          class="z-10 text-sm text-accent-700 dark:text-accent-300 size-12 rounded-full flex items-center justify-center bg-accent-100 dark:bg-accent-950 ring-2 ring-base-50 dark:ring-base-900 font-semibold mb-4"
        >
          +{postLikesCount - postLikesData.length}
        </div>
      {/if}
    </div>

    <a
      target="_blank"
      href={atUriToPostUri(postUri)}
      class="text-sm text-accent-600 dark:text-accent-300 font-semibold inline-flex w-fit items-center gap-1.5 bg-accent-100 dark:bg-accent-900/30 px-3 py-2 rounded-xl border border-accent-300 hover:bg-accent-200 dark:hover:bg-accent-800/30 dark:border-accent-900/50 transition-colors duration-100"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="currentColor"
        class="size-6"
        aria-hidden="true"
      >
        <path
          d="m11.645 20.91-.007-.003-.022-.012a15.247 15.247 0 0 1-.383-.218 25.18 25.18 0 0 1-4.244-3.17C4.688 15.36 2.25 12.174 2.25 8.25 2.25 5.322 4.714 3 7.688 3A5.5 5.5 0 0 1 12 5.052 5.5 5.5 0 0 1 16.313 3c2.973 0 5.437 2.322 5.437 5.25 0 3.925-2.438 7.111-4.739 9.256a25.175 25.175 0 0 1-4.244 3.17 15.247 15.247 0 0 1-.383.219l-.022.012-.007.004-.003.001a.752.752 0 0 1-.704 0l-.003-.001Z"
        ></path>
      </svg>

      <span class="sr-only">Like</span>
      on bluesky</a
    >
  </div>
{/if}
