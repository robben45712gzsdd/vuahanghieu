<template>
  <div id="main">
    <!-- Header -->
    <header id="main-header" class="bg-white py-5">
      <div class="container">
        <div class="d-flex align-items-center justify-content-between row">
          <!-- Logo -->
          <div class="d-flex align-items-center mb-2 mb-md-0 col-md-3 col-12">
            <img src="@/assets/images/vuahanghieu-new.svg" alt="logo" class="img-fluid" style="max-height: 50px;" />
          </div>

          <!-- Search bar -->
          <div class="mb-2 mb-md-0 col-md-6 col-12">
            <div class="input-group">
              <input type="text" class="form-control header-search" placeholder="Tìm kiếm sản phẩm, thương hiệu..." />
              <div class="input-group-append d-flex align-items-center">
                <button class="btn btn-dark btn-search" type="button">
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                    class="bi bi-search" viewBox="0 0 16 16">
                    <path
                      d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001q.044.06.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1 1 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0" />
                  </svg>
                </button>
              </div>
            </div>
          </div>

          <!-- Auth box -->
          <div class="d-flex justify-content-md-end justify-content-start mt-3 mt-md-0 col-md-3 col-12">
            <div class="d-flex align-items-center shadow-sm rounded-pill auth-box">
              <a href="#" class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor"
                  class="me-2 bi bi-person-circle" viewBox="0 0 16 16">
                  <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0" />
                  <path fill-rule="evenodd"
                    d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8m8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1" />
                </svg>
                <span>Đăng nhập</span>
              </a>
              <span class="divider"></span>
              <a href="#" class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
                <span>Đăng ký</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Content -->
    <main class="my-4 container">
      <div class="row">
        <!-- Carousel Banner bên trái -->
        <div class="banner-left mb-3 mb-md-0 col-md-8 col-12">
          <VueSlickCarousel v-bind="bannerSettings">
            <nuxt-link v-for="(banner, index) in bannerImages" :key="index" :to="banner.url">
              <img :src="banner.image" class="rounded w-100 img-fluid" :alt="banner.alt" />
            </nuxt-link>
          </VueSlickCarousel>
        </div>

        <!-- Carousel Deal bên phải -->
        <div class="slider-right p-3 col-md-4 col-12">
          <div class="deal-carousel-wrapper">
            <div class="mb-3 deal-header">
              <h5 class="mb-0 fst-italic fw-bold deal-title">
                Deal Ngon <span class="text-danger">Hoành Tráng</span>
              </h5>
              <p class="mb-0 fst-italic deal-subtitle">Rực Rỡ Việt Nam - Deal Ngon Hết Nấc!</p>
            </div>

            <VueSlickCarousel v-bind="dealSettings" ref="dealSlick">
              <nuxt-link v-for="(deal, index) in deals" :key="index" :to="deal.url" class="deal-slide">
                <div class="deal-item">
                  <div class="deal-badge">
                    <span class="badge-percent">{{ deal.sale }}%</span>
                    <span class="badge-text">OFF</span>
                  </div>
                  <img :src="deal.image" class="deal-image" alt="deal product" />
                </div>
                <div class="deal-price">
                  <div class="current-price">{{ deal.price }} ₫</div>
                  <del class="old-price">{{ deal.oldPrice }} ₫</del>
                </div>
              </nuxt-link>
            </VueSlickCarousel>
          </div>
        </div>
      </div>

      <!-- Category list -->
      <div class="mt-4 text-center list-category row">
        <div v-for="(cate, index) in categories" :key="index" class="d-flex justify-content-center mb-3">
          <nuxt-link :to="cate.url" class="d-flex flex-column align-items-center category-item">
            <img :src="cate.image" class="img-fluid" alt="category icon" />
            <span class="fw-bold">{{ cate.label }}</span>
          </nuxt-link>
        </div>
      </div>
    </main>

    <!-- Brand Top Sale  -->
    <div class="brand-top-sale my-4 container">
      <div class="d-flex align-items-center mb-3 header-brand">
        <svg width="24" height="24" _ngcontent-ng-c867881976="" xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 10.96 14.74">
          <defs _ngcontent-ng-c867881976="">
            <style _ngcontent-ng-c867881976="">
              .cls-1 {
                fill: #fdb515;
              }

              .cls-2 {
                fill: #231f20;
              }
            </style>
          </defs>
          <path _ngcontent-ng-c867881976=""
            d="M9.71.15,6.82,5.8a.11.11,0,0,0,.1.15h3.93a.11.11,0,0,1,.07.19L.18,14.71A.11.11,0,0,1,0,14.58L3.53,6.79a.11.11,0,0,0-.1-.15H.7a.11.11,0,0,1-.1-.16L3.91.06A.1.1,0,0,1,4,0H9.62A.1.1,0,0,1,9.71.15Z"
            class="cls-1"></path>
          <path _ngcontent-ng-c867881976="" d="M2.69,8.64,0,14.6a.1.1,0,0,0,.15.12L7.79,8.64Z" class="cls-2"></path>
        </svg>
        <h4 class="ms-1 text-danger text-uppercase deal-title">
          Hàng Hiệu <span class="fw-bold">Bán Chạy</span>
        </h4>
      </div>
      <!-- Content for Brand Top Sale can be added here -->
      <div class="position-relative product-carousel">
        <VueSlickCarousel v-bind="productCarouselSettings" ref="productSlick">
          <div v-for="(product, index) in products" :key="index" class="px-2">
            <nuxt-link :to="product.url" class="position-relative shadow-sm border-0 h-100 card product-card">
              <!-- Huy hiệu giảm giá -->
              <div class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8">
                {{ product.discount }}% OFF
              </div>

              <!-- Ảnh sản phẩm -->
              <img :src="product.image" :alt="product.name" class="card-img-top p-3" />

              <!-- Nội dung -->
              <div class="p-2 text-center">
                <h6 class="mb-2 text-truncate">
                  {{ product.name }}
                </h6>
                <div class="d-flex flex-column align-items-start">
                  <span class="text-danger fst-italic fs-5 fw-semibold">
                    {{ product.price }} đ
                  </span>
                  <del class="text-muted fst-italic fs-6">
                    {{ product.oldPrice }} đ
                  </del>
                </div>
              </div>
            </nuxt-link>
          </div>
        </VueSlickCarousel>
      </div>
    </div>
    <!-- To Gift is to Love -->
    <div class="to-gift-is-to-love container">
      <img src="@/assets/images/banner/banner-to-gift.webp" alt="to gift is to love" class="rounded w-100 img-fluid" />
      <!-- Content for Brand Top Sale can be added here -->
      <div class="position-relative product-carousel">
        <VueSlickCarousel v-bind="productCarouselSettings" ref="productSlick">
          <div v-for="(product, index) in products" :key="index" class="px-2">
            <nuxt-link :to="product.url" class="position-relative shadow-sm border-0 h-100 card product-card">
              <!-- Huy hiệu giảm giá -->
              <div class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8">
                {{ product.discount }}% OFF
              </div>

              <!-- Ảnh sản phẩm -->
              <img :src="product.image" :alt="product.name" class="card-img-top p-3" />

              <!-- Nội dung -->
              <div class="p-2 text-center">
                <h6 class="mb-2 text-truncate">
                  {{ product.name }}
                </h6>
                <div class="d-flex flex-column align-items-start">
                  <span class="text-danger fst-italic fs-5 fw-semibold">
                    {{ product.price }} đ
                  </span>
                  <del class="text-muted fst-italic fs-6">
                    {{ product.oldPrice }} đ
                  </del>
                </div>
              </div>
            </nuxt-link>
          </div>
        </VueSlickCarousel>
      </div>
    </div>

    <!-- Banner Second -->
    <VueSlickCarousel v-bind="bannerSecondCarouselSettings" ref="BannerSecondSlick" class="my-4 container">
      <div v-for="(banner, index) in bannerSecond" :key="index" class="px-2">
        <nuxt-link :to="banner.url">
          <img :src="banner?.image" draggable="false" 
          @dragstart.prevent 
          @contextmenu.prevent alt="banner-second" class="rounded w-100 img-fluid" />
        </nuxt-link>
      </div>
    </VueSlickCarousel>

    <!-- Category Future -->
    <div class="my-4 category-future container">
      
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel';
import bannerLeft1 from '@/assets/images/banner/1.webp';
import bannerLeft2 from '@/assets/images/banner/2.webp';
import bannerLeft3 from '@/assets/images/banner/3.webp';
import bannerLeft4 from '@/assets/images/banner/4.webp';
import bannerLeft5 from '@/assets/images/banner/5.webp';
import bannerLeft6 from '@/assets/images/banner/6.webp';
import bannerLeft7 from '@/assets/images/banner/7.webp';
import bannerLeft8 from '@/assets/images/banner/8.webp';
import bannerLeft9 from '@/assets/images/banner/9.webp';
import bannerLeft10 from '@/assets/images/banner/10.webp';
import bannerRight1 from '@/assets/images/deal/ao-khoac-lacoste-sport-bi-material-colourblock-full-zip-sweatshirt-size-xs-618f183c69782-13112021084324.webp';
import bannerRight2 from '@/assets/images/deal/6371ea9cd7218-14112022141332.webp';
import bannerRight3 from '@/assets/images/deal/ao-thun-nam-nike-as-m-nsw-club-tee-ar4999-013-mau-den-size-s-6556d6ee6f7a3-17112023095854.webp';
import imageDealCategory1 from '@/assets/images/iconDeal/1.webp';
import imageDealCategory2 from '@/assets/images/iconDeal/2.webp';
import imageDealCategory3 from '@/assets/images/iconDeal/3.webp';
import imageDealCategory4 from '@/assets/images/iconDeal/4.webp';
import imageDealCategory5 from '@/assets/images/iconDeal/5.webp';
import imageDealCategory6 from '@/assets/images/iconDeal/6.webp';
import imageDealCategory7 from '@/assets/images/iconDeal/7.webp';
import imageDealCategory8 from '@/assets/images/iconDeal/8.webp';


import bannerSecond1 from '@/assets/images/banner/11.webp';
import bannerSecond2 from '@/assets/images/banner/12.webp';
import bannerSecond3 from '@/assets/images/banner/13.webp';
import bannerSecond4 from '@/assets/images/banner/14.webp';
import bannerSecond5 from '@/assets/images/banner/15.webp';
import bannerSecond6 from '@/assets/images/banner/16.webp';
import bannerSecond7 from '@/assets/images/banner/17.webp';
import bannerSecond8 from '@/assets/images/banner/18.webp';
import bannerSecond9 from '@/assets/images/banner/19.webp';
import bannerSecond10 from '@/assets/images/banner/20.webp';
export default {
  components: { VueSlickCarousel },
  data() {
    return {
      bannerImages: [
        { image: bannerLeft1, alt: 'banner-1', url: '#' },
        { image: bannerLeft2, alt: 'banner-2', url: '#' },
        { image: bannerLeft3, alt: 'banner-3', url: '#' },
        { image: bannerLeft4, alt: 'banner-4', url: '#' },
        { image: bannerLeft5, alt: 'banner-5', url: '#' },
        { image: bannerLeft6, alt: 'banner-6', url: '#' },
        { image: bannerLeft7, alt: 'banner-7', url: '#' },
        { image: bannerLeft8, alt: 'banner-8', url: '#' },
        { image: bannerLeft9, alt: 'banner-9', url: '#' },
        { image: bannerLeft10, alt: 'banner-10', url: '#' }
      ],
      deals: [
        { title: 'Deal HOT', image: bannerRight1, sale: 6, price: '4.560.000', oldPrice: '4.900.000', url: '#' },
        { title: 'Deal Ngon Hoành Tráng', image: bannerRight2, sale: 29, price: '850.000', oldPrice: '1.200.000', url: '#' },
        { title: 'Deal HOT', image: bannerRight3, sale: 15, price: '510.000', oldPrice: '600.000', url: '#' }
      ],
      categories: [
        { label: 'Ưu Đãi Tháng 10', url: "#", image: imageDealCategory1 },
        { label: 'Deal khách mới', url: "#", image: imageDealCategory2 },
        { label: 'Hot deals', url: "#", image: imageDealCategory3 },
        { label: 'Bán Chạy', url: "#", image: imageDealCategory4 },
        { label: 'Hàng Quốc Tế', url: "#", image: imageDealCategory5 },
        { label: 'Cẩm Nang', url: "#", image: imageDealCategory6 },
        { label: 'New Arrivals', url: "#", image: imageDealCategory7 },
        { label: 'Quà tặng', url: "#", image: imageDealCategory8 }
      ],
      bannerSettings: {
        autoplay: true,
        dots: true,
        arrows: false,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1
      },
      dealSettings: {
        autoplay: false,
        dots: false,
        arrows: true,
        infinite: false,
        slidesToShow: 2,
        slidesToScroll: 2
      },

      //top sale products
      products: [
        {
          url: '#',
          name: 'Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540',
          price: '490.000',
          oldPrice: '950.000',
          discount: 48,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby',
          price: '199.000',
          oldPrice: '279.000',
          discount: 29,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Áo khoác nam Lacoste Sport - Mẫu mới',
          price: '1.120.000',
          oldPrice: '1.320.000',
          discount: 15,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Serum Vitamin C - Dưỡng sáng da',
          price: '320.000',
          oldPrice: '340.000',
          discount: 6,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Túi đeo chéo MCM Patricia - Cognac',
          price: '2.350.000',
          oldPrice: '2.950.000',
          discount: 20,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540',
          price: '490.000',
          oldPrice: '950.000',
          discount: 48,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby',
          price: '199.000',
          oldPrice: '279.000',
          discount: 29,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Áo khoác nam Lacoste Sport - Mẫu mới',
          price: '1.120.000',
          oldPrice: '1.320.000',
          discount: 15,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Serum Vitamin C - Dưỡng sáng da',
          price: '320.000',
          oldPrice: '340.000',
          discount: 6,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        },
        {
          url: '#',
          name: 'Túi đeo chéo MCM Patricia - Cognac',
          price: '2.350.000',
          oldPrice: '2.950.000',
          discount: 20,
          image: require('@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp')
        }
      ],
      productCarouselSettings: {
        slidesToShow: 5,
        slidesToScroll: 1,
        infinite: false,
        arrows: true,
        dots: false,
        responsive: [
          {
            breakpoint: 1200,
            settings: { slidesToShow: 4 }
          },
          {
            breakpoint: 992,
            settings: { slidesToShow: 3 }
          },
          {
            breakpoint: 768,
            settings: { slidesToShow: 2 }
          },
          {
            breakpoint: 576,
            settings: { slidesToShow: 1 }
          }
        ]
      },

      //Banner Second
      bannerSecond: [
        {
          image: bannerSecond1,
          alt: 'banner-second-1',
          url: '#'
        },
        {
          image: bannerSecond2,
          alt: 'banner-second-2',
          url: '#'
        },
        {
          image: bannerSecond3,
          alt: 'banner-second-3',
          url: '#'
        },
        {
          image: bannerSecond4,
          alt: 'banner-second-4',
          url: '#'
        },
        {
          image: bannerSecond5,
          alt: 'banner-second-5',
          url: '#'
        },
        {
          image: bannerSecond6,
          alt: 'banner-second-6',
          url: '#'
        },
        {
          image: bannerSecond7,
          alt: 'banner-second-7',
          url: '#'
        },
        {
          image: bannerSecond8,
          alt: 'banner-second-8',
          url: '#'
        },
        {
          image: bannerSecond9,
          alt: 'banner-second-9',
          url: '#'
        },
        {
          image: bannerSecond10,
          alt: 'banner-second-10',
          url: '#'
        }
      ],
      bannerSecondCarouselSettings: {
        autoplay: false,
        dots: false,
        arrows: false,
        infinite: true,
        slidesToShow: 2,
        slidesToScroll: 2
      }
    };
  }
};
</script>

<style>
/* ===== Header ===== */
#main-header {
  border-bottom: 2px solid #d1d1d1;
}

#main-header .input-group {
  max-width: 100%;
}

#main-header .header-search,
#main-header .btn-search {
  height: 44px;
}

#main-header .btn-search {
  border-radius: 0 8px 8px 0;
}

#main-header .auth-box {
  background-color: #f8f9fa;
  padding: 6px 12px;
  border-radius: 30px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.05);
}

#main-header .auth-link {
  color: #212529;
  font-weight: 500;
  text-decoration: none;
  padding: 6px 10px;
  border-radius: 20px;
  transition: color 0.2s ease, background-color 0.2s ease;
}

#main-header .auth-link:hover {
  background-color: #e9ecef;
  color: #000;
}

#main-header .auth-link svg {
  color: #6c757d;
  transition: color 0.2s ease;
}

#main-header .auth-link:hover svg {
  color: #000;
}

#main-header .divider {
  width: 1px;
  height: 22px;
  background-color: #dee2e6;
  margin: 0 6px;
}

@media (max-width: 768px) {
  #main-header .auth-box {
    justify-content: flex-start;
    padding: 8px 14px;
  }

  #main-header .auth-link {
    padding: 6px 8px;
  }

  #main-header .divider {
    height: 18px;
  }
}

/* ===== Deal Section ===== */
.deal-item {
  position: relative;
  background: #fff;
  margin: 10px 5px;
  text-align: center;
}

.deal-badge {
  position: absolute;
  top: 10px;
  left: 10px;
  background: red;
  color: #fff;
  padding: 4px 6px;
  font-size: 12px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.deal-image {
  max-width: 150px;
  object-fit: contain;
  margin: 0 auto;
}

.deal-price {
  margin-top: 5px;
  font-size: 14px;
}

.current-price {
  color: #d80d0d;
  font-weight: bold;
}

.old-price {
  font-size: 12px;
  color: #777;
}

/* ===== Carousel & Slick ===== */
.slider-right {
  background-color: rgb(255, 226, 226);
}

.slick-dots li button:before {
  font-size: 8px;
}

.slick-dots li {
  margin: 0 !important;
}

.slick-prev:before,
.slick-next:before {
  font-size: 30px;
  color: #d46b6ba3;
}

.slick-next {
  right: -5px;
}

.slick-prev {
  left: -10px;
}

.slick-prev,
.slick-next {
  top: 40%;
  z-index: 1000;
}

.banner-left .slick-slide img {
  height: 310px;
  object-fit: cover;
}

.slick-dots {
  bottom: 10px;
}

/* ===== Category Grid ===== */
.list-category {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(72px, 1fr));
  grid-gap: 10px;
  margin-bottom: var(--gap16);
  padding: calc(10px + (0 - 10) * ((100vw - 300px) / (1920 - 300)));
}

a {
  text-decoration: none;
  color: inherit;
}

a:hover {
  opacity: 0.7;
  transition: all .3s ease;
}

.product-card img {
  object-fit: contain;
  height: 220px;
  width: 100%;
}

.badge {
  font-size: 0.8rem;
}
</style>
