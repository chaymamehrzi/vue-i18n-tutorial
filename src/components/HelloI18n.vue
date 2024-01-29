<template>
  <div>
    <h1 class="display-4 title">{{ $t("language_select_info") }} :</h1>
    <select v-model="lang" class="form-control minimal">
      <option
        v-for="(lang, i) in languageArray"
        :key="`lang${i}`"
        :value="lang"
      >
        {{ lang }}
      </option>
    </select>
    <div class="mt-4 selected-language">{{ $t("selected_language", { language: selected_language }) }}</div>

    <div class="mt-4 hierarchy">
      <h2 class="h4">{{ $t("instructions") }}</h2>
      <p>{{ $t("instruction_paragraph") }}</p>
    </div>
  </div>
</template>

<script>
import i18n, { languages } from "@/plugins/i18n";

export default {
  name: "HelloI18n",

  data() {
    return {
      languageArray: languages,
      languagesMap: {
        en: "English",
        fr: "French",
        hi: "Hindi",
        de: "German",
      },
    };
  },

  computed: {
    lang: {
      get: function () {
        return this.$store.state.locale;
      },
      set: function (newLocale) {
        this.$store.dispatch("changeLocale", newLocale);
      },
    },

    selected_language() {
      return this.$t(this.languagesMap[this.lang]);
    },
  },

  created() {
    i18n.locale = this.$store.state.locale;
  },
};
</script>

<i18n>
{
  "en": {
    "language_select_info": "Select the language you want to use",
    "selected_language": "You have selected {language}",
    "instructions": "Instructions",
    "instruction_paragraph": "Please follow these instructions carefully."
  },
  "hi": {
    "language_select_info": "उस भाषा का चयन करें जिसका आप उपयोग करना चाहते हैं",
    "selected_language": "आपने {language} का चयन किया है",
    "instructions": "निर्देश",
    "instruction_paragraph": "कृपया इन निर्देशों का ध्यानपूर्वक पालन करें।"
  },
  "fr": {
    "language_select_info": "Sélectionnez la langue que vous souhaitez utiliser",
    "selected_language": "Vous avez sélectionné {language}",
    "instructions": "Instructions",
    "instruction_paragraph": "Veuillez suivre attentivement ces instructions."
  },
  "de": {
    "language_select_info": "Wählen Sie die Sprache aus, die Sie verwenden möchten",
    "selected_language": "Sie haben {language} ausgewählt",
    "instructions": "Anweisungen",
    "instruction_paragraph": "Bitte folgen Sie diesen Anweisungen sorgfältig."
  }
}
</i18n>

<style scoped>
.title {
  color: #009688; 
}

.minimal {
  background-color: #f0f4c3; 
  border-color: #aed581; 
}

.selected-language {
  margin-top: 30px;
  font-size: 18px;
  color: #ff5722; 
}

.hierarchy {
  margin-top: 30px;
  font-size: 16px;
  color: #795548; 
}

.hierarchy ul {
  list-style-type: none;
}

.hierarchy ul ul {
  margin-top: 10px;
}

.hierarchy ul ul ul {
  margin-top: 10px;
}

.h4 {
  font-size: 1.5rem;
  margin-top: 1.5rem;
}

.list-unstyled {
  padding-left: 0;
  list-style: none;
}
</style>
