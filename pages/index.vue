<template>
  <div class="container">
    <section class="section-container">
      <h1 class="heading">Schedule</h1>
      <p>Próximos streamings</p>
    </section>
    <hr class="divider" />

    <div class="schedule-container">
      <div class="schedule-stage__wrapper">
        <section
          v-for="evento in eventosByDay"
          :key="evento.id"
          class="schedule-stage"
        >
          <div class="schedule-stage__title">
            <h3>{{ evento.dia | weekDay }}</h3>
          </div>
          <div class="schedule-stage_guide-container">
            <div v-for="(hora, h) in horas" :key="h" class="guide-slot">
              <p class="time-slot" :data-time="hora | hora">
                {{ hora | hora }} - {{ horas[(h + 1) % 24] | hora }}
              </p>
              <div
                v-for="item in eventosByHour(
                  evento.eventos,
                  hora.format('HH:mm')
                )"
                :key="item.id"
                class="guide-slot_card"
              >
                <h4>{{ item.title }}</h4>
                <figure class="author-wrapper">
                  <picture>
                    <img :src="item.avatar" alt="" />
                  </picture>
                  <figcaption>{{ item.author }}</figcaption>
                </figure>
              </div>
            </div>
            <!--
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
            -->
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
    weekDay(date) {
      return moment(new Date(date)).format('dddd')
    },
    hora(datetime) {
      return moment(datetime).format('H:mm')
    },
  },
  data() {
    return {
      hoy: new Date(),
      horas: [],
      items: [
        {
          id: 1,
          catId: 1,
          title: 'CSR, SSR, SSG, ISR and OMG.WTF?BBQ!',
          author: 'Ahmad Awais',
          avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
          start: 'Fri Mar 26 2021 08:00:31 GMT+0100',
          end: 'Fri Mar 26 2021 09:00:31 GMT+0100',
        },
        {
          id: 2,
          catId: 1,
          title: 'Título 2',
          author: 'Josh Laudrup',
          avatar: 'https://randomuser.me/api/portraits/lego/4.jpg',
          start: 'Fri Mar 26 2021 08:00:31 GMT+0100',
          end: 'Fri Mar 26 2021 09:00:31 GMT+0100',
        },
        {
          id: 3,
          catId: 1,
          title: 'Título 3',
          author: 'Tom Berenger',
          avatar: 'https://randomuser.me/api/portraits/lego/3.jpg',
          start: 'Fri Mar 26 2021 09:00:31 GMT+0100',
          end: 'Fri Mar 26 2021 10:00:31 GMT+0100',
        },
        {
          id: 4,
          catId: 1,
          title: 'Equipos y Psicología',
          author: 'Benito Floro',
          avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
          start: 'Fri Mar 26 2021 10:00:31 GMT+0100',
          end: 'Fri Mar 26 2021 11:00:31 GMT+0100',
        },
        {
          id: 5,
          catId: 1,
          title: 'Conspiraciones de conscursantes',
          author: 'Jordi Hurtado',
          avatar: 'https://randomuser.me/api/portraits/lego/1.jpg',
          start: 'Fri Mar 26 2021 08:00:31 GMT+0100',
          end: 'Fri Mar 26 2021 09:00:31 GMT+0100',
        },
        {
          id: 4,
          catId: 1,
          title: 'Equipos y Psicología',
          author: 'Benito Floro',
          avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
          start: 'Sat Mar 27 2021 10:00:31 GMT+0100',
          end: 'Sat Mar 27 2021 11:00:31 GMT+0100',
        },
        {
          id: 5,
          catId: 1,
          title: 'Conspiraciones de conscursantes',
          author: 'Jordi Hurtado',
          avatar: 'https://randomuser.me/api/portraits/lego/1.jpg',
          start: 'Sat Mar 27 2021 08:00:31 GMT+0100',
          end: 'Sat Mar 27 2021 09:00:31 GMT+0100',
        },
      ],
    }
  },
  computed: {
    eventosByDay() {
      const items = this.items.reduce((acum, item) => {
        const d = moment(new Date(item.start)).format('YYYY-MM-DD')
        const found = acum.find((x) => x.dia === d)

        if (!found) acum.push({ dia: d, eventos: [item] })
        else found.eventos.push(item)
        return acum
      }, [])
      return items
    },
  },
  mounted() {
    moment.locale('es-ES')
    // this.parseItems()
    this.horas = Array.from(
      {
        length: 24,
      },
      (_, hour) =>
        moment({
          year: new Date().getFullYear(),
          month: new Date().getMonth(),
          day: new Date().getDate(),
          hour,
          minutes: 0,
          seconds: 0,
        })
    )
    // this.scrollTo('[data-time]=' + new Date().getHours())
    if (
      this.$el.querySelector('[data-time="' + new Date().getHours() + ':00"]')
    )
      this.$el
        .querySelector('[data-time="' + new Date().getHours() + ':00"]')
        .scrollIntoView()
  },
  methods: {
    eventosByHour(eventos, hora) {
      if (!eventos) return []
      hora = '0' + hora
      hora = hora.substr(-5)
      const h = moment(hora, 'HH:mm')
      const h1 = moment(hora, 'HH:mm').add(1, 'h')
      return eventos.filter(
        (x) =>
          (moment(x.start).format('HH:mm') >= h.format('HH:mm') &&
            h1.format('HH:mm') > moment(x.start).format('HH:mm')) ||
          (moment(x.end).format('HH:mm') < h1.format('HH:mm') &&
            h.format('HH:mm') < moment(x.end).format('HH:mm'))
      )
    },
    moment(date) {
      return moment(date)
    },
    scrollTo(param) {
      const items = document.container.getAttribute(param)
      const visible = [...items].filter((el) => {
        // jQuery-like :visible selector
        return !!(
          el.offsetWidth ||
          el.offsetHeight ||
          el.getClientRects().length
        )
      })

      if (visible.length > 0) {
        document.container.scrollTo({
          top: items[0].offsetTop,
          behavior: 'smooth',
        })
      }
    },
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
