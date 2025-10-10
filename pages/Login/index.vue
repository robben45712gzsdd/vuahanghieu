<template>
  <div class="w-100">
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


    <div class="py-5 container">
      <div class="row">
        <!-- Cột trái: Đăng nhập -->
        <div class="mb-4 mb-md-0 col-md-6">
          <div class="border h-100 card">
            <div class="card-body">
              <h2 class="mb-4 text-center card-title">Đăng nhập tài khoản</h2>
              <form>
                <div class="mb-3">
                  <label for="email" class="form-label">Email *</label>
                  <input
                    type="email"
                    class="form-control"
                    id="email"
                    placeholder="Nhập email"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="password" class="form-label">Mật khẩu *</label>
                  <input
                    type="password"
                    class="form-control"
                    id="password"
                    placeholder="Nhập mật khẩu"
                    required
                  />
                </div>
                <button type="submit" class="mb-3 w-100 btn btn-dark">
                  Đăng nhập
                </button>
                <div class="d-flex justify-content-between">
                  <a href="#" class="text-decoration-none small">Quên mật khẩu?</a>
                  <a href="#" class="text-decoration-none small">Trợ giúp</a>
                </div>
              </form>

              <hr class="my-4" />

              <h5 class="mb-3 text-center">Hoặc đăng nhập bằng</h5>
              <button class="mb-3 w-100 btn btn-primary">
                <i class="me-2 bi bi-facebook"></i> Đăng nhập bằng Facebook
              </button>
              <button class="w-100 btn btn-danger">
                <i class="me-2 bi bi-google"></i> Đăng nhập bằng Google
              </button>
            </div>
          </div>
        </div>

        <!-- Cột phải: Khách hàng đăng ký mới -->
        <div class="col-md-6">
          <div class="border h-100 card">
            <div class="d-flex flex-column justify-content-center px-4 text-center card-body">
              <h2 class="mb-4 card-title">Khách hàng đăng ký mới</h2>
              <p class="text-muted">
                Bằng cách tạo tài khoản với Vua Hàng Hiệu, bạn sẽ có thể di chuyển qua
                quy trình thanh toán nhanh hơn, lưu trữ nhiều địa chỉ giao hàng, xem và
                theo dõi đơn hàng của bạn trong tài khoản của bạn và hơn thế nữa.
              </p>
              <nuxt-link to="/signup" class="mx-auto mt-3 btn-outline-dark w-50 btn">
                Đăng ký ngay
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
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
  }
}
}
</script>
<style scoped>
.custom-width {
  width: 100vw;
}

@media (min-width: 768px) {
  .custom-width {
    width: 50vw;
  }
}
.card {
  border: none;
  border-radius: 10px;
}

.card-title {
  font-size: 1.5rem;
  font-weight: 600;
}

button i {
  vertical-align: middle;
}

.btn-outline-dark {
  transition: all 0.2s ease;
}

.btn-outline-dark:hover {
  background-color: #000;
  color: #fff;
}

@media (max-width: 768px) {
  .card-body {
    padding: 1.5rem !important;
  }
}
</style>
