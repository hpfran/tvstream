<template>
  <div class="container">
    <section class="section-container">
      <h1 class="heading">Schedule</h1>
      <p>Próximos streamings</p>
    </section>

    <hr class="divider" />

    <div class="schedule-container">
      <div class="schedule-stage__wrapper">
        <section class="schedule-stage">
          <div class="schedule-stage__title">
            <h3>{{ hoy | weekDay }}</h3>
          </div>
          <div class="schedule-stage_guide-container">
            <div class="guide-slot">
              <p class="time-slot">8:00am - 9:00am</p>
              <div class="guide-slot_card selected">
                <h4>CSR, SSR, SSG, ISR and OMG.WTF?BBQ!</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/6.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Ahmad Awais</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>9:00am - 10:00am</p>
              <div class="guide-slot_card">
                <h4>Changing Lanes with Lyft</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/2.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Joshua Callender</figcaption>
                </figure>
              </div>
              <div class="guide-slot_card">
                <h4>Magic Authentication - The Missing LEGO Piece</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/1.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Sean Li</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>10:00am - 11:00am</p>
              <div class="guide-slot_card">
                <h4>
                  Introducing: Edge Slice Rerendering. Performant A/B Testing,
                  Personalization, and more.
                </h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/3.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Jay Phelps</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>11:00am - 12:00pm</p>
              <div class="guide-slot_card selected">
                <h4>Everything Is a CMS</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/5.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Sean C Davis</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>12:00pm - 1:00pm</p>
              <div class="guide-slot_card">
                <h4>Responsive Rendering with Next.js</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/8.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Armando Gonzalez</figcaption>
                </figure>
              </div>
            </div>
          </div>
        </section>

        <hr class="divider" />

        <section class="schedule-stage">
          <div class="schedule-stage__title">
            <h3>{{ hoy.addDays(1) | weekDay }}</h3>
          </div>
          <div class="schedule-stage_guide-container">
            <div class="guide-slot">
              <p>8:00am - 9:00am</p>
              <div class="guide-slot_card">
                <h4>Changing Lanes with Lyft</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/2.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Joshua Callender</figcaption>
                </figure>
              </div>
              <div class="guide-slot_card selected">
                <h4>Magic Authentication - The Missing LEGO Piece</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/1.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Sean Li</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>9:00am - 10:00am</p>
              <div class="guide-slot_card vip">
                <h4>CSR, SSR, SSG, ISR and OMG.WTF?BBQ!</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/6.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Ahmad Awais</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>10:00am - 11:00am</p>
              <div class="guide-slot_card">
                <h4>Responsive Rendering with Next.js</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/8.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Armando Gonzalez</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>11:00am - 12:00pm</p>
              <div class="guide-slot_card">
                <h4>Everything Is a CMS</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/5.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Sean C Davis</figcaption>
                </figure>
              </div>
            </div>
            <div class="guide-slot">
              <p>12:00pm - 1:00pm</p>
              <div class="guide-slot_card">
                <h4>
                  Introducing: Edge Slice Rerendering. Performant A/B Testing,
                  Personalization, and more.
                </h4>
                <figure class="author-wrapper">
                  <picture>
                    <img
                      src="https://randomuser.me/api/portraits/lego/3.jpg"
                      alt=""
                    />
                  </picture>
                  <figcaption>Jay Phelps</figcaption>
                </figure>
              </div>
            </div>
          </div>
        </section>
        <hr class="divider" />
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
// eslint-disable-next-line no-extend-native
Date.prototype.addDays = function (d) {
  return new Date(this.valueOf() + 864e5 * d)
}

export default {
  filters: {
    weekDay(date, locale = 'es') {
      moment.locale(locale)
      return moment(new Date(date)).format('dddd')
    },
  },
  data() {
    return {
      hoy: new Date(),
    }
  },
}
</script>

<style>
.container {
  /* margin: 0 auto; */
  min-height: 100vh;
  /*
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  */
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
