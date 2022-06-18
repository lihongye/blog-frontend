<!--  -->
<template>
	<layout>
		<!-- Page Header -->
		<header
			class="masthead"
			:style="{
				backgroundImage: `url(http://106.75.37.42:1337${
					$page.post.cover.url
				})`,
			}"
		>
			<div class="overlay"></div>
			<div class="container">
				<div class="row">
					<div class="col-lg-8 col-md-10 mx-auto">
						<div class="post-heading">
							<h1>
								{{ $page.post.title }}
							</h1>
							<!-- <h2 class="subheading">
								Problems look mighty small from 150 miles up
							</h2> -->
							<span class="meta"
								>Posted by
								<a href="#">Start Bootstrap</a>
								on August 24, 2019</span
							>
						</div>
					</div>
				</div>
			</div>
		</header>

		<!-- Post Content -->
		<article>
			<div class="container">
				<div class="row">
					<div
						class="col-lg-8 col-md-10 mx-auto"
						v-html="mdToHtml($page.post.content)"
					></div>
				</div>
			</div>
		</article>
	</layout>
</template>

<page-query>
    query ($id: ID!) {
        post:strapiPost (id: $id) {
            id
            title
            content
            cover{
                url
            }
            tags {
                id
                title
            }
        }
    }
</page-query>

<script type="text/ecmascript-6">
import MarkdownIt from 'markdown-it'

const md = new MarkdownIt()

console.log(md.render('# hello'))

export default {
  name :'PostPage',
  methods: {
      mdToHtml(markdown){
          return md.render(markdown)
      }
  }
}
</script>

<style></style>
