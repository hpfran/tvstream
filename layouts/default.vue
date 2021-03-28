<template>
  <div class="wrapper" :class="{ collapsed: collapsedSidebar }">
    <div class="box header"><span class="logo">tvstream</span></div>
    <div class="box sidebar">
      <h3>categorías</h3>
      <div class="categorias-tags">
        <span class="tag selected">política</span>
        <span class="tag">deporte</span>
        <span class="tag">gaming</span>
        <span class="tag">forex</span>
        <span class="tag">inversión</span>
        <span class="tag">televisión</span>
      </div>
    </div>

    <Nuxt class="box content" />

    <div class="box footer">&copy; tvstream {{ new Date().getFullYear() }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapsedSidebar: false,
    }
  },
}
</script>

<style lang="scss">
:root {
  --padding: 4rem;
  --border: rgb(0, 0, 0, 0.2);
}
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
.heading {
  line-height: 2;
  font-weight: 900;
}

.section-container {
  padding: 0 1rem 1rem 0;
  a {
    color: var(--main-color);
  }
}

.schedule-container {
  cursor: grab;
  overflow: auto;
}

.schedule-stage__wrapper {
  display: inline-block;
}

.schedule-stage {
  display: grid;
  grid-auto-columns: max-content;
  grid-auto-flow: column;
  grid-gap: 2rem;
  padding-bottom: 5rem;
  padding-top: 2rem;
  min-width: 100vw;

  &::after {
    content: '';
    width: var(--padding);
  }
}

.divider {
  position: sticky;
  left: 0;
  border: none;
  border-bottom: 1px solid var(--border);
}

.schedule-stage:nth-child(1) > .schedule-stage__title > h3 {
  background: rgb(153, 16, 135);
  background: linear-gradient(to right, rgb(156, 41, 141), rgb(161, 10, 141));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.schedule-stage:nth-child(3) > .schedule-stage__title > h3 {
  background: rgb(51, 139, 23);
  background: linear-gradient(to right, #1d976c, #93f9b9);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.schedule-stage__title {
  position: sticky;
  left: 0;
  width: 200px;
  padding-right: 3rem;
  height: 100%;
  padding-left: 1rem;
  background: linear-gradient(to right, #efefef 25%, hsla(0, 0%, 0%, 0));
  & > h3 {
    font-weight: 900;
  }
}

.schedule-stage_guide-container {
  display: grid;
  grid-auto-flow: column;
  grid-auto-columns: 17rem;
  grid-gap: 1.5rem;
}

.guide-slot {
  color: #333;
  & > p {
    margin-bottom: 1rem;
    font-weight: 700;
    color: #666;
    text-align: center;
  }
  &.disabled {
    background: rgba(250, 250, 250, 0.5);
    & .time-slot {
      opacity: 0.5;
    }
  }
}

.guide-slot_card {
  background: #f5f5f5;
  /*border: 1px solid var(--border);*/
  box-shadow: 1px 1px 1px rgba(43, 59, 93, 0.3);
  border-radius: 0.8rem;
  font-size: 1rem;
  margin-bottom: 1rem;
  padding: 1rem;
  cursor: pointer;

  &.selected {
    background: #eedefe;
  }
  &.vip {
    background-color: var(--accent-color);
    color: white;
  }
  &:hover {
    border-color: hsl(0, 0%, 60%);
  }

  & > h4 {
    margin-right: 1rem;
    font-size: 0.9rem;
    width: 100%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

.author-wrapper {
  display: flex;
  align-items: center;
  margin-top: 0.5rem;
  & figcaption {
    font-size: 0.875rem;
  }
  & > picture {
    display: inline-block;
    inline-size: 2rem;
    block-size: 2rem;
    border-radius: 50%;
    overflow: hidden;
    margin-right: 1rem;
    border: 1px solid var(--border);
    & > img {
      inline-size: 100%;
      block-size: 100%;
      object-fit: cover;
    }
  }
}
.categorias-tags {
  display: flex;
  flex-wrap: wrap;
  & .tag {
    padding: 0.25rem 0.8rem;
    margin: 0.5rem;
    font-weight: 500;
    border-radius: 0.5rem;
    background-color: #eee;
    text-overflow: ellipsis;
    &.selected {
      background-color: var(--main-color);
      color: white;
    }
  }
}
</style>
