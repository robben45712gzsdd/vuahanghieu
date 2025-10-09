<template>
  <div id="main">
    <!-- Header -->
    <header id="main-header" class="bg-white py-5">
      <div class="container">
        <div class="d-flex align-items-center justify-content-between row">
          <!-- Logo -->
          <nuxt-link to="/" class="d-flex align-items-center mb-2 mb-md-0 col-md-3 col-12">
            <img
              src="@/assets/images/vuahanghieu-new.svg"
              alt="logo"
              class="img-fluid"
              style="max-height: 50px"
            />
          </nuxt-link>

          <!-- Search bar -->
          <div class="mb-2 mb-md-0 col-md-6 col-12">
            <div class="input-group">
              <input
                type="text"
                class="form-control header-search"
                placeholder="Tìm kiếm sản phẩm, thương hiệu..."
              />
              <div class="input-group-append d-flex align-items-center">
                <button class="btn btn-dark btn-search" type="button">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="16"
                    height="16"
                    fill="currentColor"
                    class="bi bi-search"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001q.044.06.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1 1 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0"
                    />
                  </svg>
                </button>
              </div>
            </div>
          </div>

          <!-- Auth box -->
          <div
            class="d-flex justify-content-md-end justify-content-start mt-3 mt-md-0 col-md-3 col-12"
          >
            <div
              class="d-flex align-items-center shadow-sm rounded-pill auth-box"
            >
              <nuxt-link
                to="/login"
                class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="18"
                  height="18"
                  fill="currentColor"
                  class="me-2 bi bi-person-circle"
                  viewBox="0 0 16 16"
                >
                  <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0" />
                  <path
                    fill-rule="evenodd"
                    d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8m8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1"
                  />
                </svg>
                <span>Đăng nhập</span>
              </nuxt-link>
              <span class="divider"></span>
              <nuxt-link
                to="signup"
                class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link"
              >
                <span>Đăng ký</span>
              </nuxt-link>
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
            <nuxt-link
              v-for="(banner, index) in bannerImages"
              :key="index"
              :to="banner.url"
            >
              <img
                :src="banner.image"
                class="rounded w-100 img-fluid"
                :alt="banner.alt"
              />
            </nuxt-link>
          </VueSlickCarousel>
        </div>

        <!-- Carousel Deal bên phải -->
        <div
          class="slider-right p-3 col-md-4 col-12 rounded"
          style="height: 315px"
        >
          <div class="deal-carousel-wrapper">
            <div class="mb-3 deal-header">
              <h5 class="mb-0 fst-italic fw-bold deal-title">
                Deal Ngon <span class="text-danger">Hoành Tráng</span>
              </h5>
              <p class="mb-0 fst-italic deal-subtitle">
                Rực Rỡ Việt Nam - Deal Ngon Hết Nấc!
              </p>
            </div>

            <VueSlickCarousel v-bind="dealSettings" ref="dealSlick">
              <nuxt-link
                v-for="(deal, index) in deals"
                :key="index"
                :to="deal.url"
                class="deal-slide"
              >
                <div class="deal-item">
                  <div class="deal-badge">
                    <span class="badge-percent">{{ deal.sale }}%</span>
                    <span class="badge-text">OFF</span>
                  </div>
                  <img
                    :src="deal.image"
                    class="deal-image"
                    alt="deal product"
                  />
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
        <div
          v-for="(cate, index) in categories"
          :key="index"
          class="d-flex justify-content-center mb-3"
        >
          <nuxt-link
            :to="cate.url"
            class="d-flex flex-column align-items-center category-item"
          >
            <img :src="cate.image" class="img-fluid" alt="category icon" />
            <span class="fw-bold">{{ cate.label }}</span>
          </nuxt-link>
        </div>
      </div>
    </main>

    <!-- Brand Top Sale  -->
    <div class="brand-top-sale my-4 container">
      <div class="d-flex align-items-center mb-3 header-brand">
        <svg
          width="24"
          height="24"
          _ngcontent-ng-c867881976=""
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 10.96 14.74"
        >
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
          <path
            _ngcontent-ng-c867881976=""
            d="M9.71.15,6.82,5.8a.11.11,0,0,0,.1.15h3.93a.11.11,0,0,1,.07.19L.18,14.71A.11.11,0,0,1,0,14.58L3.53,6.79a.11.11,0,0,0-.1-.15H.7a.11.11,0,0,1-.1-.16L3.91.06A.1.1,0,0,1,4,0H9.62A.1.1,0,0,1,9.71.15Z"
            class="cls-1"
          ></path>
          <path
            _ngcontent-ng-c867881976=""
            d="M2.69,8.64,0,14.6a.1.1,0,0,0,.15.12L7.79,8.64Z"
            class="cls-2"
          ></path>
        </svg>
        <h4 class="ms-1 text-danger text-uppercase deal-title">
          Hàng Hiệu <span class="fw-bold">Bán Chạy</span>
        </h4>
      </div>
      <!-- Content for Brand Top Sale can be added here -->
      <div class="position-relative product-carousel">
        <VueSlickCarousel v-bind="productCarouselSettings" ref="productSlick">
          <div v-for="(product, index) in products" :key="index" class="px-2">
            <nuxt-link
              :to="product.url"
              class="position-relative border-0 h-100 card product-card"
            >
              <!-- Huy hiệu giảm giá -->
              <div
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
              >
                {{ product.discount }}% OFF
              </div>

              <!-- Ảnh sản phẩm -->
              <img
                :src="product.image"
                :alt="product.name"
                class="card-img-top p-3"
              />

              <!-- Nội dung -->
              <div class="p-2 text-center">
                <h6 class="mb-2 truncate-2">
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
      <img
        src="@/assets/images/banner/banner-to-gift.webp"
        alt="to gift is to love"
        class="rounded w-100 img-fluid"
      />
      <!-- Content for Brand Top Sale can be added here -->
      <div class="position-relative product-carousel">
        <VueSlickCarousel v-bind="productCarouselSettings" ref="productSlick">
          <div v-for="(product, index) in products" :key="index" class="px-2">
            <nuxt-link
              :to="product.url"
              class="position-relative border-0 h-100 card product-card"
            >
              <!-- Huy hiệu giảm giá -->
              <div
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
              >
                {{ product.discount }}% OFF
              </div>

              <!-- Ảnh sản phẩm -->
              <img
                :src="product.image"
                :alt="product.name"
                class="card-img-top p-3"
              />

              <!-- Nội dung -->
              <div class="p-2 text-center">
                <h6 class="mb-2 truncate-2">
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
    <VueSlickCarousel
      v-bind="bannerSecondCarouselSettings"
      ref="BannerSecondSlick"
      class="my-4 container"
    >
      <div v-for="(banner, index) in bannerSecond" :key="index" class="px-2">
        <nuxt-link :to="banner.url">
          <img
            :src="banner?.image"
            alt="banner-second"
            class="rounded w-100 img-fluid"
          />
        </nuxt-link>
      </div>
    </VueSlickCarousel>

    <!-- Category Future -->
    <div class="container py-4 category-future">
      <h5 class="fw-bold mb-3 text-uppercase">Danh mục nổi bật</h5>
      <VueSlickCarousel
        v-bind="categoryFutureCarouselSettings"
        class="category-slider"
      >
        <div
          v-for="(item, index) in categoriesFuture"
          :key="index"
          class="d-flex flex-column align-items-center px-2"
        >
          <nuxt-link :to="item.url" class="card h-100 w-100">
            <div
              class="w-100 rounded img-wrapper d-flex justify-content-center align-items-center"
            >
              <img
                :src="item.image"
                :alt="item.title"
                class="img-fluid"
                style="height: 100px; object-fit: contain"
              />
            </div>
            <p class="text-center mt-1">{{ item.title }}</p>
          </nuxt-link>
          <nuxt-link :to="item.url" class="card h-100 w-100">
            <div
              class="w-100 rounded img-wrapper d-flex justify-content-center align-items-center"
            >
              <img
                :src="item.image"
                :alt="item.title"
                class="img-fluid"
                style="height: 100px; object-fit: contain"
              />
            </div>
            <p class="text-center mt-1">{{ item.title }}</p>
          </nuxt-link>
        </div>
      </VueSlickCarousel>
    </div>

    <!-- Brand Future -->
    <div class="container py-4 brand-future">
      <h5 class="fw-bold mb-3 text-uppercase">Thương hiệu nổi bật</h5>
      <VueSlickCarousel
        v-bind="brandFutureCarouselSettings"
        class="brand-slider"
      >
        <div
          v-for="(item, index) in brandsFuture"
          :key="index"
          class="d-flex flex-column align-items-center px-2"
        >
          <nuxt-link :to="item.url" class="card h-100 w-100">
            <div
              class="w-100 rounded img-wrapper p-2 d-flex justify-content-center align-items-center"
            >
              <img :src="item.image" :alt="item.title" class="img-fluid" />
            </div>
          </nuxt-link>
        </div>
      </VueSlickCarousel>
    </div>

    <!-- Trending search  -->
    <div class="container my-4 py-4 trending-search">
      <h5 class="fw-bold mb-3 text-uppercase">Xu Hướng Tìm Kiếm</h5>
      <div class="row row-cols-1 row-cols-md-5 g-4">
        <nuxt-link
          :to="item?.url"
          v-for="(item, index) in trendingSearch"
          :key="index"
        >
          <div class="card h-100 d-flex flex-row align-items-center">
            <div class="card-body">
              <h5 class="card-title">{{ item?.title }}</h5>
              <p class="card-text text-muted">{{ item?.quantity }}+ sản phẩm</p>
            </div>
            <img :src="item?.image" class="card-img-top" alt="Coach" />
          </div>
        </nuxt-link>
      </div>
    </div>

    <!-- Suggested products  -->
    <div class="container py-4 suggested-products">
      <h5 class="fw-bold mb-3 text-uppercase text-danger">Gợi ý cho bạn</h5>
      <div class="position-relative product-carousel">
        <VueSlickCarousel v-bind="productCarouselSettings" ref="productSlick">
          <div
            v-for="(product, index) in productsSuggest"
            :key="index"
            class="px-2"
          >
            <nuxt-link
              :to="product.url"
              class="position-relative border-0 h-100 card product-card"
            >
              <!-- Huy hiệu giảm giá -->
              <div
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
              >
                {{ product.discount }}% OFF
              </div>

              <!-- Ảnh sản phẩm -->
              <img
                :src="product.image"
                :alt="product.name"
                class="card-img-top p-3"
              />

              <!-- Nội dung -->
              <div class="p-2 text-center">
                <h6 class="mb-2 truncate-2">
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

    <!-- List perfume -->
    <div class="container py-4 perfume-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Nước hoa
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productPerfume"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List watch -->
    <div class="container py-4 watch-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Đồng hồ
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div v-for="(product, index) in productWatch" :key="index" class="px-2">
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List Cosmetic -->
    <div class="container py-4 cosmetic-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Mỹ phẩm
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productCosmetic"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List hat -->
    <div class="container py-4 hat-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Mũ Nón
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div v-for="(product, index) in productHat" :key="index" class="px-2">
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List handbag -->
    <div class="container py-4 handbag-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Túi Xách
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productHandbag"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List shoes -->
    <div class="container py-4 shoes-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Giày
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div v-for="(product, index) in productShoes" :key="index" class="px-2">
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List fashion -->
    <div class="container py-4 fashion-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Thời Trang
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productFashion"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List eyewear -->
    <div class="container py-4 eyewear-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Kính Mắt
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productEyeWear"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List lipstick -->
    <div class="container py-4 lipstick-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Son Môi
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productLipStick"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List pickleball -->
    <div class="container py-4 pickleball-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Pickleball
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-5 g-4"
      >
        <div
          v-for="(product, index) in productPickleBall"
          :key="index"
          class="px-2"
        >
          <nuxt-link
            :to="product.url"
            class="position-relative border-0 h-100 card product-card"
          >
            <!-- Huy hiệu giảm giá -->
            <div
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 rounded text-white end-0 fs-8"
            >
              {{ product.discount }}% OFF
            </div>

            <!-- Ảnh sản phẩm -->
            <img
              :src="product.image"
              :alt="product.name"
              class="card-img-top p-3"
            />

            <!-- Nội dung -->
            <div class="p-2 text-center">
              <h6 class="mb-2 truncate-2">
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
      </div>
    </div>

    <!-- List Blog -->
    <div class="container py-4 perfume-products">
      <h3
        class="m-auto border-bottom border-3 pb-2 mb-3 border-black fw-normal text-center"
        style="width: max-content"
      >
        Blog
      </h3>
      <div
        class="d-flex flex-wrap justify-content-center product-list row row-cols-1 row-cols-md-4 g-4"
      >
        <div v-for="(item, index) in blog" :key="index" class="px-2">
          <nuxt-link
            :to="item.url"
            class="position-relative border-0 h-100 card item-card"
          >
            <!-- Ảnh sản phẩm -->
            <img :src="item.image" :alt="item.title" class="card-img-top" />

            <!-- Nội dung -->
            <div class="p-2 text-start">
              <h6 class="mb-2 truncate-2 fw-bold">
                {{ item.title }}
              </h6>
              <p>{{ item.date }}</p>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- Description -->
    <div class="container description-introduce mx-auto px-4 my-4">
      <main class="container my-8">
        <section class="mb-6">
          <h4 class="text-2xl font-bold mb-4 text-gray-800">
            Vua Hàng Hiệu™ - Mua hàng hiệu chính hãng trực tuyến, Giá Tốt
          </h4>
          <p class="text-gray-600 leading-relaxed">
            Vua Hàng Hiệu là sàn thương mại điện tử thời trang hàng hiệu, địa
            chỉ mua sắm online trực tuyến uy tín, tin cậy và an toàn tại Việt
            Nam! Sàn VHH là sự gợi ý lý tưởng hàng đầu khi mua sắm đồ hiệu chính
            hãng, sang trọng và đắt tiền. Với sự đảm bảo của chúng tôi, bạn sẽ
            mua hàng trực tuyến an tâm và nhanh chóng hơn bao giờ hết!
          </p>
        </section>

        <section class="mb-6">
          <h4 class="text-2xl font-bold mb-4 text-gray-800">
            MUA SẮM HÀNG HIỆU ONLINE ĐƠN GIẢN
          </h4>
          <p class="text-gray-600 leading-relaxed">
            Nếu bạn đang tìm kiếm một sàn thương mại điện tử để mua và làm đối
            tác bán hàng trực tuyến thì Vua Hàng Hiệu là một sự gợi ý lý tưởng
            ấn tượng. Tại đây, người mua sẽ dễ dàng tìm kiếm các sản phẩm cao
            cấp mong muốn, xem các thông tin chi tiết về sản phẩm, chương trình
            khuyến mãi, các
            <a href="#" class="text-blue-500 hover:underline"
              >mã voucher giảm giá</a
            >
            và nhận được dịch vụ chăm sóc chuyên nghiệp hàng đầu.
          </p>
          <p class="text-gray-600 leading-relaxed">
            Nhờ đó, việc mua bán trên sàn Vua Hàng Hiệu trở nên nhanh chóng và
            tiện lợi hơn bao giờ hết. Bạn có thể trao đổi trực tiếp với nhà bán
            hàng qua các kênh như chat trên website, gọi vào hotline hoặc các
            kênh mạng xã hội liên kết khác như Facebook, Instagram để hỏi về mặt
            hàng cần mua và chắc chắn luôn được hỗ trợ nhiệt tình.
          </p>
          <p class="text-gray-600 leading-relaxed">
            Còn nếu bạn muốn tìm mua những dòng sản phẩm hàng hiệu chưa có sẵn
            tại website thì dịch vụ
            <a href="#" class="text-blue-500 hover:underline"
              >Order Hàng Quốc Tế</a
            >
            của Vua Hàng Hiệu là sự gợi ý lý tưởng dành cho bạn. Bạn có thể
            order các sản phẩm như thời trang, đồng hồ, kính mắt, túi xách,
            trang sức, nước hoa, mỹ phẩm… từ những thương hiệu quốc tế như
            <a href="#" class="text-blue-500 hover:underline">Seiko</a>,
            <a href="#" class="text-blue-500 hover:underline">Citizen</a>,
            <a href="#" class="text-blue-500 hover:underline">Michael Kors</a>,
            <a href="#" class="text-blue-500 hover:underline">Calvin Klein</a>,
            <a href="#" class="text-blue-500 hover:underline">Movado</a>,
            <a href="#" class="text-blue-500 hover:underline">Dior</a>,...
          </p>
          <p class="text-gray-600 leading-relaxed">
            Để bạn có thể dễ dàng khi tìm hiểu và sử dụng sản phẩm, trang
            <a href="#" class="text-blue-500 hover:underline"
              >Blog Vua Hàng Hiệu</a
            >
            sẽ giúp bạn có thể tìm được cho mình các kiến thức về xu hướng thời
            trang, review sản phẩm, mẹo làm đẹp, tin tức khuyến mãi và deal giá
            tốt bất ngờ.
          </p>
          <p class="text-gray-600 leading-relaxed">
            Ngoài ra, nếu bạn ở khu vực nội thành Hà Nội và Hồ Chí Minh có thể
            chọn dịch vụ giao hàng nhanh 2h trong ngày với mức phí ship hợp lý.
          </p>
        </section>

        <div
          id="collapseDescription"
          class="collapse"
          :class="{ show: isExpanded }"
        >
          <section class="mb-6">
            <h4 class="text-2xl font-bold mb-4 text-gray-800">
              TẢI ỨNG DỤNG VUA HÀNG HIỆU NGAY ĐỂ MUA BÁN ONLINE MỌI LÚC, MỌI NƠI
            </h4>
            <p class="text-gray-600 leading-relaxed">
              Để giúp việc mua sắm của bạn trở nên tiện lợi, dễ dàng và nhanh
              chóng hơn, Vua Hàng Hiệu đã tạo ứng dụng mua sắm trên điện thoại
              thông minh, cho phép bạn tìm kiếm và mua hàng mọi lúc mọi nơi. Chỉ
              cần
              <a href="#" class="text-blue-500 hover:underline"
                >tải ứng dụng Vua Hàng Hiệu</a
              >
              về máy bạn sẽ nhận được những ưu điểm có "1-0-2" như sau:
            </p>
            <ul class="list-disc pl-5 text-gray-600 leading-relaxed">
              <li>
                Giao diện thân thiện, đơn giản, dễ sử dụng. Bạn sẽ dễ dàng thấy
                được ngay những sản phẩm nổi bật cũng như dễ dàng tìm đến các ô
                tìm kiếm, giỏ hàng hoặc tính năng chat liền tay.
              </li>
              <li>
                Ứng dụng tích hợp công nghệ quản lý đơn mua tiện lợi, theo dõi
                được tình trạng đơn hàng dễ dàng.
              </li>
              <li>
                Cập nhật thông tin khuyến mãi, các mã giảm giá "hot" nhanh chóng
                và liên tục.
              </li>
              <li>
                Tại đây, bạn có thể lưu các mã giảm giá của Vua Hàng Hiệu, của
                shop và mã miễn phí vận chuyển toàn quốc.
              </li>
            </ul>
          </section>

          <section class="mb-6">
            <h4 class="text-2xl font-bold mb-4 text-gray-800">
              CHƯƠNG TRÌNH KHUYẾN MÃI, VOUCHER GIẢM GIÁ "KHỦNG"
            </h4>
            <p class="text-gray-600 leading-relaxed">
              Bên cạnh đó, Vua Hàng Hiệu liên tục cũng sẽ có những
              <a href="#" class="text-blue-500 hover:underline"
                >chương trình Flash Sale</a
              >
              lớn hằng năm như các ngày lễ tết: Tết Dương Lịch 1/1, Tết Nguyên
              Đán, Valentine 14/2, Quốc tế Phụ nữ 8/3, Ngày của Mẹ, Ngày của
              Cha,
              <a href="#" class="text-blue-500 hover:underline"
                >Phụ Nữ Việt Nam 20-10</a
              >, Ngày Nhà Giáo 20/11, Giáng Sinh…
            </p>
            <p class="text-gray-600 leading-relaxed">
              Không chỉ vậy, trong các tháng luôn diễn ra các sự kiện giảm giá
              "đỉnh cao" khác vào các ngày như: Sale 4.4, Sale 5.5, Sale 6.6,
              Sale 7.7, Sale 8.8, Sale 9.9, Sale 10.10, Sale 11.11, Sale 12.12.
              Đây là thời điểm để người mua hàng có thể nhanh tay chọn ngay cho
              mình những mặt hàng ưa thích với mức giá giảm kỷ lục.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Ngoài ra, bạn còn có thể thỏa thích săn sale vào các ngày trong
              tháng như Sale đồng giá giữa tháng và Sale cuối tháng.
            </p>
          </section>

          <section class="mb-6">
            <h4 class="text-2xl font-bold mb-4 text-gray-800">
              MUA HÀNG HIỆU LIMITED CAO CẤP GIÁ TỐT TẠI VUA HÀNG HIỆU
            </h4>
            <p class="text-gray-600 leading-relaxed">
              Bên cạnh mua được những sản phẩm chính hãng với mức giá tốt, tại
              Vua Hàng Hiệu bạn còn có thể sở hữu những món hàng hiệu phiên bản
              giới hạn khó tìm, các mẫu trendy vừa được ra mắt của những thương
              hiệu đình đám thế giới. Bởi Vua Hàng Hiệu liên tục cập nhật những
              mẫu mới và “siêu hot", nhằm đáp ứng nhu cầu của các khách hàng một
              cách nhanh chóng và đầy đủ.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Hơn hết, Vua Hàng Hiệu hợp tác trực tiếp với rất nhiều thương hiệu
              đình đám được các nhà bán lẻ uy tín phân phối bán trên website,
              top sản phẩm hot deal cho bạn săn sale luôn cập nhật mỗi giờ, mỗi
              ngày, đem đến cho bạn sự gợi ý lý tưởng đa dạng. Từ các hãng
              <a href="#" class="text-blue-500 hover:underline"
                >thời trang cao cấp</a
              >
              như <a href="#" class="text-blue-500 hover:underline">Gucci</a>,
              <a href="#" class="text-blue-500 hover:underline">Versace</a>,
              <a href="#" class="text-blue-500 hover:underline">Lacoste</a>,
              <a href="#" class="text-blue-500 hover:underline">Dolce Gabbana</a
              >, <a href="#" class="text-blue-500 hover:underline">Burberry</a>,
              <a href="#" class="text-blue-500 hover:underline">MLB</a>,
              <a href="#" class="text-blue-500 hover:underline">Adidas</a>,… Đến
              những thương hiệu mỹ phẩm nổi tiếng:
              <a href="#" class="text-blue-500 hover:underline">Obagi</a>,
              <a href="#" class="text-blue-500 hover:underline"
                >Paula’s Choice</a
              >,
              <a href="#" class="text-blue-500 hover:underline">Estée Lauder</a
              >, <a href="#" class="text-blue-500 hover:underline">Kiehl's</a>,
              <a href="#" class="text-blue-500 hover:underline">Vichy</a>,
              <a href="#" class="text-blue-500 hover:underline">SK-II</a>,
              <a href="#" class="text-blue-500 hover:underline">MAC</a>,
              <a href="#" class="text-blue-500 hover:underline">YSL</a>,
              <a href="#" class="text-blue-500 hover:underline">TomFord</a>,…
            </p>
            <p class="text-gray-600 leading-relaxed">
              Tại Vua Hàng Hiệu, bạn có thể dễ dàng tìm thấy các thương hiệu
              <a href="#" class="text-blue-500 hover:underline"
                >nước hoa sang trọng</a
              >
              được yêu thích như
              <a href="#" class="text-blue-500 hover:underline">Chanel</a>,
              <a href="#" class="text-blue-500 hover:underline">Dior</a>,
              <a href="#" class="text-blue-500 hover:underline">Lancome</a>,
              <a href="#" class="text-blue-500 hover:underline">Le Labo</a>,
              <a href="#" class="text-blue-500 hover:underline">Jo Malone</a>,
              <a href="#" class="text-blue-500 hover:underline">Versace</a>,...
            </p>
            <p class="text-gray-600 leading-relaxed">
              Hay các hãng
              <a href="#" class="text-blue-500 hover:underline"
                >giày hàng hiệu</a
              >
              phổ biến hiện nay như: MLB, Adidas, Nike, Converse, New Balance,
              Vans,... Hay những mẫu
              <a href="#" class="text-blue-500 hover:underline"
                >túi xách đắt tiền</a
              >
              từ những cái tên nhắc tới ai cũng biết: Charles & Keith, Louis
              Vuitton, Michael Kors, Furla, Coach,...
            </p>
            <p class="text-gray-600 leading-relaxed">
              Đôi khi, ngân sách mua sắm cũng là vấn đề đáng lo ngại. Với những
              khách hàng kinh tế có hạn nhưng vẫn muốn được sở hữu các sản phẩm
              hàng hiệu chính hãng được bảo hộ bởi Vua Hàng Hiệu. Đừng ngần ngại
              chọn ngay những món
              <a href="#" class="text-blue-500 hover:underline"
                >đồ hiệu cũ chính hãng</a
              >. Đây là các sản phẩm đã qua sử dụng nhưng được chúng tôi cam kết
              chất lượng và đồng hành với bạn về chất lượng sản phẩm trong suốt
              quá trình sử dụng.
            </p>
          </section>

          <section class="mb-6">
            <h4 class="text-2xl font-bold mb-4 text-gray-800">
              BẢO MẬT THÔNG TIN - ƯU ĐÃI THÀNH VIÊN HẤP DẪN
            </h4>
            <p class="text-gray-600 leading-relaxed">
              Mua hàng trên Vua Hàng Hiệu luôn là một trải nghiệm ấn tượng. Dù
              bạn đang có nhu cầu mua bất kỳ mặt hàng
              <a href="#" class="text-blue-500 hover:underline"
                >thời trang nam</a
              >,
              <a href="#" class="text-blue-500 hover:underline">thời trang nữ</a
              >, <a href="#" class="text-blue-500 hover:underline">đồng hồ</a>,
              túi xách, giày dép,
              <a href="#" class="text-blue-500 hover:underline">mũ nón</a>,
              <a href="#" class="text-blue-500 hover:underline">kính mắt</a>,
              <a href="#" class="text-blue-500 hover:underline">trang sức</a>,
              mỹ phẩm, máy chăm sóc da… thì Vua Hàng Hiệu cũng sẽ đảm bảo cung
              cấp cho bạn những sản phẩm chất lượng ưng ý tuyệt đối.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Là một kênh bán hàng trực tuyến uy tín, Vua Hàng Hiệu luôn cam kết
              mang lại cho khách hàng những trải nghiệm mua sắm ấn tượng, với
              các sản phẩm chính hãng cùng mức giá “siêu hời”. Mọi thông tin về
              người mua và các đối tác đều được bảo mật tuyệt đối. Các hoạt động
              giao dịch thanh toán tại Vua Hàng Hiệu luôn được đảm bảo diễn ra
              nhanh chóng, an toàn.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Đến với sàn thương mại điện tử Vua Hàng Hiệu ngay hôm nay để mua
              hàng hiệu cao cấp giá tốt và trải nghiệm dịch vụ chăm sóc khách
              hàng ấn tượng tại đây. Đặc biệt khi đăng ký thành viên Vua Hàng
              Hiệu, bạn sẽ nhận được những ưu đãi độc quyền siêu hấp dẫn:
              Freeship cho mọi đơn hàng, nhận voucher 200K vào tháng sinh nhật,
              được
              <a href="#" class="text-blue-500 hover:underline"
                >mã giảm giá đến 50%</a
              >, đổi điểm khi mua hàng và còn rất nhiều quà tặng thú vị khác
              nữa.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Hãy truy cập ngay
              <a
                href="https://vuahanghieu.com"
                target="_blank"
                class="text-blue-500 hover:underline"
                >Vuahanghieu.com</a
              >
              hoặc tải ngay
              <a href="#" class="text-blue-500 hover:underline"
                >ứng dụng Vua Hàng Hiệu</a
              >
              về điện thoại ngay hôm nay!
            </p>
          </section>
        </div>

        <button
          class="btn text-gray border rounded-0 text-uppercase border-gray border-2 font-semibold py-2 px-6 shadow-md d-block mx-auto"
          type="button"
          @click="toggleCollapse"
        >
          {{ isExpanded ? "Thu Gọn" : "Xem Thêm" }}
        </button>
      </main>
    </div>

    <!-- Contact and Footer  -->
    <section class="subscribe-section">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-4 text-md-start text-center">
            <div class="subscribe-label">Đăng ký để nhận ưu đãi qua email:</div>
          </div>
          <!-- Form đăng ký -->
          <div class="col-md-4 mb-3 mb-md-0">
            <div class="d-flex subscribe-form">
              <input type="email" placeholder="Nhập email của bạn" />
              <button>Đăng ký</button>
            </div>
            <div class="subscribe-policy">
              Bằng cách đăng ký, bạn đồng ý với
              <a href="#">Chính sách bảo mật của chúng tôi</a>
            </div>
          </div>

          <!-- Icon mạng xã hội -->
          <div class="col-md-4 text-md-end text-center">
            <div class="social-icons">
              <a href="#"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-facebook"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951"
                  /></svg
              ></a>
              <a href="#"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-instagram"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598 2.5 2.5 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334"
                  /></svg
              ></a>
              <a href="#"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-pinterest"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M8 0a8 8 0 0 0-2.915 15.452c-.07-.633-.134-1.606.027-2.297.146-.625.938-3.977.938-3.977s-.239-.479-.239-1.187c0-1.113.645-1.943 1.448-1.943.682 0 1.012.512 1.012 1.127 0 .686-.437 1.712-.663 2.663-.188.796.4 1.446 1.185 1.446 1.422 0 2.515-1.5 2.515-3.664 0-1.915-1.377-3.254-3.342-3.254-2.276 0-3.612 1.707-3.612 3.471 0 .688.265 1.425.595 1.826a.24.24 0 0 1 .056.23c-.061.252-.196.796-.222.907-.035.146-.116.177-.268.107-1-.465-1.624-1.926-1.624-3.1 0-2.523 1.834-4.84 5.286-4.84 2.775 0 4.932 1.977 4.932 4.62 0 2.757-1.739 4.976-4.151 4.976-.811 0-1.573-.421-1.834-.919l-.498 1.902c-.181.695-.669 1.566-.995 2.097A8 8 0 1 0 8 0"
                  /></svg
              ></a>
              <a href="#"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-twitter-x"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M12.6.75h2.454l-5.36 6.142L16 15.25h-4.937l-3.867-5.07-4.425 5.07H.316l5.733-6.57L0 .75h5.063l3.495 4.633L12.601.75Zm-.86 13.028h1.36L4.323 2.145H2.865z"
                  /></svg
              ></a>
              <a href="#"
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="currentColor"
                  class="bi bi-rss"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z"
                  />
                  <path
                    d="M5.5 12a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0m-3-8.5a1 1 0 0 1 1-1c5.523 0 10 4.477 10 10a1 1 0 1 1-2 0 8 8 0 0 0-8-8 1 1 0 0 1-1-1m0 4a1 1 0 0 1 1-1 6 6 0 0 1 6 6 1 1 0 1 1-2 0 4 4 0 0 0-4-4 1 1 0 0 1-1-1"
                  /></svg
              ></a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer class="bg-light text-center text-lg-start">
      <div class="container p-4">
        <div class="row row-cols-4">
          <div class="col-lg-3 col-md-6 mb-4 mb-md-0">
            <h5 class="text-uppercase fw-semibold">THÔNG TIN</h5>
            <ul class="list-unstyled">
              <a href=""><li>Gọi hotline về Vua Hàng Hiệu Việt Nam</li></a>
              <a href=""><li>Quy chế hoạt động</li></a>
              <a href=""><li>Hợp tác với Vua Hàng Hiệu</li></a>
              <a href=""><li>Chương trình Affiliate - Cộng tác viên</li></a>
              <a href=""><li>Tuyển dụng</li></a>
              <a href=""><li>Liên hệ</li></a>
            </ul>
            <div class="d-flex flex-column w-50">
              <img
                src="@/assets/images/footer/da-dang-ky-bo-cong-thuong.svg"
                alt="Ba Dang Ky"
              />
              <img
                src="@/assets/images/footer/dmca_copyright_protected150b.png"
                alt="DMCA"
              />
              <div class="d-flex flex-row w-100 gap-2">
                <img
                  class="w-50"
                  src="@/assets/images/footer/business-trust-seal-trust-lock.png"
                  alt="Business"
                />
                <img
                  class="w-50"
                  src="@/assets/images/footer/privacy-trust-seal-trust-lock.png"
                  alt="Privacy"
                />
              </div>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 mb-4 mb-md-0">
            <h5 class="text-uppercase fw-semibold">CÂU HỎI THƯỜNG GẶP</h5>
            <ul class="list-unstyled">
              <li>
                <a href="#"
                  >Hướng dẫn cách tra cứu mã đơn hàng mua trên Vua Hàng Hiệu</a
                >
              </li>
              <li>
                <a href="#">Sản phẩm cần đổi hết hàng?</a>
              </li>
              <li>
                <a href="#"
                  >Nếu không có hóa đơn mua hàng tôi có thể trả lại sản phẩm
                  không?</a
                >
              </li>
              <li>
                <a href="#"
                  >Đơn hàng nhận được bị thiếu so với đơn hàng đã đặt</a
                >
              </li>
              <li>
                <a href="#"
                  >Sản phẩm nhận được không giống với hình ảnh trên website?</a
                >
              </li>
              <li>
                <a href="#"
                  >Vì sao tôi nhận được thông báo đơn hàng đã hủy do hết
                  hàng?</a
                >
              </li>
              <li>
                <a href="#"
                  >Nếu gặp vấn đề trong quá trình sử dụng sản phẩm, tôi cần liên
                  hệ với ai?</a
                >
              </li>
            </ul>
            <h6 class="fw-semibold">Tải ứng dụng Vua Hàng Hiệu ngay!</h6>
            <div class="mt-3 d-flex flex-row gap-2 w-100">
              <a href="#">
                <img
                  class="w-100 h-100"
                  src="@/assets/images/footer/apple-store.svg"
                  alt="App Store"
              /></a>
              <a href="#">
                <img
                  class="w-100 h-100"
                  src="@/assets/images/footer/google-play.svg"
                  alt="Google Play"
              /></a>
              <a href="#">
                <img
                  class="w-100 h-100"
                  src="@/assets/images/footer/huawei-gallery.svg"
                  alt="AppGallery"
              /></a>
            </div>
          </div>
          <div class="col-lg-3 col-md-6 mb-4 mb-md-0">
            <h5 class="text-uppercase fw-semibold">CHĂM SÓC KHÁCH HÀNG</h5>
            <ul class="list-unstyled">
              <li><a href="#">Chính sách bán hàng</a></li>
              <li><a href="#">Chính sách bảo hành</a></li>
              <li><a href="#">Chính sách giao hàng</a></li>
              <li><a href="#">Chính sách đổi trả và hoàn tiền</a></li>
              <li><a href="#">Chính sách thanh toán</a></li>
              <li><a href="#">Chính sách bảo mật thanh toán</a></li>
              <li><a href="#">Chính sách bảo mật</a></li>
              <li><a href="#">Điều khoản dịch vụ</a></li>
              <li><a href="#">Cơ chế giải quyết tranh chấp</a></li>
              <li><a href="#">Dịch vụ giao hàng siêu tốc 2H</a></li>
              <li><a href="#">Hướng dẫn đăng ký thành viên</a></li>
              <li><a href="#">Quyền lợi thành viên</a></li>
              <li><a href="#">Hướng dẫn mua hàng trả góp</a></li>
              <li><a href="#">Báo cáo vi phạm (Reporting Infringements)</a></li>
            </ul>
          </div>
          <div class="col-lg-3 col-md-6 mb-4 mb-md-0">
            <h5 class="text-uppercase fw-semibold">Dịch vụ khách hàng</h5>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Công ty</div>
              <div class="col-7">Công Ty Cổ Phần Thương Mại Vua Hàng Hiệu</div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Hotline</div>
              <div class="col-7">093.934.8888</div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Tổng đài</div>
              <div class="col-7">1900 232322</div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Email</div>
              <div class="col-7">cskh@vuahanghieu.com</div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Thời gian</div>
              <div class="col-7">
                Thứ 2 - Thứ 6: 8:00 - 17:00<br />
                Thứ 7: 8:00 - 11:30
              </div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Địa chỉ</div>
              <div class="col-7">
                Tầng 3, Tòa nhà 24T3 Thanh Xuân Complex,<br />
                Số 6 Lê Văn Thiêm, Thanh Xuân Trung, Thanh Xuân, Hà Nội
              </div>
            </div>
            <div class="row mb-2">
              <div class="col-5 fw-semibold">Mã số thuế</div>
              <div class="col-7">
                0108603370 do Sở Kế hoạch và Đầu tư Hà Nội cấp ngày 28/01/2019
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
    <!-- Copyright © 2024 Vua Hàng Hiệu. All rights reserved. -->
    <div
      class="d-flex justify-content-between align-items-center container my-2"
    >
      <div class="d-flex align-items-center gap-3" style="font-size: 10px">
        <p class="fst-italic mb-0">© 2025 VUA HÀNG HIỆU.</p>
        <a href=""><p class="text-uppercase mb-0">Điều khoản</p></a>
        <a href=""><p class="text-uppercase mb-0">Chính sách bảo mật</p></a>
      </div>
      <img
        src="@/assets/images/footer/payment-method.svg"
        alt="Thanh toán"
        height="28"
      />
    </div>

    <!-- List category footer -->
    <div class="border-top">
      <div class="container my-4">
        <div class="row">
          <!-- Cột 1 -->
          <div class="col-md-2 col-6 mb-4">
            <a href="#"><h6 class="fw-bold">TÚI XÁCH</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Túi xách nam</a></li>
              <li><a href="#">Túi nữ</a></li>
              <li><a href="#">Túi đeo chéo</a></li>
              <li><a href="#">Ví cao cấp</a></li>
              <li><a href="#">Túi đeo vai</a></li>
              <li><a href="#">Túi xách tay</a></li>
              <li><a href="#">Balo</a></li>
              <li><a href="#">Túi tote</a></li>
              <li><a href="#">Túi đeo hông</a></li>
              <li><a href="#">Ví dáng dài</a></li>
              <li><a href="#">Túi trống</a></li>
              <li><a href="#">Vali</a></li>
              <li><a href="#">Túi laptop</a></li>
              <li><a href="#">Túi Golf</a></li>
              <li><a href="#">Túi đeo cổ</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">THỜI TRANG CAO CẤP</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Thời trang nam</a></li>
              <li><a href="#">Áo thun</a></li>
              <li><a href="#">Quần jeans</a></li>
              <li><a href="#">Váy liền</a></li>
              <li><a href="#">Áo sơ mi</a></li>
              <li><a href="#">Áo khoác</a></li>
              <li><a href="#">Áo hoodie</a></li>
              <li><a href="#">Chân váy</a></li>
              <li><a href="#">Áo vest</a></li>
              <li><a href="#">Áo polo</a></li>
            </ul>
          </div>

          <!-- Cột 2 -->
          <div class="col-md-2 col-6 mb-4">
            <a href="#"><h6 class="fw-bold">SKINCARE</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Máy rửa mặt</a></li>
              <li><a href="#">Máy triệt lông</a></li>
              <li><a href="#">Máy trị mụn</a></li>
              <li><a href="#">Máy xông hơi mặt</a></li>
              <li><a href="#">Máy hút mụn</a></li>
              <li><a href="#">Máy massage mặt</a></li>
              <li><a href="#">Cây lăn massage</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">VOUCHER & DỊCH VỤ</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Order hàng quốc tế</a></li>
              <li><a href="#">Hàng hiệu giảm 50%</a></li>
              <li><a href="#">Khung giờ săn sale</a></li>
              <li><a href="#">Sale đồng giá</a></li>
              <li><a href="#">Sale Ưu Đãi Tháng 7</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">ĐỒNG HỒ</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Đồng hồ nam</a></li>
              <li><a href="#">Đồng hồ nữ</a></li>
              <li><a href="#">Đồng hồ đôi</a></li>
              <li><a href="#">Dây đồng hồ</a></li>
            </ul>
          </div>

          <!-- Cột 3 -->
          <div class="col-md-2 col-6 mb-4">
            <a href="#"><h6 class="fw-bold">MŨ NÓN HIỆU</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Nón nam</a></li>
              <li><a href="#">Nón nữ</a></li>
              <li><a href="#">Mũ Golf</a></li>
              <li><a href="#">Mũ cói</a></li>
              <li><a href="#">Mũ len</a></li>
              <li><a href="#">Mũ nồi</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">CHĂM SÓC CƠ THỂ</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Lăn khử mùi</a></li>
              <li><a href="#">Bàn chải điện</a></li>
              <li><a href="#">Máy uốn mi</a></li>
              <li><a href="#">Chăm sóc răng miệng</a></li>
              <li><a href="#">Chăm sóc móng</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">PHỤ KIỆN CÔNG NGHỆ</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Ốp lưng</a></li>
              <li><a href="#">Vỏ bọc</a></li>
              <li><a href="#">Phụ kiện điện thoại</a></li>
              <li><a href="#">Phụ kiện Laptop</a></li>
            </ul>
          </div>

          <!-- Cột 4 -->
          <div class="col-md-3 col-6 mb-4">
            <a href="#"><h6 class="fw-bold">NƯỚC HOA</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Nước hoa nam</a></li>
              <li><a href="#">Nước hoa nữ</a></li>
              <li><a href="#">EDP</a></li>
              <li><a href="#">EDT</a></li>
              <li><a href="#">Parfum</a></li>
              <li><a href="#">Cologne</a></li>
              <li><a href="#">Nước hoa Niche</a></li>
              <li><a href="#">Nước hoa mini</a></li>
              <li><a href="#">Nước hoa Unisex</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">KÍNH MẮT</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Kính nam</a></li>
              <li><a href="#">Kính nữ</a></li>
              <li><a href="#">Kính chống nắng</a></li>
              <li><a href="#">Kính trẻ em</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">CHĂM SÓC TÓC</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Serum tóc</a></li>
              <li><a href="#">Dầu gội</a></li>
              <li><a href="#">Dầu xả</a></li>
              <li><a href="#">Xịt thơm tóc</a></li>
              <li><a href="#">Bộ chăm sóc tóc</a></li>
            </ul>
          </div>

          <!-- Cột 5 -->
          <div class="col-md-3 col-6 mb-4">
            <a href="#"><h6 class="fw-bold">HÀNG HIỆU USED</h6></a>

            <a href="#"><h6 class="fw-bold mt-4">MỸ PHẨM</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Sữa rửa mặt</a></li>
              <li><a href="#">Kem chống nắng</a></li>
              <li><a href="#">Toner</a></li>
              <li><a href="#">Serum</a></li>
              <li><a href="#">Kem dưỡng da</a></li>
              <li><a href="#">Son môi</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">SON MÔI</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Son lì</a></li>
              <li><a href="#">Son kem</a></li>
              <li><a href="#">Son dưỡng</a></li>
              <li><a href="#">Son nước</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">TRANG ĐIỂM</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Phấn nước</a></li>
              <li><a href="#">Phấn mắt</a></li>
              <li><a href="#">Kẻ mắt</a></li>
              <li><a href="#">Phấn má</a></li>
              <li><a href="#">Kem nền</a></li>
              <li><a href="#">Mascara</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">GIÀY</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Giày nam</a></li>
              <li><a href="#">Giày nữ</a></li>
              <li><a href="#">Sneaker</a></li>
              <li><a href="#">Giày thể thao</a></li>
              <li><a href="#">Giày cao gót</a></li>
              <li><a href="#">Sandals</a></li>
              <li><a href="#">Giày Slip On</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">TRANG SỨC CAO CẤP</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Dây chuyền</a></li>
              <li><a href="#">Nhẫn</a></li>
              <li><a href="#">Vòng đeo tay</a></li>
              <li><a href="#">Khuyên tai</a></li>
              <li><a href="#">Nhẫn cưới</a></li>
            </ul>

            <a href="#"><h6 class="fw-bold mt-4">HÀNG CHÍNH HÃNG KHÁC</h6></a>
            <ul class="list-unstyled">
              <li><a href="#">Phụ kiện thời trang</a></li>
              <li><a href="#">Dép</a></li>
              <li><a href="#">Thắt lưng</a></li>
              <li><a href="#">Bút viết</a></li>
              <li><a href="#">Nến thơm</a></li>
              <li><a href="#">Ô/Dù</a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import bannerLeft1 from "@/assets/images/banner/1.webp";
import bannerLeft2 from "@/assets/images/banner/2.webp";
import bannerLeft3 from "@/assets/images/banner/3.webp";
import bannerLeft4 from "@/assets/images/banner/4.webp";
import bannerLeft5 from "@/assets/images/banner/5.webp";
import bannerLeft6 from "@/assets/images/banner/6.webp";
import bannerLeft7 from "@/assets/images/banner/7.webp";
import bannerLeft8 from "@/assets/images/banner/8.webp";
import bannerLeft9 from "@/assets/images/banner/9.webp";
import bannerLeft10 from "@/assets/images/banner/10.webp";
import bannerRight1 from "@/assets/images/deal/ao-khoac-lacoste-sport-bi-material-colourblock-full-zip-sweatshirt-size-xs-618f183c69782-13112021084324.webp";
import bannerRight2 from "@/assets/images/deal/6371ea9cd7218-14112022141332.webp";
import bannerRight3 from "@/assets/images/deal/ao-thun-nam-nike-as-m-nsw-club-tee-ar4999-013-mau-den-size-s-6556d6ee6f7a3-17112023095854.webp";
import imageDealCategory1 from "@/assets/images/iconDeal/1.webp";
import imageDealCategory2 from "@/assets/images/iconDeal/2.webp";
import imageDealCategory3 from "@/assets/images/iconDeal/3.webp";
import imageDealCategory4 from "@/assets/images/iconDeal/4.webp";
import imageDealCategory5 from "@/assets/images/iconDeal/5.webp";
import imageDealCategory6 from "@/assets/images/iconDeal/6.webp";
import imageDealCategory7 from "@/assets/images/iconDeal/7.webp";
import imageDealCategory8 from "@/assets/images/iconDeal/8.webp";

import bannerSecond1 from "@/assets/images/banner/11.webp";
import bannerSecond2 from "@/assets/images/banner/12.webp";
import bannerSecond3 from "@/assets/images/banner/13.webp";
import bannerSecond4 from "@/assets/images/banner/14.webp";
import bannerSecond5 from "@/assets/images/banner/15.webp";
import bannerSecond6 from "@/assets/images/banner/16.webp";
import bannerSecond7 from "@/assets/images/banner/17.webp";
import bannerSecond8 from "@/assets/images/banner/18.webp";
import bannerSecond9 from "@/assets/images/banner/19.webp";
import bannerSecond10 from "@/assets/images/banner/20.webp";
export default {
  components: { VueSlickCarousel },
  data() {
    return {
      bannerImages: [
        { image: bannerLeft1, alt: "banner-1", url: "#" },
        { image: bannerLeft2, alt: "banner-2", url: "#" },
        { image: bannerLeft3, alt: "banner-3", url: "#" },
        { image: bannerLeft4, alt: "banner-4", url: "#" },
        { image: bannerLeft5, alt: "banner-5", url: "#" },
        { image: bannerLeft6, alt: "banner-6", url: "#" },
        { image: bannerLeft7, alt: "banner-7", url: "#" },
        { image: bannerLeft8, alt: "banner-8", url: "#" },
        { image: bannerLeft9, alt: "banner-9", url: "#" },
        { image: bannerLeft10, alt: "banner-10", url: "#" },
      ],
      deals: [
        {
          title: "Deal HOT",
          image: bannerRight1,
          sale: 6,
          price: "4.560.000",
          oldPrice: "4.900.000",
          url: "#",
        },
        {
          title: "Deal Ngon Hoành Tráng",
          image: bannerRight2,
          sale: 29,
          price: "850.000",
          oldPrice: "1.200.000",
          url: "#",
        },
        {
          title: "Deal HOT",
          image: bannerRight3,
          sale: 15,
          price: "510.000",
          oldPrice: "600.000",
          url: "#",
        },
      ],
      categories: [
        { label: "Ưu Đãi Tháng 10", url: "#", image: imageDealCategory1 },
        { label: "Deal khách mới", url: "#", image: imageDealCategory2 },
        { label: "Hot deals", url: "#", image: imageDealCategory3 },
        { label: "Bán Chạy", url: "#", image: imageDealCategory4 },
        { label: "Hàng Quốc Tế", url: "#", image: imageDealCategory5 },
        { label: "Cẩm Nang", url: "#", image: imageDealCategory6 },
        { label: "New Arrivals", url: "#", image: imageDealCategory7 },
        { label: "Quà tặng", url: "#", image: imageDealCategory8 },
      ],
      bannerSettings: {
        autoplay: false,
        dots: true,
        arrows: false,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1,
      },
      dealSettings: {
        autoplay: false,
        dots: false,
        arrows: true,
        infinite: false,
        slidesToShow: 2,
        slidesToScroll: 2,
      },

      //products
      products: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
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
            settings: { slidesToShow: 4 },
          },
          {
            breakpoint: 992,
            settings: { slidesToShow: 3 },
          },
          {
            breakpoint: 768,
            settings: { slidesToShow: 2 },
          },
          {
            breakpoint: 576,
            settings: { slidesToShow: 1 },
          },
        ],
      },

      //Banner Second
      bannerSecond: [
        {
          image: bannerSecond1,
          alt: "banner-second-1",
          url: "#",
        },
        {
          image: bannerSecond2,
          alt: "banner-second-2",
          url: "#",
        },
        {
          image: bannerSecond3,
          alt: "banner-second-3",
          url: "#",
        },
        {
          image: bannerSecond4,
          alt: "banner-second-4",
          url: "#",
        },
        {
          image: bannerSecond5,
          alt: "banner-second-5",
          url: "#",
        },
        {
          image: bannerSecond6,
          alt: "banner-second-6",
          url: "#",
        },
        {
          image: bannerSecond7,
          alt: "banner-second-7",
          url: "#",
        },
        {
          image: bannerSecond8,
          alt: "banner-second-8",
          url: "#",
        },
        {
          image: bannerSecond9,
          alt: "banner-second-9",
          url: "#",
        },
        {
          image: bannerSecond10,
          alt: "banner-second-10",
          url: "#",
        },
      ],
      bannerSecondCarouselSettings: {
        autoplay: false,
        dots: false,
        arrows: false,
        infinite: true,
        slidesToShow: 2,
        slidesToScroll: 2,
      },

      // Category Future
      categoriesFuture: [
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
        {
          url: "#",
          title: "Nước hoa Nam",
          image: require("@/assets/images/category/1.webp"),
        },
      ],
      categoryFutureCarouselSettings: {
        infinite: false,
        slidesToShow: 8,
        slidesToScroll: 1,
        arrows: true,
        dots: false,
        autoplay: false,
        responsive: [
          { breakpoint: 1200, settings: { slidesToShow: 5 } },
          { breakpoint: 992, settings: { slidesToShow: 4 } },
          { breakpoint: 768, settings: { slidesToShow: 3 } },
          { breakpoint: 576, settings: { slidesToShow: 2 } },
        ],
      },

      // Brand Future
      brandsFuture: [
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/2.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/3.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/4.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/5.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/6.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/7.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/8.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/9.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/10.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/11.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/12.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/13.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/14.webp"),
        },
        {
          url: "#",
          title: "Thương hiệu Nổi bật",
          image: require("@/assets/images/brand/15.webp"),
        },
      ],
      brandFutureCarouselSettings: {
        infinite: false,
        slidesToShow: 6,
        slidesToScroll: 1,
        arrows: true,
        dots: false,
        autoplay: false,
        responsive: [
          { breakpoint: 1200, settings: { slidesToShow: 5 } },
          { breakpoint: 992, settings: { slidesToShow: 4 } },
          { breakpoint: 768, settings: { slidesToShow: 3 } },
          { breakpoint: 576, settings: { slidesToShow: 2 } },
        ],
      },

      //trending search
      trendingSearch: [
        {
          title: "Coach",
          url: "#",
          quantity: 1870,
          image: require("@/assets/images/searchTrending/1.webp"),
        },
        {
          title: "Túi",
          url: "#",
          quantity: 15585,
          image: require("@/assets/images/searchTrending/2.webp"),
        },
        {
          title: "Nước Hoa Nữ",
          url: "#",
          quantity: 3298,
          image: require("@/assets/images/searchTrending/3.webp"),
        },
        {
          title: "Đồng Hồ Nam",
          url: "#",
          quantity: 7786,
          image: require("@/assets/images/searchTrending/4.webp"),
        },
        {
          title: "Narciso",
          url: "#",
          quantity: 222,
          image: require("@/assets/images/searchTrending/5.webp"),
        },
      ],

      // Suggested products
      productsSuggest: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List perfume
      productPerfume: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Son môi cao cấp Longlasting Lipstick - Màu Đỏ Ruby",
          price: "199.000",
          oldPrice: "279.000",
          discount: 29,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Áo khoác nam Lacoste Sport - Mẫu mới",
          price: "1.120.000",
          oldPrice: "1.320.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Serum Vitamin C - Dưỡng sáng da",
          price: "320.000",
          oldPrice: "340.000",
          discount: 6,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          url: "#",
          name: "Túi đeo chéo MCM Patricia - Cognac",
          price: "2.350.000",
          oldPrice: "2.950.000",
          discount: 20,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List watch
      productWatch: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List cosmetic
      productCosmetic: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List Hat
      productHat: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List Handbag
      productHandbag: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List Shoes
      productShoes: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List Fashion
      productFashion: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List EyeWear
      productEyeWear: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      // List LipStick
      productLipStick: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      //PickleBall
      productPickleBall: [
        {
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
      ],

      //List blog
      blog: [
        {
          url: "#",
          title:
            "Trend tạo ảnh bằng AI Gemini: Hướng dẫn chi tiết cho người mới",
          image: require("@/assets/images/blog/1.webp"),
          date: "06/10/2025",
          author: "Vuahanghieu",
        },
        {
          url: "#",
          title:
            "Mugler Xuân/Hè 2026: Lời kêu gọi quyến rũ và cám dỗ thơ mộng với “Stardust Aphrodite”",
          image: require("@/assets/images/blog/2.webp"),
          date: "04/10/2025",
          author: "Vuahanghieu",
        },
        {
          url: "#",
          title: "LOEWE Xuân/Hè 2026: Hành Trình Kiến Tạo Hình Hài Mới",
          image: require("@/assets/images/blog/3.webp"),
          date: "03/10/2025",
          author: "Vuahanghieu",
        },
        {
          url: "#",
          title: "Top 10 Vòng Tay Van Cleef Bán Chạy, Được Săn Đón Hiện Nay",
          image: require("@/assets/images/blog/4.webp"),
          date: "01/10/2025",
        },
        {
          url: "#",
          title: "Review Các Mẫu Túi Lyn Nơ Bán Chạy, Vô Cùng Điệu Đà Hiện Nay",
          image: require("@/assets/images/blog/5.webp"),
          date: "15/09/2025",
        },
        {
          url: "#",
          title: "Top 10 Kính Râm Gucci Bán Chạy, Cực Sành Điệu Trong Năm 2025",
          image: require("@/assets/images/blog/6.webp"),
          date: "10/09/2025",
        },
        {
          url: "#",
          title: "Top 10 Kính Râm Gucci Bán Chạy, Cực Sành Điệu Trong Năm 2025",
          image: require("@/assets/images/blog/7.webp"),
          date: "04/09/2025",
        },
        {
          url: "#",
          title:
            "Nước Hoa Minh Béo Là Gì? Review Có Nên Mua Nước Hoa Minh Béo Hay Không?",
          image: require("@/assets/images/blog/8.webp"),
          date: "08/08/2025",
        },
      ],

      isExpanded: false,
    };
  },
  methods: {
    toggleCollapse() {
      this.isExpanded = !this.isExpanded;
      const collapseElement = document.getElementById("collapseDescription");
      if (this.isExpanded) {
        collapseElement.classList.add("show");
      } else {
        collapseElement.classList.remove("show");
      }
    },
  },
};
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* ===== Header ===== */
#main-header {
  border-bottom: 2px solid #d1d1d1;
}

#main-header .truncate-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2; /* Giới hạn 2 dòng */
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
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

.deal-carousel-wrapper .slick-next {
  right: -5px;
}

.deal-carousel-wrapper .slick-prev {
  left: -10px;
}

.deal-carousel-wrapper .slick-prev,
.deal-carousel-wrapper .slick-next {
  top: 40%;
  z-index: 1000;
}

.banner-left .slick-slide img {
  height: 315px;
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
  transition: all 0.3s ease;
}

.product-card img {
  object-fit: contain;
  height: 220px;
  width: 100%;
}

.badge {
  font-size: 0.8rem;
}

.category-future .card {
  margin: 10px;
  border: none;
}

.category-future .card .img-wrapper {
  background-color: #f5f5f5;
  width: 150px;
  height: 150px;
}

.category-future .card img {
  object-fit: contain;
}

.category-future .slick-prev,
.category-future .slick-next {
  top: 45%;
}

.brand-future .card .img-wrapper {
  height: 80px;
  object-fit: contain;
}

.brand-future .card .img-wrapper img {
  height: 80px;
  object-fit: contain;
}

.brand-future .slick-prev,
.brand-future .slick-next {
  top: 50%;
}

.trending-search {
  background-color: #f5f5f5;
}

.trending-search img {
  width: 100px;
  height: 100px;
  object-fit: contain;
  padding: 10px;
  background-color: white;
}
.description-introduce * {
  line-height: 1.5;
  color: #000;
  font-size: 15px;
}

.description-introduce h4 {
  font-size: 25px;
}
.description-introduce a {
  color: blue;
}

footer {
  background: #fff;
  color: #000;
  font-size: 13px;
  border-top: 1px solid #e0e0e0;
  line-height: 1.8;
}
footer h6 {
  font-weight: 700;
  font-size: 14px;
  text-transform: uppercase;
  margin-bottom: 10px;
}
.footer-list {
  display: flex;
  flex-wrap: wrap;
  gap: 4px 6px;
}
.footer-list a {
  position: relative;
  text-decoration: none;
  color: #000;
  white-space: nowrap;
  padding-right: 6px;
  margin-right: 6px;
}
.footer-list a:not(:last-child)::after {
  content: "|";
  position: absolute;
  right: 0;
  color: #999;
}
.footer-list a:hover {
  text-decoration: underline;
}
hr {
  border-color: #ddd;
}
.subscribe-section {
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
  padding: 30px 0;
  background-color: #fff;
}
.subscribe-label {
  font-weight: 600;
  font-size: 15px;
  margin-bottom: 10px;
}
.subscribe-form input {
  border: 1px solid #ccc;
  border-right: none;
  height: 40px;
  padding: 0 12px;
  width: 260px;
  outline: none;
}
.subscribe-form button {
  background: #000;
  color: #fff;
  border: none;
  height: 40px;
  padding: 0 20px;
  font-weight: 600;
  text-transform: uppercase;
}
.subscribe-form button:hover {
  background: #333;
}
.subscribe-policy {
  font-size: 13px;
  margin-top: 8px;
}
.subscribe-policy a {
  color: #000;
  text-decoration: none;
}
.subscribe-policy a:hover {
  text-decoration: underline;
}
.social-icons a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  background: #4a4a4a;
  color: #fff;
  margin-left: 6px;
  text-decoration: none;
  font-size: 16px;
}
.social-icons a:hover {
  background: #000;
}
</style>
