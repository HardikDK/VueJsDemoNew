<template>

    <div class="modal" v-if="isOpen">

        <div>
            <div class="topmodal">
                <button @click="isOpen = false">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M6.2253 4.81108C5.83477 4.42056 5.20161 4.42056 4.81108 4.81108C4.42056 5.20161 4.42056 5.83477 4.81108 6.2253L10.5858 12L4.81114 17.7747C4.42062 18.1652 4.42062 18.7984 4.81114 19.1889C5.20167 19.5794 5.83483 19.5794 6.22535 19.1889L12 13.4142L17.7747 19.1889C18.1652 19.5794 18.7984 19.5794 19.1889 19.1889C19.5794 18.7984 19.5794 18.1652 19.1889 17.7747L13.4142 12L19.189 6.2253C19.5795 5.83477 19.5795 5.20161 19.189 4.81108C18.7985 4.42056 18.1653 4.42056 17.7748 4.81108L12 10.5858L6.2253 4.81108Z"
                            fill="red" />
                    </svg>
                </button>
                <div class="cartIcon">
                    <svg width="40" height="40" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M5 4H19C19.5523 4 20 4.44771 20 5V19C20 19.5523 19.5523 20 19 20H5C4.44772 20 4 19.5523 4 19V5C4 4.44772 4.44771 4 5 4ZM2 5C2 3.34315 3.34315 2 5 2H19C20.6569 2 22 3.34315 22 5V19C22 20.6569 20.6569 22 19 22H5C3.34315 22 2 20.6569 2 19V5ZM12 12C9.23858 12 7 9.31371 7 6H9C9 8.56606 10.6691 10 12 10C13.3309 10 15 8.56606 15 6H17C17 9.31371 14.7614 12 12 12Z"
                            fill="var(--secondary)" />
                    </svg>
                </div>
                <div class="details">
                    <h2><strong> 
                        <!-- MON PANIER  -->
                        MY WISH
                    </strong></h2>
                    <p style="color: gray;"> 
                        <!-- À noter qu'aucun article ne sera retourné au delà de 30 jours à compter de la date de livraison effective. --> 
                        <!-- Note that no item will be returned beyond 30 days from the actual delivery date. -->
                    </p>
                    <p style="color: gray;"> 
                        <!-- Conctactez le <a href="">service client</a> pour toute information
                        supplémentaire -->
                        Contact <a href="">customer service</a> for any additional information
                    </p>
                </div>
            </div>
            <hr>
            <!-- {{store_wish.items}} -->
            <div class="empty" v-if="store_wish.items.length === 0">
                <img src="@/assets/empty.svg" alt="Empty wish">
                <h4 style="color: var(--secondary);"> Your wish is empty </h4>
                <small> Add somthing to make me happy for real :-) </small>
            </div>
            <!-- <modalCard v-for="item_in_cart in cart_products.data" :image="item_in_cart.thumbnail"
                :quantity="item_in_cart.number" :computedPrice="item_in_cart.number * item_in_cart.price">
                {{ item_in_cart.title }}
                <template v-slot:reduceQuantity>
                    <button class="handleQuantity" @click="reduceQuantity(item_in_cart)"> - </button>
                </template>
                <template v-slot:addQuantity>
                    <button class="handleQuantity" @click="addQuantity(item_in_cart)"> + </button>
                </template>
                <template v-slot:btnDelete>
                    <svg @click="deleteItem(item_in_cart)" class="trashIcon" width="24" height="24" viewBox="0 0 24 24"
                        fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M17 5V4C17 2.89543 16.1046 2 15 2H9C7.89543 2 7 2.89543 7 4V5H4C3.44772 5 3 5.44772 3 6C3 6.55228 3.44772 7 4 7H5V18C5 19.6569 6.34315 21 8 21H16C17.6569 21 19 19.6569 19 18V7H20C20.5523 7 21 6.55228 21 6C21 5.44772 20.5523 5 20 5H17ZM15 4H9V5H15V4ZM17 7H7V18C7 18.5523 7.44772 19 8 19H16C16.5523 19 17 18.5523 17 18V7Z"
                            fill="currentColor" />
                        <path d="M9 9H11V17H9V9Z" fill="currentColor" />
                        <path d="M13 9H15V17H13V9Z" fill="currentColor" />
                    </svg>
                </template>
            </modalCard> -->

            <!-- <modalCard v-for="item_in_cart in cart_products.data" :image="item_in_cart.thumbnail"
                :quantity="item_in_cart.number" :computedPrice="item_in_cart.number * item_in_cart.price">
                {{ item_in_cart.title }}
                <template v-slot:reduceQuantity>
                    <button class="handleQuantity" @click="reduceQuantity(item_in_cart)"> - </button>
                </template>
                <template v-slot:addQuantity>
                    <button class="handleQuantity" @click="addQuantity(item_in_cart)"> + </button>
                </template>
                <template v-slot:btnDelete>
                    <svg @click="deleteItem(item_in_cart)" class="trashIcon" width="24" height="24" viewBox="0 0 24 24"
                        fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M17 5V4C17 2.89543 16.1046 2 15 2H9C7.89543 2 7 2.89543 7 4V5H4C3.44772 5 3 5.44772 3 6C3 6.55228 3.44772 7 4 7H5V18C5 19.6569 6.34315 21 8 21H16C17.6569 21 19 19.6569 19 18V7H20C20.5523 7 21 6.55228 21 6C21 5.44772 20.5523 5 20 5H17ZM15 4H9V5H15V4ZM17 7H7V18C7 18.5523 7.44772 19 8 19H16C16.5523 19 17 18.5523 17 18V7Z"
                            fill="currentColor" />
                        <path d="M9 9H11V17H9V9Z" fill="currentColor" />
                        <path d="M13 9H15V17H13V9Z" fill="currentColor" />
                    </svg>
                </template>
            </modalCard> -->
            <!-- {{ item_in_wish.items.product }} -->
            <!-- {{ item_in_wish.items }} -->
            <!-- {{ item_in_wish }} -->
            <modalCard v-for="item_in_wish in store_wish.items" :image="item_in_wish.item ? item_in_wish.item.thumbnail : item_in_wish.product.thumbnail"
                :quantity="item_in_wish.number ? item_in_wish.number : item_in_wish.quantity" :computedPrice="item_in_wish.product.price" :id="'product-'+item_in_wish.productId">
                <!-- {{ item_in_wish.product }} -->
                <!-- {{ item_in_wish.item.title }} -->
                <div v-if="item_in_wish.item">
                    {{ item_in_wish.item.title }}
                </div>
                <div v-else>
                    {{ item_in_wish.product.title }}
                </div>
                <div>
                    <span :id="'stock-'+index" v-if="item_in_wish.product.stock < 2">
                        Out of Stock
                    </span>
                </div>
                <!-- <template v-slot:reduceQuantity>
                    <button class="handleQuantity" @click="reduceQuantity(item_in_wish)"> - </button>
                </template>
                <template v-slot:addQuantity>
                    <button class="handleQuantity" @click="addQuantity(item_in_wish)"> + </button>
                </template> -->
                <template v-slot:btnDelete>
                    <svg @click="deleteItem(item_in_wish)" class="trashIcon" width="24" height="24" viewBox="0 0 24 24"
                        fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd"
                            d="M17 5V4C17 2.89543 16.1046 2 15 2H9C7.89543 2 7 2.89543 7 4V5H4C3.44772 5 3 5.44772 3 6C3 6.55228 3.44772 7 4 7H5V18C5 19.6569 6.34315 21 8 21H16C17.6569 21 19 19.6569 19 18V7H20C20.5523 7 21 6.55228 21 6C21 5.44772 20.5523 5 20 5H17ZM15 4H9V5H15V4ZM17 7H7V18C7 18.5523 7.44772 19 8 19H16C16.5523 19 17 18.5523 17 18V7Z"
                            fill="currentColor" />
                        <path d="M9 9H11V17H9V9Z" fill="currentColor" />
                        <path d="M13 9H15V17H13V9Z" fill="currentColor" />
                    </svg>
                </template>
            </modalCard>
            <div class="total" v-if="store_wish.items.length !== 0">
                <h5> Total <span class="amount"> {{ total }}€ </span> </h5>
            </div>
            <div class="promo" v-if="store_wish.items.length !== 0">
                <!-- <input type="checkbox" class="isActive" id="ring" name="ring" value="ring" @click="fetchData('ring')"> <label for="ring">Rings</label><br> -->
                <span><input type="checkbox" v-model="have_promo"> I have a promo code </span><br>
                <input type="text" v-if="have_promo" placeholder="Code promo" v-model="promo_value"
                    @input="check_promo_code">
            </div>

            <button class="pay" @click="goPayement" v-if="store_wish.items.length !== 0">
                <svg class="iconLock" width="24" height="24" viewBox="0 0 24 24" fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd" clip-rule="evenodd"
                        d="M18 10.5C19.6569 10.5 21 11.8431 21 13.5V19.5C21 21.1569 19.6569 22.5 18 22.5H6C4.34315 22.5 3 21.1569 3 19.5V13.5C3 11.8431 4.34315 10.5 6 10.5V7.5C6 4.18629 8.68629 1.5 12 1.5C15.3137 1.5 18 4.18629 18 7.5V10.5ZM12 3.5C14.2091 3.5 16 5.29086 16 7.5V10.5H8V7.5C8 5.29086 9.79086 3.5 12 3.5ZM18 12.5H6C5.44772 12.5 5 12.9477 5 13.5V19.5C5 20.0523 5.44772 20.5 6 20.5H18C18.5523 20.5 19 20.0523 19 19.5V13.5C19 12.9477 18.5523 12.5 18 12.5Z"
                        fill="currentColor" />
                </svg>
                Make payment
            </button>
        </div>
    </div>

</template>

<script setup>
import { onMounted, ref, inject, watchEffect, watch } from 'vue';
import modalCard from './modalCard.vue';
import { useWish } from '@/store/wish.store.js'
import { element_index_in_array } from '@/services/utils/utils'
import axios from 'axios';

let limit = ref(0);
// let productId = ref(0);
let totalProducts = ref(0);
let length = ref(0);
let items = ref([]);
// let columns = ref([]);
let totalProductsLimit = ref(0);

let wish_products = ref([]);
const store_wish = useWish()
const isOpen = inject('dataModalWish')
// let productId = store_wish.productId;

const have_promo = ref(false)
const total = ref(0)
const promo_value = ref("")

const deleteItem = (e) => {
    // console.log(e)
    // console.log(e.id)
    // let id = e.product[0].id;
  if (!localStorage.jwtToken) {
    store_wish.delete_item(element_index_in_array(JSON.parse(JSON.stringify(store_wish)).items, e))
    $('#wish-'+e.id).trigger();
    // console.log($('#wish'))
    // console.log($('#deleteItem').attr('fill'))
    // console.log($('#deleteItem').attr('fillsvg'))
  } else {
    // alert(e.id)
    axios
    .delete(`http://localhost:3001/api/wishes/removefromwishes/${e.id}`)
    .then(function(response) {
        store_wish.items.map(e => e.id)
        store_wish.length = store_wish.items.length;
        store_wish.delete_item(element_index_in_array(JSON.parse(JSON.stringify(store_wish)).items, e))
    })
    .catch(function(error) {
        console.error(error)
    })
  }
}

wish_products.value = store_wish.getItems ? store_wish.getItems : store_wish.items;
watchEffect(() => {
 // console.log(`store_wish.total_amount() ${store_wish.total_amount()}`)
    // total.value = store_wish.total_amount() != 0 ? store_wish.total_amount().toFixed(2) : store_wish.total_amount()
    total.value = store_wish.total_amount().toFixed(2)
 // console.log(isOpen + "zfzfzefzefez")
})
const goPayement = () => {}
</script>

<style scoped>
.modal {
    z-index: 9999;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.568);
    overflow-y: hidden;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal>div {
    background-color: #fff;
    width: 60%;
    height: 90%;
    padding: 50px;
    border-radius: 10px;
    overflow-y: scroll;
    position: relative;

}

.topmodal {
    display: inline-flex;
    flex-direction: row;
    gap: 25px;
}

.topmodal button {
    cursor: pointer;
    position: absolute;
    top: 30px;
    right: 30px;
    width: 40px;
    height: 40px;
    border: 1px solid var(--secondary);
    border-radius: 50%;
    background-color: transparent;
}

.empty {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
}

.empty img {
    height: 150px;
}

.empty h4 {
    margin-top: 40px;
}

.cartIcon {
    flex-basis: 200px;
    width: 120px;
    height: 90px;
    background-color: transparent;
    display: grid;
    place-items: center;
}

.details {
    width: 60%;
}

hr {
    margin: 40px 0px;
    border-top: 0px;
    border-color: var(--fourth);
}

.trashIcon {
    margin: 0px 25px;
}

.trashIcon:hover {
    cursor: pointer;
    color: var(--secondary);
}

.handleQuantity {
    padding: 8px 15px;
    border: 1px solid var(--secondary);
    color: var(--secondary);
    background-color: transparent;
    transition: all 100ms;
}

.handleQuantity:hover {
    cursor: pointer;
    border: 1px solid var(--secondary);
    background-color: var(--secondary);
    color: white;
}

.promo {
    padding: 5px;
    width: 30%;
}

.promo input[type="text"] {
    padding: 0px 20px;
    border: 1px solid var(--secondary);
    border-radius: 5px;
    outline: none;
    height: 50px;
}

.total {
    float: inline-end;
    padding: 25px 0px;
}

.amount {
    border: 1px solid transparent;
    border-radius: 10px;
    background-color: var(--fourth);
    color: var(--secondary);
    padding: 10px 20px;
    margin: 0px 15px;
    font-weight: bolder;
    font-size: 1.3em;
}

.pay {
    border: 1px solid var(--secondary);
    border-radius: 10px;
    background-color: var(--secondary);
    color: white;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 12px 0px;
    transition: all 150ms;
}

.pay:hover {
    cursor: pointer;
    border: 1px solid var(--secondary);
    background-color: transparent;
    color: var(--secondary);
}

.pay .iconLock {
    margin: 0px 15px;
}
</style>