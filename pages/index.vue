<template>
	<div class="min-h-screen p-5 lg:p-12 bg-gray-100">
		<h1 class="text-center text-4xl font-bold">Courses</h1>
		<ul class="grid grid-cols-4">
			<li class="flex">
				<NuxtLink class="bg-white w-full rounded-xl p-4 text-xl text-center hover:text-blue-500" :to="courseSlug">
					{{ title }}
				</NuxtLink>
			</li>
		</ul>
	</div>
</template>

<script setup>
import slugify from 'slugify';
const { title } = useCourse();
const courseSlug = slugify(title, { lower: true });

useHead({
	title: 'Courses',
});
</script>
