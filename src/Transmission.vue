<template>
  <FocusFrame :header-label="headerLabel" :header-number="headerNumber" :footer-label="footerLabel">
    <router-link to="/" class="">
      <div class="federation-logo m-auto">
        <FederationLogo />
      </div>
      <h1>{{title}}</h1>
      <h3 class="color6" v-html="subtitle"></h3>
    </router-link>
  </FocusFrame>
</template>

<script>
import { makeRandomNumber, pickRandom } from './utils'
import FocusFrame from './FocusFrame.vue';
import FederationLogo from './federation-logo.svg'

export default {
  data() {
    const locations = [
      'Main Bridge',
      'Terminal Access'
    ]
    const labels = [
      'Subspace Comm Net',
      'System Monitor',
      'LCARS'
    ]
    const titles = [
      'Incoming Transmission',
      'Incoming Communication',
    ]
    const subtitles = [
      'Starfleet Command &#8226; Authorized access only',
      'Starfleet Command &#8226; Command authorization required',
      'From: Starfleet Command<br/>Command authorization required'
    ]
    const location = pickRandom(locations)
    const label = pickRandom(labels)
    const title = pickRandom(titles)
    const subtitle = pickRandom(subtitles)
    const showLocation = Math.random() > 0.5 ? true : false

    return {
      headerLabel: label,
      headerNumber: makeRandomNumber(4, false),
      footerLabel: showLocation ? location : null,
      title,
      subtitle,
    }
  },
  components: {
    FocusFrame,
    FederationLogo
  }
}
</script>

<style>
h1,
h2,
h3,
h4,
h5,
h6 {
  color: #f93;
  padding: 0 10px;
  background-color: #090909;
  margin: 0;
  text-transform: uppercase;
  font-weight: normal;
}
h1 {
  font-size: 84px !important;
  line-height: 0.9em;
}
h3 {
  font-size: 42px !important;
  line-height: 1em;
}
.federation-logo {
  max-width: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 1em;
}
.federation-logo svg {
  object-fit: contain;
}
.color6 {
  color: #9cf;
}
a {
  text-decoration: none;
  color: inherit;
}
</style>
