<!-- eslint-disable no-tabs -->
<template>
	<div :data-theme="theme">
		<div className="navbar bg-base-100">
			<div className="navbar-start">
				<div className="dropdown">
					<div
						tabIndex="{0}"
						role="button"
						className="btn btn-ghost btn-circle"
					>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							className="h-5 w-5"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
						>
							<path
								strokeLinecap="round"
								strokeLinejoin="round"
								strokeWidth="2"
								d="M4 6h16M4 12h16M4 18h7"
							/>
						</svg>
					</div>
					<ul
						tabIndex="{0}"
						className="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52"
					>
						<li><a>Homepage</a></li>
						<li><a>Portfolio</a></li>
						<li><a>About</a></li>
					</ul>
				</div>
			</div>
			<div className="navbar-center">
				<a className="btn btn-ghost text-xl">iLodhi</a>
			</div>
			<div className="navbar-end">
				<!-- <button className="btn btn-ghost btn-circle"> -->
				<select
					v-model="theme"
					class="dropdown-content z-[1] card card-compact w-21 p-2 shadow bg-primary text-primary-content"
				>
					<div className="card-body"></div>
					<option disabled selected>Select Theme</option>
					<option v-for="theme in themes" :value="theme" :key="theme">
						<span class="uppercase">{{ theme }}</span>
					</option>
				</select>
			</div>
		</div>
		<slot />
		<footer class="footer footer-center p-10 bg-base-50">
			<div>
				<h1 class="text-2xl md:text-3xl font-bold">Footer</h1>
				<p class="md:font-bold">
					Create beautiful and fast websites without the tedious setup
				</p>
				<p>Copyright © {{ new Date().getFullYear() }} - All right reserved</p>
			</div>
			<div>
				<div class="grid grid-flow-col gap-4">
					<a href="https://twitter.com/jrtiquez" target="_blank">
						<i class="lab la-twitter text-4xl"></i>
					</a>
					<a
						href="https://github.com/ossphilippines/nuxtwind-daisy"
						target="_blank"
					>
						<i class="lab la-github text-4xl"></i>
					</a>
					<a href="https://facebook.com/ossph.org" target="_blank">
						<i class="lab la-facebook text-4xl"></i>
					</a>
				</div>
			</div>
		</footer>
	</div>
</template>

<script>
import { ref, watch, onMounted } from "vue";
const THEMES = [
	"light",
	"dark",
	"cupcake",
	"bumblebee",
	"emerald",
	"corporate",
	"synthwave",
	"retro",
	"cyberpunk",
	"valentine",
	"halloween",
	"garden",
	"forest",
	"aqua",
	"lofi",
	"pastel",
	"fantasy",
	"wireframe",
	"black",
	"luxury",
	"dracula",
	"cmyk",
	"autumn",
	"business",
	"acid",
	"lemonade",
	"night",
	"coffee",
	"winter",
	"mytheme",
	"forest",
	"aqua",
	"lofi",
	"pastel",
	"fantasy",
	"wireframe",
	"black",
	"luxury",
	"dracula",
	"cmyk",
	"forest",
];
export default {
	setup() {
		const theme = ref(null);
		watch(theme, (value) => {
			localStorage.setItem("daisyui-theme", value);
		});
		onMounted(() => {
			theme.value = localStorage.getItem("daisyui-theme") || "dark";
		});
		return {
			theme,
			themes: THEMES,
		};
	},
};
</script>
