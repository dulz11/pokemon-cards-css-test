<script>
  import { onMount } from "svelte";

	import Search from "./Search.svelte";
	import CardList from "./Cards.svelte";
	import Card from "./lib/components/CardProxy.svelte";

	let showcase, basics, reverse, holos, cosmos, amazings, radiant, basicGallery, 
			vee, veeUltra, veeAlt, veeMax, veeMaxAlt, veeStar, 
			trainerHolo, rainbow, gold, veeGallery, shinyVault;

	let query = "";
	let isLoading = true;

	const getCards = async () => {
		let promiseArray = [];
		let cardFetch = await fetch("/data/cards.json");
		let cards = await cardFetch.json();
		return cards;
	};

	const loadCards = async() => {
		return getCards()
			.then((cards) => {
				window.cards = cards;
				showcase = cards[0];
				basics = cards.slice(1, 4);
				reverse = [...cards.slice(4, 7), ...cards.slice(70,76)];
				holos = cards.slice(7, 13);
				cosmos = cards.slice(13, 16);
				amazings = cards.slice(76, 85);
				radiant = cards.slice(16, 19);
				basicGallery = cards.slice(19, 22);
				vee = cards.slice(22, 25);
				veeUltra = cards.slice(25, 28);
				veeAlt = cards.slice(28, 34);
				veeMax = cards.slice(37, 40);
				veeMaxAlt = cards.slice(40, 43);
				veeStar = cards.slice(43, 46);
				trainerHolo = cards.slice(46, 52);
				rainbow = cards.slice(52, 58);
				gold = cards.slice(58, 64);
				veeGallery = cards.slice(64, 70);
				shinyVault = cards.slice(85,91);
				isLoading = false;
			});
	};

	onMount(() => {
		loadCards();
		const $headings = document.querySelectorAll("h1,h2,h3");
		const $anchor = [...$headings].filter((el) => {
			const id = el.getAttribute("id")?.replace(/^.*?-/g,"");
			const hash = window.location.hash?.replace(/^.*?-/g,"")
			return id === hash;
		})[0];
		if( $anchor ) {
			setTimeout(() => {
				$anchor.scrollIntoView();
			},100);
		}
	});
</script>

<main>

	{#if query.length < 3}

		<CardList>
			<Card
				id='1'
				name='ElevenLabs'
				img='/cards/card-1.png'
				back='/cards/card-back.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare secret'
			/>
			<Card
				id='2'
				name='Granola'
				img='/cards/card-2.png'
				back='/cards/card-back.png'
				number='002'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='3'
				name='Pika'
				img='/cards/card-3.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='4'
				name='Freepik'
				img='/cards/card-4.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='5'
				name='Flora'
				img='/cards/card-5.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='6'
				name='Magnific'
				img='/cards/card-6.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='7'
				name='Notion'
				img='/cards/card-7.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='8'
				name='Viggle'
				img='/cards/card-8.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='9'
				name='HeyGen'
				img='/cards/card-9.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='10'
				name='Hedra'
				img='/cards/card-10.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='11'
				name='Higgsfield'
				img='/cards/card-11.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='12'
				name='Luma'
				img='/cards/card-12.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='13'
				name='Lovable'
				img='/cards/card-13.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
			<Card
				id='14'
				name='Veed'
				img='/cards/card-14.png'
				number='001'
				types={['Fire']}
				supertype='Pokémon'
				subtypes={['Basic']}
				rarity='rare holo vmax'
			/>
		</CardList>
	{/if}
</main>

<div class="back-to-top">
  <a href="#⚓-top">Back to Top</a>
</div>

<style>
  .back-to-top a {
    color: inherit;
    text-decoration: none;
		z-index: 999;
  }
</style>
