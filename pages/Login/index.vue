<template>
  <div class="w-100">
     <!-- Header -->
    <header id="main-header" class="bg-white">
      <!-- Top black bar -->
      <div class="bg-dark py-1 text-white">
        <div class="d-flex justify-content-end container">
          <ul class="nav">
            <!-- Shop -->
            <li class="nav-item">
              <a class="text-warning text-uppercase nav-link" href="/createShop">Tạo Shop</a>
            </li>

            <!-- Tài khoản with dropdown -->
            <li class="nav-item dropdown">
              <a class="text-white text-uppercase nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                aria-expanded="false">
                Tài khoản
              </a>
              <ul class="dropdown-menu dropdown-menu-end">
                <li><a class="text-uppercase dropdown-item" href="/login">Đăng nhập</a></li>
                <li><a class="text-uppercase dropdown-item" href="/signup">Đăng ký</a></li>
              </ul>
            </li>

            <!-- Giỏ hàng -->
            <li class="nav-item">
              <a class="d-flex align-items-center text-white text-uppercase nav-link" href="/cart">
                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" c fill="currentColor" class="me-2 bi bi-cart3"
                  viewBox="0 0 16 16">
                  <path
                    d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .49.598l-1 5a.5.5 0 0 1-.465.401l-9.397.472L4.415 11H13a.5.5 0 0 1 0 1H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5M3.102 4l.84 4.479 9.144-.459L13.89 4zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4m7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4m-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2m7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2" />
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
          <nuxt-link to="/" class="d-flex align-items-center mb-2 mb-md-0 col-md-3 col-12">
            <img src="@/assets/images/vuahanghieu-new.svg" alt="logo" class="img-fluid" style="max-height: 50px" />
          </nuxt-link>

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
              <nuxt-link to="/login" class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor"
                  class="me-2 bi bi-person-circle" viewBox="0 0 16 16">
                  <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0" />
                  <path fill-rule="evenodd"
                    d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8m8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1" />
                </svg>
                <span>Đăng nhập</span>
              </nuxt-link>
              <span class="divider"></span>
              <nuxt-link to="signup" class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
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

<style scoped>
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
