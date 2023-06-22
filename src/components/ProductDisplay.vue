<script>
    export default {
        name: 'ProductDisplay',
        data() {
            return {
                price: 75,
                amount: 0,
                // subTotal: 0,
                isAmountGreaterThan3: 0
            }
        },
        methods: {
            addToCart() {
                if (this.amount > 3) {
                    this.isAmountGreaterThan3 = 1 
                } else if (this.amount === 0) {
                    this.isAmountGreaterThan3 = 3
                } else if (this.amount <=3) {
                    this.isAmountGreaterThan3 = 2 
                }
            },
            minusAmount() {
                if (!(this.amount <= 0)) {
                    this.amount--
                }
            }
        },
    }
</script>

<template>
    <div class="flex w-full flex-col md:flex-row">
        <div class="w-full md:w-1/2 h-[60vh] md:h-screen md:fixed bg-gray-200 flex justify-center items-center">
            <!-- thumbnail -->
            <img src="../assets/images/sofa.png" alt="sofa thumbnail">
        </div>
        <div class="hidden md:block md:w-1/2 h-[60vh] md:h-screen bg-gray-200">
        </div>
        <div class="w-full md:w-1/2 px-5 md:px-10 py-10 md:py-20 lg:py-10 flex flex-col justify-between">
            <!-- details -->
            <div>
                <!-- title & desc -->
                <h1 class="text-4xl md:text-5xl font-bold">Greyana Sofa</h1>
                <p class="mt-2">
                    Introducing the Greyana Sofa. The perfect combination of style and comfort. With its sleek and modern design, this sofa is a statement piece that will elevate any living space. The Greyana Sofa features a stunning grey upholstery that is both soft to the touch and durable for everyday use. Crafted with a sturdy wooden frame and high-density foam cushions, the Greyana Sofa offers unbeatable comfort and support. The seat and back cushions are also removable and reversible, making it easy to maintain and keep looking like new.
                </p>
            </div>
            <div>
                <!-- price, counter, & bubtton -->
                <div class="text-3xl font-semibold">
                    ${{ price }}
                </div>
                <div class="flex mt-2">
                  <button @click="minusAmount()" class="bg-black text-white px-2">-</button>
                    <div class="border border-black px-5 bg-gray-100">{{ amount }}</div>
                    <button @click="amount++" class="bg-black text-white  px-2">+</button>
                </div>
                <p style="color: #FF0000;" class="text-[#FF0000] mt-1" v-if="isAmountGreaterThan3 === 1">maximum items that can be added is 3</p>
                <p style="color: #1DD000;" class="text-[#1DD000] mt-1" v-if="isAmountGreaterThan3 === 2">successfully added to cart</p>
                <p style="color: #FF0000;" class="text-[#FF0000] mt-1" v-if="isAmountGreaterThan3 === 3">item minimum is 1</p>
                <div class="text-xl font-semibold mt-10">Subtotal: ${{ price * amount }}</div>
                <div class="flex w-full justify-between items-center gap-5 mt-2 mr-5">
                    <button class="text-center w-full bg-black text-white py-4">Buy Now</button>
                    <button @click="addToCart()" class="text-center w-full bg-black text-white py-4">Add To Cart</button>
                </div>
            </div>
        </div>
    </div>
</template>
