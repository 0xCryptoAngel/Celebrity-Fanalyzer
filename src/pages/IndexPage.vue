<template>
  <q-header class="shadow-1">
    <q-toolbar class="bg-white q-px-lg">
      <q-toolbar-title>
        <q-img src="~assets/logo.svg" width="1.7rem" />
        <span class="q-ml-sm inline row text-secondary">
          <b>Celebrity</b>
          Fanalyzer
        </span>
      </q-toolbar-title>
      <q-btn flat icon="notifications" round size="1rem" text-color="secondary" />
    </q-toolbar>
  </q-header>

  <!-- *** -->

  <q-page class="q-pa-md">
    <section class="text-center">
      <h2 class="q-my-sm text-h6">Welcome to Celebrity Fanalyzer!</h2>
      <RouterLink to="month">
        <p class="text-body1">Take a look at this month's competition!</p>
        <q-img :src="monthPrompt?.image" spinner-color="primary" style="border: 3px solid #e54757; border-radius: 12px" />
      </RouterLink>
      <p class="q-my-md text-body1">
        Question of the Month:
        <br />
        <RouterLink to="month">
          {{ monthPrompt?.title }}
        </RouterLink>
      </p>
      <article class="q-my-xl text-body1 text-left">
        <h3 class="text-bold text-h6">
          <i>“Celebrity Fanalyzer?”</i>
          &nbsp;

          <!-- *** -->

          <span>What’s This All About?</span>
        </h3>
        <p>
          Every month, the team at Celebrity Fanalyzer hosts an essay and art contest. Every month there is a Question-of-the-Month or
          Prompt that entrants must give there opinion about.
        </p>
        <p>Participants join the competition through the Freelancer web platform.</p>
        <p>
          The way the competition / site works is simple: Entrants must have a Freelancer account. No money is handled outside the
          Freelancer platform.
        </p>
        <ul>
          <li>The top 5 essays are chosen to be finalist. Each finalist receives $50.</li>
          <li>
            The criteria for winning the grand prize ($250) is an open formula published with each month’s question. For example: the entry
            with the most likes, shares, or comments, etc. wins. All voting occurs on www.CelebrityFanalyzer.com.
          </li>
          <li>Winners of the art competition are chosen by the team at Celebrity Fanalyzer.</li>
          <li>All submissions must be original work: essays and art.</li>
        </ul>
        <p>
          Every month a winner is chosen, paid, and then we do it again! The first and second week of the month are for writing. The third
          and fourth week are for voting. What's the point of all this? Read more here:
          <span class="text-primary text-bold cursor-pointer" @click="whyModal = !whyModal">Why?</span>
        </p>
      </article>

      <!-- *** -->

      <div>
        <h3 class="text-bold text-h5">Development Roadmap</h3>
        <div class="q-pa-md text-body1" style="max-width: 100%">
          <q-list bordered class="rounded-borders">
            <q-expansion-item expand-separator icon="stars" label="Build Celebrity Fanalyzer" caption="2022/23">
              <q-card>
                <q-card-section>
                  Celebrity Fanalyzer is an iteration engine: give us your feedback! We try to release a new version every month. We are
                  particularly interested in how to tweek the competition parameters for winning.
                </q-card-section>
              </q-card>
            </q-expansion-item>

            <q-expansion-item expand-separator icon="language" label="Make it a DAPP" caption="2023">
              <q-card>
                <q-card-section>
                  Celebrity Fanalyzer is one of many projects exploring how blockchain technology can be used. Our goal is to make Celebrity
                  Fanalyzer a DAPP (a Distributed APPlication) by connecting it to Ethereum. Anyone with a crypto wallet (we suggest
                  Metamask) should be able to participate in our competitions.
                </q-card-section>
              </q-card>
            </q-expansion-item>

            <q-expansion-item expand-separator icon="code" label="Build Layer 8" caption="2023/24">
              <q-card>
                <q-card-section>
                  Ultimately, our goal is to launch Celebrity Fanalyzer behind a custom built anonymizing reverse proxy scheduled for
                  development in late 2023 that we call “Layer 8.”
                </q-card-section>
              </q-card>
            </q-expansion-item>

            <q-expansion-item icon="assessment" label="Connect C.F. to Layer 8" caption="2024">
              <q-card>
                <q-card-section>
                  How to determine the definition of "better" when opinions are subjective by definition? The simplest way is to implement a
                  centralized process but this, of course, means only a single perspective is represented. A decentralize model of "better"
                  is necessary and this is a hard problem. Once Layer 8 is deployed, Celebrity Fanalyzer will have vast amounts of anonymous
                  data to analyze freely. How to rank (and reward) authors who contribute the "best" work? The answer is to-be-determined.
                </q-card-section>
              </q-card>
            </q-expansion-item>

            <q-expansion-item icon="rocket_launch" label="Launch Globe & Citizen" caption="2025">
              <q-card>
                <q-card-section>
                  Deep fakes, fake media, toxic hate speech, and a consolidated media industry: this is the reality of the internet today.
                  How to decentralize control of the media we consume but still provide a quality online service on par with a
                  <a href="https://moxie.org/2022/01/07/web3-first-impressions.html">centralized one</a>
                  ? Once Layer 8 is established, the AI ranking algorithm is open sourced, and Celebrity Fanalyzer is a successful DAPP,
                  it’s finally time to launch Globe & Citizen — our answer to this question. Reach out to us if you’re interested in getting
                  involved.
                </q-card-section>
              </q-card>
            </q-expansion-item>
          </q-list>
        </div>
      </div>

      <!-- *** -->

      <div>
        <div class="text-body1">
          <h3 class="text-bold text-h5">Contact Us!</h3>
          <p>
            Want to communicate with the team here at Celebrity Fanalyzer? Contact us through a message on our Discord server: give an
            opinion, suggest a topic, or give feedback. We would love to hear from you! Celebrity Fanalyzer is a work in progress. If you
            want to get involved shaping the future of the application, reach out to us. You can learn more about what we are doing by
            checking out the Road Map below or reading:
            <span class="text-primary text-bold cursor-pointer" @click="whyModal = !whyModal">Why?</span>
          </p>
          <q-btn flat rounded icon="img:/icons/discord.svg" href="https://discord.gg/z4P3UrhhSH" size="xl" target="_blank">
            <q-tooltip anchor="bottom middle" self="center middle">Community on Discord</q-tooltip>
          </q-btn>
        </div>
      </div>
    </section>

    <!-- *** -->

    <q-dialog v-model="whyModal">
      <q-card>
        <q-card-section>
          <div class="text-h6">What's The Point of Celebrity Fanalyzer?</div>
        </q-card-section>
        <q-separator />
        <q-card-section style="max-height: 60vh" class="scroll">
          <div class="text-body1">
            <p>
              Celebrity Fanalyzer is the first iteration of a multi year endeavor to produce an
              <span class="text-italic">anthroscope.</span>
              “And what”, you will certainly be asking, “is an anthroscope?”
            </p>
            <p>
              An
              <span class="text-italic">anthroscope</span>
              , like any scope (e.g., telescope, microscope, oscilloscope, etc.), is designed to give its users the capacity to view
              something with new perspective. In the case of this application, the specimen under investigation is society and that new
              perspective is the distribution and variety of opinions held within it. The prefix “anthro” being borrowed from the Greek word
              “anthropo” meaning human.
            </p>
            <p>
              To function as intended, Celebrity Fanalyzer will use modern statistics, artificial intelligence, and big data to produce
              visuals reflecting the opinion scape of any particular topic. The team collectively refers to these visuals as anthrograms.
              Anthrograms should, if done properly, make obvious the inherent biases of any
              <span class="text-bold">one</span>
              opinion and, from this new perspective, a user should be able to infer their own truth.
            </p>
            <p>
              Celebrity Fanalyzer cannot produce anthrograms in its current form. To do this, a technological solution which scrubs user
              data of all identifiers, is necessary. In fact, Celebrity Fanalyzer is one of few applications THAT DOES NOT WANT YOUR
              PERSONAL DATA. Ultimately, our goal is to launch the application behind a custom built anonymizing reverse proxy we call
              “Layer 8.” Once launched, this specialized server will scrub all personally identifying information from incoming traffic.
            </p>
            <p>
              Following the launch and debugging of Layer 8, Celebrity Fanalyzer is to be recast as a general news website entitled “Globe &
              Citizen.” Though following approximately the same mechanics as its simple forebearer, Globe & Citizen is to be an anthroscope
              in the fullest sense: by coming preconfigured to receive only anonymized user data, it will immediately produce anthrograms
              that users will hopefully find both insightful and beautiful. Globe & Citizen, unlike Celebrity Fanalyzer, will deal with
              topics such as climate change, inflation, COVID vaccines, and much more because, for obvious reasons, the Internet needs an
              anthroscope.
            </p>
            <p>This is “why.”</p>
          </div>
        </q-card-section>
        <q-separator />
        <q-card-actions align="right">
          <q-btn flat label="Close" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { usePromptStore } from 'src/stores'
import { onMounted, ref } from 'vue'

const promptStore = usePromptStore()

const monthPrompt = ref(promptStore.getMonthPrompt)

onMounted(async () => {
  await promptStore.fetchMonthPrompt()
  monthPrompt.value = promptStore.getMonthPrompt
})

const whyModal = ref(false)
</script>

<style scoped lang="scss">
a {
  text-decoration: none;
  transition: all 0.3s;

  &:visited {
    color: #e54757;
  }
}
</style>
