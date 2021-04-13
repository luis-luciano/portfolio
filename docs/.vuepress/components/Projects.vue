<template>
	<div class="projects-container">
		<div v-for="(page, index) in files" :key="index" class="card">
			<router-link :to="page.path" class="link-card">
				<div
					class="thumb"
					:style="{
						'background-image': `url(${page.frontmatter.images})`
					}"
				></div>
				<h1 class="card-title">{{ page.title }}</h1>
			</router-link>
		</div>
	</div>
</template>

<script>
export default {
	name: "Projects",
	computed: {
		files() {
			return this.$site.pages.filter(
				page => page.path.indexOf("/portafolio/projects/") >= 0
			);
		}
	}
};
</script>

<style lang="stylus">

/* For theme original */
.theme-default-content:not(.custom)
    max-width: 840px;

.theme-default-content:not(.custom) a:hover
	text-decoration none

.projects-container
    max-width 840px
    margin 0 auto
    display grid
    grid-template-columns 1fr
    grid-template-rows auto
    grid-gap 20px

@media only screen and (min-width: 850px)
    .projects-container
        grid-template-columns: 1fr 1fr 1fr;

.card
    min-height 100%
    background white;
    box-shadow 0 2px 5px rgba(0,0,0,0.3)
    display flex
    flex-direction column
    position relative
    top: 0
    transition: all .2s ease-in;

.card:hover
    top -4px
    box-shadow 0 4px 5px rgba(0,0,0,0.6)

.card-title
	font-size 25px
	margin 0
	color #333

.card h1
    padding 25px
    display flex
    flex 1
    justify-content space-between
    flex-direction column

.link-card .thumb
    padding-bottom 75%
    background-size cover
    background-position center center
</style>
