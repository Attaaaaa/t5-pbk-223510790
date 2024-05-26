<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-brown-10 text-red">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title class="q-ml-md">
          <span class="q-ml-sm text-h5">SAVAGE.CO</span>
        </q-toolbar-title>
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/home" label="Home" />
        <q-route-tab to="/top-seller" label="Top Seller" />
        <q-route-tab to="/about" label="About Us" />
      </q-tabs>
    </q-header>

    <!-- Drawer -->
    <q-drawer v-model="leftDrawerOpen" side="left" bordered>
      <q-scroll-area class="fit">
        <q-list padding class="menu-list">
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="mail" />
            </q-item-section>
            <q-item-section class="text-black"> Inbox </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="star" />
            </q-item-section>
            <q-item-section class="text-black"> Favorites </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="send" />
            </q-item-section>
            <q-item-section class="text-black"> Sent </q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="drafts" />
            </q-item-section>
            <q-item-section class="text-black"> Drafts </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <!-- Page Container -->
    <q-page-container>
      <q-page class="q-pa-md">
        <!-- Hero Section -->
        <section class="q-pb-xl q-pt-md bg-brown text-white text-center">
          <h1 class="text-h2 q-mb-md">Welcome to Savage.co</h1>
          <p class="text-subtitle1 q-mb-lg">Find the best deals on the latest trendy style on our store.</p>
          <q-btn label="Shop Now" color="brown" class="q-mt-lg" size="lg" />
        </section>

        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          animated
          infinite
          control-color="white"
          arrows
          navigation
          navigation-position="bottom"
          swipeable
        >
          <q-carousel-slide
            name="1"
            img-src="https://savagefitness.com.au/cdn/shop/products/Stickers2022-03.png?v=1662789654&width=1946"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              Best Deals!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="2"
            img-src="https://cdn.shopify.com/s/files/1/0385/2405/9780/files/Enlace_savage_9e53530a-036b-493b-b0a9-8ee50384f5ae.png?v=1612290826"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              Special Discounts!
            </div>
          </q-carousel-slide>
          <q-carousel-slide
            name="3"
            img-src="https://res.cloudinary.com/teepublic/image/private/s--WiIw9Lqo--/t_Preview/b_rgb:191919,c_lpad,f_jpg,h_630,q_90,w_1200/v1505495770/production/designs/1902438_1.jpg"
          >
            <div
              class="absolute-bottom bg-black bg-opacity-50 text-h5 text-white q-pa-sm"
            >
              New Arrivals!
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Featured Products -->
        <section class="q-py-md">
          <h2 class="text-center text-h4 q-mb-md">Featured Products</h2>
          <div class="row q-col-gutter-md q-pt-md">
            <q-card
              v-for="(product, index) in products"
              :key="index"
              class="col-xs-12 col-sm-6 col-md-4 q-hover-shadow"
            >
              <q-img :src="product.image" class="q-mb-sm" :size="product.size" />
              <q-card-section>
                <div class="text-subtitle1 text-black">{{ product.name }}</div>
                <div class="text-caption text-black">
                  {{ product.description }}
                </div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat label="Details" color="primary" />
                <q-btn flat label="Add to Cart" color="primary" />
              </q-card-actions>
            </q-card>
          </div>
        </section>

        <!-- Newsletter Signup -->
        <section class="q-py-md text-center bg-brown text-white">
          <h2 class="text-h4 q-mb-md">Stay Updated</h2>
          <p class="text-subtitle2 q-mb-md">Sign up for our newsletter to get the latest news and offers.</p>
          <div class="q-mx-auto" style="max-width: 400px;">
            <q-input outlined placeholder="Enter your email" type="email" class="q-mb-md bg-white" />
            <q-btn label="Subscribe" color="primary" />
          </div>
        </section>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-brown-10 text-white q-pa-md">
      <div class="row items-center">
        <div class="col text-red">© 2024 SAVAGE.CO</div>
        <div class="col-auto">
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref("1");
    const products = ref([
      {
        name: "Hoodie Boxy You <3 Me",
        description: "Best for starboy",
        image: "https://down-id.img.susercontent.com/file/id-11134207-7qul6-ljbzdilro5i686",
        size: "50px", // Adjust image size here
      },
      {
        name: "Hoodie Boxy Kiss Me",
        description: "Comfortable and stylish",
        image: "https://down-id.img.susercontent.com/file/id-11134207-7r98q-lnvg75p9shae8b",
        size: "50px", // Adjust image size here
      },
      {
        name: "Hoodie Boxy Apocalypse",
        description: "Best of the Best",
        image: "https://d2kchovjbwl1tk.cloudfront.net/vendor/3859/product/0AA158AB-49E4-4870-9751-D24623077966_1690626727345.jpeg",
        size: "50px", // Adjust image size here
      },
      {
        name: "Kaos Casual",
        description: "Ready for size XS S M L XL",
        image: "https://wezen.ca/wp-content/uploads/2020/01/4281-a525e1.jpeg",
        size: "50px", // Adjust image size here
      },
      {
        name: "Kaos Vaneskrz",
        description: "Ready for size XS S M L XL",
        image: "https://www.dauletapparel.com/cdn/shop/products/Sae050a8b0b084378b7c92b651ec36853t.jpg?v=1666054077&width=700",
        size: "50px", // Adjust image size here
      },
      {
        name: "Kaos Regular Shibuya",
        description: "Ready for size XS S M L XL",
        image: "https://cf.shopee.co.id/file/c2dbec328f44475532cb33d74699cd5c",
        size: "50px", // Adjust image size here
      },
      {
        name: "Short Pants Cream",
        description: "Ready for size XS S M L XL",
        image: "https://ph-test-11.slatic.net/p/e7e49396e0a10bfe4d181b38b72a83a2.jpg",
        size: "50px", // Adjust image size here
      },
      {
        name: "Short Pants Dark Green",
        description: "Ready for size XS S M L XL",
        image: "https://down-ph.img.susercontent.com/file/ph-11134207-7qul0-li1ivoujnap356",
        size: "50px", // Adjust image size here
      },
      {
        name: "Short Pants Green",
        description: "Ready for size XS S M L XL",
        image: "https://cf.shopee.co.id/file/a92d95637ca79875a659737d4e6ecfb1",
        size: "50px", // Adjust image size here
      },
    ]);

    function toggleLeftDrawer() {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    }

    function deleteProduct(index) {
      products.value.splice(index, 1);
    }

    return {
      leftDrawerOpen,
      slide,
      products,
      toggleLeftDrawer,
      deleteProduct,
    };
  },
};
</script>

<style>
.menu-list {
  padding-top: 20px;
}

.q-hover-shadow:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.q-carousel-slide .absolute-bottom {
  background: rgba(0, 0, 0, 0.5);
  padding: 1rem;
  text-align: center;
  width: 100%;
}

.text-black {
  color: black;
}

.bg-secondary {
  background-color: #2d2d2d; /* Adjust color as needed */
}

.q-pb-xl {
  padding-bottom: 48px;
}

.q-pt-md {
  padding-top: 24px;
}

.q-py-md {
  padding-top: 24px;
  padding-bottom: 24px;
}

.bg-grey-1 {
  background-color: #f5f5f5;
}

.text-center {
  text-align: center;
}
</style>
