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
        </div>
      </div>
    </header>

    <!-- Product Section -->
    <div class="container py-2">
      <div class="row">
        <!-- Breadcrumb -->
        <nav aria-label="breadcrumb">
          <ol class="breadcrumb">
            <li class="breadcrumb-item">
              <nuxt-link to="/">Trang chủ</nuxt-link>
            </li>
            <li class="breadcrumb-item active" aria-current="page">
              Son Dior Addict Lip Maximizer 024 Intense Brick Màu Đỏ Đất
            </li>
          </ol>
        </nav>

        <!-- Product Info and Gallery -->
        <div class="row">
          <!-- Ảnh sản phẩm -->
          <div class="col-lg-5">
            <div
              id="productCarousel"
              class="carousel slide"
              data-bs-ride="carousel"
            >
              <div class="carousel-inner border rounded">
                <div
                  v-for="(image, index) in productImages"
                  :key="index"
                  :class="['carousel-item', { active: index === 0 }]"
                >
                  <img
                    :src="image.src"
                    class="d-block w-100 rounded"
                    :alt="image.alt"
                    style="max-height: 500px; object-fit: contain"
                  />
                </div>
              </div>
              <button
                class="carousel-control-prev"
                type="button"
                data-bs-target="#productCarousel"
                data-bs-slide="prev"
              >
                <span class="carousel-control-prev-icon"></span>
              </button>
              <button
                class="carousel-control-next"
                type="button"
                data-bs-target="#productCarousel"
                data-bs-slide="next"
              >
                <span class="carousel-control-next-icon"></span>
              </button>
            </div>

            <!-- thumbnail nhỏ -->
            <div class="d-flex flex-wrap mt-2">
              <a
                v-for="(image, index) in productImages"
                :key="index"
                href="#"
                @click.prevent="setActiveSlide(index)"
                class="me-2 mb-2 border rounded overflow-hidden d-block"
              >
                <img
                  :src="image.src"
                  :alt="image.alt"
                  class="img-fluid"
                  style="width: 80px; height: 80px; object-fit: cover"
                />
              </a>
            </div>
          </div>

          <!-- Thông tin sản phẩm -->
          <div class="col-lg-7">
            <h2 class="fw-bold mb-2">
              <nuxt-link to="/dior" class="text-decoration-none text-dark"
                >Dior</nuxt-link
              >
            </h2>

            <h1 class="h4 fw-semibold text-dark mb-3">
              Son Dior Addict Lip Maximizer 024 Intense Brick Màu Đỏ Đất
            </h1>

            <div class="mb-3">
              <p class="mb-1">
                Mã SP: <span class="fw-semibold">h064757</span>
              </p>
              <p class="mb-1">
                Danh mục:
                <nuxt-link
                  to="/son-moi"
                  class="text-decoration-none text-primary"
                  >Son Môi</nuxt-link
                >
              </p>
              <p class="mb-1">
                Lượt mua: <span class="fw-semibold text-dark">660</span>
              </p>
              <p class="text-muted small">
                Lượt mua này được tổng hợp từ lượt bán thành công của các sản
                phẩm tương tự trên Vua Hàng Hiệu.
              </p>
            </div>

            <div class="mb-3 d-flex align-items-center">
              <span class="me-2">Đánh giá:</span>
              <div class="text-warning me-2">
                <!-- <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i> -->
                <img
                  src="@/assets/images/productThumnail/star-list.svg"
                  alt="star"
                  width="100"
                />
              </div>
              <a href="#" class="text-decoration-none text-primary small"
                >Viết đánh giá</a
              >
            </div>

            <div class="d-flex product-price">
              <!-- Cột trái -->
              <div class="w-50 pe-3">
                <!-- Giá -->
                <div class="mb-3">
                  <h3 class="text-danger fw-bold fs-3 mb-1">
                    {{ productSelected.priceReal }}
                  </h3>
                  <p class="text-muted mb-0">
                    <s>{{ productSelected.priceSale }}</s>
                    <span class="badge bg-danger ms-2"
                      >Giảm {{ productSelected.discount }}</span
                    >
                  </p>
                </div>

                <!-- Thông tin sản phẩm -->
                <div class="mb-3">
                  <p class="mb-1">
                    <strong>Giới tính:</strong> {{ productSelected.sex }}
                  </p>
                  <p class="mb-1">
                    <strong>Màu sắc:</strong> {{ productSelected.color }}
                  </p>
                  <p class="mb-1">
                    <strong>Xuất xứ thương hiệu:</strong>
                    {{ productSelected.origin }}
                  </p>
                  <p class="mb-1">
                    <strong>Phân loại:</strong> {{ productSelected.category }}
                  </p>
                  <p class="mb-1">
                    <strong>Gọi đặt mua:</strong>
                    <a
                      href="tel:0939348888"
                      class="text-decoration-none text-danger fw-semibold"
                      >093.934.8888</a
                    >
                    <small class="text-muted">(08:00 - 21:00)</small>
                  </p>
                  <p class="text-success fw-semibold mb-0">
                    Freeship nội thành Hà Nội & nội thành Hồ Chí Minh
                  </p>
                </div>

                <!-- Nút hành động -->
                <div class="d-flex flex-wrap gap-2 mb-3">
                  <button class="btn btn-dark fw-semibold text-uppercase">
                    Thêm vào giỏ
                  </button>
                  <button class="btn btn-danger fw-semibold text-uppercase">
                    Mua ngay
                  </button>
                </div>

                <!-- Chia sẻ -->
                <div>
                  <strong>Chia sẻ:</strong>
                  <ul
                    class="list-inline d-inline-flex align-items-center ms-2 mb-0"
                  >
                    <li class="list-inline-item">
                      <div class="d-inline-block" style="width: 20px">
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          xmlns:xlink="http://www.w3.org/1999/xlink"
                          version="1.1"
                          id="Capa_1"
                          x="0px"
                          y="0px"
                          viewBox="0 0 155.139 155.139"
                          style="enable-background: new 0 0 155.139 155.139"
                          xml:space="preserve"
                          class="mdl-js"
                        >
                          <g>
                            <path
                              id="f_1_"
                              style="fill: #010002"
                              d="M89.584,155.139V84.378h23.742l3.562-27.585H89.584V39.184   c0-7.984,2.208-13.425,13.67-13.425l14.595-0.006V1.08C115.325,0.752,106.661,0,96.577,0C75.52,0,61.104,12.853,61.104,36.452   v20.341H37.29v27.585h23.814v70.761H89.584z"
                            />
                          </g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                        </svg>
                      </div>
                    </li>
                    <li class="list-inline-item">
                      <div class="d-inline-block" style="width: 20px">
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          xmlns:xlink="http://www.w3.org/1999/xlink"
                          version="1.1"
                          id="Capa_1"
                          x="0px"
                          y="0px"
                          viewBox="0 0 512 512"
                          style="enable-background: new 0 0 512 512"
                          xml:space="preserve"
                          class="mdl-js"
                        >
                          <g>
                            <g>
                              <path
                                d="M512,97.248c-19.04,8.352-39.328,13.888-60.48,16.576c21.76-12.992,38.368-33.408,46.176-58.016    c-20.288,12.096-42.688,20.64-66.56,25.408C411.872,60.704,384.416,48,354.464,48c-58.112,0-104.896,47.168-104.896,104.992    c0,8.32,0.704,16.32,2.432,23.936c-87.264-4.256-164.48-46.08-216.352-109.792c-9.056,15.712-14.368,33.696-14.368,53.056    c0,36.352,18.72,68.576,46.624,87.232c-16.864-0.32-33.408-5.216-47.424-12.928c0,0.32,0,0.736,0,1.152    c0,51.008,36.384,93.376,84.096,103.136c-8.544,2.336-17.856,3.456-27.52,3.456c-6.72,0-13.504-0.384-19.872-1.792    c13.6,41.568,52.192,72.128,98.08,73.12c-35.712,27.936-81.056,44.768-130.144,44.768c-8.608,0-16.864-0.384-25.12-1.44    C46.496,446.88,101.6,464,161.024,464c193.152,0,298.752-160,298.752-298.688c0-4.64-0.16-9.12-0.384-13.568    C480.224,136.96,497.728,118.496,512,97.248z"
                              />
                            </g>
                          </g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                        </svg>
                      </div>
                    </li>
                    <li class="list-inline-item">
                      <div class="d-inline-block" style="width: 20px">
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          xmlns:xlink="http://www.w3.org/1999/xlink"
                          version="1.1"
                          id="Capa_1"
                          x="0px"
                          y="0px"
                          viewBox="0 0 438.529 438.529"
                          style="enable-background: new 0 0 438.529 438.529"
                          xml:space="preserve"
                          class="mdl-js"
                        >
                          <g>
                            <path
                              d="M409.141,109.203c-19.608-33.592-46.205-60.189-79.798-79.796C295.751,9.801,259.065,0,219.281,0   C179.5,0,142.812,9.801,109.22,29.407c-33.597,19.604-60.194,46.201-79.8,79.796C9.809,142.8,0.008,179.485,0.008,219.267   c0,44.35,12.085,84.611,36.258,120.767c24.172,36.172,55.863,62.912,95.073,80.232c-0.762-20.365,0.476-37.209,3.709-50.532   l28.267-119.348c-4.76-9.329-7.139-20.93-7.139-34.831c0-16.175,4.089-29.689,12.275-40.541   c8.186-10.85,18.177-16.274,29.979-16.274c9.514,0,16.841,3.14,21.982,9.42c5.142,6.283,7.705,14.181,7.705,23.7   c0,5.896-1.099,13.084-3.289,21.554c-2.188,8.471-5.041,18.273-8.562,29.409c-3.521,11.132-6.045,20.036-7.566,26.692   c-2.663,11.608-0.476,21.553,6.567,29.838c7.042,8.278,16.372,12.423,27.983,12.423c20.365,0,37.065-11.324,50.107-33.972   c13.038-22.655,19.554-50.159,19.554-82.514c0-24.938-8.042-45.21-24.129-60.813c-16.085-15.609-38.496-23.417-67.239-23.417   c-32.161,0-58.192,10.327-78.082,30.978c-19.891,20.654-29.836,45.352-29.836,74.091c0,17.132,4.854,31.505,14.56,43.112   c3.235,3.806,4.283,7.898,3.14,12.279c-0.381,1.143-1.141,3.997-2.284,8.562c-1.138,4.565-1.903,7.522-2.281,8.851   c-1.521,6.091-5.14,7.994-10.85,5.708c-14.654-6.085-25.791-16.652-33.402-31.689c-7.614-15.037-11.422-32.456-11.422-52.246   c0-12.753,2.047-25.505,6.14-38.256c4.089-12.756,10.468-25.078,19.126-36.975c8.663-11.9,19.036-22.417,31.123-31.549   c12.082-9.135,26.787-16.462,44.108-21.982s35.972-8.28,55.959-8.28c27.032,0,51.295,5.995,72.8,17.986   c21.512,11.992,37.925,27.502,49.252,46.537c11.327,19.036,16.987,39.403,16.987,61.101c0,28.549-4.948,54.243-14.842,77.086   c-9.896,22.839-23.887,40.778-41.973,53.813c-18.083,13.042-38.637,19.561-61.675,19.561c-11.607,0-22.456-2.714-32.548-8.135   c-10.085-5.427-17.034-11.847-20.839-19.273c-8.566,33.685-13.706,53.77-15.42,60.24c-3.616,13.508-11.038,29.119-22.27,46.819   c20.367,6.091,41.112,9.13,62.24,9.13c39.781,0,76.47-9.801,110.062-29.41c33.595-19.602,60.192-46.199,79.794-79.791   c19.606-33.599,29.407-70.287,29.407-110.065C438.527,179.485,428.74,142.795,409.141,109.203z"
                            />
                          </g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                          <g></g>
                        </svg>
                      </div>
                    </li>
                  </ul>
                  <button
                    class="btn btn-link text-decoration-none text-dark p-0 ms-3"
                  >
                    <i class="bi bi-heart me-1"></i> Đã thích (403)
                  </button>
                </div>
              </div>

              <!-- Cột phải -->
              <div class="w-50 ps-3">
                <div class="border rounded p-2 bg-white">
                  <!-- Banner -->
                  <a href="/app" class="d-block mb-2">
                    <img
                      src="@/assets/images/productThumnail/banner-app-dk.png"
                      alt="VHH App"
                      class="img-fluid rounded"
                    />
                  </a>

                  <!-- Shop Info -->
                  <div class="border rounded p-3 mb-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="me-2">
                        <img
                          src="@/assets/images/productThumnail/shop.svg"
                          width="20"
                          height="20"
                          alt="shop"
                        />
                      </div>
                      <div class="flex-grow-1">
                        <div
                          class="d-flex justify-content-between align-items-center"
                        >
                          <a
                            href="/shop/the-signature-hub"
                            class="fw-bold text-dark text-decoration-none"
                            >The Signature Hub</a
                          >
                          <button
                            class="btn btn-sm btn-outline-warning py-0 px-2"
                          >
                            Theo dõi
                          </button>
                        </div>
                        <div class="text-muted small">
                          ★★★★☆ <span>(4787)</span>
                        </div>
                      </div>
                    </div>

                    <ul class="list-unstyled mb-3 small">
                      <li class="d-flex align-items-start mb-1">
                        <img
                          src="@/assets/images/productThumnail/checkbox.svg"
                          width="16"
                          height="16"
                          alt="check"
                          class="me-2 mt-1"
                        />
                        <span
                          >Miễn phí đổi trả
                          <a
                            href="/tin-tuc/chinh-sach-doi-tra"
                            target="_blank"
                            class="text-primary"
                            >(Xem điều kiện đổi trả)</a
                          ></span
                        >
                      </li>
                      <li class="d-flex align-items-start mb-1">
                        <img
                          src="@/assets/images/productThumnail/checkbox.svg"
                          width="16"
                          height="16"
                          alt="check"
                          class="me-2 mt-1"
                        />
                        <span>Kiểm tra hàng trước khi nhận</span>
                      </li>
                      <li class="d-flex align-items-start mb-2">
                        <img
                          src="@/assets/images/productThumnail/checkbox.svg"
                          width="16"
                          height="16"
                          alt="check"
                          class="me-2 mt-1"
                        />
                        <span>Hoàn tiền nếu phát hiện hàng giả</span>
                      </li>
                    </ul>

                    <div class="text-center mb-2">
                      <a
                        href="/shop/the-signature-hub"
                        class="btn btn-outline-dark w-100"
                        >XEM SHOP</a
                      >
                    </div>
                    <div class="text-center small">
                      Bán hàng cùng Vua Hàng Hiệu?
                      <a href="" target="_blank" class="text-primary"
                        >Đăng ký</a
                      >
                    </div>
                  </div>

                  <!-- Báo lỗi -->
                  <div class="d-flex align-items-start small text-muted">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="16"
                      height="16"
                      fill="#ff0000"
                      class="bi bi-exclamation-triangle mdl-js"
                      viewBox="0 0 16 16"
                    >
                      <path
                        d="M7.938 2.016A.13.13 0 0 1 8.002 2a.13.13 0 0 1 .063.016.146.146 0 0 1 .054.057l6.857 11.667c.036.06.035.124.002.183a.163.163 0 0 1-.054.06.116.116 0 0 1-.066.017H1.146a.115.115 0 0 1-.066-.017.163.163 0 0 1-.054-.06.176.176 0 0 1 .002-.183L7.884 2.073a.147.147 0 0 1 .054-.057zm1.044-.45a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566z"
                      />
                      <path
                        d="M7.002 12a1 1 0 1 1 2 0 1 1 0 0 1-2 0zM7.1 5.995a.905.905 0 1 1 1.8 0l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995z"
                      />
                    </svg>
                    <span
                      >Nếu bạn không thêm được sản phẩm vào giỏ hàng? Hãy
                      <span class="text-danger fw-semibold">báo lỗi</span> cho
                      chúng tôi.</span
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- Product Description and Tabs -->
        <div class="d-flex gap-5 product-description">
          <div class="mt-5 col-md-8">
            <ul class="nav nav-tabs">
              <li class="nav-item">
                <a
                  class="nav-link"
                  :class="{ active: activeTab === 'details' }"
                  @click="activeTab = 'details'"
                  >Chi tiết</a
                >
              </li>
              <li class="nav-item">
                <a
                  class="nav-link"
                  :class="{ active: activeTab === 'reviews' }"
                  @click="activeTab = 'reviews'"
                  >Bình luận <span class="badge bg-secondary">106</span></a
                >
              </li>
              <li class="nav-item">
                <a
                  class="nav-link"
                  :class="{ active: activeTab === 'qa' }"
                  @click="activeTab = 'qa'"
                  >Hỏi đáp</a
                >
              </li>
            </ul>
            <div class="tab-content p-4 border">
              <div v-if="activeTab === 'details'" class="tab-pane active">
                <div v-html="productSelected.descriptionHtml"></div>
                <!-- Add more product description content here -->
              </div>
              <div v-if="activeTab === 'reviews'" class="tab-pane active">
                <div class="d-flex align-items-center mb-3 w-100">
                  <div class="p-4 bg-light rounded border w-100">
                    <div class="row">
                      <!-- Cột trái: Tổng đánh giá -->
                      <div class="col-md-4 text-center">
                        <h2 class="text-danger fw-bold mb-0">5/5</h2>
                        <div class="text-warning fs-4 mb-1">
                          <i class="bi bi-star-fill"></i>
                          <i class="bi bi-star-fill"></i>
                          <i class="bi bi-star-fill"></i>
                          <i class="bi bi-star-fill"></i>
                          <i class="bi bi-star-fill"></i>
                        </div>
                        <p class="text-muted small mb-0">(106 đánh giá)</p>
                      </div>

                      <!-- Cột giữa: biểu đồ sao -->
                      <div class="col-md-5">
                        <div
                          class="d-flex align-items-center mb-1"
                          v-for="i in 5"
                          :key="i"
                        >
                          <span class="me-2 text-warning"
                            ><i class="bi bi-star-fill"></i> {{ 6 - i }}</span
                          >
                          <div class="progress flex-grow-1" style="height: 6px">
                            <div
                              class="progress-bar bg-dark"
                              :style="{ width: getPercent(6 - i) + '%' }"
                            ></div>
                          </div>
                          <span class="ms-2 text-muted small"
                            >({{ getCount(6 - i) }})</span
                          >
                        </div>
                      </div>

                      <!-- Cột phải: nút -->
                      <div
                        class="col-md-3 text-center d-flex flex-column justify-content-center"
                      >
                        <span class="small text-muted mb-2"
                          >Chia sẻ nhận xét về sản phẩm</span
                        >
                        <button
                          class="btn btn-dark px-4 text-uppercase fw-semibold"
                        >
                          Viết nhận xét
                        </button>
                      </div>
                    </div>

                    <hr class="my-4" />

                    <!-- Danh sách bình luận -->
                    <div class="review-item mb-3 d-flex">
                      <div class="me-3">
                        <div
                          class="bg-secondary text-white rounded-circle d-flex align-items-center justify-content-center"
                          style="width: 40px; height: 40px"
                        >
                          H
                        </div>
                      </div>
                      <div>
                        <div class="text-warning small mb-1">
                          <i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i>
                        </div>
                        <strong>Huỳnh Thị Phúc Khiêm</strong>
                        <small class="text-muted">15:41, 13/10/2025</small>
                        <div class="text-success small">
                          <i class="bi bi-check-circle"></i> Đã mua hàng
                        </div>
                        <p class="mb-0">Rất tốt</p>
                      </div>
                    </div>

                    <div class="review-item mb-3 d-flex">
                      <div class="me-3">
                        <div
                          class="bg-secondary text-white rounded-circle d-flex align-items-center justify-content-center"
                          style="width: 40px; height: 40px"
                        >
                          N
                        </div>
                      </div>
                      <div>
                        <div class="text-warning small mb-1">
                          <i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i>
                        </div>
                        <strong>Nguyễn Thị Báu</strong>
                        <small class="text-muted">18:30, 09/10/2025</small>
                        <p class="mb-0">Quá đẹp</p>
                      </div>
                    </div>

                    <div class="review-item d-flex">
                      <div class="me-3">
                        <div
                          class="bg-secondary text-white rounded-circle d-flex align-items-center justify-content-center"
                          style="width: 40px; height: 40px"
                        >
                          N
                        </div>
                      </div>
                      <div>
                        <div class="text-warning small mb-1">
                          <i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i
                          ><i class="bi bi-star-fill"></i>
                        </div>
                        <strong>Nguyễn Thị Báu</strong>
                        <small class="text-muted">18:28, 09/10/2025</small>
                        <p class="mb-0">Đẹp quá</p>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- Add review content here -->
              </div>
              <div v-if="activeTab === 'qa'" class="tab-pane active">
                <div class="card mb-3">
                  <div class="card-body">
                    <h5 class="card-title">GỬI CÂU HỎI</h5>
                    <div
                      v-for="(item, index) in sampleQuestions"
                      :key="index"
                      class="mb-4"
                    >
                      <p><strong>Hỏi:</strong> {{ item.question }}</p>
                      <p>
                        <strong>Đáp:</strong>
                        <!-- <span v-if="item.answer !== 'TRẢ LỜI'">{{ item.answer }}</span>
                        <input v-else v-model="item.answer" type="text" class="form-control mb-2"
                          placeholder="Nhập câu trả lời..." /> -->
                      </p>
                      <p><strong>Bởi:</strong> {{ item.author }}</p>
                      <p><strong>Ngày:</strong> {{ item.date }}</p>
                      <button
                        v-if="item.answer === 'TRẢ LỜI'"
                        @click="saveAnswer(index)"
                        class="btn btn-primary btn-sm"
                      >
                        Gửi
                      </button>
                      <hr v-if="index < sampleQuestions.length - 1" />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Cột lựa chọn khác -->
          <div class="col-lg-4 mt-5 col-md-4">
            <h6 class="fw-bold mb-3">Sản phẩm tương tự:</h6>
            <div class="row g-2">
              <div
                class="col-4 text-center"
                v-for="(item, index) in otherProducts"
                :key="index"
              >
                <img
                  :src="item.image"
                  alt="option"
                  class="img-fluid border rounded mb-1"
                  style="width: 100%; height: 90px; object-fit: contain"
                />
                <p class="text-danger fw-semibold small mb-0">
                  {{ item.price }}
                </p>
              </div>
            </div>
          </div>
        </div>
        <!-- Suggested products  -->
        <div class="py-4 container suggested-products">
          <h3
            class="m-auto mb-3 pb-2 border-3 border-black border-bottom text-center fw-normal"
          >
            Sản phẩm khác của gian hàng The Signature Hub
          </h3>
          <div class="position-relative product-carousel">
            <VueSlickCarousel
              v-bind="productCarouselSettings"
              ref="productSlick"
            >
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
        <!-- To Gift is to Love -->
        <div class="to-gift-is-to-love container">
          <img
            src="@/assets/images/banner/banner-to-gift.webp"
            alt="to gift is to love"
            class="rounded w-100 img-fluid"
          />
          <!-- Content for Brand Top Sale can be added here -->
          <div class="position-relative product-carousel">
            <VueSlickCarousel
              v-bind="productCarouselSettings"
              ref="productSlick"
            >
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
          <p class="mt-4">
            <b>Miễn trừ trách nhiệm</b>: Mặc dù chúng tôi luôn cố gắng đảm bảo
            rằng mọi thông tin đều chính xác, nhưng đôi khi nhà sản xuất có thể
            thay đổi danh sách thành phần của sản phẩm. Bao bì và thành phần
            trong thực tế có thể khác biệt với những gì được mô tả trên website.
            Chúng tôi khuyến cáo bạn không nên chỉ dựa trên thông tin được ghi
            trên website, mà hãy luôn luôn đọc nhãn mác, cảnh báo và hướng dẫn
            sử dụng trước khi dùng sản phẩm. Để biết thêm thông tin, vui lòng
            liên hệ nhà sản xuất. Nội dung trên trang web này chỉ được dùng để
            tham khảo, không thể thay thế chỉ dẫn của dược sỹ, bác sỹ và các
            chuyên gia sức khỏe. Bạn không nên sử dụng thông tin này để tự chẩn
            đoán và điều trị bệnh của mình. Hãy liên hệ các cơ quan y tế ngay
            lập tức nếu bạn nghi ngờ mình đang gặp vấn đề về sức khỏe. Các thông
            tin và công bố liên quan đến thực phẩm chức năng giảm cân chưa được
            thẩm định bởi Cục quản lý Thực phẩm và Dược phẩm, cũng như không
            được dùng để chẩn đoán, điều trị, chữa trị, hay phòng ngừa bệnh tật
            cùng các vấn đề sức khỏe khác. Chúng tôi không chịu trách nhiệm về
            nhầm lẫn hay sai lệch về sản phẩm.
          </p>
        </div>
      </div>
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
import { products } from "../../constants/product";
export default {
  components: { VueSlickCarousel },
  layout: "nonelayout",
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
      sampleQuestions: [
        {
          question: "Này là trên li hay trên bông?",
          answer: "TRẢ LỜI",
          author: "Ngọc Trinh vào 23:52, 17/12/2023",
          date: "TRẢ LỜI",
        },
        {
          question:
            "Hôm nay đá hàng thị trường ngay 2 ngày có nhắn dược không à?",
          answer: "TRẢ LỜI",
          author: "Lái Thị Trà My vào 10:50, 26/06/2023",
          date: "TRẢ LỜI",
        },
        {
          question: "Có nhieu mau không à?",
          answer: "TRẢ LỜI",
          author: "Quách Diệu Trà vào 03:19, 16/06/2023",
          date: "TRẢ LỜI",
        },
        {
          question: "Màu đỏ đat co sang da không à?",
          answer: "TRẢ LỜI",
          author: "Trần Tiến vào 07:37, 07/05/2023",
          date: "TRẢ LỜI",
        },
      ],
      comments: [
        {
          name: "Ngọc Anh",
          stars: 5,
          content:
            "Son rất đẹp, màu lên chuẩn, mùi thơm dễ chịu. Giao hàng nhanh!",
          date: "2 ngày trước",
        },
        {
          name: "Thu Hằng",
          stars: 4,
          content:
            "Chất son mịn, hơi khô nhẹ nếu không dưỡng môi trước, nói chung ok.",
          date: "5 ngày trước",
        },
      ],
      starData: {
        5: 75,
        4: 18,
        3: 5,
        2: 1,
        1: 1,
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
      productImages: [],
      otherProducts: [],
      activeTab: "details",
      productSelected: null,
    };
  },
  created() {
    const productId = this.$route.params.id;
    this.productSelected = products.find(
      (product) => product.id === parseInt(productId)
    );
    if (this.productSelected) {
      this.productImages = this.productSelected.productImages;
      this.otherProducts = this.productSelected.otherProducts;
    }
  },
  methods: {
    setActiveSlide(index) {
      const carousel = document.querySelector("#productCarousel");
      const bsCarousel = new bootstrap.Carousel(carousel);
      bsCarousel.to(index);
    },

    // Trả về số lượt đánh giá theo sao
    getCount(star) {
      // return this.starData && this.starData[star] ? this.starData[star] : 0; -->
        return Math.floor(Math.random() * 5);
    },

    // Tính phần trăm chiều rộng thanh rating
    getPercent(star) {
      if (!this.starData) return 0;
      const total = Object.values(this.starData).reduce(
        (sum, val) => sum + val,
        0
      );
      const count = this.getCount(star);
      return total > 0 ? (count / total) * 100 : 0;
    },
    saveAnswer(index) {
      // Logic để lưu câu trả lời (có thể gửi lên server hoặc cập nhật state)
      this.$emit("update-answer", {
        index,
        answer: this.questions[index].answer,
      });
    },
  },
};
</script>

<style>
img.product-img-responsive {
  width: -webkit-fill-available !important;
}
</style>
<style scoped>
body {
  width: 100vw;
  overflow-x: hidden;
}
@media screen and (max-width: 768px) {
  .row{
    margin: auto;
    padding: 0;
  }
  .w-50.ps-3 {
    width: 100% !important;
    padding: 20px 0 !important;
  }

  .w-50.pe-3 {
    width: 100% !important;
    padding: 20px 0 !important;
  }

  .d-flex.product-price {
    flex-direction: column;
    padding: 20px 0 !important;
  }

  .product-description{
    flex-direction: column-reverse ;
    padding: 20px 0 !important;
  }

  .tab-content.p-4.border{
    padding: 15px !important;
  }
}
.rating-star-list {
  /* Add custom star rating styles */
  display: inline-block;
  width: 100px;
  height: 20px;
  background: url("/assets/images/stars.png") 0 calc(-20px * var(--rating-star)) /
    100px 100px no-repeat;
}

.custom-width {
  width: 100vw;
}

@media (min-width: 768px) {
  .custom-width {
    width: 50vw;
  }
}

hr {
  border-color: #ddd;
}

/* ===== Header ===== */
#main-header {
  border-bottom: 2px solid #d1d1d1;
}

#main-header .truncate-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  /* Giới hạn 2 dòng */
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
</style>
