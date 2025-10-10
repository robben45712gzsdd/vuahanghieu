<template>
  <div id="cart">
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
              <a class="text-white text-uppercase nav-link dropdown-toggle" href="#" role="button"
                data-bs-toggle="dropdown" aria-expanded="false">
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
                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" fill="currentColor"
                  class="me-2 bi bi-cart3" viewBox="0 0 16 16">
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
          <nuxt-link to="/" class="d-flex align-items-center mb-2 mb-md-0 col-12 col-md-3">
            <img src="@/assets/images/vuahanghieu-new.svg" alt="logo" class="img-fluid"
              style="max-height: 50px" />
          </nuxt-link>

          <!-- Search bar -->
          <div class="mb-2 mb-md-0 col-12 col-md-6">
            <div class="input-group">
              <input type="text" class="form-control header-search"
                placeholder="Tìm kiếm sản phẩm, thương hiệu..." />
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
          <div class="d-flex justify-content-md-end justify-content-start mt-3 mt-md-0 col-12 col-md-3">
            <div class="d-flex align-items-center shadow-sm rounded-pill auth-box">
              <nuxt-link to="/login"
                class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor"
                  class="me-2 bi bi-person-circle" viewBox="0 0 16 16">
                  <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0" />
                  <path fill-rule="evenodd"
                    d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8m8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1" />
                </svg>
                <span>Đăng nhập</span>
              </nuxt-link>
              <span class="divider"></span>
              <nuxt-link to="signup"
                class="d-flex align-items-center px-2 py-1 text-decoration-none auth-link">
                <span>Đăng ký</span>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </header>

    <div class="bg-light py-4">
      <!-- Breadcrumb -->
      <div class="mb-4 container">
        <a-breadcrumb>
          <a-breadcrumb-item>
            <a href="/">Trang chủ</a>
          </a-breadcrumb-item>
          <a-breadcrumb-item>Giỏ hàng</a-breadcrumb-item>
        </a-breadcrumb>
      </div>

      <div class="container">
        <!-- Empty Cart Section -->
        <div class="shadow-sm mb-4 border-0 card">
          <div class="py-5 card-body">
            <div class="row">
              <!-- Left: Empty cart illustration -->
              <div class="d-flex align-items-center justify-content-center mb-4 mb-md-0 col-md-5">
                <img src="@/assets/images/empty.png" alt="empty cart" class="img-fluid" style="max-width: 320px;">
              </div>

              <!-- Right: Content -->
              <div class="d-flex flex-column justify-content-center col-md-7">
                <h1 class="mb-3 h3 fw-bold">Giỏ hàng của bạn đang rỗng!</h1>

                <div class="mb-4 text-muted">
                  <p class="mb-2">Thật tiếc! Chúng tôi biết bạn đang muốn mua món đồ gì đó.</p>
                  <p class="mb-2">Nhưng trước tiên bạn cần thêm món đồ đó vào giỏ hàng của mình.</p>
                  <p class="mb-0">Nhấn <strong class="text-danger cursor-pointer">vào đây</strong> để tiếp tục mua sắm.</p>
                </div>

                <!-- App Download Section -->
                <h2 class="mb-4 text-danger h5 fw-semibold">
                  Tải app Vua Hàng Hiệu để tìm kiếm sản phẩm dễ hơn
                </h2>

                <div class="align-items-center row g-3">
                  <div class="col-auto">
                    <div class="bg-white p-2 border border-2 rounded">
                      <img src="@/assets/images/cartpage/app.png" alt="qr" style="width: 120px; height: 120px;">
                    </div>
                  </div>

                  <div class="col">
                    <div class="d-flex flex-column gap-2">
                      <a href="#" class="d-inline-block">
                        <img src="@/assets/images/cartpage/appleStore.png" alt="App Store" style="height: 40px;">
                      </a>
                      <a href="#" class="d-inline-block">
                        <img src="@/assets/images/cartpage/googlePlay.png" alt="Google Play" style="height: 40px;">
                      </a>
                      <a href="#" class="d-inline-block">
                        <img src="@/assets/images/cartpage/huaweiPlay.png" alt="App Gallery" style="height: 40px;">
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Features Section -->
        <div class="shadow-sm border-0 card">
          <div class="p-4 p-md-5 card-body">
            <h2 class="mx-auto mb-5 pb-3 border-3 border-warning border-bottom text-center h4 fw-semibold"
              style="max-width: 600px;">
              An tâm khi mua sắm tại Vua Hàng Hiệu
            </h2>

            <div class="row g-4">
              <div class="col-md-6 col-lg-3">
                <div class="p-3 h-100 text-center feature-hover">
                  <div class="mb-3">
                    <img src="@/assets/images/cartpage/mien-phi-van-chuyen.svg" alt="freeship" style="height: 80px;" />
                  </div>
                  <h3 class="mb-2 h6 fw-semibold">Miễn phí vận chuyển</h3>
                  <p class="mb-0 text-muted small">
                    Miễn phí vận chuyển các đơn nội thành Hà Nội và nội thành Hồ Chí Minh từ 500K
                  </p>
                </div>
              </div>

              <div class="col-md-6 col-lg-3">
                <div class="p-3 h-100 text-center feature-hover">
                  <div class="mb-3">
                    <img src="@/assets/images/cartpage/doi-tra.svg" alt="doitra" style="height: 80px;" />
                  </div>
                  <h3 class="mb-2 h6 fw-semibold">Đổi trả đơn giản</h3>
                  <p class="mb-0 text-muted small">
                    Đổi trả và hoàn tiền trong vòng 5 ngày. Với bất kỳ sản phẩm lỗi, không đúng mô tả
                  </p>
                </div>
              </div>

              <div class="col-md-6 col-lg-3">
                <div class="p-3 h-100 text-center feature-hover">
                  <div class="mb-3">
                    <img src="@/assets/images/cartpage/san-pham-chinh-hang.svg" alt="chinhhang" style="height: 80px;" />
                  </div>
                  <h3 class="mb-2 h6 fw-semibold">Sản phẩm chính hãng</h3>
                  <p class="mb-0 text-muted small">
                    Bảo đảm sản phẩm chính hãng 100%. Hoàn tiền 150% nếu phát hiện hàng giả
                  </p>
                </div>
              </div>

              <div class="col-md-6 col-lg-3">
                <div class="p-3 h-100 text-center feature-hover">
                  <div class="mb-3">
                    <img src="@/assets/images/cartpage/bao-mat-thong-tin.svg" alt="ssl" style="height: 80px;" />
                  </div>
                  <h3 class="mb-2 h6 fw-semibold">Bảo mật thông tin</h3>
                  <p class="mb-0 text-muted small">
                    100% thông tin cá nhân và giao dịch của bạn được bảo vệ an toàn
                  </p>
                </div>
              </div>
            </div>
          </div>
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
              <button style="font-size: smaller;">Đăng ký</button>
            </div>
            <div class="subscribe-policy">
              Bằng cách đăng ký, bạn đồng ý với
              <a href="#">Chính sách bảo mật của chúng tôi</a>
            </div>
          </div>

          <!-- Icon mạng xã hội -->
          <div class="text-md-end text-center col-md-4">
            <div class="social-icons">
              <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                  class="bi bi-facebook" viewBox="0 0 16 16">
                  <path
                    d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951" />
                </svg></a>
              <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                  class="bi bi-instagram" viewBox="0 0 16 16">
                  <path
                    d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598 2.5 2.5 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334" />
                </svg></a>
              <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                  class="bi bi-pinterest" viewBox="0 0 16 16">
                  <path
                    d="M8 0a8 8 0 0 0-2.915 15.452c-.07-.633-.134-1.606.027-2.297.146-.625.938-3.977.938-3.977s-.239-.479-.239-1.187c0-1.113.645-1.943 1.448-1.943.682 0 1.012.512 1.012 1.127 0 .686-.437 1.712-.663 2.663-.188.796.4 1.446 1.185 1.446 1.422 0 2.515-1.5 2.515-3.664 0-1.915-1.377-3.254-3.342-3.254-2.276 0-3.612 1.707-3.612 3.471 0 .688.265 1.425.595 1.826a.24.24 0 0 1 .056.23c-.061.252-.196.796-.222.907-.035.146-.116.177-.268.107-1-.465-1.624-1.926-1.624-3.1 0-2.523 1.834-4.84 5.286-4.84 2.775 0 4.932 1.977 4.932 4.62 0 2.757-1.739 4.976-4.151 4.976-.811 0-1.573-.421-1.834-.919l-.498 1.902c-.181.695-.669 1.566-.995 2.097A8 8 0 1 0 8 0" />
                </svg></a>
              <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                  class="bi bi-twitter-x" viewBox="0 0 16 16">
                  <path
                    d="M12.6.75h2.454l-5.36 6.142L16 15.25h-4.937l-3.867-5.07-4.425 5.07H.316l5.733-6.57L0 .75h5.063l3.495 4.633L12.601.75Zm-.86 13.028h1.36L4.323 2.145H2.865z" />
                </svg></a>
              <a href="#"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                  class="bi bi-rss" viewBox="0 0 16 16">
                  <path
                    d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2z" />
                  <path
                    d="M5.5 12a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0m-3-8.5a1 1 0 0 1 1-1c5.523 0 10 4.477 10 10a1 1 0 1 1-2 0 8 8 0 0 0-8-8 1 1 0 0 1-1-1m0 4a1 1 0 0 1 1-1 6 6 0 0 1 6 6 1 1 0 1 1-2 0 4 4 0 0 0-4-4 1 1 0 0 1-1-1" />
                </svg></a>
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
              <img src="@/assets/images/footer/da-dang-ky-bo-cong-thuong.svg" alt="Ba Dang Ky" />
              <img src="@/assets/images/footer/dmca_copyright_protected150b.png" alt="DMCA" />
              <div class="d-flex flex-row gap-2 w-100">
                <img class="w-50" src="@/assets/images/footer/business-trust-seal-trust-lock.png" alt="Business" />
                <img class="w-50" src="@/assets/images/footer/privacy-trust-seal-trust-lock.png" alt="Privacy" />
              </div>
            </div>
          </div>
          <div class="mb-4 mb-md-0 col-lg-3 col-md-6">
            <h5 class="text-uppercase fw-semibold">CÂU HỎI THƯỜNG GẶP</h5>
            <ul class="list-unstyled">
              <li>
                <a href="#">Hướng dẫn cách tra cứu mã đơn hàng mua trên Vua Hàng Hiệu</a>
              </li>
              <li>
                <a href="#">Sản phẩm cần đổi hết hàng?</a>
              </li>
              <li>
                <a href="#">Nếu không có hóa đơn mua hàng tôi có thể trả lại sản phẩm
                  không?</a>
              </li>
              <li>
                <a href="#">Đơn hàng nhận được bị thiếu so với đơn hàng đã đặt</a>
              </li>
              <li>
                <a href="#">Sản phẩm nhận được không giống với hình ảnh trên website?</a>
              </li>
              <li>
                <a href="#">Vì sao tôi nhận được thông báo đơn hàng đã hủy do hết
                  hàng?</a>
              </li>
              <li>
                <a href="#">Nếu gặp vấn đề trong quá trình sử dụng sản phẩm, tôi cần liên
                  hệ với ai?</a>
              </li>
            </ul>
            <h6 class="fw-semibold">Tải ứng dụng Vua Hàng Hiệu ngay!</h6>
            <div class="d-flex flex-row gap-2 mt-3 w-100">
              <a href="#">
                <img class="w-100 h-100" src="@/assets/images/footer/apple-store.svg" alt="App Store" /></a>
              <a href="#">
                <img class="w-100 h-100" src="@/assets/images/footer/google-play.svg" alt="Google Play" /></a>
              <a href="#">
                <img class="w-100 h-100" src="@/assets/images/footer/huawei-gallery.svg" alt="AppGallery" /></a>
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
    <div class="d-flex flex-column flex-lg-row align-items-center justify-content-between gap-2 my-2 container">
      <div class="d-flex align-items-center gap-3" style="font-size: 10px">
        <p class="mb-0 fst-italic">© 2025 VUA HÀNG HIỆU.</p>
        <a href="">
          <p class="mb-0 text-uppercase">Điều khoản</p>
        </a>
        <a href="">
          <p class="mb-0 text-uppercase">Chính sách bảo mật</p>
        </a>
      </div>
      <img src="@/assets/images/footer/payment-method.svg" alt="Thanh toán" height="28" />
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
export default {
  name: 'CartPage',
  head() {
    return {
      title: 'Giỏ hàng - Vua Hàng Hiệu'
    }
  }
}
</script>

<style scoped>
.cursor-pointer {
  cursor: pointer;
}

.cursor-pointer:hover {
  text-decoration: underline;
}

.feature-hover {
  transition: transform 0.3s ease;
}

.feature-hover:hover {
  transform: translateY(-5px);
}

.auth-box {
  border: 1px solid #e0e0e0;
  padding: 2px;
}

.auth-link {
  color: #333;
  font-size: 14px;
}

.auth-link:hover {
  color: #000;
}

.divider {
  width: 1px;
  height: 20px;
  background: #e0e0e0;
  margin: 0 5px;
}

.header-search {
  border-right: none;
}

.btn-search {
  border-radius: 0 4px 4px 0;
}

::v-deep .ant-breadcrumb a {
  color: #666;
  text-decoration: none;
}

::v-deep .ant-breadcrumb a:hover {
  color: #1890ff;
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

a{
    color: #000;
}

.social-icons a:hover {
  background: #000;
}
</style>