<template>
  <div id="main">
    <!-- Header -->
    <header id="main-header" class="bg-white">
      <!-- Top black bar -->
      <div class="bg-dark py-1 text-white">
        <div class="d-flex justify-content-end container">
          <ul class="nav">
            <li class="nav-item">
              <a class="text-warning text-uppercase nav-link" href="/createShop"
                >Tạo Shop</a
              >
            </li>
            <li class="nav-item dropdown">
              <a
                class="text-white text-uppercase nav-link dropdown-toggle"
                href="#"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Tài khoản
              </a>
              <ul class="dropdown-menu dropdown-menu-end">
                <li>
                  <a class="text-uppercase dropdown-item" href="/login"
                    >Đăng nhập</a
                  >
                </li>
                <li>
                  <a class="text-uppercase dropdown-item" href="/signup"
                    >Đăng ký</a
                  >
                </li>
              </ul>
            </li>
            <li class="nav-item">
              <a
                class="d-flex align-items-center text-white text-uppercase nav-link"
                href="/cart"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="14"
                  height="14"
                  fill="currentColor"
                  class="me-2 bi bi-cart3"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .49.598l-1 5a.5.5 0 0 1-.465.401l-9.397.472L4.415 11H13a.5.5 0 0 1 0 1H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5M3.102 4l.84 4.479 9.144-.459L13.89 4zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4m7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4m-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2m7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2"
                  />
                </svg>
                Giỏ hàng
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div class="py-5 container">
        <div class="d-flex align-items-center justify-content-between row">
          <!-- Logo -->
          <nuxt-link
            to="/"
            class="d-flex align-items-center mb-2 mb-md-0 col-md-3 col-12"
          >
            <img
              src="@/assets/images/vuahanghieu-new.svg"
              alt="logo"
              class="img-fluid"
              style="max-height: 50px"
            />
          </nuxt-link>

          <!-- Search bar with Ant Design dropdown -->
          <div class="mb-2 mb-md-0 col-md-6 col-12">
            <a-dropdown
              :visible="showDropdown"
              :trigger="[]"
              placement="bottomLeft"
            >
              <div class="input-group">
                <input
                  type="text"
                  class="form-control header-search"
                  placeholder="Tìm kiếm sản phẩm, thương hiệu..."
                  @focus="showDropdown = true"
                  @blur="showDropdown = false"
                  v-model="searchQuery"
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

              <!-- Dropdown menu -->
              <div
                slot="overlay"
                class="search-custom-w bg-white shadow-lg border rounded search-dropdown-content p-4"
                @mousedown.prevent
              >
                <!-- Có thể bạn quan tâm -->
                <div class="mb-4">
                  <h6 class="fw-bold mb-3">CÓ THỂ BẠN QUAN TÂM</h6>
                  <nuxt-link
                    v-for="(item, index) in trendingLinks"
                    :key="index"
                    :to="item.url"
                    class="d-flex flex-row align-items-center text-decoration-none text-dark mb-2"
                  >
                    <div class="icon-trending me-2">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        width="16"
                        height="16"
                        fill="currentColor"
                        class="bi bi-graph-up-arrow text-danger"
                        viewBox="0 0 16 16"
                      >
                        <path
                          fill-rule="evenodd"
                          d="M0 0h1v15h15v1H0zm10 3.5a.5.5 0 0 1 .5-.5h4a.5.5 0 0 1 .5.5v4a.5.5 0 0 1-1 0V4.9l-3.613 4.417a.5.5 0 0 1-.74.037L7.06 6.767l-3.656 5.027a.5.5 0 0 1-.808-.588l4-5.5a.5.5 0 0 1 .758-.06l2.609 2.61L13.445 4H10.5a.5.5 0 0 1-.5-.5"
                        />
                      </svg>
                    </div>
                    <span>{{ item.title }}</span>
                  </nuxt-link>
                </div>

                <!-- Danh mục nổi bật -->
                <div class="mb-4">
                  <h6 class="fw-bold mb-3">DANH MỤC NỔI BẬT</h6>
                  <div class="row g-2">
                    <div
                      v-for="cat in categoriesSearch"
                      :key="cat.name"
                      class="col-4 col-md-2"
                    >
                      <nuxt-link
                        :to="cat.link"
                        class="d-block text-decoration-none text-center p-2 bg-light rounded"
                      >
                        <div
                          class="mb-1"
                          style="
                            height: 50px;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                          "
                        >
                          <img
                            :src="cat.icon"
                            :alt="cat.name"
                            style="
                              max-height: 100%;
                              max-width: 100%;
                              object-fit: contain;
                            "
                          />
                        </div>
                        <small class="text-dark d-block">{{ cat.name }}</small>
                      </nuxt-link>
                    </div>
                  </div>
                </div>

                <!-- Thương hiệu nổi bật -->
                <div>
                  <h6 class="fw-bold mb-3">THƯƠNG HIỆU NỔI BẬT</h6>
                  <div class="row g-2">
                    <div
                      v-for="(brand, idx) in brandsSearch"
                      :key="idx"
                      class="col-4 col-md-2"
                    >
                      <nuxt-link
                        :to="brand.link"
                        class="d-block text-decoration-none text-center p-2 bg-light rounded"
                      >
                        <div
                          style="
                            height: 50px;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                          "
                        >
                          <img
                            :src="brand.logo"
                            :alt="brand.name"
                            style="
                              max-height: 100%;
                              max-width: 100%;
                              object-fit: contain;
                            "
                          />
                        </div>
                      </nuxt-link>
                    </div>
                  </div>
                </div>
              </div>
            </a-dropdown>
          </div>

          <!-- Auth box -->
          <div
            class="d-flex justify-content-md-end justify-content-start mt-3 mt-md-0 col-md-3 col-12"
          >
            <div
              class="d-flex align-items-center shadow-sm rounded-pill border p-1"
            >
              <nuxt-link
                to="/login"
                class="d-flex align-items-center px-2 py-1 text-decoration-none text-dark"
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
              <span class="border-end" style="height: 20px"></span>
              <nuxt-link
                to="/signup"
                class="d-flex align-items-center px-2 py-1 text-decoration-none text-dark"
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
          class="slider-right p-3 rounded col-md-4 col-12"
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
                  <div class="deal-badge" v-if="deal.sale">
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
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
                v-if="product.discount"
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
              <div class="p-2">
                <h6 class="mb-2 truncate-2">
                  {{ product.name }}
                </h6>
                <div class="d-flex flex-column align-items-start">
                  <span class="text-danger fst-italic fs-5 fw-semibold">
                    {{ product.price }} đ
                  </span>
                  <del
                    class="text-muted fst-italic fs-6"
                    v-if="product.oldPrice"
                  >
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
          <div
            v-for="(product, index) in productsGiftToLove"
            :key="index"
            class="px-2"
          >
            <nuxt-link
              :to="product.url"
              class="position-relative border-0 h-100 card product-card"
            >
              <!-- Huy hiệu giảm giá -->
              <div
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
                v-if="product.discount"
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
              <div class="p-2">
                <h6 class="mb-2 truncate-2">
                  {{ product.name }}
                </h6>
                <div class="d-flex flex-column align-items-start">
                  <span class="text-danger fst-italic fs-5 fw-semibold">
                    {{ product.price }} đ
                  </span>
                  <del
                    class="text-muted fst-italic fs-6"
                    v-if="product.oldPrice"
                  >
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
    <div class="py-4 container category-future">
      <h5 class="mb-3 text-uppercase fw-bold">Danh mục nổi bật</h5>
      <VueSlickCarousel
        v-bind="categoryFutureCarouselSettings"
        class="category-slider"
      >
        <div
          v-for="(item, index) in categoriesFuture"
          :key="index"
          v-if="index < 16"
          class="d-flex flex-column align-items-center px-2"
        >
          <nuxt-link :to="item.url" class="w-100 h-100 card">
            <div
              class="d-flex align-items-center justify-content-center rounded w-100 img-wrapper"
            >
              <img
                :src="item.image"
                :alt="item.title"
                class="p-3 img-fluid"
                style="height: 100px; object-fit: contain"
              />
            </div>
            <p class="mt-1 text-center">{{ item.title }}</p>
          </nuxt-link>
          <nuxt-link
            :to="categoriesFuture[index + 16].url"
            class="w-100 h-100 card"
          >
            <div
              class="d-flex align-items-center justify-content-center rounded w-100 img-wrapper"
            >
              <img
                :src="categoriesFuture[index + 16].image"
                :alt="categoriesFuture[index + 16].title"
                class="p-3 img-fluid"
                style="height: 100px; object-fit: contain"
              />
            </div>
            <p class="mt-1 text-center">
              {{ categoriesFuture[index + 16].title }}
            </p>
          </nuxt-link>
        </div>
      </VueSlickCarousel>
    </div>

    <!-- Brand Future -->
    <div class="py-4 container brand-future">
      <h5 class="mb-3 text-uppercase fw-bold">Thương hiệu nổi bật</h5>
      <VueSlickCarousel
        v-bind="brandFutureCarouselSettings"
        class="brand-slider"
      >
        <div
          v-for="(item, index) in brandsFuture"
          :key="index"
          class="d-flex flex-column align-items-center px-2"
        >
          <nuxt-link :to="item.url" class="w-100 h-100 card">
            <div
              class="d-flex align-items-center justify-content-center p-2 rounded w-100 img-wrapper"
            >
              <img :src="item.image" :alt="item.title" class="p-3 img-fluid" />
            </div>
          </nuxt-link>
        </div>
      </VueSlickCarousel>
    </div>

    <!-- Trending search  -->
    <div class="my-4 py-4 container trending-search">
      <h5 class="mb-3 text-uppercase fw-bold">Xu Hướng Tìm Kiếm</h5>
      <div class="row row-cols-1 row-cols-md-5 g-4">
        <nuxt-link
          :to="item?.url"
          v-for="(item, index) in trendingSearch"
          :key="index"
        >
          <div class="d-flex flex-row align-items-center h-100 card">
            <div class="card-body" style="font-size: 12px">
              <h6 class="card-title">{{ item?.title }}</h6>
              <p class="text-muted card-text">{{ item?.quantity }}+ sản phẩm</p>
            </div>
            <img :src="item?.image" class="card-img-top" alt="Coach" />
          </div>
        </nuxt-link>
      </div>
    </div>

    <!-- Suggested products  -->
    <div class="py-4 container suggested-products">
      <h5 class="mb-3 text-danger text-uppercase fw-bold">Gợi ý cho bạn</h5>
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
                class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
                v-if="product.discount"
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
              <div class="p-2">
                <h6 class="mb-2 truncate-2">
                  {{ product.name }}
                </h6>
                <div class="d-flex flex-column align-items-start">
                  <span class="text-danger fst-italic fs-5 fw-semibold">
                    {{ product.price }} đ
                  </span>
                  <del
                    class="text-muted fst-italic fs-6"
                    v-if="product.oldPrice"
                  >
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
    <div class="py-4 container perfume-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List watch -->
    <div class="py-4 container watch-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List Cosmetic -->
    <div class="py-4 container cosmetic-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List hat -->
    <div class="py-4 container hat-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List handbag -->
    <div class="py-4 container handbag-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List shoes -->
    <div class="py-4 container shoes-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List fashion -->
    <div class="py-4 container fashion-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List eyewear -->
    <div class="py-4 container eyewear-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List lipstick -->
    <div class="py-4 container lipstick-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List pickleball -->
    <div class="py-4 container pickleball-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
              class="top-0 position-absolute bg-danger m-2 px-2 py-1 text-white end-0 fs-8"
              v-if="product.discount"
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
            <div class="p-2">
              <h6 class="mb-2 truncate-2">
                {{ product.name }}
              </h6>
              <div class="d-flex flex-column align-items-start">
                <span class="text-danger fst-italic fs-5 fw-semibold">
                  {{ product.price }} đ
                </span>
                <del class="text-muted fst-italic fs-6" v-if="product.oldPrice">
                  {{ product.oldPrice }} đ
                </del>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- List Blog -->
    <div class="py-4 container perfume-products">
      <h3
        class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
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
    <div class="mx-auto my-4 px-4 container description-introduce">
      <main class="my-8 container">
        <section class="mb-6">
          <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
          <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
            <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
            <ul class="pl-5 text-gray-600 leading-relaxed list-disc">
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
            <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
            <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
            <h4 class="mb-4 font-bold text-gray-800 text-2xl">
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
          class="d-block shadow-md mx-auto px-6 py-2 border border-2 border-gray rounded-0 font-semibold text-gray text-uppercase btn"
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
        <div class="align-items-center row">
          <div class="text-md-start text-center col-md-4">
            <div class="subscribe-label">Đăng ký để nhận ưu đãi qua email:</div>
          </div>
          <!-- Form đăng ký -->
          <div class="mb-3 mb-md-0 col-md-4">
            <div class="d-flex subscribe-form">
              <input type="email" placeholder="Nhập email của bạn" />
              <button style="font-size: smaller">Đăng ký</button>
            </div>
            <div class="subscribe-policy">
              Bằng cách đăng ký, bạn đồng ý với
              <a href="#">Chính sách bảo mật của chúng tôi</a>
            </div>
          </div>

          <!-- Icon mạng xã hội -->
          <div class="text-md-end text-center col-md-4">
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

    <footer class="bg-light text-lg-start">
      <div class="p-4 container">
        <div class="row row-cols-1 row-cols-md-4">
          <div class="mb-4 mb-md-0 col-lg-3 col-md-6">
            <h5 class="text-uppercase fw-semibold">THÔNG TIN</h5>
            <ul class="list-unstyled">
              <a href="">
                <li>Gọi hotline về Vua Hàng Hiệu Việt Nam</li>
              </a>
              <a href="">
                <li>Quy chế hoạt động</li>
              </a>
              <a href="">
                <li>Hợp tác với Vua Hàng Hiệu</li>
              </a>
              <a href="">
                <li>Chương trình Affiliate - Cộng tác viên</li>
              </a>
              <a href="">
                <li>Tuyển dụng</li>
              </a>
              <a href="">
                <li>Liên hệ</li>
              </a>
            </ul>
            <div class="d-flex flex-column gap-2 m-auto mx-md-0 w-50">
              <img
                src="@/assets/images/footer/da-dang-ky-bo-cong-thuong.svg"
                alt="Ba Dang Ky"
              />
              <img
                src="@/assets/images/footer/dmca_copyright_protected150b.png"
                alt="DMCA"
              />
              <div class="d-flex flex-row gap-2 w-100">
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
          <div class="mb-4 mb-md-0 col-lg-3 col-md-6">
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
            <div class="d-flex flex-row gap-2 mt-3 w-100">
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
          <div class="mb-4 mb-md-0 col-lg-3 col-md-6">
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
          <div class="mb-4 mb-md-0 col-lg-3 col-md-6">
            <h5 class="text-uppercase fw-semibold">Dịch vụ khách hàng</h5>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Công ty</div>
              <div class="col-7">Công Ty Cổ Phần Thương Mại Vua Hàng Hiệu</div>
            </div>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Hotline</div>
              <div class="col-7">093.934.8888</div>
            </div>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Tổng đài</div>
              <div class="col-7">1900 232322</div>
            </div>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Email</div>
              <div class="col-7">cskh@vuahanghieu.com</div>
            </div>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Thời gian</div>
              <div class="col-7">
                Thứ 2 - Thứ 6: 8:00 - 17:00<br />
                Thứ 7: 8:00 - 11:30
              </div>
            </div>
            <div class="mb-2 row">
              <div class="col-5 fw-semibold">Địa chỉ</div>
              <div class="col-7">
                Tầng 3, Tòa nhà 24T3 Thanh Xuân Complex,<br />
                Số 6 Lê Văn Thiêm, Thanh Xuân Trung, Thanh Xuân, Hà Nội
              </div>
            </div>
            <div class="mb-2 row">
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
      class="d-flex flex-column flex-lg-row align-items-center justify-content-between gap-2 my-2 container"
    >
      <div class="d-flex align-items-center gap-3" style="font-size: 10px">
        <p class="mb-0 fst-italic">© 2025 VUA HÀNG HIỆU.</p>
        <a href="">
          <p class="mb-0 text-uppercase">Điều khoản</p>
        </a>
        <a href="">
          <p class="mb-0 text-uppercase">Chính sách bảo mật</p>
        </a>
      </div>
      <img
        src="@/assets/images/footer/payment-method.svg"
        alt="Thanh toán"
        height="28"
      />
    </div>

    <!-- List category footer -->
    <div class="border-top">
      <div class="my-4 container">
        <div class="row">
          <!-- Cột 1 -->
          <div class="mb-4 col-md-2 col-6">
            <a href="#">
              <h6 class="fw-bold">TÚI XÁCH</h6>
            </a>
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

            <a href="#">
              <h6 class="mt-4 fw-bold">THỜI TRANG CAO CẤP</h6>
            </a>
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
          <div class="mb-4 col-md-2 col-6">
            <a href="#">
              <h6 class="fw-bold">SKINCARE</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Máy rửa mặt</a></li>
              <li><a href="#">Máy triệt lông</a></li>
              <li><a href="#">Máy trị mụn</a></li>
              <li><a href="#">Máy xông hơi mặt</a></li>
              <li><a href="#">Máy hút mụn</a></li>
              <li><a href="#">Máy massage mặt</a></li>
              <li><a href="#">Cây lăn massage</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">VOUCHER & DỊCH VỤ</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Order hàng quốc tế</a></li>
              <li><a href="#">Hàng hiệu giảm 50%</a></li>
              <li><a href="#">Khung giờ săn sale</a></li>
              <li><a href="#">Sale đồng giá</a></li>
              <li><a href="#">Sale Ưu Đãi Tháng 7</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">ĐỒNG HỒ</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Đồng hồ nam</a></li>
              <li><a href="#">Đồng hồ nữ</a></li>
              <li><a href="#">Đồng hồ đôi</a></li>
              <li><a href="#">Dây đồng hồ</a></li>
            </ul>
          </div>

          <!-- Cột 3 -->
          <div class="mb-4 col-md-2 col-6">
            <a href="#">
              <h6 class="fw-bold">MŨ NÓN HIỆU</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Nón nam</a></li>
              <li><a href="#">Nón nữ</a></li>
              <li><a href="#">Mũ Golf</a></li>
              <li><a href="#">Mũ cói</a></li>
              <li><a href="#">Mũ len</a></li>
              <li><a href="#">Mũ nồi</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">CHĂM SÓC CƠ THỂ</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Lăn khử mùi</a></li>
              <li><a href="#">Bàn chải điện</a></li>
              <li><a href="#">Máy uốn mi</a></li>
              <li><a href="#">Chăm sóc răng miệng</a></li>
              <li><a href="#">Chăm sóc móng</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">PHỤ KIỆN CÔNG NGHỆ</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Ốp lưng</a></li>
              <li><a href="#">Vỏ bọc</a></li>
              <li><a href="#">Phụ kiện điện thoại</a></li>
              <li><a href="#">Phụ kiện Laptop</a></li>
            </ul>
          </div>

          <!-- Cột 4 -->
          <div class="mb-4 col-md-3 col-6">
            <a href="#">
              <h6 class="fw-bold">NƯỚC HOA</h6>
            </a>
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

            <a href="#">
              <h6 class="mt-4 fw-bold">KÍNH MẮT</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Kính nam</a></li>
              <li><a href="#">Kính nữ</a></li>
              <li><a href="#">Kính chống nắng</a></li>
              <li><a href="#">Kính trẻ em</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">CHĂM SÓC TÓC</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Serum tóc</a></li>
              <li><a href="#">Dầu gội</a></li>
              <li><a href="#">Dầu xả</a></li>
              <li><a href="#">Xịt thơm tóc</a></li>
              <li><a href="#">Bộ chăm sóc tóc</a></li>
            </ul>
          </div>

          <!-- Cột 5 -->
          <div class="mb-4 col-md-3 col-6">
            <a href="#">
              <h6 class="fw-bold">HÀNG HIỆU USED</h6>
            </a>

            <a href="#">
              <h6 class="mt-4 fw-bold">MỸ PHẨM</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Sữa rửa mặt</a></li>
              <li><a href="#">Kem chống nắng</a></li>
              <li><a href="#">Toner</a></li>
              <li><a href="#">Serum</a></li>
              <li><a href="#">Kem dưỡng da</a></li>
              <li><a href="#">Son môi</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">SON MÔI</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Son lì</a></li>
              <li><a href="#">Son kem</a></li>
              <li><a href="#">Son dưỡng</a></li>
              <li><a href="#">Son nước</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">TRANG ĐIỂM</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Phấn nước</a></li>
              <li><a href="#">Phấn mắt</a></li>
              <li><a href="#">Kẻ mắt</a></li>
              <li><a href="#">Phấn má</a></li>
              <li><a href="#">Kem nền</a></li>
              <li><a href="#">Mascara</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">GIÀY</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Giày nam</a></li>
              <li><a href="#">Giày nữ</a></li>
              <li><a href="#">Sneaker</a></li>
              <li><a href="#">Giày thể thao</a></li>
              <li><a href="#">Giày cao gót</a></li>
              <li><a href="#">Sandals</a></li>
              <li><a href="#">Giày Slip On</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">TRANG SỨC CAO CẤP</h6>
            </a>
            <ul class="list-unstyled">
              <li><a href="#">Dây chuyền</a></li>
              <li><a href="#">Nhẫn</a></li>
              <li><a href="#">Vòng đeo tay</a></li>
              <li><a href="#">Khuyên tai</a></li>
              <li><a href="#">Nhẫn cưới</a></li>
            </ul>

            <a href="#">
              <h6 class="mt-4 fw-bold">HÀNG CHÍNH HÃNG KHÁC</h6>
            </a>
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

      //dropdown search
      showDropdown: false,
      searchQuery: "",
      trendingLinks: [
        {
          url: "/voucher",
          title: "Tặng Voucher Ưu Đãi 150K [9/10 - 15/10/2025]",
        },
        {
          url: "/flash-sale",
          title: "Loa Marshall: 1 Đổi 1 - Bảo Hành 12 Tháng",
        },
        { url: "/new-arrivals", title: "Ưu Đãi Giá SỐC - OFF tới 50%+" },
      ],
      categoriesSearch: [
        {
          name: "Nước Hoa",
          icon: require("@/assets/images/category/1614234988_Nuoc_hoa_Perfume.webp"),
          link: "/category/nuoc-hoa",
        },
        {
          name: "Nước Hoa Nam",
          icon: require("@/assets/images/category/1752560727_nuoc-hoa-nam.webp"),
          link: "/category/nuoc-hoa-nam",
        },
        {
          name: "Nước Hoa Nữ",
          icon: require("@/assets/images/category/1752560745_nuoc-hoa-nu.webp"),
          link: "/category/nuoc-hoa-nu",
        },
        {
          name: "Đồng Hồ",
          icon: require("@/assets/images/category/1614234709_dong-do-chinh-hang.webp"),
          link: "/category/dong-ho",
        },
        {
          name: "Mũ Nón",
          icon: require("@/assets/images/category/1614235850_mu_non_caps.webp"),
          link: "/category/mu-non",
        },
        {
          name: "Mỹ Phẩm",
          icon: require("@/assets/images/category/1614236856_my_pham-Cosmetics.webp"),
          link: "/category/my-pham",
        },
        {
          name: "Kem Chống Nắng",
          icon: require("@/assets/images/category/1642492758_kem-chong-nang.webp"),
          link: "/category/kem-chong-nang",
        },
        {
          name: "Giày Nam",
          icon: require("@/assets/images/category/1642494665_shoes.webp"),
          link: "/category/giay-nam",
        },
        {
          name: "Son Môi",
          icon: require("@/assets/images/category/1642492020_lipstick.webp"),
          link: "/category/son-moi",
        },
        {
          name: "Loa Bluetooth",
          icon: require("@/assets/images/category/1744624289_loa-bluetooth.webp"),
          link: "/category/loa-bluetooth",
        },
        {
          name: "Tai Nghe",
          icon: require("@/assets/images/category/1744685875_tai-nghe-bluetooth.webp"),
          link: "/category/tai-nghe",
        },
        {
          name: "Túi Xách",
          icon: require("@/assets/images/category/1642491921_bag.webp"),
          link: "/category/tui-xach",
        },
      ],
      brandsSearch: [
        {
          name: "Dior",
          logo: require("@/assets/images/brand/1.webp"),
          link: "/brand/dior",
        },
        {
          name: "YSL",
          logo: require("@/assets/images/brand/2.webp"),
          link: "/brand/ysl",
        },
        {
          name: "Lacoste",
          logo: require("@/assets/images/brand/3.webp"),
          link: "/brand/lacoste",
        },
        {
          name: "Gucci",
          logo: require("@/assets/images/brand/4.webp"),
          link: "/brand/gucci",
        },
        {
          name: "Versace",
          logo: require("@/assets/images/brand/5.webp"),
          link: "/brand/versace",
        },
        {
          name: "Armaf",
          logo: require("@/assets/images/brand/6.webp"),
          link: "/brand/armaf",
        },
        {
          name: "Adidas",
          logo: require("@/assets/images/brand/7.webp"),
          link: "/brand/adidas",
        },
        {
          name: "CK",
          logo: require("@/assets/images/brand/8.webp"),
          link: "/brand/ck",
        },
        {
          name: "Nike",
          logo: require("@/assets/images/brand/9.webp"),
          link: "/brand/nike",
        },
        {
          name: "Chanel",
          logo: require("@/assets/images/brand/10.webp"),
          link: "/brand/chanel",
        },
        {
          name: "Swarovski",
          logo: require("@/assets/images/brand/11.webp"),
          link: "/brand/swarovski",
        },
        {
          name: "MLB",
          logo: require("@/assets/images/brand/12.webp"),
          link: "/brand/mlb",
        },
      ],

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
        autoplay: true,
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
          id: 1,
          url: "#",
          name: "Fragrance World Nước Hoa Unisex Maison Barakkat Rouge 540",
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
        },
        {
          id: 2,
          url: "#",
          name: "Nước Hoa Calvin Klein CK One Cho Cả Nam Và Nữ 100ml",
          price: "539.000",
          oldPrice: "1.120.000",
          discount: 52,
          image: require("@/assets/images/topSale/nuoc-hoa-calvin-klein-ck-ck-one-cho-ca-nam-va-nu-100ml-6666827566326-10062024113501.webp"),
        },
        {
          id: 3,
          url: "#",
          name: "Nước Hoa Nam Armaf Club De Nuit Intense Man EDT 105ml",
          price: "950.000",
          oldPrice: "1.800.000",
          discount: 47,
          image: require("@/assets/images/topSale/nuoc-hoa-armaf-club-de-nuit-intense-for-man-105ml-5cecf9ac49316-28052019160444.webp"),
        },
        {
          id: 4,
          url: "#",
          name: "Nước Hoa Nam Versace Eros Man EDT 5ml",
          price: "199.000",
          oldPrice: "375.000",
          discount: 47,
          image: require("@/assets/images/topSale/nuoc-hoa-versace-eros-cho-nam-say-dam-phai-nu-minisize-5ml-5db936dcd37ed-30102019140812.webp"),
        },
        {
          id: 5,
          url: "#",
          name: "Nước Hoa Calvin Klein CK Be EDT Màu Đen 100ml",
          price: "520.000",
          oldPrice: "995.000",
          discount: 48,
          image: require("@/assets/images/topSale/nuoc-hoa-calvin-klein-ck-be-huong-thom-phan-tang-manh-me-15ml-5c60dc199b5f2-11022019092113.webp"),
        },
        {
          id: 6,
          url: "#",
          name: "Son Dior 777 Fahrenheit Velvet Finish Mini 1.5g",
          price: "545.000",
          oldPrice: "690.000",
          discount: 21,
          image: require("@/assets/images/topSale/son-dior-777-fahrenheit-velvet-finish-mini-mau-do-cam-65d6f7a0ce451-22022024142832.webp"),
        },
        {
          id: 7,
          url: "#",
          name: "Nước Hoa Nam Dior Sauvage EDP 10ml",
          price: "475.000",
          oldPrice: "560.000",
          discount: 15,
          image: require("@/assets/images/topSale/nuoc-hoa-dior-sauvage-edp-cho-nam-10ml-5e982e62b3715-16042020170730.webp"),
        },
        {
          id: 8,
          url: "#",
          name: "Son Dưỡng Dior Addict Lip Maximizer 009 Intense Rosewood",
          price: "895.000",
          oldPrice: "1.300.000",
          discount: 31,
          image: require("@/assets/images/topSale/son-dior-addict-lip-maximizer-009-intense-rosewood-mau-hong-dat-moi-nhat-2022-63ae8817888b4-30122022134127 (1).webp"),
        },
        {
          id: 9,
          url: "#",
          name: "Nước Hoa Nữ Yves Saint Laurent YSL Libre EDP 7.5ml",
          price: "400.000",
          oldPrice: "630.000",
          discount: 37,
          image: require("@/assets/images/topSale/nuoc-hoa-nu-yves-saint-laurent-ysl-libre-edp-7-5ml-6805f9af5a8ed-21042025145423.webp"),
        },
        {
          id: 10,
          url: "#",
          name: "Son Dior Addict Lip Maximizer 024 Intense Brick",
          price: "849.000",
          oldPrice: "1.300.000",
          discount: 35,
          image: require("@/assets/images/topSale/son-dior-addict-lip-maximizer-024-intense-brick-mau-do-dat-64239aaf6d3e7-29032023085559.webp"),
        },
        {
          id: 11,
          url: "#",
          name: "Nước Hoa Nữ Gucci Bloom EDP For Women 50ml",
          price: "1.390.000",
          oldPrice: "2.100.000",
          discount: 34,
          image: require("@/assets/images/topSale/nuoc-hoa-nu-gucci-bloom-edp-for-women-50ml-n-md-67f5f95e3fb84-09042025113646.webp"),
        },
        {
          id: 12,
          url: "#",
          name: "Lăn Khử Mùi Nam Armaf Club De Nuit Intense Man 75ml",
          price: "345.000",
          oldPrice: "850.000",
          discount: 59,
          image: require("@/assets/images/topSale/lan-khu-mui-armaf-club-de-nuit-intense-man-75ml-62c52de9054f0-06072022133833.webp"),
        },
        {
          id: 13,
          url: "#",
          name: "Son Dưỡng Dior Addict Lip Maximizer 009 Intense Rosewood",
          price: "890.000",
          oldPrice: "1.300.000",
          discount: 32,
          image: require("@/assets/images/topSale/son-dior-addict-lip-maximizer-009-intense-rosewood-mau-hong-dat-moi-nhat-2022-63ae8817888b4-30122022134127 (1).webp"),
        },
        {
          id: 14,
          url: "#",
          name: "Nước Hoa Nam Nautica Voyage EDT 100ml",
          price: "645.000",
          oldPrice: "1.050.000",
          discount: 39,
          image: require("@/assets/images/topSale/nuo-c-hoa-nam-nautica-voyage-edt-100ml-61359a4222f30-06092021113410.webp"),
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

      // gift to love
      productsGiftToLove: [
        {
          id: 1,
          url: "#",
          name: "Vợt Pickleball Proton Series 3 Project Flamingo Paddle Màu Đen Phối Hồng",
          price: "6.990.000",
          oldPrice: "7.600.000",
          discount: 8,
          image: require("@/assets/images/giftToLove/vot-pickleball-proton-series-3-project-flamingo-paddle-mau-den-phoi-hong-67f74103eba61-10042025105443.webp"),
        },
        {
          id: 2,
          url: "#",
          name: "Son Tom Ford Love Lip Color Matte Limited Edition TF 16 Scarlet Rouge Màu Đỏ Thuần",
          price: "1.050.000",
          oldPrice: "1.800.000",
          discount: 41,
          image: require("@/assets/images/giftToLove/son-tom-ford-love-lip-color-matte-limited-edition-tf-16-scarlet-rouge-mau-do-thuan-c_tn-67cf99ae5231e-11032025090222.webp"),
        },
        {
          id: 3,
          url: "#",
          name: "Son Lì Dior Velvet 539 Tera Bella Màu Đỏ Cam Đất",
          price: "950.000",
          oldPrice: "1.500.000",
          discount: 36,
          image: require("@/assets/images/giftToLove/son-li-dior-velvet-539-tera-bella-mau-do-cam-dat-68dde569cfcdb-02102025093729.webp"),
        },
        {
          id: 4,
          url: "#",
          name: "Kính Mát Rayban Sunglasses RB4391D 645087 65-18 Màu Xám",
          price: "3.050.000",
          oldPrice: "3.800.000",
          discount: 19,
          image: require("@/assets/images/giftToLove/kinh-mat-rayban-sunglasses-rb4391d-645087-65-18-mau-xam-68bf87e0248e7-09092025085024.webp"),
        },
        {
          id: 5,
          url: "#",
          name: "Giày Tennis/Pickleball Skechers Viper Court Pro 172069C-LAV Màu Tím Size 38",
          price: "3.750.000",
          oldPrice: "5.000.000",
          discount: 25,
          image: require("@/assets/images/giftToLove/giay-tennis-pickleball-skechers-viper-court-pro-172069c-lav-mau-tim-size-36-68ce0e3c34595-20092025091524.webp"),
        },
        {
          id: 6,
          url: "#",
          name: "Kính Mát Rayban Caravan RB3136 001/51 55mm Màu Nâu",
          price: "3.100.000",
          oldPrice: "4.000.000",
          discount: 22,
          image: require("@/assets/images/giftToLove/kinh-mat-rayban-caravan-rb3136-001-51-mau-nau-685f50dda0acd-28062025091805.webp"),
        },
        {
          id: 7,
          url: "#",
          name: "Túi Đeo Chéo Nữ Marc Jacobs The Croc-embossed Snapshot Màu Đen",
          price: "6.290.000",
          oldPrice: "8.900.000",
          discount: 29,
          image: require("@/assets/images/giftToLove/tui-deo-cheo-nu-marc-jacobs-the-croc-embossed-snapshot-mau-den-6802fb031ccdf-19042025082315.webp"),
        },
        {
          id: 8,
          url: "#",
          name: "Kính Mát Rayban Sunglasses RB4391D 601/80 65-18 Màu Xanh Blue/Đen",
          price: "3.050.000",
          oldPrice: "3.800.000",
          discount: 19,
          image: require("@/assets/images/giftToLove/kinh-mat-rayban-sunglasses-rb4391d-601-80-65-18-mau-xanh-blue-den-68bf81e10741c-09092025082449.webp"),
        },
        {
          id: 9,
          url: "#",
          name: "Mũ MLB Varsity Boston Red Sox 3ACPVV04N-43GNS Màu Xanh Green",
          price: "1.090.000",
          oldPrice: "1.900.000",
          discount: 42,
          image: require("@/assets/images/giftToLove/mu-mlb-varsity-boston-red-sox-3acpvv04n-43gns-mau-xanh-green-67d27aa9c6597-13032025132649.webp"),
        },
      ],

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
          id: 1,
          title: "Nước hoa",
          url: "#",
          image: require("@/assets/images/category/1614234988_Nuoc_hoa_Perfume.webp"),
        },
        {
          id: 2,
          title: "Nước hoa Nam",
          url: "#",
          image: require("@/assets/images/category/1752560727_nuoc-hoa-nam.webp"),
        },
        {
          id: 3,
          title: "Nước hoa Nữ",
          url: "#",
          image: require("@/assets/images/category/1752560745_nuoc-hoa-nu.webp"),
        },
        {
          id: 4,
          title: "Đồng hồ",
          url: "#",
          image: require("@/assets/images/category/1614234709_dong-do-chinh-hang.webp"),
        },
        {
          id: 5,
          title: "Mũ nón",
          url: "#",
          image: require("@/assets/images/category/1614235850_mu_non_caps.webp"),
        },
        {
          id: 6,
          title: "Mỹ phẩm",
          url: "#",
          image: require("@/assets/images/category/1614236856_my_pham-Cosmetics.webp"),
        },
        {
          id: 7,
          title: "Kem chống nắng",
          url: "#",
          image: require("@/assets/images/category/1642492758_kem-chong-nang.webp"),
        },
        {
          id: 8,
          title: "Giày nam",
          url: "#",
          image: require("@/assets/images/category/1642494665_shoes.webp"),
        },
        {
          id: 9,
          title: "Son môi",
          url: "#",
          image: require("@/assets/images/category/1642492020_lipstick.webp"),
        },
        {
          id: 10,
          title: "Loa Bluetooth",
          url: "#",
          image: require("@/assets/images/category/1744624289_loa-bluetooth.webp"),
        },
        {
          id: 11,
          title: "Tai nghe",
          url: "#",
          image: require("@/assets/images/category/1744685875_tai-nghe-bluetooth.webp"),
        },
        {
          id: 12,
          title: "Túi xách",
          url: "#",
          image: require("@/assets/images/category/1642491921_bag.webp"),
        },
        {
          id: 13,
          title: "Kính mắt",
          url: "#",
          image: require("@/assets/images/category/1614235638_kinh_mat_sunglasses.webp"),
        },
        {
          id: 14,
          title: "Giày nữ",
          url: "#",
          image: require("@/assets/images/category/1643083743_giay-nu.webp"),
        },
        {
          id: 15,
          title: "Thời trang",
          url: "#",
          image: require("@/assets/images/category/1642491919_fashion.webp"),
        },
        {
          id: 16,
          title: "Trang sức",
          url: "#",
          image: require("@/assets/images/category/1642491760_icon_trang-suc-11012022145839[1].webp"),
        },
        {
          id: 17,
          title: "Đồ chơi mô hình",
          url: "#",
          image: require("@/assets/images/category/1657768241_dochoimohinh.webp"),
        },
        {
          id: 18,
          title: "Máy rửa mặt",
          url: "#",
          image: require("@/assets/images/category/1642492212_may-rua-mat.webp"),
        },
        {
          id: 19,
          title: "Máy Massage",
          url: "#",
          image: require("@/assets/images/category/1642492397_may-massage.webp"),
        },
        {
          id: 20,
          title: "Lăn khử mùi",
          url: "#",
          image: require("@/assets/images/category/1642492469_lan-khu-mui.webp"),
        },
        {
          id: 21,
          title: "Sữa rửa mặt",
          url: "#",
          image: require("@/assets/images/category/1642492618_sua-rua-mat.webp"),
        },
        {
          id: 22,
          title: "Trang điểm",
          url: "#",
          image: require("@/assets/images/category/1634096891_trang-diem-vuahanghieu.webp"),
        },
        {
          id: 23,
          title: "Dép Hiệu",
          url: "#",
          image: require("@/assets/images/category/1642495869_dep.webp"),
        },
        {
          id: 24,
          title: "Chăm sóc tóc",
          url: "#",
          image: require("@/assets/images/category/1634096911_cham-soc-toc-vuahanghieu.webp"),
        },
        {
          id: 25,
          title: "Công nghệ",
          url: "#",
          image: require("@/assets/images/category/1667617963_phu-kien-cong-nghe.webp"),
        },
        {
          id: 26,
          title: "Máy triệt lông",
          url: "#",
          image: require("@/assets/images/category/1642493924_may-triet-long.webp"),
        },
        {
          id: 27,
          title: "Phụ kiện",
          url: "#",
          image: require("@/assets/images/category/1657768681_phukienthoitrang.webp"),
        },
        {
          id: 28,
          title: "Máy trị mụn",
          url: "#",
          image: require("@/assets/images/category/1642492897_may-tri-mun.webp"),
        },
        {
          id: 29,
          title: "Máy phun sương",
          url: "#",
          image: require("@/assets/images/category/1645780422_may-phun-suong.webp"),
        },
        {
          id: 30,
          title: "Móc khóa",
          url: "#",
          image: require("@/assets/images/category/1739774892_moc-khoa-hang-hieu.webp"),
        },
        {
          id: 31,
          title: "Nến thơm",
          url: "#",
          image: require("@/assets/images/category/1739775239_nen-thom-hang-hieu.webp"),
        },
        {
          id: 32,
          title: "Thắt lưng",
          url: "#",
          image: require("@/assets/images/category/1739775466_that-lung-cao-cap.webp"),
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
          name: "Nước Hoa Unisex Fragrance World Maison Vaporisateur Barakkat Rouge 540 Extrait De Parfum 100ml",
          url: "/fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-ph085936",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
          price: "490.000",
          oldPrice: "950.000",
          discount: 48,
        },
        {
          name: "Nước Hoa Nam Nautica Voyage EDT 100ml Tinh Te",
          url: "/nuoc-hoa-nam-nautica-voyage-edt-100ml-tinh-te-ph169951",
          image: require("@/assets/images/listProduct/suggest/nuo-c-hoa-nam-nautica-voyage-edt-100ml-66e7aaacf1efd-16092024104900.webp"),
          price: "850.000",
          oldPrice: "1.500.000",
          discount: 43,
        },
        {
          name: "Nước Hoa Nam Nautica Voyage EDT 100ml",
          url: "/nautica-voyage-edt-100ml-ph033274",
          image: require("@/assets/images/listProduct/suggest/nuo-c-hoa-nam-nautica-voyage-edt-100ml-61359a4222f30-06092021113410.webp"),
          price: "645.000",
          oldPrice: "1.050.000",
          discount: 39,
        },
        {
          name: "Vòng Đeo Tay Nữ Swarovski Teddy Bracelet Bear Pink Rose Gold-Tone Plated 5669169 Mau Hong",
          url: "/vong-deo-tay-swarovski-teddy-bracelet-bear-pink-rose-gold-tone-plated-5669169-mau-hong-ph198167",
          image: require("@/assets/images/listProduct/suggest/vong-deo-tay-nu-swarovski-teddy-bracelet-bear-pink-rose-gold-tone-plated-5669169-mau-hong-65ded6c1184c8-28022024134625.webp"),
          price: "4.254.000",
          oldPrice: "5.900.000",
          discount: 28,
        },
        {
          name: "Sữa Tắm Hương Nước Hoa Armaf Club De Nuit Iconic 360ml",
          url: "/sua-tam-huong-nuoc-hoa-armaf-club-de-nuit-iconic-360ml-ph208772",
          image: require("@/assets/images/listProduct/suggest/sua-tam-huong-nuoc-hoa-armaf-club-de-nuit-iconic-360ml-6888706a517ff-29072025135538.webp"),
          price: "470.000",
          oldPrice: "990.000",
          discount: 53,
        },
        {
          name: "Nước Hoa Nam Versace Pour Homme EDT 100ml",
          url: "/nuoc-hoa-versace-pour-homme-100ml-ph003824",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-nam-versace-pour-homme-edt-100ml-67370dec145e5-15112024160132.webp"),
          price: "1.370.000",
          oldPrice: "2.400.000",
          discount: 43,
        },
        {
          name: "Nước Hoa Unisex Maison Francis Kurkdjian Baccarat Rouge 540 Extrait De Parfum 70ml",
          url: "/nuoc-hoa-maison-francis-kurkdjian-baccarat-rouge-540-extrait-de-parfum-ph025838",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-maison-francis-kurkdjian-baccarat-rouge-540-extrait-de-parfum-70ml-62184af34d44c-25022022102019.webp"),
          price: "8.600.000",
          oldPrice: "12.000.000",
          discount: 28,
        },
        {
          name: "Set Trang Diem Dior Miss Dior Gift Set 5 Mon",
          url: "/set-trang-diem-dior-miss-dior-gift-set-5-mon-ph217929",
          image: require("@/assets/images/listProduct/suggest/set-trang-diem-dior-miss-dior-gift-set-5-mon-68d34c27e6129-24092025084055.webp"),
          price: "1.200.000",
          oldPrice: "1.900.000",
          discount: 37,
        },
        {
          name: "Nước Hoa Calvin Klein CK One Cho Ca Nam Va Nu 100ml",
          url: "/calvin-klein-ck-one-edt-100ml-ph000511",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-calvin-klein-ck-ck-one-cho-ca-nam-va-nu-100ml-6666827566326-10062024113501.webp"),
          price: "539.000",
          oldPrice: "1.120.000",
          discount: 52,
        },
        {
          name: "Set Son Va Nuoc Hoa Dior Beauty Mini 3 Mon Kem Tui",
          url: "/set-son-va-nuoc-hoa-dior-beauty-mini-3-mon-kem-tui-ph220668",
          image: require("@/assets/images/listProduct/suggest/set-son-va-nuoc-hoa-dior-beauty-mini-3-mon-kem-tui-68e6258620ebc-08102025154910.webp"),
          price: "1.050.000",
          oldPrice: "1.790.000",
          discount: 41,
        },
        {
          name: "Nước Hoa Nam Versace Eros Man EDT 5ml",
          url: "/versace-eros-edt-5ml-ph008740",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-versace-eros-cho-nam-say-dam-phai-nu-minisize-5ml-5db936dcd37ed-30102019140812.webp"),
          price: "199.000",
          oldPrice: "375.000",
          discount: 47,
        },
        {
          name: "Nước Hoa Nam Armaf Club De Nuit Intense Man EDT 105ml",
          url: "/nuoc-hoa-nam-armaf-club-de-nuit-intense-man-eau-de-toilette-105ml-ph162196",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-nam-armaf-club-de-nuit-intense-man-eau-de-toilette-105ml-6711b6a62a9b0-18102024081518.webp"),
          price: "950.000",
          oldPrice: "1.800.000",
          discount: 47,
        },
        {
          name: "Nước Hoa Nam Ralph Lauren Polo Blue EDP 125ml",
          url: "/nuoc-hoa-ralph-lauren-polo-blue-edp-125ml-ph173084",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-nam-ralph-lauren-polo-blue-edp-125ml-677207c2ecd78-30122024093858.webp"),
          price: "1.590.000",
          oldPrice: "3.700.000",
          discount: 57,
        },
        {
          name: "Nước Hoa Ralph Lauren Polo Blue EDP Cho Nam 125ml",
          url: "/nuoc-hoa-ralph-lauren-polo-blue-edp-nam-125ml-ph000421",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-ralph-lauren-polo-blue-edp-cho-nam-125ml-67c134a5d4712-28022025105933.webp"),
          price: "1.590.000",
          oldPrice: "2.500.000",
          discount: 36,
        },
        {
          name: "Nước Hoa Nam Ralph Lauren Polo Blue EDP 125ml",
          url: "/nuoc-hoa-nam-ralph-lauren-polo-blue-edp-125ml-c-tn-ph171684",
          image: require("@/assets/images/listProduct/suggest/nuoc-hoa-nam-ralph-lauren-polo-blue-edp-125ml-66348bfa5e4c7-03052024140218.webp"),
          price: "1.850.000",
          oldPrice: "3.000.000",
          discount: 38,
        },
      ],

      // List perfume
      productPerfume: [
        {
          name: "Nước Hoa Nam Calvin Klein CK Man EDT 100ml (Không Seal)",
          url: "/nuoc-hoa-nam-calvin-klein-ck-man-edt-100ml-khong-seal-ph220985",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-nam-calvin-klein-ck-man-edt-100ml-657194a7c73af-07122023164719.webp"),
          price: "890,000",
          oldPrice: "1,400,000",
          discount: 36,
        },
        {
          name: "Nước Hoa Nữ Dior Miss Dior Blooming Bouquet Eau De Toilette 30ml",
          url: "/nuoc-hoa-nu-dior-miss-dior-blooming-bouquet-eau-de-toilette-30ml-ph220932",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-nu-dior-miss-dior-blooming-bouquet-edt-30ml-ban-2023-68cb7583162a3-18092025095915.webp"),
          price: "1,390,000",
          oldPrice: "2,000,000",
          discount: 31,
        },
        {
          name: "Set Nước Hoa Nam Jean Paul Gaultier Le Male Elixir Parfum Gift Set 2 Món (125 +75ml)",
          url: "/set-nuoc-hoa-nam-jean-paul-gaultier-le-male-elixir-parfum-gift-set-2-mon-125-75ml-ph220835",
          image: require("@/assets/images/listProduct/nuochoa/set-nuoc-hoa-nam-jean-paul-gaultier-le-male-elixir-parfum-gift-set-2-mon-6710c28942039-17102024145345.webp"),
          price: "2,450,000",
          oldPrice: "3,200,000",
          discount: 23,
        },
        {
          name: "Set Nước Hoa Nữ YSL Yves Saint Laurent Lash Clash Mascara Holiday 4 Món (EDP 7.5ml + Mascara + Son YSL 21 Rouge Paradoxe)",
          url: "/set-nuoc-hoa-ysl-yves-saint-laurent-lash-clash-mascara-holiday-4-mon-edp-7-5ml-mascara-son-ysl-21-rouge-paradoxe-ph220826",
          image: require("@/assets/images/listProduct/nuochoa/set-nuoc-hoa-ysl-yves-saint-laurent-lash-clash-mascara-holiday-4-mon-edp-7-5ml-mascara-son-ysl-21-rouge-paradoxe-68e75cd02cdf7-09102025135720.webp"),
          price: "1,890,000",
          oldPrice: "2,900,000",
          discount: 35,
        },
        {
          name: "Nước Hoa Nữ Gucci Bloom For Women EDP 30ml Quyến Rũ",
          url: "/nuoc-hoa-nu-gucci-bloom-for-women-edp-30ml-quyen-ru-ph220809",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-nu-gucci-bloom-for-women-edp-30ml-6758ff2a00c94-11122024095538.webp"),
          price: "1,090,000",
          oldPrice: "1,600,000",
          discount: 32,
        },
        {
          name: "Nước Hoa Unisex Fragrance World Maison Vaporisateur Barakkat Rouge 540 Extrait De Parfum 100ml",
          url: "/fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-ph085936",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-unisex-fragrance-world-maison-vaporisateur-barakkat-rouge-540-extrait-de-parfum-100ml-64376521e8cff-13042023091249.webp"),
          price: "490,000",
          oldPrice: "950,000",
          discount: 48,
        },
        {
          name: "Nước Hoa Calvin Klein (CK) CK One Cho Cả Nam Và Nữ, 100ml",
          url: "/calvin-klein-ck-one-edt-100ml-ph000511",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-calvin-klein-ck-ck-one-cho-ca-nam-va-nu-100ml-6666827566326-10062024113501.webp"),
          price: "539,000",
          oldPrice: "1,120,000",
          discount: 52,
        },
        {
          name: "Nước Hoa Nam Armaf Club De Nuit Intense Man EDT 105ml",
          url: "/nuoc-hoa-nam-armaf-club-de-nuit-intense-man-eau-de-toilette-105ml-ph162196",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-nam-armaf-club-de-nuit-intense-man-eau-de-toilette-105ml-6711b6a62a9b0-18102024081518.webp"),
          price: "950,000",
          oldPrice: "1,800,000",
          discount: 47,
        },
        {
          name: "Nước Hoa Nam Versace Eros Man EDT 5ml",
          url: "/versace-eros-edt-5ml-ph008740",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-versace-eros-cho-nam-say-dam-phai-nu-minisize-5ml-5db936dcd37ed-30102019140812.webp"),
          price: "199,000",
          oldPrice: "375,000",
          discount: 47,
        },
        {
          name: "Nước Hoa Calvin Klein CK Be EDT Màu Đen 100ml",
          url: "/nuoc-hoa-calvin-klein-ck-be-huong-thom-phan-tang-manh-me-100ml-ph000466",
          image: require("@/assets/images/listProduct/nuochoa/nuoc-hoa-calvin-klein-ck-be-huong-thom-phan-tang-manh-me-15ml-5c60dc199b5f2-11022019092113.webp"),
          price: "520,000",
          oldPrice: "995,000",
          discount: 48,
        },
      ],

      // List watch
      productWatch: [
        {
          name: "Đồng Hồ Nữ Daniel Wellington DW00100247 Petite Cornwall 28mm Màu Đen",
          url: "/dong-ho-nu-daniel-wellington-dw00100247-petite-cornwall-28mm-mau-den-ph220982",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-daniel-wellington-dw00100247-petite-cornwall-28mm-mau-den-68e8778a772ab-10102025100338.webp"),
          price: "3.290.000",
          oldPrice: "3.650.000",
          discount: 10,
        },
        {
          name: "Đồng Hồ Nữ Daniel Wellington Quadro Mini Reflection Rose Gold Màu Vàng Hồng",
          url: "/dong-ho-nu-daniel-wellington-quadro-mini-reflection-rose-gold-mau-vang-hong-ph220956",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-daniel-wellington-quadro-mini-reflection-rose-gold-mau-vang-hong-68e86e6276cc5-10102025092434.webp"),
          price: "4.760.000",
          oldPrice: "5.280.000",
          discount: 10,
        },
        {
          name: "Đồng Hồ Nam Daniel Wellington Classic Piano Link Onyx Silver DW00100778 Màu Xám Đen",
          url: "/dong-ho-nam-daniel-wellington-classic-piano-link-onyx-silver-dw00100778-mau-xam-den-ph220939",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nam-daniel-wellington-classic-piano-link-onyx-silver-dw00100778-mau-xam-den-68e8687666e46-10102025085918.webp"),
          price: "5.420.000",
          oldPrice: "6.020.000",
          discount: 10,
        },
        {
          name: "Đồng Hồ Nữ Daniel Wellington Chunky Chain Màu Vàng Gold",
          url: "/dong-ho-nu-daniel-wellington-chunky-chain-mau-vang-gold-ph220923",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-daniel-wellington-chunky-chain-mau-vang-gold-68e78e902ee2b-09102025172936.webp"),
          price: "5.710.000",
          oldPrice: "6.340.000",
          discount: 10,
        },
        {
          name: "Đồng Hồ Nữ Daniel Wellington Ophelia Mini Màu Bạc Xanh",
          url: "/dong-ho-nu-daniel-wellington-ophelia-mini-mau-bac-xanh-ph220922",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-daniel-wellington-ophelia-mini-mau-bac-xanh-68e78bf26ced3-09102025171826.webp"),
          price: "5.550.000",
          oldPrice: null,
          discount: null,
        },
        {
          name: "Đồng Hồ Nam Bentley Cellini BL2216-10MWWB-MS-GL-T Màu Trắng Đen",
          url: "/dong-ho-nam-bentley-cellini-bl2216-10mwwb-ms-gl-t-mau-trang-den-ph138479",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nam-bentley-cellini-bl2216-10mwwb-ms-gl-t-mau-trang-den-65fe3289d26a0-23032024083817.webp"),
          price: "2.850.000",
          oldPrice: "4.500.000",
          discount: 37,
        },
        {
          name: "Đồng Hồ Nữ Seiko Quartz White Dial Black Leather Ladies Watch SWR053 Màu Đen Bạc",
          url: "/dong-ho-nu-seiko-quartz-white-dial-black-leather-ladies-watch-swr053-mau-den-bac-ph099988",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-seiko-quartz-white-dial-black-leather-ladies-watch-swr053-mau-den-bac-64e4132f7df51-22082023084519.webp"),
          price: "4.500.000",
          oldPrice: "5.800.000",
          discount: 22,
        },
        {
          name: "Đồng Hồ Nữ FL Franklin Silver Đính Đá 31mm Màu Trắng Bạc (Tặng Kèm Khuyên Tai)",
          url: "/dong-ho-nu-fl-franklin-silver-dinh-da-31mm-mau-trang-bac-tang-kem-khuyen-tai-ph188379",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-fl-franklin-silver-dinh-da-31mm-mau-trang-bac-tang-kem-khuyen-tai-67f88c6722b41-11042025102839.webp"),
          price: "3.550.000",
          oldPrice: "5.000.000",
          discount: 29,
        },
        {
          name: "Đồng Hồ Nam Orient Caballero FAG00003W0",
          url: "/dong-ho-orient-caballero-fag00003w0-ph002806",
          image: require("@/assets/images/listProduct/dongho/dong-ho-orient-caballero-fag00003w0-5ca32fe92b156-02042019164825.webp"),
          price: "5.250.000",
          oldPrice: "6.150.000",
          discount: 15,
        },
        {
          name: "Đồng Hồ Nữ Christian Van Sant Elegant Quartz White Dial Ladies Watch CV4821B Màu Đen",
          url: "/dong-ho-nu-christian-van-sant-elegant-quartz-white-dial-ladies-watch-cv4821b-mau-den-ph047707",
          image: require("@/assets/images/listProduct/dongho/dong-ho-nu-christian-van-sant-elegant-quartz-white-dial-ladies-watch-cv4821b-mau-den-62b94ddfd53f0-27062022132743.webp"),
          price: "5.500.000",
          oldPrice: "7.910.000",
          discount: 30,
        },
      ],

      // List cosmetic
      productCosmetic: [
        {
          name: "Sữa Tắm Hương Nước Hoa Nữ Armaf Club De Nuit Woman Shower Gel 360ml",
          url: "/sua-tam-huong-nuoc-hoa-nu-armaf-club-de-nuit-woman-shower-gel-360ml-ph220926",
          image: require("@/assets/images/listProduct/mypham/sua-tam-huong-nuoc-hoa-nu-armaf-club-de-nuit-woman-intense-shower-gel-360ml-c_tn-6794566563876-25012025101133.webp"),
          price: "380.000",
          oldPrice: "490.000",
          discount: 22,
        },
        {
          name: "Tinh Chất Hỗ Trợ Ngăn Ngừa Lão Hóa Da Estée Lauder Advanced Night Repair Serum 50ml",
          url: "/tinh-chat-ho-tro-ngan-ngua-lao-hoa-da-estee-lauder-advanced-night-repair-serum-50ml-ph220914",
          image: require("@/assets/images/listProduct/mypham/tinh-chat-ho-tro-ngan-ngua-lao-hoa-da-estee-lauder-advanced-night-repair-serum-synchronized-multi-recovery-complex-50ml-65dff7658c40e-29022024101757.webp"),
          price: "1.500.000",
          oldPrice: "2.200.000",
          discount: 32,
        },
        {
          name: "Set Dưỡng Da Estée Lauder Glow Repair + Lift + Brighten 4 Món",
          url: "/set-duong-da-estee-lauder-glow-repair-lift-brighten-4-mon-ph220814",
          image: require("@/assets/images/listProduct/mypham/set-duong-da-estee-lauder-glow-repair-lift-brighten-4-mon-68e7584c17dd9-09102025133804.webp"),
          price: "1.400.000",
          oldPrice: "2.000.000",
          discount: 30,
        },
        {
          name: "Set Dưỡng Da Estée Lauder Glow Revitalizing Suprekem + Skin Care Starter 4 Món",
          url: "/set-duong-da-estee-lauder-glow-revitalizing-suprekem-skin-care-starter-4-mon-ph220808",
          image: require("@/assets/images/listProduct/mypham/set-duong-da-revitalizing-suprekem-skin-care-starter-4-mon-68cb786517114-18092025101133.webp"),
          price: "1.400.000",
          oldPrice: "2.000.000",
          discount: 30,
        },
        {
          name: "Set Dưỡng Da Estée Lauder 4-PC DayWear Moisturizer Skincare 4 Món",
          url: "/set-duong-da-estee-lauder-4-pc-daywear-moisturizer-skincare-4-mon-ph220799",
          image: require("@/assets/images/listProduct/mypham/set-duong-da-estee-lauder-4-pc-daywear-moisturizer-skincare-4-mon-68e7510d437a6-09102025130709.webp"),
          price: "2.200.000",
          oldPrice: "3.500.000",
          discount: 37,
        },
        {
          name: "Sữa Tắm Hương Nước Hoa Nam Armaf Club De Nuit Intense Man Shower Gel 360ml",
          url: "/sua-tam-huong-nuoc-hoa-nam-armaf-club-de-nuit-intense-man-shower-gel-360ml-ph173521",
          image: require("@/assets/images/listProduct/mypham/sua-tam-huong-nuoc-hoa-nam-armaf-club-de-nuit-intense-man-shower-gel-360ml-6775f2e56ee9b-02012025085901.webp"),
          price: "390.000",
          oldPrice: "680.000",
          discount: 43,
        },
        {
          name: "Sữa Tắm Hương Nước Hoa Nữ Armaf Club De Nuit Woman Shower Gel 360ml",
          url: "/sua-tam-huong-nuoc-hoa-nu-armaf-club-de-nuit-intense-woman-shower-gel-ph137040",
          image: require("@/assets/images/listProduct/mypham/sua-tam-huong-nuoc-hoa-nu-armaf-club-de-nuit-intense-woman-shower-gel-65efb238a8094-12032024083904.webp"),
          price: "390.000",
          oldPrice: "680.000",
          discount: 43,
        },
        {
          name: "Tinh Chất Hỗ Trợ Phục Hồi Da Estée Lauder  Advanced Night Repair Serum Synchronized Multi-Recovery Complex 100ml",
          url: "/tinh-chat-ho-tro-phuc-hoi-da-estee-lauder-advanced-night-repair-serum-synchronized-multi-recovery-complex-100ml-c-tn-ph171760",
          image: require("@/assets/images/listProduct/mypham/tinh-chat-ho-tro-phuc-hoi-da-estee-lauder-advanced-night-repair-serum-synchronized-multi-recovery-complex-100ml-659b958403a1d-08012024132612.webp"),
          price: "2.450.000",
          oldPrice: "3.900.000",
          discount: 37,
        },
        {
          name: "Sữa Tắm Hương Nước Hoa Nam Armaf Club De Nuit Intense Man Shower Gel 360ml",
          url: "/sua-tam-huong-nuoc-hoa-nam-armaf-club-de-nuit-intense-man-shower-gel-ph137043",
          image: require("@/assets/images/listProduct/mypham/sua-tam-huong-nuoc-hoa-nam-armaf-club-de-nuit-intense-man-shower-gel-65efb76d62331-12032024090117.webp"),
          price: "390.000",
          oldPrice: "680.000",
          discount: 43,
        },
        {
          name: "Sữa Tắm Nam Versace Eros Flame Perfumed Shower Gel 250ml",
          url: "/sua-tam-nam-versace-eros-flame-perfumed-shower-gel-250ml-ph155112",
          image: require("@/assets/images/listProduct/mypham/sua-tam-nam-versace-eros-flame-perfumed-shower-gel-250ml-66cd76063dbe0-27082024134526.webp"),
          price: "650.000",
          oldPrice: "1.150.000",
          discount: 43,
        },
      ],

      // List Hat
      productHat: [
        {
          name: "Mũ Lacoste Golf Corduroy Visor RK345E-54N 70V Màu Trắng",
          url: "/mu-lacoste-golf-corduroy-visor-rk345e-54n-70v-mau-trang-ph220851",
          image: require("@/assets/images/listProduct/munon/mu-lacoste-golf-corduroy-visor-rk345e-54n-70v-mau-trang-68e77052298b5-09102025152034.webp"),
          price: "1.750.000",
          oldPrice: "2.550.000",
          discount: 31,
        },
        {
          name: "Mũ Lacoste Golf Corduroy Visor RK345E-54N YZP Màu Xanh Green",
          url: "/mu-lacoste-golf-corduroy-visor-rk345e-54n-yzp-mau-xanh-green-ph220850",
          image: require("@/assets/images/listProduct/munon/mu-lacoste-golf-corduroy-visor-rk345e-54n-yzp-mau-xanh-green-68e76f7603683-09102025151654.webp"),
          price: "1.750.000",
          oldPrice: "2.550.000",
          discount: 31,
        },
        {
          name: "Mũ Lacoste Common Terry Material Sun Visor RK3592 53N 166 Cap Màu Xanh Navy",
          url: "/mu-lacoste-common-terry-material-sun-visor-rk3592-53n-166-cap-mau-xanh-navy-ph220841",
          image: require("@/assets/images/listProduct/munon/mu-lacoste-common-terry-material-sun-visor-rk3592-53n-166-mau-xanh-navy-67b2ab85b1666-17022025102245.webp"),
          price: "1.750.000",
          oldPrice: "2.550.000",
          discount: 31,
        },
        {
          name: "Mũ Lacoste Common Terry Material Sun Visor RK3592 53N 001 White Màu Trắng",
          url: "/mu-lacoste-common-terry-material-sun-visor-rk3592-53n-001-white-mau-trang-ph220838",
          image: require("@/assets/images/listProduct/munon/mu-lacoste-common-terry-material-sun-visor-rk3592-53n-001-mau-trang-67b2ad88eb107-17022025103120.webp"),
          price: "1.750.000",
          oldPrice: "2.200.000",
          discount: 20,
        },
        {
          name: "Mũ Nam Lacoste Men's Tennis Mesh Panel Cap RK4971 53G White Màu Trắng",
          url: "/mu-nam-lacoste-men-s-tennis-mesh-panel-cap-rk4971-53g-white-mau-trang-ph220744",
          image: require("@/assets/images/listProduct/munon/mu-nam-lacoste-men-s-tennis-mesh-panel-cap-rk4971-53g-mau-trang-67402bd995fdd-22112024135937.webp"),
          price: "1.650.000",
          oldPrice: "2.050.000",
          discount: 20,
        },
        {
          name: "Mũ MLB New York Yankees Diamond Adjustable Hat In Black",
          url: "/mu-mlb-new-york-yankees-diamond-adjustable-hat-in-black-ph016662",
          image: require("@/assets/images/listProduct/munon/mu-mlb-new-york-yankees-diamond-adjustable-hat-in-black-5dcf6f33ea823-16112019103827.webp"),
          price: "890.000",
          oldPrice: "1.400.000",
          discount: 36,
        },
        {
          name: "Mũ MLB La Dodgers Diamond Adjustable Cap Màu Đen",
          url: "/mu-mlb-la-dodgers-diamond-adjustable-cap-mau-den-ph021508",
          image: require("@/assets/images/listProduct/munon/mu-mlb-la-dodgers-diamond-adjustable-cap-mau-den-6482f235be738-09062023163445.webp"),
          price: "980.000",
          oldPrice: "1.400.000",
          discount: 30,
        },
        {
          name: "Mũ MLB Unisex New York Yankees CP77 Màu Đen - 3ACP7701NK0010",
          url: "/mu-mlb-unisex-new-york-yankees-cp77-mau-den-ph024236",
          image: require("@/assets/images/listProduct/munon/mu-mlb-unisex-new-york-yankees-cp77-mau-den-5efab8434f811-30062020105755.webp"),
          price: "850.000",
          oldPrice: "1.200.000",
          discount: 29,
        },
        {
          name: "Mũ MLB Rookie Ball Cap LA Dodgers 3ACP7701N-07BKS Màu Đen",
          url: "/mu-mlb-rookie-ball-cap-la-dodgers-3acp7701n-07bks-mau-den-ph043203",
          image: require("@/assets/images/listProduct/munon/mu-mlb-rookie-ball-cap-la-dodgers-3acp7701n-07bks-mau-den-625faa93b1aba-20042022133915.webp"),
          price: "850.000",
          oldPrice: "1.100.000",
          discount: 23,
        },
        {
          name: "Mũ MLB Rookie Ballcap New York Yankees 3ACP7701N-50NYS Màu Xanh Navy",
          url: "/mu-mlb-rookie-ballcap-new-york-yankees-3acp7701n-50nys-mau-xanh-navy-ph039077",
          image: require("@/assets/images/listProduct/munon/mu-mlb-rookie-ballcap-new-york-yankees-3acp7701n-50nys-mau-xanh-navy-61ea2ef096fcf-21012022105632.webp"),
          price: "739.000",
          oldPrice: "1.200.000",
          discount: 38,
        },
      ],

      // List Handbag
      productHandbag: [
        {
          name: "Túi Đeo Chéo Nam Lacoste Leather Monogram Print Pouch Purse Bag NH4398MR B43 Màu Xanh Rêu",
          url: "/tui-deo-cheo-nam-lacoste-leather-monogram-print-pouch-purse-bag-nh4398mr-b43-mau-xanh-reu-ph220897",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-cheo-lacoste-men-s-leather-monogram-print-pouch-purse-bag-nh4398mr-b43-mau-xanh-reu-677e1e525cb07-08012025134226.webp"),
          price: "3.300.000",
          oldPrice: "4.700.000",
          discount: 30,
        },
        {
          name: "Túi Đeo Chéo Nam Lacoste Monogram Pouch With Strap NH4398MR 000 Black Màu Đen",
          url: "/tui-deo-cheo-nam-lacoste-monogram-pouch-with-strap-nh4398mr-000-black-mau-den-ph220892",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-cheo-nam-lacoste-monogram-pouch-with-strap-nh4398mr-000-mau-den-68c904c7e3150-16092025133343.webp"),
          price: "3.300.000",
          oldPrice: "4.900.000",
          discount: 33,
        },
        {
          name: "Túi Đeo Chéo Nữ Gucci Interlocking G Crossbody Chain Bag 615523 CAO0G 6420 Red Màu Đỏ",
          url: "/tui-deo-cheo-nu-gucci-interlocking-g-crossbody-chain-bag-615523-cao0g-6420-red-mau-do-ph220812",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-cheo-nu-gucci-interlocking-g-crossbody-chain-bag-615523-cao0g-6420-mau-do-682199522bbb5-12052025134642.webp"),
          price: "17.500.000",
          oldPrice: "22.000.000",
          discount: 20,
        },
        {
          name: "Túi Đeo Vai Nữ Michael Kors MK Empire Medium Leather Chain-Link Pochette 32H3S8EW6L Màu Đen",
          url: "/tui-deo-vai-nu-michael-kors-mk-empire-medium-leather-chain-link-pochette-32h3s8ew6l-mau-den-ph220742",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-vai-nu-michael-kors-mk-empire-medium-leather-chain-link-pochette-32h3s8ew6l-mau-den-68e71e85e2b34-09102025093133.webp"),
          price: "2.590.000",
          oldPrice: "3.100.000",
          discount: 16,
        },
        {
          name: "Túi Tote Nữ Crocs Classic Small Woman Tote Bag Charm Pinky Girl -Pink Milk Màu Hồng Sữa",
          url: "/tui-tote-crocs-classic-small-woman-tote-bag-charm-pinky-girl-pink-milk-mau-hong-sua-ph220722",
          image: require("@/assets/images/listProduct/tuixach/tui-tote-crocs-classic-small-woman-tote-bag-charm-pinky-girl-pink-milk-mau-hong-sua-68e71505eadae-09102025085101.webp"),
          price: "1.055.000",
          oldPrice: "1.600.000",
          discount: 34,
        },
        {
          name: "Túi Cầm Tay Nam Coach Small Travel Kit In Signature Canvas CAR15 Màu Đen Xám",
          url: "/tui-cam-tay-nam-coach-small-travel-kit-in-signature-canvas-car15-mau-den-xam-ph105151",
          image: require("@/assets/images/listProduct/tuixach/tui-cam-tay-nam-coach-small-travel-kit-in-signature-canvas-car15-mau-den-xam-68d49e04bbdc7-25092025084228.webp"),
          price: "3.290.000",
          oldPrice: "3.560.000",
          discount: 8,
        },
        {
          name: "Set Ví Nam + Móc Khoá Michael Kors MK Logo Wallet And Key Chain 36T4LGFF1B Màu Đen",
          url: "/set-vi-nam-moc-khoa-michael-kors-mk-logo-wallet-and-key-chain-36t4lgff1b-mau-den-ph184912",
          image: require("@/assets/images/listProduct/tuixach/set-vi-nam-moc-khoa-michael-kors-mk-logo-wallet-and-key-chain-36t4lgff1b-mau-den-67de118b218ed-22032025082531.webp"),
          price: "1.690.000",
          oldPrice: "2.550.000",
          discount: 34,
        },
        {
          name: "Ví Nam Pedro Leather Bi-Fold Flip Wallet PM4-15940241 Màu Đen",
          url: "/vi-nam-pedro-leather-bi-fold-flip-wallet-pm4-15940241-mau-den-ph090610",
          image: require("@/assets/images/listProduct/tuixach/vi-nam-pedro-leather-bi-fold-flip-wallet-pm4-15940241-mau-den-647800901dd33-01062023092104.webp"),
          price: "1.090.000",
          oldPrice: "2.500.000",
          discount: 56,
        },
        {
          name: "Túi Đeo Chéo MLB Mini Monogram Jacquard New York Yankees 3ACRS014N-50BKS Màu Đen",
          url: "/tui-deo-cheo-mlb-mini-monogram-jacquard-new-york-yankees-3acrs014n-50bks-mau-den-ph133321",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-cheo-mlb-mini-monogram-jacquard-new-york-yankees-3acrs014n-50bks-mau-den-65bb48ef42b75-01022024143159.webp"),
          price: "2.390.000",
          oldPrice: "2.600.000",
          discount: 8,
        },
        {
          name: "Túi Đeo Chéo Nam Coach Warner Crossbody Bag In Signature Canvas CW217 Màu Xanh Navy",
          url: "/tui-deo-cheo-nam-coach-warner-crossbody-bag-in-signature-canvas-cw217-mau-xanh-navy-ph198972",
          image: require("@/assets/images/listProduct/tuixach/tui-deo-cheo-nam-coach-warner-crossbody-bag-in-signature-canvas-cw217-mau-xanh-navy-68465fc24fdbd-09062025111458.webp"),
          price: "4.890.000",
          oldPrice: "6.500.000",
          discount: 25,
        },
      ],

      // List Shoes
      productShoes: [
        {
          name: "Giày Tennis/Pickleball On Running Roger Pro 2 White 3WE10332840 Màu Trắng Size 38",
          url: "/giay-tennis-pickleball-on-running-roger-pro-2-white-3we10332840-mau-trang-ph220964",
          image: require("@/assets/images/listProduct/giay/tennis-pickleball-nu-on-running-roger-pro-2-white-3we10332840-68e86fee56b37-10102025093110.webp"),
          price: "4.800.000",
          oldPrice: "6.000.000",
          discount: 20,
        },
        {
          name: "Giày Tennis/Pickleball Nữ On Running The Roger Pro Fire Women 3WF30032626 Màu Trắng Ngà Size 36.5",
          url: "/giay-tennis-pickleball-nu-on-running-the-roger-pro-fire-women-3wf30032626-mau-trang-nga-size-36-5-ph220950",
          image: require("@/assets/images/listProduct/giay/giay-tennis-pickleball-nu-on-running-the-roger-pro-fire-women-3wf30032626-mau-trang-nga-size-36-5-68e86d6179ba2-10102025092017.webp"),
          price: "5.800.000",
          oldPrice: "7.000.000",
          discount: 17,
        },
        {
          name: "Giày Pickleball/Tennis Nike GP Challenge Pro Cannon White FB3145-004 Màu Xanh Trắng Size 41",
          url: "/giay-pickleball-tennis-nike-gp-challenge-pro-cannon-white-fb3145-004-mau-xanh-trang-size-41-ph220943",
          image: require("@/assets/images/listProduct/giay/giay-pickleball-tennis-nike-gp-challenge-pro-cannon-white-fb3145-004-mau-xanh-trang-size-41-68e86a12908e7-10102025090610.webp"),
          price: "2.650.000",
          oldPrice: "3.300.000",
          discount: 20,
        },
        {
          name: "Giày Sneaker Nam Dolce & Gabbana D&G White Portofino Sports Shoes CS2343 AE629 8T907 Màu Trắng Size 40",
          url: "/giay-sneaker-nam-dolce-gabbana-d-g-white-portofino-sports-shoes-cs2343-ae629-8t907-mau-trang-size-40-ph220745",
          image: require("@/assets/images/listProduct/giay/giay-sneaker-nam-dolce-gabbana-d-g-white-portofino-sports-shoes-cs2343-ae629-8t907-mau-trang-size-40-68e721bba54cc-09102025094515.webp"),
          price: "14.700.000",
          oldPrice: "16.380.000",
          discount: 10,
        },
        {
          name: "Giày Sneaker Nam Dolce & Gabbana D&G Painted Calfskin Portofino 'Black' CS2005 AY142 80999 Màu Đen Size 5",
          url: "/giay-sneaker-nam-dolce-gabbana-d-g-painted-calfskin-portofino-black-cs2005-ay142-80999-mau-den-size-5-ph220738",
          image: require("@/assets/images/listProduct/giay/giay-sneaker-nam-dolce-gabbana-d-g-painted-calfskin-portofino-black-cs2005-ay142-80999-mau-den-size-5-68e71ece7f19a-09102025093246.webp"),
          price: "15.200.000",
          oldPrice: "18.000.000",
          discount: 16,
        },
        {
          name: "Giày Pickleball Asics Upcourt 6 Pale Pink Light Ube 1074A045-701 Màu Hồng Tím Size 36",
          url: "/giay-pickleball-asics-upcourt-6-pale-pink-light-ube-1074a045-701-mau-hong-tim-size-36-ph193278",
          image: require("@/assets/images/listProduct/giay/giay-pickleball-asics-upcourt-6-pale-pink-light-ube-1074a045-701-mau-hong-tim-size-36-681d7c544b72d-09052025105356.webp"),
          price: "2.300.000",
          oldPrice: "4.550.000",
          discount: 49,
        },
        {
          name: "Giày Thể Thao Nam Nike Air Force 1 07 White CW2288-111/DD8959-100 Màu Trắng Size 42",
          url: "/giay-the-thao-nam-nike-air-force-1-07-white-cw2288-111-dd8959-100-mau-trang-size-42-ph068668",
          image: require("@/assets/images/listProduct/giay/giay-the-thao-nam-nike-air-force-1-07-white-cw2288-111-dd8959-100-mau-trang-size-42-63a556b51c21e-23122022142021.webp"),
          price: "2.750.000",
          oldPrice: "3.900.000",
          discount: 29,
        },
        {
          name: "Giày Thể Thao Adidas Advantage Base Court Lifestyle Shoes GW2063 Màu Trắng Size 39",
          url: "/giay-the-thao-adidas-advantage-base-court-lifestyle-shoes-gw2063-mau-trang-size-39-ph070302",
          image: require("@/assets/images/listProduct/giay/giay-the-thao-adidas-advantage-base-court-lifestyle-shoes-gw2063-mau-trang-size-39-63be2592d27a2-11012023095722.webp"),
          price: "1.550.000",
          oldPrice: "2.150.000",
          discount: 28,
        },
        {
          name: "Giày Bệt Michael Kors Mk Fulton Signature Brown Stud Màu Nâu Size 37",
          url: "/giay-bet-michael-kors-mk-fulton-signature-brown-stud-mau-nau-ph076582",
          image: require("@/assets/images/listProduct/giay/giay-bet-michael-kors-mk-fulton-signature-brown-stud-mau-nau-63f32f88cdb11-20022023153000.webp"),
          price: "2.890.000",
          oldPrice: "3.500.000",
          discount: 17,
        },
        {
          name: "Giày Thể Thao Nữ Nike WMNS Air Force 1 Low Valentine’s Day 2024 FZ5068-161 Màu Trắng Size 36.5",
          url: "/giay-the-thao-nu-nike-wmns-air-force-1-low-valentine-s-day-2024-fz5068-161-mau-trang-size-36-5-ph116297",
          image: require("@/assets/images/listProduct/giay/giay-the-thao-nu-nike-wmns-air-force-1-low-valentine-s-day-2024-fz5068-161-mau-trang-size-36-5-65840186854a8-21122023161238.webp"),
          price: "3.400.000",
          oldPrice: "4.560.000",
          discount: 25,
        },
      ],

      // List Fashion
      productFashion: [
        {
          name: "Áo Sơ Mi Cộc Tay Nam Ralph Lauren With Logo In Beige",
          url: "/ao-so-mi-coc-tay-nam-ralph-lauren-with-logo-in-beige-710978031001-mau-be-size-xs",
          image: require("@/assets/images/listProduct/thoitrang/ao-so-mi-coc-tay-nam-ralph-lauren-with-logo-in-beige-710978031001-mau-be-size-xs-68e887397b48d-10102025111033.webp"),
          price: "1.900.000",
          oldPrice: "2.500.000",
          discount: 24,
        },
        {
          name: "Áo Sơ Mi Nam Burberry Stone Check Grey Co Màu Xám",
          url: "/ao-so-mi-nam-burberry-stone-check-grey-co-mau-xam",
          image: require("@/assets/images/listProduct/thoitrang/ao-so-mi-nam-burberry-stone-check-grey-co-mau-xam-68e884230cc3d-10102025105723.webp"),
          price: "3.200.000",
          oldPrice: "4.000.000",
          discount: 20,
        },
        {
          name: "Áo Sơ Mi Nam Burberry Cambridge Long Sleeve Cotton Shirt Green Màu Xanh Lá",
          url: "/ao-so-mi-nam-burberry-cambridge-long-sleeve-cotton-shirt-green-mau-xanh-la",
          image: require("@/assets/images/listProduct/thoitrang/ao-so-mi-nam-burberry-cambridge-long-sleeve-cotton-shirt-green-mau-xanh-la-68e88239e4719-10102025104913.webp"),
          price: "3.400.000",
          oldPrice: "4.100.000",
          discount: 17,
        },
        {
          name: "Áo Len Cardigan Unisex Lacoste Timeline Clock V-Neck",
          url: "/ao-len-cardigan-unisex-lacoste-timeline-clock-v-neck-ah0823-mau-be-size-xxs",
          image: require("@/assets/images/listProduct/thoitrang/ao-len-cardigan-unisex-lacoste-timeline-clock-v-neck-ah0823-mau-be-size-xxs-68e87cb81b0c3-10102025102544.webp"),
          price: "2.150.000",
          oldPrice: "2.700.000",
          discount: 20,
        },
        {
          name: "Áo Nỉ Nam Lacoste Men’s Tennis Zipped Ripstop Sweatshirt",
          url: "/ao-ni-nam-lacoste-men-s-tennis-zipped-ripstop-sweatshirt-sh5199-x2i-mau-xanh-size-2",
          image: require("@/assets/images/listProduct/thoitrang/ao-ni-nam-lacoste-men-s-tennis-zipped-ripstop-sweatshirt-sh5199-x2i-mau-xanh-size-2-68e874f75d652-10102025095239.webp"),
          price: "3.100.000",
          oldPrice: "3.800.000",
          discount: 18,
        },
        {
          name: "Tất Nike Everyday Cushioned SX7672-100 Màu Trắng",
          url: "/tat-nike-everyday-cushioned-sx7672-100-mau-trang",
          image: require("@/assets/images/listProduct/thoitrang/tat-nike-everyday-cushioned-sx7672-100-mau-trang-65d5b91063685-21022024154920.webp"),
          price: "190.000",
          oldPrice: "230.000",
          discount: 17,
        },
        {
          name: "Tất Nike Everyday Cushioned SX7672-100 Màu Trắng",
          url: "/tat-nike-everyday-cushioned-sx7672-100-mau-trang",
          image: require("@/assets/images/listProduct/thoitrang/tat-nike-everyday-cushioned-sx7672-100-mau-trang-65d5b91063685-21022024154920.webp"),
          price: "190.000",
          oldPrice: "230.000",
          discount: 17,
        },
        {
          name: "Áo Khoác Adidas Essentials Down GH4589 Màu Đen",
          url: "/ao-khoac-adidas-essentials-down-gh4589-mau-den",
          image: require("@/assets/images/listProduct/thoitrang/ao-khoac-adidas-essentials-down-gh4589-mau-den-61baa4b4e301c-16122021093012.webp"),
          price: "2.450.000",
          oldPrice: "3.000.000",
          discount: 18,
        },
        {
          name: "Khăn Louis Vuitton Monogram Confidential Square Màu Trắng Đen",
          url: "/khan-louis-vuitton-m78667-monogram-confidential-square-mau-trang-den",
          image: require("@/assets/images/listProduct/thoitrang/khan-louis-vuitton-m78667-monogram-confidential-square-mau-trang-den-6333bfdca4feb-28092022103036.webp"),
          price: "7.900.000",
          oldPrice: "9.200.000",
          discount: 14,
        },
        {
          name: "Áo Phông Nam Lacoste Sport Regular Fit T-shirt With Contrast Branding",
          url: "/ao-phong-nam-lacoste-sport-regular-fit-tshirt-with-contrast-branding-th5189-00-mau-trang",
          image: require("@/assets/images/listProduct/thoitrang/ao-phong-nam-lacoste-sport-regular-fit-tshirt-with-contrast-branding-th5189-00-mau-trang-6487d4b9a14e7-13062023093017.webp"),
          price: "1.350.000",
          oldPrice: "1.700.000",
          discount: 21,
        },
      ],

      // List EyeWear
      productEyeWear: [
        {
          name: "Kính Mát Nam Cartier Sunglasses CT0473S 001 Màu Vàng",
          url: "/kinh-mat-cartier-sunglasses-ct0473s-001-mau-vang-ph220849",
          image: require("@/assets/images/listProduct/kinhmat/kinh-mat-cartier-sunglasses-ct0473s-001-mau-vang-68e76f9761937-09102025151727.webp"),
          price: "31.500.000",
          oldPrice: "35.000.000",
          discount: 10,
        },
        {
          name: "Gọng Kính Nam Cartier CT0349O 001 Màu Vàng Đen",
          url: "/gong-kinh-cartier-glasses-ct0349o-001-mau-vang-den-ph220842",
          image: require("@/assets/images/listProduct/kinhmat/gong-kinh-nam-cartier-ct0349o-001-mau-vang-den-6768da5529236-23122024103445.webp"),
          price: "22.500.000",
          oldPrice: "24.000.000",
          discount: 6,
        },
        {
          name: "Gọng Kính Nam Cartier CT0563O 002 Màu Bạc",
          url: "/gong-kinh-cartier-ct0563o-002-mau-bac-ph220839",
          image: require("@/assets/images/listProduct/kinhmat/gong-kinh-nam-cartier-ct0563o-002-mau-bac-68b176268bfd0-29082025164302.webp"),
          price: "22.000.000",
          oldPrice: "24.767.000",
          discount: 11,
        },
        {
          name: "Gọng Kính Nam Cartier CT0563O 001 Màu Vàng Gold",
          url: "/gong-kinh-cartier-ct0563o-001-mau-vang-gold-ph220837",
          image: require("@/assets/images/listProduct/kinhmat/gong-kinh-nam-cartier-ct0563o-001-mau-vang-gold-68b1704fb84e5-29082025161807.webp"),
          price: "22.000.000",
          oldPrice: "25.000.000",
          discount: 12,
        },
        {
          name: "Kính Mát Cartier Sunglasses CT0505S 003 Màu Nâu - Vàng",
          url: "/kinh-mat-cartier-ct0505s-003-mau-nau-vang-ph220785",
          image: require("@/assets/images/listProduct/kinhmat/kinh-mat-cartier-sunglasses-ct0505s-003-mau-nau-vang-68c76c95f006c-15092025083205.webp"),
          price: "29.800.000",
          oldPrice: "31.000.000",
          discount: 4,
        },
        {
          name: "Kính Bơi Unisex Speedo Biofuse 2.0 Màu Đen",
          url: "/kinh-boi-unisex-speedo-biofuse-2-0-mau-den-ph208666",
          image: require("@/assets/images/listProduct/kinhmat/kinh-boi-unisex-speedo-biofuse-2-0-mau-den-6887493254e99-28072025165602.webp"),
          price: "420.000",
          oldPrice: "699.000",
          discount: 40,
        },
        {
          name: "Kính Bơi Unisex Speedo Hydrosity 2.0 Goggle Au Grey/Blue Màu Xanh Xám",
          url: "/kinh-boi-unisex-speedo-hydrosity-2-0-goggle-au-grey-blue-mau-xanh-xam-ph208730",
          image: require("@/assets/images/listProduct/kinhmat/kinh-boi-unisex-speedo-hydrosity-2-0-goggle-au-grey-blue-mau-xanh-xam-6888403066e01-29072025102952.webp"),
          price: "360.000",
          oldPrice: "599.000",
          discount: 40,
        },
        {
          name: "Kính Mát Unisex Lacoste Grey Aviator Sunglasses L193S 035 58 Màu Xám",
          url: "/kinh-mat-unisex-lacoste-grey-aviator-sunglasses-l193s-035-58-mau-xam-ph150494",
          image: require("@/assets/images/listProduct/kinhmat/kinh-mat-unisex-lacoste-grey-aviator-sunglasses-l193s-035-58-mau-xam-6698847d95ecc-18072024095701.webp"),
          price: "2.050.000",
          oldPrice: "2.680.000",
          discount: 24,
        },
        {
          name: "Kính Mát Unisex Calvin Klein CK Grey Gradient Pilot Sunglasses CK20120S 045 55 Màu Xám Gradient",
          url: "/kinh-mat-unisex-calvin-klein-ck-grey-gradient-pilot-sunglasses-ck20120s-045-55-mau-xam-gradient-ph171690",
          image: require("@/assets/images/listProduct/kinhmat/kinh-mat-unisex-calvin-klein-ck-grey-gradient-pilot-sunglasses-ck20120s-045-55-mau-xam-gradient-6764e156b926c-20122024101534.webp"),
          price: "950.000",
          oldPrice: "1.500.000",
          discount: 37,
        },
        {
          name: "Kính Mát Unisex Lacoste Square Sunglasses L683S 006 55 Màu Tím Đen",
          url: "/kinh-mat-unisex-lacoste-square-sunglasses-l683s-006-55-mau-tim-den-ph181970",
          image: require("@/assets/images/listProduct/kinhmat/kinh-mat-lacoste-square-sunglasses-l683s-006-55-mau-tim-den-635a38ad69aa9-27102022145213.webp"),
          price: "1.800.000",
          oldPrice: "2.200.000",
          discount: 18,
        },
      ],

      // List LipStick
      productLipStick: [
        {
          name: "Son Dưỡng Yves Saint Laurent YSL Loveshine Candy Glow 5B Nude Crush Màu Đỏ Nâu",
          url: "/son-yves-saint-laurent-ysl-loveshine-candy-glow-5b-nude-crush-mau-do-nau-ph220998",
          image: require("@/assets/images/listProduct/sonmoi/son-yves-saint-laurent-ysl-loveshine-candy-glow-5b-nude-crush-mau-do-nau-68e882d246892-10102025105146.webp"),
          price: "1.500.000",
          oldPrice: "2.000.000",
          discount: 25,
        },
        {
          name: "Son Bobbi Brown Limited Edition Holiday Luxe Lip Colour Sweet Cherry Màu Đỏ Cam Đất",
          url: "/son-bobbi-brown-limited-edition-holiday-luxe-lip-colour-sweet-cherry-mau-do-cam-dat-ph220994",
          image: require("@/assets/images/listProduct/sonmoi/son-bobbi-brown-limited-edition-holiday-luxe-lip-colour-sweet-cherry-mau-do-cam-dat-68e87ef05026a-10102025103512.webp"),
          price: "1.200.000",
          oldPrice: "1.800.000",
          discount: 33,
        },
        {
          name: "Son Dưỡng Môi x Clé De Peau The Lip Serum 15ml (Dạng Tinh Chất)",
          url: "/son-duong-moi-x-cle-de-peau-the-lip-serum-15ml-dang-tinh-chat-ph220928",
          image: require("@/assets/images/listProduct/sonmoi/son-duong-moi-dang-tinh-chat-cle-de-peau-the-lip-serum-15ml-661c87a50a8eb-15042024084925.webp"),
          price: "1.650.000",
          oldPrice: "1.900.000",
          discount: 13,
        },
        {
          name: "Son Tom Ford Slim Lip Color Shine #153 Velvet Tux - Reddish Plum Màu Đỏ Hồng",
          url: "/son-tom-ford-slim-lip-color-shine-153-velvet-tux-reddish-plum-mau-do-hong-ph220921",
          image: require("@/assets/images/listProduct/sonmoi/son-tom-ford-slim-lip-color-shine-153-velvet-tux-reddish-plum-mau-do-hong-68e78ab3e2cf2-09102025171307.webp"),
          price: "1.590.000",
          oldPrice: "1.900.000",
          discount: 16,
        },
        {
          name: "Son Kem Chanel Le Rouge Duo Ultra Tenue Ultrawear Liquid Lip 48 Soft Rose Màu Hồng Đất",
          url: "/son-kem-chanel-le-rouge-duo-ultra-tenue-ultrawear-liquid-lip-48-soft-rose-mau-hong-dat-ph220829",
          image: require("@/assets/images/listProduct/sonmoi/son-kem-chanel-le-rouge-duo-ultra-tenue-ultrawear-liquid-lip-48-soft-rose-mau-hong-dat-68e7618369787-09102025141723.webp"),
          price: "1.650.000",
          oldPrice: "2.100.000",
          discount: 21,
        },
        {
          name: "Son Dior 777 Fahrenheit Velvet Finish Mini Màu Đỏ Cam 1.5g",
          url: "/son-dior-777-fahrenheit-velvet-finish-mini-mau-do-cam-ph134773",
          image: require("@/assets/images/listProduct/sonmoi/son-dior-777-fahrenheit-velvet-finish-mini-mau-do-cam-65d6f7a0ce451-22022024142832.webp"),
          price: "545.000",
          oldPrice: "690.000",
          discount: 21,
        },
        {
          name: "Son Dưỡng Dior Addict Lipstick Maximizer 009 Intense Rosewood Màu Hồng Đất",
          url: "/son-duong-dior-addict-lipstick-maximizer-009-intense-rosewood-mau-hong-dat-ph173735",
          image: require("@/assets/images/listProduct/sonmoi/son-dior-addict-lip-maximizer-009-intense-rosewood-mau-hong-dat-moi-nhat-2022-63ae8817888b4-30122022134127.webp"),
          price: "895.000",
          oldPrice: "1.300.000",
          discount: 31,
        },
        {
          name: "Son Dior Addict Lip Maximizer 024 Intense Brick Màu Đỏ Đất",
          url: "/son-dior-addict-lip-maximizer-024-intense-brick-mau-do-dat-ph064757",
          image: require("@/assets/images/listProduct/sonmoi/son-dior-addict-lip-maximizer-024-intense-brick-mau-do-dat-64239aaf6d3e7-29032023085559.webp"),
          price: "849.000",
          oldPrice: "1.300.000",
          discount: 35,
        },
        {
          name: "Son Dưỡng Dior Addict Lip Maximizer 009 Intense Rosewood Màu Hồng Đất",
          url: "/son-dior-addict-lip-maximizer-009-mau-hong-dat-ph064622",
          image: require("@/assets/images/listProduct/sonmoi/son-dior-addict-lip-maximizer-009-intense-rosewood-mau-hong-dat-moi-nhat-2022-63ae8817888b4-30122022134127.webp"),
          price: "890.000",
          oldPrice: "1.300.000",
          discount: 32,
        },
        {
          name: "Son Dưỡng Dior Addict Lip Glow Màu 001 Pink",
          url: "/son-duong-dior-addict-lip-glow-mau-001-pink-ph029642",
          image: require("@/assets/images/listProduct/sonmoi/son-duong-dior-addict-lip-glow-mau-001-pink-moi-nhat-2021-62061f790260d-11022022153401.webp"),
          price: "850.000",
          oldPrice: "1.050.000",
          discount: 19,
        },
      ],

      //PickleBall
      productPickleBall: [
        {
          name: "Giày Tennis/Pickleball On Running The Roger Pro Fire Shoes 3WF30032626 Màu Trắng Size 40",
          url: "/giay-tennis-pickleball-on-running-the-roger-pro-fire-women-s-shoes-3wf300032626-mau-trang-ph220945",
          image: require("@/assets/images/listProduct/pickleball/giay-tennis-pickleball-on-running-the-roger-pro-fire-shoes-mau-trang-68e86b92ef393-10102025091234.webp"),
          price: "5.800.000",
          oldPrice: "7.200.000",
          discount: 19,
        },
        {
          name: "Giày Tennis/Pickleball On Running The Roger Pro 2 Clay White Flame 3WE10330256 Màu Trắng Size 36.5",
          url: "/giay-tennis-pickleball-on-running-the-roger-pro-2-clay-white-flame-3we10330256-mau-trang-size-36-5-ph220587",
          image: require("@/assets/images/listProduct/pickleball/giay-tennis-pickleball-on-running-the-roger-pro-2-clay-white-flame-3we10330256-mau-trang-size-36-5-68e5e1bd90352-08102025105957.webp"),
          price: "5.400.000",
          oldPrice: "7.000.000",
          discount: 23,
        },
        {
          name: "Giày Tennis/Pickleball On Running On The Roger Pro 2 White Lime 3WE10332929 Phối Màu Size 38",
          url: "/giay-tennis-pickleball-on-running-on-the-roger-pro-2-white-lime-3we10332929-phoi-mau-size-38-ph220574",
          image: require("@/assets/images/listProduct/pickleball/giay-the-thao-on-running-on-the-roger-pro-2-white-lime-3we10332929-phoi-mau-size-37-685e6a4dc0bbf-27062025165421.webp"),
          price: "5.400.000",
          oldPrice: "7.000.000",
          discount: 23,
        },
        {
          name: "Giày Tennis/Pickleball On Running The Roger Pro 2 3ME10303602 Màu Hồng Size 40",
          url: "/giay-tennis-pickleball-on-running-the-roger-pro-2-3me10303602-mau-hong-size-40-ph220551",
          image: require("@/assets/images/listProduct/pickleball/giay-tennis-pickleball-on-running-the-roger-pro-2-3me10303602-mau-hong-size-40-68e5cc0b21952-08102025092723.webp"),
          price: "5.500.000",
          oldPrice: "7.000.000",
          discount: 21,
        },
        {
          name: "Vợt Pickleball Gearbox GX2 Power Hybrid 16mm Màu Đen",
          url: "/vot-pickleball-gearbox-gx2-power-hybrid-16mm-mau-den-ph219976",
          image: require("@/assets/images/listProduct/pickleball/vot-pickleball-gearbox-gx2-power-hybrid-16mm-mau-den-68df96e869d78-03102025162704.webp"),
          price: "6.500.000",
          oldPrice: "8.000.000",
          discount: 19,
        },
        {
          name: "Vợt Pickleball Joola Perseus Gen 4 Màu Đen Size 16mm",
          url: "/vot-pickleball-joola-perseus-gen-4-mau-den-size-16mm-ph182218",
          image: require("@/assets/images/listProduct/pickleball/vot-pickleball-joola-perseus-gen-4-mau-den-size-16mm-67ca74bdd29d1-07032025112325.webp"),
          price: "6.300.000",
          oldPrice: "7.500.000",
          discount: 16,
        },
        {
          name: "Vợt Pickleball Joola Ben Johns Perseus 3 - 16mm Paddle Màu Xanh Xám",
          url: "/vot-pickleball-joola-paddle-ben-johns-perseus-3-16mm-mau-xanh-xam-ph199343",
          image: require("@/assets/images/listProduct/pickleball/vot-pickleball-joola-ben-johns-perseus-3-16mm-paddle-mau-xanh-xam-6833e37f3207d-26052025104359.webp"),
          price: "4.900.000",
          oldPrice: "10.200.000",
          discount: 52,
        },
        {
          name: "Vợt Pickleball Selkirk LABS Project Boomstik Elongated Màu Đen",
          url: "/vot-pickleball-selkirk-labs-project-boomstik-elongated-mau-den-ph211635",
          image: require("@/assets/images/listProduct/pickleball/vot-pickleball-selkirk-labs-project-boomstik-elongated-mau-den-689ee965ecd7c-15082025150141.webp"),
          price: "8.800.000",
          oldPrice: "10.000.000",
          discount: 12,
        },
        {
          name: "Set Vợt Pickleball Joola Summer Daze Perseus Pro IV Limited Edition 16mm Màu Đen",
          url: "/set-vot-pickleball-joola-summer-daze-perseus-pro-iv-limited-edition-16mm-mau-den-ph214217",
          image: require("@/assets/images/listProduct/pickleball/set-vot-pickleball-joola-summer-daze-perseus-pro-iv-limited-edition-16mm-mau-den-68b7f3fa39c0b-03092025145330.webp"),
          price: "16.500.000",
          oldPrice: "20.900.000",
          discount: 21,
        },
        {
          name: "Vợt Pickleball Joola Gen Ben Johns Perseus Pro IV 16mm Màu Đen",
          url: "/vot-pickleball-joola-gen-ben-johns-perseus-pro-iv-16mm-mau-den-ph211626",
          image: require("@/assets/images/listProduct/pickleball/vo-t-pickleball-joola-gen-ben-johns-perseus-pro-iv-16mm-mau-den-689eddad51136-15082025141141.webp"),
          price: "6.300.000",
          oldPrice: "8.500.000",
          discount: 26,
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

  computed: {
    showFilterBox() {
      return this.showDropdown;
    },
  },
};
</script>

<style>

.search-custom-w {
  width: 100vw;
}

@media (min-width: 768px) {
  .search-custom-w {
    width: 50vw;
  }
} 

* {
  font-family: Arial, Helvetica, sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#body {
  width: 100vw;
  overflow-x: hidden;
}

/* ===== Header ===== */
#main-header {
  border-bottom: 2px solid #d1d1d1;
}

.truncate-2 {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: normal;
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

.slick-prev,
.slick-next {
  z-index: 1000;
}

@media screen and (max-width: 768px) {
  .slick-prev {
    left: 0;
  }

  .slick-next {
    right: 0;
  }
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
