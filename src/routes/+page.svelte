<script>
	import { Gutter } from '$lib/components';
</script>

<main>
	<section>
		<Gutter>
			<div class="flow">
				<h1><span class="underline">v</span>aut</h1>
				<p>designing and building for the <em>modern web</em></p>
			</div>
		</Gutter>
	</section>
	<section class="is-inverted">
		<Gutter>
			<div class="flow">
				<h2>Services</h2>
				<p>Do you need a personal or business website? Tell a story, sell your brand.</p>
				<p>
					Central to our process is <span class="underline">identifying your need</span>. What does
					this mean in practice?
				</p>
				<p></p>
				<h3>Design</h3>
				<p>We design websites to be responsive and accessible.</p>
				<h3>Development</h3>
				<p>
					We focus on accessibility, speed, security. Using robust technologies. Accessible, fast,
					secure.
				</p>
				<p>Integrations? Content management system? Need a way to manage your content? Or maybe you don't.</p>
				<p>We'll choose the right CMS solution for you: Sanity, Storyblok</p>
				<!--
				<ul class="cluster">
					<li>1</li>
					<li>2</li>
					<li>3</li>
				</ul>
				-->
				<h3>SEO</h3>
				<p>SEO (search engine optimization) involves. Need content produced? We can help.</p>
				<h3>Support</h3>
				<p>
					A purpose-built CMS (content management system) solution just for your needs. No, we don't
					work with WordPress.
				</p>
			</div>
		</Gutter>
	</section>
</main>
<footer>
	<Gutter>
		<div class="flow">
			<h2>Eager to learn more?</h2>
			<p>Whatever you are looking for, we can figure something out.</p>
			<p>Reach out at <a href="mailto:email@example.com">email@example.com</a></p>
			<p><small>&copy; 2024 vaut.io</small></p>
		</div>
	</Gutter>
</footer>

<style>
	main,
	footer {
		background-color: var(--color-light);
		color: var(--color-dark);
	}

	.is-inverted {
		background-color: var(--color-dark);
		color: var(--color-light);
	}

	section,
	footer {
		padding-block: var(--space-2xl-3xl);
	}

	.flow > * + * {
		margin-block-start: var(--space-s-m);
	}

	/*
	.cluster {
		display: flex;
		flex-wrap: wrap;
		justify-content: flex-start;
		align-items: flex-start;
		gap: var(--s-1);
	}
	*/

	h1 {
		font-size: var(--step-3);
	}
	h2 {
		font-size: var(--step-2);
	}
	h3 {
		font-size: var(--step-1);
	}
	p {
		font-size: var(--step-0);
	}
	small {
		font-size: var(--step--1);
	}

	.underline {
		text-decoration: underline;
	}
</style>
