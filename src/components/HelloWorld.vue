<template>
    <div class="w-full flex items-center justify-center flex-col">
        <h1 class="text-4xl font-semibold mt-10">{{ msg }}</h1>

        <button @click="showForm = !showForm" class="border-1 border-black pl-4 pr-4 cursor-pointer mt-2">
            Add Post
        </button>

        <div v-if="showForm" class="fixed inset-0 bg-black/50 flex items-center justify-center z-50" @click="closeForm">
            <div class="bg-white w-full max-w-md p-6 rounded-lg shadow-lg" @click.stop>
                <button @click="closeForm" class="absolute top-2 right-2 text-gray-500 hover:text-black">
                    &times;
                </button>

                <h2 class="text-2xl font-semibold mb-4">Create a New Post</h2>

                <input v-model="newPost.img" type="text" placeholder="Image URL" class="w-full p-2 mb-2 border rounded" />
                <input v-model="newPost.title" type="text" placeholder="Post Title" class="w-full p-2 mb-2 border rounded" />
                <textarea v-model="newPost.description" placeholder="Post Description" class="w-full p-2 mb-2 border rounded"></textarea>

                <button @click="addPost" class="mt-2 p-2 bg-blue-500 text-white rounded">
                    Submit Post
                </button>
            </div>
        </div>

        <div class="grid grid-cols-3 mt-[3vh]">
            <div v-for="(item, index) in cards" :key="index" class="w-full max-w-xs mx-4 mb-6 flex items-center justify-center flex-col text-center border border-gray-300 p-4 rounded-lg shadow-lg">
                <img class="w-full h-auto rounded-lg" :src="item.img" :alt="item.alt">
                <h2 class="text-xl font-semibold text-gray-800 mb-2">{{ item.title }}</h2>
                <p class="text-gray-600 text-sm">{{ item.description }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: "Hello, Welcome to Our Gallery",
            showForm: false,
            newPost: {
                img: '',
                title: '',
                description: ''
            },
            cards: [
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Beautiful Landscape",
                    title: "Nature's Beauty",
                    description: "Explore the serene and breathtaking views of nature. Whether it's a quiet forest, a stunning mountain, or a peaceful lake, nature always offers peace and tranquility."
                },
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Coffee and Laptop",
                    title: "Work & Coffee",
                    description: "The perfect combination for productivity – a hot cup of coffee and a laptop to get things done. Whether you're working from home or in a café, coffee fuels your day."
                },
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Mountain Hiking",
                    title: "Mountain Adventures",
                    description: "Hiking up to the peaks and witnessing the world from above. The challenge, the fresh air, and the panoramic views make it all worth it."
                },
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Bicycle Ride",
                    title: "Cycling Journeys",
                    description: "There's nothing quite like feeling the wind in your hair as you cycle through picturesque landscapes, exploring new places and enjoying the freedom of movement."
                },
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Delicious Dish",
                    title: "Foodie's Paradise",
                    description: "Indulge in mouthwatering dishes from all over the world. Food brings us together, and each bite tells a story of culture, tradition, and love."
                },
                {
                    img: "https://static.wixstatic.com/media/11062b_ecc8a610417c4f5fbc5d9c623db4ad1b~mv2.jpg/v1/crop/x_672,y_0,w_2935,h_2855/fill/w_324,h_302,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/Tattooed%20Chef.jpg",
                    alt: "Urban City View",
                    title: "City Life",
                    description: "The bustling energy of city life, with towering buildings, neon lights, and the endless stream of people. There's always something happening in the heart of a metropolis."
                }
            ]
        }
    },
    methods: {
        addPost() {
            if (this.newPost.img && this.newPost.title && this.newPost.description) {
                this.cards.push({
                    img: this.newPost.img,
                    alt: this.newPost.title,
                    title: this.newPost.title,
                    description: this.newPost.description
                });

                this.newPost.img = '';
                this.newPost.title = '';
                this.newPost.description = '';
                this.showForm = false;
            } else {
                alert('Please fill in all fields');
            }
        },
        closeForm() {
            this.showForm = false;
        }
    }
}
</script>
