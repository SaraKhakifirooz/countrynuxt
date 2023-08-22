<template>
    <div>
        <h1>Home</h1>
        <!-- query Link(optional) :  <NuxtLink to="/city?id=55555">Link parameter</NuxtLink>
       <br>
       parameter :  <NuxtLink to="/city/55555">Link parameter</NuxtLink>
        <br>
        <NuxtLink :to="{
            name: 'city-id',
            params: {
                id: 1234
            }
        }"> Link Go To Input</NuxtLink> -->
        <br>
        <div class="flag_sec">
            <ul>
                <li v-for="(item, i ) in   result  " :key="i">
                    <!-- <NuxtLink to="/flag"> -->
                    <NuxtLink style="border: 2px solid #000;" :to="{
                        name: 'flag',
                        params: {
                            flag: item.name.common,
                            // img: item.flags.png,
                            // ccn3: item.ccn3 // از این همم خواستم استفاده کنم، نوشت این میس شده (miss)
                            // borders: item.borders  /// ?? آاریاه خوانده نشد در لینک
                        },
                    }">
                        <img class="flag" :src="item.flags.png" :alt="item.flags.alt">
                        <span style="color: black;font-weight: bold;">{{ item.name.common }}</span>
                    </NuxtLink>
                </li>
            </ul>
        </div>

    </div>
</template>

<script setup>

const result = await $fetch('https://restcountries.com/v3.1/all').catch((error) => error.data)

console.log(result)
</script>

<style>
.flag_sec {
    position: relative;
    width: 100%;
    height: 100%;
}

.flag_sec ul {
    position: relative;
    display: flex;
    flex-wrap: wrap;
}

.flag_sec ul li {
    position: relative;
    width: 280px;
    height: 150px;
    overflow: hidden;
    border: 1px solid #000;
    margin: 10px;
}

.flag_sec ul li a {
    position: relative;
    width: 100%;
    display: block;
    height: 100%;
}

.flag_sec ul li a img {
    object-fit: cover;
    height: 85%;
    width: 100%;
}
</style>