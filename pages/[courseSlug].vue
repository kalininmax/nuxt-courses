<template>
	<div class="min-h-screen p-5 lg:p-12 bg-gray-100">
		<div class="mb-12 prose">
			<h1 class="text-4xl text-center">
				<span class="text-lg font-medium">Course:</span><br>
				<span class="font-bold">{{ title }}</span>
			</h1>
		</div>

		<div class="flex flex-col gap-4 lg:flex-row justify-center flex-grow">
			<div class="prose p-8 bg-white rounded-md lg:w-[30%]">
				<h2 class="text-xl font-bold">Chapters</h2>
				<div class="space-y-1 my-4 flex flex-col" v-for="chapter in chapters" :key="chapter.slug">
					<p class="text-lg font-bold">{{ chapter.title }}</p>
					<NuxtLink v-for="(lesson, index) in chapter.lessons" :key="lesson.slug"
						class="flex flex-row space-x-1 no-underline prose-sm font-normal py-1 px-4 -mx-4 hover:text-blue-500"
						:to="`/${route.params.courseSlug}/${chapter.slug}/${lesson.slug}`" :class="{
							'text-blue-500': lesson.slug === $route.params.lessonSlug,
							'text-gray-600': lesson.slug !== $route.params.lessonSlug,
						}">
						<span class="text-gray-500">{{ index + 1 }}.</span>
						<span>{{ lesson.title }}</span>
					</NuxtLink>
				</div>
			</div>

			<div class="prose p-12 bg-white rounded-md lg:w-[70%]">
				<NuxtPage />
			</div>
		</div>
	</div>
</template>

<script setup>
const { title, chapters } = useCourse();
const route = useRoute();
</script>
