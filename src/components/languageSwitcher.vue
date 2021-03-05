<template>
  <div>
    <a @click="onLangList">
      <flag class="flagImg" :iso="$i18n.locale"></flag>
      <span class="black--text">{{ $t(`lang_${$i18n.locale}`) }}</span>
    </a>
    <v-menu
        v-model="showLangList"
        :position-x="showLangListX"
        :position-y="showLangListY"
        absolute
        offset-y
        left
        :nudge-bottom="8"
        :nudge-right="0"
        content-class="dropdown right"
    >
      <v-list>
        <template v-for="v in languageList">
          <v-list-item
              v-if="v.code !== $i18n.locale"
              :key="v.code"
              @click="setLocale(v.code)"
          >
            <v-list-item-title >
              <flag class="flagImg" :iso="v.code"></flag>
              {{ $t(`lang_${v.code}`) }}
            </v-list-item-title>
          </v-list-item>
        </template>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
name: "languageSwitcher",
  data: () => ({
    languageList: [
      {code: 'ru', title: 'russian'},
      {code: 'uz', title: 'ozbekcha'},
      {code: 'us', title: 'english'},
    ],
    showLangList: false,
    showLangListX: 0,
    showLangListY: 0,
  }),
  methods: {
    setLocale(locale) {
      import(`../locales/${locale}.json`).then((msg) => {
        this.$i18n.setLocaleMessage(locale, msg)
        this.$i18n.locale = locale
      })
    },
    onLangList(e) {
      e.preventDefault()
      this.showLangList = false
      this.showLangListX = e.target.offsetLeft + 106
      this.showLangListY = e.target.offsetTop + 24
      this.$nextTick(() => {
        this.showLangList = true
      })
    },
  }
}
</script>

<style scoped>
.flagImg {
  border-radius: 10px;
  margin-right: 5px;
  font-size: 20px;
}
</style>
