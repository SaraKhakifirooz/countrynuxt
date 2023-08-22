<template>
    <div>
        <h1>Flag Details</h1>
        <br>
        <h2>{{ flagInfo.flag }}</h2>

        {{ flagInfo.code }}


        <div style="background-color: aquamarine;">

            <ul>
                <li v-for="(item, i) in resultBorder" :key="i">
                    <h1>
                        All Border Of <span style="color:blue ;border-bottom: 2px solid blue;">{{ item.name.common }}</span> :
                    </h1>
                    <img class="flag" :src="item.flags.img" :alt="item.flags.alt">

                    <div>
                        <span v-for="border in item.borders">
                            {{ border }} 
                            <br>
                        </span>
                    </div>
                </li>
            </ul>
        </div>
        <!-- <h5>{{ flagInfo.ccn3 }}</h5> -->

        <!-- <h4 v-for="b in flagInfo.borders">
            {{ b }}
        </h4> -->
    </div>
</template>

<script setup>

const flagInfo = useRoute().params;
console.log(flagInfo)

const code = ref();

const url = `https://restcountries.com/v3.1/name/${flagInfo.flag}`

const resultBorder = await $fetch(url).catch((error) => error.data)

console.log(url)

</script>

<style>
img.flag {
    width: 280px;
    height: 150px;
    background-color: #ddd;
    display: block;
}
</style>