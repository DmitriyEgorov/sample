<template>
    <div class="hello">
        <yandex-map
                zoom="4"
                style="width: 100%; max-width: 100%; height: 98vh;"
                :coords="coords"
        >
            <ymap-marker
                    v-for="(billboard, index) in surfaces"
                    marker-type="placemark"
                    :balloon-template="mapBalloon(billboard, index)"
                    :coords="billboard.coords.split(',')"
                    :marker-id="index"
                    :icon="{ content: billboard.id }"
                    :key="index"
            ></ymap-marker>
        </yandex-map>
    </div>
</template>

<script>
    /* eslint-disable */
    import { yandexMap, ymapMarker } from "vue-yandex-maps";
    export default {
        name: "HelloWorld",
        components: { yandexMap, ymapMarker },
        data() {
            return {
                coords: [55.099943, 50.706567],
                options: {
                    layout: "default#image",
                    imageSize: [30, 40],
                    contentOffset: [0, 0]
                },
                selectedSurfaces: this.$selectedSurfaces,
                layout:
                    "<div>{{ properties.balloonContentHeader }}</div><div>{{ properties.balloonContentBody }}</div><div>{{ properties.balloonContentFooter }}</div>",
                surfaces: [
                    {
                        id: "<b>Бля</b>, Дима, сколько можно ждать?! Сорян.",
                        city: "Chelyabinsk",
                        type: "Mediawall",
                        address: "Проспект Победы, д.168",
                        side: "A",
                        coords: "55.184901, 61.398493"
                    },
                    {"id":"ООО \"ЛЕРАН\"","city":"Челябинск","type":"Mediawall","address":"ул. Пушкина, д. 65, ПОМЕЩЕНИЕ 6","side":"A","coords":"55.1937143, 61.3648531"}
                ]
            };
        },
        mounted() {
            console.log(this.$selectedSurfaces[0]);
        },
        watch: {
            selectedSurfaces() {
                this.makeSurfaceSelected(
                    this.selectedSurfaces[this.selectedSurfaces.length - 1].SURFACEID
                );
            }
        },
        methods: {
            selectedBillboard(billboard) {
                let data = {
                    SURFACEID: billboard.surface_id,
                    NETWORKID: billboard.networkid
                };
                return data;
            },
            makeSurfaceSelected: function(surface_id) {
                this.surfaces.forEach(surface => {
                    if (surface.surface_id === surface_id) {
                        surface.selected = true;
                    }
                });
            },
            mapBalloon: function(billboard, index) {
                return `
      <div><h1>${billboard.id}</h1>
      <p><strong>City</strong>: ${billboard.city}</p>
      <p><strong>Type</strong>: ${billboard.type}</p>
      <p><strong>Side</strong>: ${billboard.side}</p>
      <p><strong>Address</strong>: ${billboard.address}</p>
      </div>
      `;
            }
        }
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1,
    h2 {
        font-weight: normal;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0;
    }
    a {
        color: #42b983;
    }
</style>
