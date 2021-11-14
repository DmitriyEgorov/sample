<template>
    <div>
        <b-sidebar id="sidebar-1" title="Выберите фильтр:" shadow>
            <div class="px-3 py-2">
                <p>
                    <b-button variant="primary" class="px-5" id="loadDangerButton0">Все зарегистрированные</b-button>
                </p>
                <p>
                    <b-button variant="success" class="px-5" id="loadDangerButton1">Все лицензированные</b-button>
                </p>
                <p>
                    <b-button variant="info" class="px-5" id="loadDangerButton2">Зарегистрированные+ лицензированные</b-button>
                </p>
                <p>
                    <b-button variant="warning" class="px-5" id="loadDangerButton3">Все потенциально вредные</b-button>
                </p>
                <p>
                    <b-button variant="danger" class="px-5" id="loadDangerButton4">Потенциально вредные -Лицензированные</b-button>

                </p>
                <br>
                <p>
                    <b-button variant="info" class="px-5" id="loadFileButton">Скачать файл данных</b-button>

                </p>
            </div>
        </b-sidebar>

        <div class="px-3 py-2">
            <p align="right">
            <b-button v-b-toggle.sidebar-1>Открыть настройки</b-button>
            </p>
        </div>
        <div id="container" style="position:relative">
            <div id="map"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'MainPage',
        props: {
            msg: String
        },
        created() {
        },
        data() {
            return {
                layout:
                    "<div>{{ properties.balloonContentHeader }}</div><div>{{ properties.balloonContentBody }}</div><div>{{ properties.balloonContentFooter }}</div>",
            }
                ;
        },
        async mounted() {
        },
        watch: {},
        methods: {},
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
