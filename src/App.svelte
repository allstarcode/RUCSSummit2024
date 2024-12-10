<script lang="ts">
  import anime from 'animejs';
  import { onMount } from 'svelte';
  import asterik from './assets/logo.svg';
  import Schedule from './lib/ScheduleParser.svelte';

  let mainSchedule: HTMLDivElement;

  const toggleClassIfFound = (ele: Element, className: string) =>
    ele.classList.contains(className) ? ele.classList.toggle(className) : null;
  const toggleClassIfNotFound = (ele: Element, className: string) =>
    !ele.classList.contains(className) ? ele.classList.toggle(className) : null;

  const animateSchedule = () => {
    const allListItems = document.querySelectorAll('#schedulecont > ul.collapsible > li');
    anime({
      targets: allListItems,
      translateY: [250, 0],
      opacity: [0, 1],
      easing: 'easeInOutExpo',
      duration: 500,
      delay: anime.stagger(150),
    });
  };

  onMount(() => {
    animateSchedule();
  });
</script>

<main class="container">
  <div id="anchor" />
  <div class="row">
    <div class="col s12 center">
      <div class="title mainheader">
        <img class="titleAsterik" src={asterik} alt="ASC Asterik" />
        7th Annual Rutgers University Computer Science Summit <br /> ChatGPT for Learning: Dos and Don'ts
        <img class="titleAsterik" src={asterik} alt="ASC Asterik" />
      </div>
    </div>
  </div>
  <ul class="collapsible">
    <div id="schedulecont" bind:this={mainSchedule}>
      <Schedule />
    </div>
  </ul>
  <div id="footerLogo">
    <a href="https://allstarcode.org" rel="noreferrer noopener" target="_blank">
      <img src="https://i.imgur.com/w1tzpDH.png" alt="All Star Code Official Logo" />
    </a>
  </div>
</main>
