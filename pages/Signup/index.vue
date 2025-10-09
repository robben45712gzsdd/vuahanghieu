<template>
  <div class="w-100">
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
    <div class="container py-5">
      <div class="row">
        <div class="col-md-6">
          <div class="card">
            <div class="card-body">
              <h2 class="card-title text-center">
                Thông tin đăng ký tài khoản
              </h2>
              <form>
                <div class="mb-3">
                  <label for="hoVaTen" class="form-label">Họ và tên *</label>
                  <input
                    type="text"
                    class="form-control"
                    id="hoVaTen"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="email" class="form-label">Email *</label>
                  <input
                    type="email"
                    class="form-control"
                    id="email"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="dienThoai" class="form-label">Điện thoại *</label>
                  <input
                    type="tel"
                    class="form-control"
                    id="dienThoai"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="tenTaiKhoan" class="form-label"
                    >Tên tài khoản *</label
                  >
                  <input
                    type="text"
                    class="form-control"
                    id="tenTaiKhoan"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="matKhau" class="form-label">Mật khẩu *</label>
                  <input
                    type="password"
                    class="form-control"
                    id="matKhau"
                    required
                  />
                </div>
                <div class="mb-3">
                  <label for="xacNhan" class="form-label">Xác nhận *</label>
                  <input
                    type="password"
                    class="form-control"
                    id="xacNhan"
                    required
                  />
                </div>
                <div class="mb-3 form-check">
                  <input
                    type="checkbox"
                    class="form-check-input"
                    id="dieuKhoan"
                    required
                  />
                  <label class="form-check-label" for="dieuKhoan"
                    >Bằng cách nhấn vào "Đăng Ký", bạn đã đồng ý với các điều
                    khoản và chính sách của chúng tôi.</label
                  >
                </div>
                <button type="submit" class="btn btn-dark w-100">
                  ĐĂNG KÝ
                </button>
              </form>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="card">
            <div class="card-body text-center">
              <h2 class="card-title">Hoặc đăng nhập bằng</h2>
              <button class="btn btn-primary w-100 mb-3">
                Đăng nhập bằng Facebook
              </button>
              <button class="btn btn-danger w-100">
                Đăng nhập bằng Google
              </button>
              <hr />
              <p class="mt-3">Các điều quyền khi đăng ký tài khoản</p>
              <p>
                Nhận quyền truy cập để quản lý tài khoản và sử dụng dịch vụ.
              </p>
              <p>Lưu các mục yêu thích và danh sách yêu thích của bạn.</p>
              <p>Lưu các đơn đã hàng và số thẻ để đơn hàng của bạn.</p>
              <p>Dịch vụ hỗ trợ</p>
              <p>Bạn cần giúp đỡ? Xin hãy gọi điện đến Hotline: 093.934.8888</p>
              <p>Bạn đã có tài khoản? <nuxt-link to="/login">Đăng nhập</nuxt-link></p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
hr {
  border-color: #ddd;
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

</style>
