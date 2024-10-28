<script setup lang="ts">
const timelineList = [
    {
        time: '2022 - Present',
        corporate: {
            name: 'LMN Pictures',
            location: 'Jakarta, Indonesia'
        },
        role: 'Senior FX Artist / TD',
        projects: ['Muromachi Burai (室町無頼)', 'Kabut Berduri', 'Nightmare & Daydreams', 'LEMBAYUNG', 'Siksa Kubur', 'LEGO DREAMZzz Night of The Never Witch', 'Moving']
    },

    {
        time: '2021 - 2022',
        corporate: {
            name: 'Lumine Studio',
            location: 'Jakarta, Indonesia'
        },
        role: 'Junior FX Artist',
        projects: ['Little Angel : Nursery Rhymes & Kids Songs', 'Johny Walker Blue Label 3D Videotron Ads', 'CIMB NIAGA 3D Videotron Ads', 'Mary', 'Sri Asih (Disney+)', 'Tira And The Nine Dragon (Disney+)', 'Moving (무빙) (Disney+)']
    },

    {
        time: '2018 - 2020 ',
        corporate: {
            name: 'RUS ANIMATION STUDIO',
            location: 'Kudus, Jawa Tengah'
        },
        role: 'Intern FX Artist ',
        projects: ['Little Angel : Nursery Rhymes & Kids Songs', 'Petualangan Olla Ello', 'GooGoo Space Journey', 'Sabda Alam', 'Internal VR Project']
    },

]


</script>
<template>

    <div class="w-full min-h-svh bg-gray-50 px-4 py-6 flex items-center justify-center">
        <ol class="relative border-s border-gray-200 dark:border-gray-700 w-full min-h-svh flex flex-col">
            <li class="my-4 mx-4 border p-4 rounded-xl" v-for="item in timelineList">
                <div
                    class="absolute w-3 h-3 bg-gray-200 rounded-full mt-1.5 -start-1.5 border border-white dark:border-gray-900 dark:bg-gray-700">
                </div>
                <time class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{{ item.time
                    }}</time>
                <h4 class="text-xs text-gray-400">{{ item.corporate.name }} - {{ item.corporate.location }}</h4>
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{ item.role }}</h3>
                <ul class="list-disc list px-4 text-xs">
                    <li v-for="p in item.projects">{{ p }}</li>
                </ul>

            </li>
        </ol>
    </div>


</template>