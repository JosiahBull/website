<template>
	<div>
		<div id="landingImage"></div>
		<section id="welcomeCard" class="section container column is-10">
			<div class="columns is-desktop ">
				<div class="column desktop-only is-half" />
				<div class="card column">
					<div class="card-content content">
						<h1 class="title is-1 extended">Kia Ora, We Are Kēmu Kupu</h1>
						<p class="content is-size-4">Welcome! We are an aspiring development organisation focussing on the development of language learning tools for Te Reo Maori. We believe that all members of New Zealand should engage with the vibrant culture of Maori life, to better understand the roots of our beautiful Aotearoa! </p>
					</div>
					<div class="card-footer">
						<a class="card-footer-item is-primary is-light button m-2" href="#about">
							Learn More
						</a>
						<a class="card-footer-item is-primary button m-2" href="https://github.com/SOFTENG206-2021/assignment-3-and-project-team-11">
							Download
						</a>
					</div>
				</div>
			</div>
		</section>
		<section class="section container column is-10">
			<ContentPane
				title="Client Centric: For the Kids!"
				body="Bee themed. Fun and Colourful. Big Playful Buttons. Sound Effects. Music."
				image="game/title.png"
				:left="true"
				id="about"
			/>
			<div class="spacer-desktop" />
			<div class="spacer-desktop" />
			<ContentPane
				title="Learning at its core!"
				body="Aiming to improve the tamariki of NZ in their proficiency of Maori in a fun and playful manner"
				image="game/quiz.png"
				:left="true"
			/>
			<div class="spacer-desktop" />
			<div class="spacer-desktop" />
			<ContentPane
				title="Gamification!"
				body="Personalisation of games. Via unlocking costumes, collecting of achievements, accummulating stars, and tracking your high score"
				image="game/costume.png"
				:left="false"
			/>
			<div class="spacer-desktop" />
			<div class="spacer-desktop" />
			<ContentPane
				title="Keeping track of progress!"
				body="Allow users to create/login/delete/modify accounts with full backend functionality so that users don't have to worry about getting back their progress. Persistent login."
				image="game/profile.png"
				:left="true"
			/>
			<div class="spacer-desktop" />
			<div class="spacer-desktop" />
			<ContentPane
				title="Extra Goodies!"
				body="Keeping the user occupied with a spin-to-win spinning wheel, as well as custom game timers, input fields, and progress bars."
				image="game/spinner.png"
				:left="true"
			/>
			<div class="spacer-desktop" />
			<div class="spacer-desktop" />
			<span id="team"></span>
			<div class="columns">
				<ProfileCard
					class="column"
					name="Josiah Bull"
					image="profiles/jo.jpeg"
					github="https://github.com/JosiahBull"
					linkedin="https://www.linkedin.com/in/josiah-bull/"
					blurb="Backend developer, enjoys tinkering with electronics in his free time."
				/>
				<ProfileCard
					class="column"
					name="John Chen"
					image="profiles/john.jpeg"
					github="https://github.com/johnchen383"
					linkedin="https://www.linkedin.com/in/johnc383/"
					blurb="An avid learner, excited by the potential that the technology of tomorrow holds."
				/>
				<ProfileCard
					class="column"
					name="Serena Lau"
					image="profiles/serena.jpeg"
					github="https://github.com/serenalau272"
					linkedin="https://www.linkedin.com/in/serena-lau-2166111a0/"
					blurb="Loves having fun with software projects and always curious to learn more. Also passionate about Chopin and tiramisu macarons."
				/>
			</div>
		</section>
	</div>
</template>

<script>
import ContentPane from '~/components/ContentPane';
import ProfileCard from '~/components/ProfileCard';

function convertRemToPixels(rem) {    
    return rem * parseFloat(getComputedStyle(document.documentElement).fontSize);
}




export default {
	name: 'HomePage',
	components: {
		ContentPane,
		ProfileCard
	},
	created() {
		window.addEventListener("resize", this.scaleOnSizeChange);
	},
	destroyed() {
		window.removeEventListener("resize", this.scaleOnSizeChange);
	},
	methods: {
		//Scale the landing page image when the page is resized
		scaleOnSizeChange(_e) {
			//Get height of card
			let heightCard = document.getElementById("welcomeCard").offsetHeight + convertRemToPixels(3);
			let heightWindow = window.innerHeight;
			let backgroundHeight = Math.max(heightCard, heightWindow);
			document.getElementById("landingImage").style.height = backgroundHeight + "px";
		}
	}
}
</script>


<style>

#landingImage {
	height: 100vh;
	width: 100vw;
	background-image: url("~assets/cartoon-landscape.png");
	background-size: cover;                      
    background-repeat: no-repeat;
    background-position: center center;
}

#welcomeCard {
	position: absolute;
	top: 10vh;
	left: 8.35%;
}

.desktop-only {
	display: none;
}

@media only screen and (min-width: 1024px) {
	.spacer-desktop {
		width: 100%;
		margin-top: 5em;
		height:1px;
	}

	#welcomeCard {
		position: absolute;
		top: 20vh;
		right: 5vw;
	}

	.desktop-only {
		display:block;
	}
}

@media only screen and (max-width: 600px) {
	h1 {
		font-size: 2em !important;
	}
}

</style>