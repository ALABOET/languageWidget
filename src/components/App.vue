<template>
    <div class="main">
        <div class="select">
            <vue-select :options="languages"
                        :value=placeholderValue
                        @input="onInput"
            >
                <template v-slot:option="option">
                    <component :is="option.icon" style="margin-left: -15px"/>
                    <span style="margin: 0px 9px 0px 0px"></span>
                    {{option.text}}
                </template>
            </vue-select>

            <div class="flags">
                <icon-language style="margin-top: -4px" v-if="placeholderValue==='Change language'"></icon-language>
                <icon-en v-if="placeholderValue==='English'"></icon-en>
                <icon-es v-if="placeholderValue==='Spanish'"></icon-es>
                <icon-por v-if="placeholderValue==='Portuguese'"></icon-por>
                <icon-pl v-if="placeholderValue==='Polish'"></icon-pl>
                <icon-jp v-if="placeholderValue==='Japanese'"></icon-jp>
                <icon-it v-if="placeholderValue==='Italian'"></icon-it>
                <icon-fr v-if="placeholderValue==='French'"></icon-fr>
                <icon-ger v-if="placeholderValue==='German'"></icon-ger>
            </div>
        </div>
        THE JAPANESE JUST ATTACKED PEARL HARBOR! <br>
        WARNING, THIS IS NOT A TRAINING ROOTING, WE ARE UNDER ATTACK<br>
        London is the capital...
    </div>
</template>

<script>

    import 'vue-select/dist/vue-select.css';
    import VueSelect from 'vue-select'
    import iconEn from "@/components/LanguageSelector/icons/iconEn";
    import iconPl from "@/components/LanguageSelector/icons/iconPl";
    import iconGer from "@/components/LanguageSelector/icons/iconGer";
    import iconPor from "@/components/LanguageSelector/icons/iconPor";
    import iconJp from "@/components/LanguageSelector/icons/iconJp";
    import iconFr from "@/components/LanguageSelector/icons/iconFr";
    import iconEs from "@/components/LanguageSelector/icons/iconEs";
    import iconIt from "@/components/LanguageSelector/icons/iconIt";
    import IconLanguage from "@/components/LanguageSelector/icons/iconLanguage";

    export default {
        name: 'App',
        data() {
            return {
                currentFlag: null,
                placeholderValue: 'Change language',
                languages: [
                    {
                        icon: iconEn,
                        text: 'English',
                        value: 'en|en'
                    },
                    {
                        icon: iconFr,
                        text: 'French',
                        value: 'en|fr'
                    },
                    {
                        icon: iconGer,
                        text: 'German',
                        value: 'en|de'
                    },
                    {
                        icon: iconIt,
                        text: 'Italian',
                        value: 'en|it'
                    },
                    {
                        icon: iconJp,
                        text: 'Japanese',
                        value: 'en|ja'
                    },
                    {
                        icon: iconPl,
                        text: 'Polish',
                        value: 'en|pl'
                    },
                    {
                        icon: iconPor,
                        text: 'Portuguese',
                        value: 'en|pt'
                    },
                    {
                        icon: iconEs,
                        text: 'Spanish',
                        value: 'en|es'
                    }]
            }
        },
        methods: {
            onInput(event) {
                window.doGTranslate(event.value);
                this.placeholderValue = event.text
            },
        },
        components: {
            IconLanguage,
            VueSelect, iconIt, iconEs, iconFr, iconJp, iconPor, iconGer, iconPl, iconEn
        }
    }
</script>

<style>
    .main {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        color: #2c3e50;

    }

    .flags {
        position: absolute;
        top: 8px;
        left: 5px;
    }

    .select {
        width: 225px;
        position: relative;
    }

    .vs__clear {
        display: none;
    }

    .vs__selected {
        font-size: 14px;
        color: grey;
    }

    #vs1__listbox {
        font-size: 14px;
    }

    .vs--single .vs__selected {
        margin-left: 23px;
    }


</style>