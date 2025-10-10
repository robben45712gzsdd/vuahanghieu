<template>
    <div class="registration-page">
        <div class="logo-container">
            <img src="@/assets/images/vhh.png" alt="logo">
        </div>

        <div class="form-container">
            <a-form-model ref="registrationForm" :model="form" :rules="rules" :label-col="{ span: 0 }"
                :wrapper-col="{ span: 24 }">
                <a-form-model-item prop="storeName">
                    <a-input v-model="form.storeName" placeholder="Tên gian hàng" size="large" />
                </a-form-model-item>

                <a-form-model-item prop="phone">
                    <a-input v-model="form.phone" placeholder="Điện thoại" size="large" />
                </a-form-model-item>

                <a-form-model-item prop="email">
                    <a-input v-model="form.email" placeholder="Email" size="large" type="email" />
                </a-form-model-item>

                <a-form-model-item prop="password">
                    <a-input-password v-model="form.password" placeholder="Password" size="large" />
                </a-form-model-item>

                <a-form-model-item prop="taxCode">
                    <a-input v-model="form.taxCode" placeholder="Đăng ký kinh doanh/Mã số thuế" size="large">
                        <template #suffix>
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <rect x="4" y="4" width="16" height="16" rx="2" stroke="#999" stroke-width="2" />
                                <path d="M8 4V20M16 4V20M4 12H20" stroke="#999" stroke-width="2" />
                            </svg>
                        </template>
                    </a-input>
                </a-form-model-item>

                <a-form-model-item prop="businessType">
                    <a-input v-model="form.businessType" placeholder="Ngành hàng kinh doanh" size="large">
                        <template #suffix>
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <rect x="3" y="3" width="8" height="8" rx="1" stroke="#999" stroke-width="2" />
                                <rect x="13" y="3" width="8" height="8" rx="1" stroke="#999" stroke-width="2" />
                                <rect x="3" y="13" width="8" height="8" rx="1" stroke="#999" stroke-width="2" />
                                <rect x="13" y="13" width="8" height="8" rx="1" stroke="#999" stroke-width="2" />
                            </svg>
                        </template>
                    </a-input>
                </a-form-model-item>

                <a-form-model-item prop="website">
                    <a-input v-model="form.website" placeholder="Website/ Link Facebook" size="large" />
                </a-form-model-item>

                <a-form-model-item prop="address">
                    <a-textarea v-model="form.address" placeholder="Địa chỉ" :rows="4" />
                </a-form-model-item>

                <div class="section-title">Giấy phép kinh doanh / CCCD</div>

                <div class="upload-section">
                    <a-button type="primary" size="large" block @click="triggerFileUpload" class="upload-button">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"
                            style="margin-right: 8px;">
                            <path d="M12 4V16M12 4L8 8M12 4L16 8" stroke="white" stroke-width="2"
                                stroke-linecap="round" />
                            <path d="M4 17V19C4 20.1046 4.89543 21 6 21H18C19.1046 21 20 20.1046 20 19V17"
                                stroke="white" stroke-width="2" stroke-linecap="round" />
                        </svg>
                        Chọn giấy phép kinh doanh/CCCD
                    </a-button>

                    <input ref="fileInput" type="file" accept="image/*,.pdf" multiple style="display: none"
                        @change="handleFileChange" />

                    <div v-if="fileList.length > 0" class="preview-container">
                        <div v-for="(file, index) in fileList" :key="index" class="preview-item">
                            <img v-if="file.type.startsWith('image/')" :src="file.preview" :alt="file.name" />
                            <div v-else class="pdf-preview">
                                <svg width="48" height="48" viewBox="0 0 24 24" fill="none"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path
                                        d="M7 2H14L20 8V20C20 21.1046 19.1046 22 18 22H7C5.89543 22 5 21.1046 5 20V4C5 2.89543 5.89543 2 7 2Z"
                                        fill="#ff4d4f" stroke="#ff4d4f" stroke-width="2" />
                                    <path d="M14 2V8H20" stroke="#ff4d4f" stroke-width="2" stroke-linecap="round" />
                                    <text x="12" y="16" text-anchor="middle" fill="white" font-size="6"
                                        font-weight="bold">PDF</text>
                                </svg>
                                <span class="file-name">{{ file.name }}</span>
                            </div>
                            <a-button type="danger" size="small" shape="circle" class="remove-button"
                                @click="removeFile(index)">
                                <svg width="12" height="12" viewBox="0 0 24 24" fill="none"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path d="M6 6L18 18M6 18L18 6" stroke="white" stroke-width="3"
                                        stroke-linecap="round" />
                                </svg>
                            </a-button>
                        </div>
                    </div>
                </div>

                <a-form-model-item prop="agree">
                    <a-checkbox v-model="form.agree">
                        <span class="terms-text">
                            Tôi đã đọc, hiểu rõ và đồng ý với
                            <a href="#" @click.prevent>Quy chế hoạt động</a>,
                            <a href="#" @click.prevent>điều khoản</a> và
                            <a href="#" @click.prevent>Chính sách bảo mật thông tin</a> của Vua Hàng Hiệu.
                        </span>
                    </a-checkbox>
                </a-form-model-item>

                <a-button type="primary" size="large" block class="register-button" @click="handleSubmit">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"
                        style="margin-right: 8px;">
                        <path d="M5 13L9 17L19 7" stroke="white" stroke-width="3" stroke-linecap="round"
                            stroke-linejoin="round" />
                    </svg>
                    Đăng ký
                </a-button>

                <div class="login-link">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"
                        style="margin-right: 4px; vertical-align: middle;">
                        <circle cx="12" cy="8" r="4" stroke="#666" stroke-width="2" />
                        <path d="M4 20C4 16.6863 6.68629 14 10 14H14C17.3137 14 20 16.6863 20 20" stroke="#666"
                            stroke-width="2" stroke-linecap="round" />
                    </svg>
                    Bạn đã có tài khoản ? <a href="#" @click.prevent="goToLogin">Đăng nhập</a>
                </div>
            </a-form-model>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RegistrationPage',
    data() {
        const validatePhone = (rule, value, callback) => {
            const phoneRegex = /^(0|\+84)[0-9]{9,10}$/;
            if (!value) {
                callback(new Error('Vui lòng nhập số điện thoại'));
            } else if (!phoneRegex.test(value)) {
                callback(new Error('Số điện thoại không hợp lệ'));
            } else {
                callback();
            }
        };

        const validateAgree = (rule, value, callback) => {
            if (!value) {
                callback(new Error('Vui lòng đồng ý với điều khoản và chính sách'));
            } else {
                callback();
            }
        };

        return {
            form: {
                storeName: '',
                phone: '',
                email: '',
                password: '',
                taxCode: '',
                businessType: '',
                website: '',
                address: '',
                agree: false
            },
            fileList: [],
            rules: {
                storeName: [
                    { required: true, message: 'Vui lòng nhập tên gian hàng', trigger: 'blur' },
                    { min: 3, max: 100, message: 'Tên gian hàng phải từ 3-100 ký tự', trigger: 'blur' }
                ],
                phone: [
                    { required: true, validator: validatePhone, trigger: 'blur' }
                ],
                email: [
                    { required: true, message: 'Vui lòng nhập email', trigger: 'blur' },
                    { type: 'email', message: 'Email không hợp lệ', trigger: 'blur' }
                ],
                password: [
                    { required: true, message: 'Vui lòng nhập mật khẩu', trigger: 'blur' },
                    { min: 6, message: 'Mật khẩu phải có ít nhất 6 ký tự', trigger: 'blur' }
                ],
                taxCode: [
                    { required: true, message: 'Vui lòng nhập đăng ký kinh doanh/Mã số thuế', trigger: 'blur' }
                ],
                businessType: [
                    { required: true, message: 'Vui lòng nhập ngành hàng kinh doanh', trigger: 'blur' }
                ],
                address: [
                    { required: true, message: 'Vui lòng nhập địa chỉ', trigger: 'blur' }
                ],
                agree: [
                    { validator: validateAgree, trigger: 'change' }
                ]
            }
        };
    },
    methods: {
        triggerFileUpload() {
            this.$refs.fileInput.click();
        },
        handleFileChange(e) {
            const files = Array.from(e.target.files);
            files.forEach(file => {
                const fileObj = {
                    name: file.name,
                    type: file.type,
                    size: file.size,
                    preview: null,
                    raw: file
                };

                if (file.type.startsWith('image/')) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        fileObj.preview = e.target.result;
                        this.fileList.push(fileObj);
                    };
                    reader.readAsDataURL(file);
                } else {
                    this.fileList.push(fileObj);
                }
            });

            // Reset input để có thể chọn lại cùng file
            e.target.value = '';
        },
        removeFile(index) {
            this.fileList.splice(index, 1);
        },
        handleSubmit() {
            this.$refs.registrationForm.validate(valid => {
                if (valid) {
                    if (this.fileList.length === 0) {
                        this.$message.warning('Vui lòng tải lên giấy phép kinh doanh/CCCD');
                        return;
                    }

                    this.$message.success('Đăng ký thành công!');
                    console.log('Form data:', this.form);
                    console.log('Files:', this.fileList);

                    // Xử lý submit form ở đây
                    // this.$router.push('/success')
                } else {
                    this.$message.error('Vui lòng kiểm tra lại thông tin!');
                    return false;
                }
            });
        },
        goToLogin() {
            // this.$router.push('/login')
            this.$message.info('Chuyển đến trang đăng nhập');
        }
    }
};
</script>

<style scoped>
.registration-page {
    background: linear-gradient(135deg, rgba(2,0,36,1) 0%, rgba(9,9,121,1) 35%, rgba(14,172,204,1) 100%);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
}

.logo-container {
    text-align: center;
    margin-bottom: 30px;
}



.form-container {
    background: white;
    border-radius: 5px;
    padding: 30px 20px;
    box-shadow: 0 15px 50px rgba(0, 0, 0, 0.3);
    max-width: 500px;
    width: 100%;
}

.section-title {
    color: #333;
    font-size: 14px;
    font-weight: 500;
    margin: 20px 0 15px 0;
}

.upload-section {
    margin-bottom: 20px;
}

.upload-button {
    background: #17a2b8;
    border-color: #17a2b8;
    height: 45px;
    font-weight: 500;
    display: flex;
    align-items: center;
    justify-content: center;
}

.upload-button:hover {
    background: #138496;
    border-color: #138496;
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(23, 162, 184, 0.3);
}

.preview-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 15px;
    margin-top: 15px;
}

.preview-item {
    position: relative;
    border: 2px solid #e8e8e8;
    border-radius: 8px;
    overflow: hidden;
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fafafa;
}

.preview-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.pdf-preview {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 10px;
    text-align: center;
}

.file-name {
    font-size: 11px;
    color: #666;
    margin-top: 8px;
    word-break: break-all;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.remove-button {
    position: absolute;
    top: 5px;
    right: 5px;
    width: 24px;
    height: 24px;
    min-width: 24px;
    padding: 0;
    display: flex;
    align-items: center;
    justify-content: center;
}

.terms-text {
    color: #666;
    font-size: 13px;
    line-height: 1.6;
}

.terms-text a {
    color: #17a2b8;
    text-decoration: none;
}

.terms-text a:hover {
    text-decoration: underline;
}

.register-button {
    background: #5a9ec5;
    border-color: #5a9ec5;
    height: 45px;
    font-weight: 600;
    font-size: 16px;
    margin-top: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.register-button:hover {
    background: #4a8eb5;
    border-color: #4a8eb5;
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(90, 158, 197, 0.3);
}

.login-link {
    text-align: center;
    margin-top: 20px;
    color: #666;
    font-size: 14px;
}

.login-link a {
    color: #17a2b8;
    text-decoration: none;
    font-weight: 500;
}

.login-link a:hover {
    text-decoration: underline;
}

/* Ant Design customization */
::v-deep .ant-input,
::v-deep .ant-input-password,
::v-deep .ant-input-affix-wrapper {
    border-radius: 8px;
}

::v-deep .ant-input-lg {
    padding: 12px 15px;
    font-size: 14px;
}

::v-deep .ant-form-item {
    margin-bottom: 15px;
}

::v-deep .ant-checkbox-wrapper {
    line-height: 1.6;
}

@media (max-width: 576px) {
    .form-container {
        padding: 30px 20px;
    }

    .logo-text {
        font-size: 20px;
    }

    .v-letter {
        font-size: 50px;
    }

    .preview-container {
        grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    }
}
</style>