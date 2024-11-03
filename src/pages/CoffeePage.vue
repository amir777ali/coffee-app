<template>
  <div class="container">
    <main id="HOME">
      <div class="p1">
        <h2 class="text-weight-bolder">
          Start your day <br />
          with a black <span class="text-efect">coffee</span>
        </h2>
        <p>
          choose and taste delicious coffee <br />
          from the best beans
        </p>
        <div class="btns">
          <a href="#PRODUCTS"><button class="btn1">Order Now</button></a>
          <a href="#ABOUT"><button class="btn2">Learn About Us</button></a>
        </div>
      </div>
      <div class="p2">
        <img src="/images/cup.png" alt="" style="width: 750px" />
      </div>
    </main>

    <div class="basket-cart" :style="{ right: w1 }">
      <div class="pro-wrapper" :style="{ right: w1 }">
        <div class="top">
          <i class="fa-solid fa-xmark" @click="hideCart()"></i>
          <h3>YOUR CART</h3>
        </div>
        <div class="pro" v-for="(product, index) in basket" :key="index">
          <div class="des">
            <div class="t">
              <img :src="`/images/${basket[index].pic}.jpg`" alt="" />
              <h5>{{ basket[index].name }}</h5>
            </div>
            <h5>${{ basket[index].price * basket[index].counter }}</h5>
          </div>
          <div class="counter">
            <i
              class="fa fa-minus"
              aria-hidden="true"
              @click="removeP(index)"
            ></i>
            <span> {{ basket[index].counter }} </span>
            <i
              class="fa fa-plus"
              aria-hidden="true"
              @click="basket[index].counter++"
            ></i>
          </div>
        </div>
      </div>
    </div>

    <section id="PRODUCTS" v-for="(topic, k) in topics" :key="k">
      <h2>{{ k }}</h2>
      <div class="p-container">
        <i class="fa fa-arrow-left" aria-hidden="true"></i>
        <div class="p-box" v-for="(popular, k2) in topic" :key="k2">
          <img :src="`/images/${popular.pic}.jpg`" alt="" />
          <div class="des">
            <h4>{{ popular.name }}</h4>
            <p>{{ popular.des }}</p>
            <div class="pb">
              <h4 class="price">${{ popular.price }}</h4>
              <button>
                <q-icon name="add" @click="addToCart(k2, topic)" />
              </button>
            </div>
          </div>
        </div>
      </div>
      <i class="fa fa-arrow-right" aria-hidden="true"></i>
    </section>

    <article id="ABOUT">
      <h2>About Us</h2>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Repudiandae
        totam expedita dolorum!
      </p>
      <h3>About</h3>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Cupiditate,
        aspernatur! Expedita laboriosam in quas ipsam possimus repellendus est,
        dolores molestiae quaerat. Accusamus, labore iusto. Distinctio, fugit
        qui incidunt consequatur voluptatibus voluptatum exercitationem quasi
        excepturi aspernatur! Doloremque, error. Doloribus eaque dolores hic
        tempore suscipit est incidunt molestias, dolor facere, modi magnam.
      </p>
      <h3>Compony</h3>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Distinctio
        veritatis enim voluptatem adipisci placeat possimus totam magni odit
        commodi eius tenetur officia, quaerat dicta vel officiis aspernatur
        delectus, architecto dolore fugit fugiat consequatur illo accusamus
        quibusdam illum. Iusto pariatur animi molestiae obcaecati sint quisquam
        velit aspernatur placeat. Amet laboriosam minima assumenda quaerat vel!
        Perspiciatis tenetur temporibus numquam ipsa? Animi nobis repudiandae
        ipsam nesciunt ullam est magni quasi rerum nisi necessitatibus mollitia
        asperiores atque eius quisquam illum ea dolor recusandae ex, porro sint
        quidem quo quam incidunt excepturi! Eum placeat omnis ab facilis, animi
        numquam velit porro, sit earum excepturi dolorum.
      </p>
      <h3>Shop</h3>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Cupiditate,
        aspernatur! Expedita laboriosam in quas ipsam possimus repellendus est,
        dolores molestiae quaerat. Accusamus, labore iusto. Distinctio, fugit
        qui incidunt consequatur voluptatibus voluptatum exercitationem quasi
        excepturi aspernatur! Doloremque, error. Doloribus eaque dolores hic
        tempore suscipit est incidunt molestias, dolor facere, modi magnam.
      </p>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Recusandae,
        distinctio!
      </p>
    </article>

    <footer id="CONTACT-US">
      <div class="sec">
        <h4>Popular Products</h4>
        <a href="">Coffee Beans</a>
        <a href="">Latte</a>
        <a href="">Milk</a>
        <a href="">test</a>
      </div>
      <div class="sec">
        <h4>Names</h4>
        <a href="">Amir</a>
        <a href="">Reza</a>
        <a href="">Mohamad</a>
        <a href="">ALi</a>
      </div>
      <div class="sec">
        <h4>CONTACT</h4>
        <a href="">
          <i class="fa fa-phone" aria-hidden="true"> </i> : +98 09922006252</a
        >
        <a href=""
          ><i class="fa fa-envelope" aria-hidden="true"></i> :
          amir.hkh77.ali@gmail.com</a
        >
        <a href=""
          ><i class="fas fa-map-marker-alt" aria-hidden="true"></i> :
          Tehran-Iran</a
        >
      </div>
    </footer>
    <p style="color: gray; text-align: center; text-decoration: underline">
      تمامی حقوق این صفحه متعلق به بنده است ©
    </p>
  </div>
</template>

<script setup>
import { ref } from "vue";
// import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css";

const basket = JSON.parse(localStorage.getItem("basket")) || [];
const w1 = ref("-450px");
const productAdded = ref({});
const topics = {
  populars: {
    product1: {
      name: "Esperesso Coffee",
      des: "with milk",
      price: 5.0,
      pic: "E",
      counter: 0,
    },
    product2: {
      name: "Latte Coffee",
      des: "with milk",
      price: 7.5,
      pic: "L",
      counter: 0,
    },
    product3: {
      name: "Cappuccino Coffee",
      des: "with chocolate",
      price: 6.2,
      pic: "C",
      counter: 0,
    },
  },
  bestSellers: {
    product1: {
      name: "americano Coffee",
      des: "with milk",
      price: 10.3,
      pic: "A",
      counter: 0,
    },
    product2: {
      name: "macchiato Coffee",
      des: "with cream",
      price: 8.5,
      pic: "M",
      counter: 0,
    },
    product3: {
      name: "mocha Coffee",
      des: "with oat milk",
      price: 11.2,
      pic: "MC",
      counter: 0,
    },
  },
};
const showCart = () => {
  w1.value = "0";
};

const hideCart = () => {
  w1.value = "-450px";
};
const addToCart = (k, topic) => {
  const product = topic[k];
  productAdded.value = topic[k];

  if (basket.includes(product)) {
    basket.filter((item) => item !== product);
    alert(`${product.name} already exist!`);
    console.log(product.name);
  } else {
    basket.push(product);
    product.counter = 1;
    alert(`${product.name} added to basket!`);
  }

  localStorage.setItem("basket", JSON.stringify(basket));
};

const removeP = (index) => {
  if (basket[index].counter === 1) {
    basket.splice(index, 1);
  } else {
    basket[index].counter--;
  }
  localStorage.setItem("basket", JSON.stringify(basket));
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
  list-style: none;
  text-decoration: none;
  font-family: "Poppins", sans-serif;
  font-optical-sizing: auto;
  font-style: normal;
  border: none;
}
:root {
  --bg-color: #000000;
  --btn: #cb863f;
  --border: #6c4620;
  --white: #ffffff;
  --text-gray: #9e9e9e;
  --bg-gray: #424242;
  --bg-s-gray: #616161;
}
body {
  background-color: var(--bg-color);
  position: relative;
  overflow: auto;
}

.container {
    width: 1500px;
    max-width: 1500px;
    height: 100vh;
    margin: 0 auto;
    /* border: solid 5px red; */
}

main {
  position: relative;
  margin-top: 50px;
  color: var(--white);
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 100px;
}

main h2 {
  font-size: 65px;
  word-spacing: 5px;
  letter-spacing: 1px;
  margin-bottom: 30px;
  line-height: 90px;
}

main p {
  font-size: 20px;
  color: var(--text-gray);
  word-spacing: 3px;
  letter-spacing: 0.5px;
  line-height: 30px;
  margin-bottom: 30px;
}

.text-efect {
  background: -webkit-linear-gradient(62deg, #fbab7e 20%, #f7ce68 80%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
.text-efect:hover {
  background: -webkit-linear-gradient(62deg, #f7ce68 20%, #fbab7e 80%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

main .btns {
  display: flex;
  gap: 50px;
}
main .btns .btn1 {
  color: var(--white);
  background-color: var(--btn);
  border: 1px solid var(--btn);
  padding: 5px;
  height: 40px;
  width: 150px;
  border-radius: 2px;
  font-size: 16px;
  cursor: pointer;
  transition: 0.5s;
}
main .btns .btn1:active {
  color: var(--btn);
  border: 1px solid var(--border);
  background: none;
}
main .btns .btn2 {
  color: var(--btn);
  border: 1px solid var(--border);
  background: none;
  height: 41px;
  padding: 5px;
  width: 150px;
  border-radius: 2px;
  font-size: 16px;
  cursor: pointer;
  transition: 0.5s;
}
main .btns .btn2:active {
  color: var(--white);
  background-color: var(--btn);
  border: none;
}

section {
  height: 300px;
  border: 3px solid var(--border);
  border-radius: 3px;
  margin-bottom: 50px;
  text-align: center;
}

section .p-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 10px;
}

section .p-container i {
  color: var(--btn);
  font-size: 20px;
  cursor: pointer;
}

section h2 {
  color: var(--white);
  margin-top: 10px;
  font-size: 36px;
  margin: 30px auto 30px;
}

section .p-box {
  display: flex;
  gap: 30px;
  background: linear-gradient(
    51deg,
    rgba(66, 66, 66, 1) 0%,
    rgba(33, 33, 33, 1) 20%,
    rgba(33, 33, 33, 1) 100%
  );
  box-shadow: rgba(17, 17, 26, 0.1) 0px 0px 16px;
  border-radius: 3px;
  width: 400px;
  height: 150px;
  text-align: left;
  padding: 10px;
  position: relative;
}
section .p-box::before {
  content: "";
  background: linear-gradient(
    51deg,
    rgba(33, 33, 33, 1) 29%,
    rgba(66, 66, 66, 1) 47%,
    rgba(33, 33, 33, 1) 80%
  );
  border-radius: 3px;
  top: 0;
  right: 0;
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: 0.4s;
}
section .p-box:hover::before {
  opacity: 1;
}

section .p-box .des {
  line-height: 40px;
  z-index: 2;
}

section .p-box h4 {
  color: var(--white);
  word-spacing: 5px;
  z-index: 2;
  font-size: 22px;
}

section .p-box p {
  color: var(--text-gray);
  font-size: 20px;
  margin-bottom: 15px;
}

section .p-box .price {
  color: var(--white);
  letter-spacing: 3px;
  font-size: 26px;
  color: var(--btn);
  z-index: 2;
}
section .p-box img {
  width: 100px;
  height: 100px;
  border-radius: 50px;
  border: 5px solid var(--border);
  z-index: 2;
  margin-top: 10px;
}

section .p-box .pb {
  display: flex;
  gap: 50px;
  align-items: center;
}

section .p-box .pb button {
  background: none;
  color: var(--btn);
  font-size: 18px;
  width: 20px;
  height: 20px;
}
section .p-box .pb button i {
  transition: ease 0.2s;
}
section .p-box .pb button i:active {
  transform: scale(1.1);
  color: #9e9e9e;
}

article {
  margin-top: 100px;
  width: 1100px;
  margin: 0 auto;
}

article h2 {
  color: var(--white);
  font-size: 36px;
  margin-bottom: 50px;
  text-align: center;
}

article h3 {
  color: var(--white);
  font-size: 20px;
  margin-bottom: 10px;
}

article p {
  color: var(--white);
  margin: 15px auto 30px;
  text-align: justify;
  line-height: 25px;
}

footer {
  display: flex;
  justify-content: space-around;
  padding: 20px;
  border-top: 3px solid var(--border);
  margin: 100px auto 20px;
}

footer .sec h4 {
  color: var(--white);
  font-size: 20px;
}
footer .sec a {
  display: block;
  color: var(--text-gray);
  margin-top: 5px;
  font-size: 14px;
}
footer .sec:last-child a {
  margin-top: 10px;
}

.basket-cart .pro-wrapper {
  position: fixed;
  height: 100%;
  width: 450px;
  top: 0;
  bottom: 0;
  border-left: 3px solid var(--border);
  background-color: var(--bg-color);
  overflow-y: auto;
  z-index: 1000;
  transition: 0.5s;
}
.basket-cart .pro-wrapper .top {
  background-color: var(--border);
  color: var(--white);
  display: flex;
  align-items: center;
  gap: 150px;
  padding: 5px;
  cursor: pointer;
  transition: 0.3s;
}

.basket-cart .pro-wrapper .top i:active {
  color: var(--btn);
}

.basket-cart .pro-wrapper .pro {
  width: 430px;
  height: 125px;
  border: 3px solid var(--btn);
  background-color: var(--bg-gray);
  color: var(--white);
  margin: 10px auto;
  padding: 10px;
  border-radius: 5px;
}

.basket-cart .pro-wrapper .pro .des .t {
  display: flex;
  gap: 20px;
}
.basket-cart .pro-wrapper .pro .des .t img {
  width: 70px;
  border-radius: 50px;
  border: 3px solid var(--btn);
}
.basket-cart .pro-wrapper .pro .des {
  display: flex;
  justify-content: space-between;
  text-align: center;
  margin: 5px 15px 0px 0;
  font-size: 24px;
  letter-spacing: 1px;
}

.basket-cart .pro-wrapper .pro .counter {
  display: flex;
  gap: 16px;
  text-align: center;
  align-items: baseline;
  justify-content: center;
  font-weight: 600;
  margin: 0 auto;
  padding: 1px 2px;
  color: var(--btn);
  background: none;
  border: 2px solid var(--btn);
  border-radius: 5px;
  width: 100px;
}

.basket-cart .pro-wrapper .pro .counter i {
  cursor: pointer;
  transition: ease 0.3s;
}

.basket-cart .pro-wrapper .pro .counter i:hover {
  color: var(--white);
}
</style>
