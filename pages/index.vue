<template>
  <div class="container">
    <section class="section-container">
      <h1 class="heading">Schedule</h1>
      <p>Próximos streamings</p>
    </section>
    <hr class="divider" />
    <button @click.prevent="scrollTo('slot-' + ahora)">ahora</button>

    <div id="schedule-container" class="schedule-container">
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
            <div
              v-for="(hora, h) in horas"
              :key="h"
              class="guide-slot"
              :class="[
                `slot-${h}`,
                {
                  disabled: moment(hoy).isAfter(
                    moment(
                      evento.dia + ' ' + hora.format('HH:mm'),
                      'YYYY-MM-DD HH:mm'
                    )
                  ),
                },
              ]"
            >
              <p class="time-slot">
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
                <span class="hora"
                  >{{ item.start | hora }} - {{ item.end | hora }}</span
                >
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
      return moment(datetime).local().format('H:mm')
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
          start: 'Sun Mar 28 2021 08:00:31 GMT+0200',
          end: 'Sun Mar 28 2021 09:00:31 GMT+0200',
        },
        {
          id: 2,
          catId: 1,
          title: 'Título 2',
          author: 'Josh Laudrup',
          avatar: 'https://randomuser.me/api/portraits/lego/4.jpg',
          start: 'Sun Mar 28 2021 08:00:31 GMT+0200',
          end: 'Sun Mar 28 2021 09:00:31 GMT+0200',
        },
        {
          id: 3,
          catId: 1,
          title: 'Título 3',
          author: 'Tom Berenger',
          avatar: 'https://randomuser.me/api/portraits/lego/3.jpg',
          start: 'Sun Mar 28 2021 09:00:31 GMT+0200',
          end: 'Sun Mar 28 2021 10:00:31 GMT+0200',
        },
        {
          id: 4,
          catId: 1,
          title: 'Equipos y Psicología',
          author: 'Benito Floro',
          avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
          start: 'Sun Mar 28 2021 10:00:31 GMT+0200',
          end: 'Sun Mar 28 2021 11:00:31 GMT+0200',
        },
        {
          id: 5,
          catId: 1,
          title: 'Conspiraciones de conscursantes',
          author: 'Jordi Hurtado',
          avatar: 'https://randomuser.me/api/portraits/lego/1.jpg',
          start: 'Sun Mar 28 2021 18:00:31 GMT+0200',
          end: 'Sun Mar 28 2021 19:00:31 GMT+0200',
        },
        {
          id: 5,
          catId: 1,
          title: 'España - Georgia',
          author: 'Tomas Guasch',
          avatar: 'https://randomuser.me/api/portraits/lego/3.jpg',
          start: 'Mon Mar 29 2021 18:00:31 GMT+0200',
          end: 'Mon Mar 29 2021 19:00:31 GMT+0200',
        },
        {
          id: 4,
          catId: 1,
          title: 'Equipos y Psicología',
          author: 'Benito Floro',
          avatar: 'https://randomuser.me/api/portraits/lego/6.jpg',
          start: 'Tue Mar 30 2021 10:00:31 GMT+0200',
          end: 'Tue Mar 30 2021 11:00:31 GMT+0200',
        },
        {
          id: 5,
          catId: 1,
          title: 'Conspiraciones de conscursantes',
          author: 'Jordi Hurtado',
          avatar: 'https://randomuser.me/api/portraits/lego/1.jpg',
          start: 'Tue Mar 30 2021 17:00:31 GMT+0200',
          end: 'Tue Mar 30 2021 18:15:31 GMT+0200',
        },
      ],
    }
  },
  computed: {
    ahora() {
      const h = new Date().getHours()
      // this.scrollTo('.slot-' + h)
      return h
    },
    eventosByDay() {
      const items = this.items
        .filter(
          (x) =>
            moment(x.start).format('YYYYMMDD') >=
            moment(this.hoy).format('YYYYMMDD')
        )
        .reduce((acum, item) => {
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
    moment.locale(['es', 'en'])
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
    this.ini()
    setTimeout(() => {
      this.scrollTo('slot-' + this.ahora)
    })
  },
  methods: {
    eventosByHour(eventos, hora) {
      if (!eventos) return []
      hora = '0' + hora
      hora = hora.substr(-5)
      const h = moment(hora, 'HH:mm').local()
      const h1 = moment(hora, 'HH:mm').local().add(1, 'h')
      return eventos.filter(
        (x) =>
          (moment(x.start).local().format('HH:mm') >= h.format('HH:mm') &&
            h1.format('HH:mm') > moment(x.start).local().format('HH:mm')) ||
          (moment(x.end).local().format('HH:mm') < h1.format('HH:mm') &&
            h.format('HH:mm') < moment(x.end).local().format('HH:mm'))
      )
    },
    moment(date) {
      return moment(date)
    },
    scrollTo(param) {
      const items = document.getElementsByClassName(param)

      if (items.length)
        items[0].scrollIntoView({
          // block: 'start',
          inline: 'center',
          behavior: 'smooth',
        })
    },
    scrollToX(param) {
      const items = document.getElementsByClassName(param)
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
    ini() {
      const ele = document.getElementById('schedule-container')
      ele.style.cursor = 'grab'

      let pos = { top: 0, left: 0, x: 0, y: 0 }

      const mouseDownHandler = function (e) {
        ele.style.cursor = 'grabbing'
        ele.style.userSelect = 'none'

        pos = {
          left: ele.scrollLeft,
          top: ele.scrollTop,
          // Get the current mouse position
          x: e.clientX,
          y: e.clientY,
        }

        document.addEventListener('mousemove', mouseMoveHandler)
        document.addEventListener('mouseup', mouseUpHandler)
      }

      const mouseMoveHandler = function (e) {
        // How far the mouse has been moved
        const dx = e.clientX - pos.x
        const dy = e.clientY - pos.y

        // Scroll the element
        ele.scrollTop = pos.top - dy
        ele.scrollLeft = pos.left - dx
      }

      const mouseUpHandler = function () {
        ele.style.cursor = 'grab'
        ele.style.removeProperty('user-select')

        document.removeEventListener('mousemove', mouseMoveHandler)
        document.removeEventListener('mouseup', mouseUpHandler)
      }

      // Attach the handler
      ele.addEventListener('mousedown', mouseDownHandler)
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
</style>
