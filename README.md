<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VCLOUD - Kết nối, bảo vệ và xây dựng mọi nơi</title>
    <style>
        /* Reset CSS */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
        }

        /* Header styles */
        header {
            background: #f8f9fa; /* Màu xám trắng */
            color: #333; /* Đổi màu chữ thành tối hơn để tương phản */
            padding: 0;
            display: flex;
            flex-direction: column;
            position: relative;
            z-index: 100;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .header-top {
            width: 100%;
            display: flex;
            justify-content: space-between; /* Thay đổi từ flex-start sang space-between */
            align-items: center;
            padding: 10px 40px;
            background: #ffffff;
            border-bottom: 1px solid #e9ecef;
        }

        .header-top-right {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .header-contact {
            display: flex;
            align-items: center;
            gap: 5px;
            color: #333;
            font-size: 0.9rem;
        }

        .language-selector {
            display: flex;
            align-items: center;
            gap: 5px;
            color: #333;
            font-size: 0.9rem;
            cursor: pointer;
        }

        .support-dropdown {
            position: relative;
            display: inline-block;
        }

        .support-dropdown > a {
            color: #333;
            text-decoration: none;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo img {
            height: 36px; /* Giảm 30% từ 120px xuống còn 36px */
            width: auto;
            object-fit: contain;
        }

        /* Responsive cho logo */
        @media (max-width: 768px) {
            .logo img {
                height: 24px; /* Giảm tương ứng cho mobile */
            }
        }

        .header-bottom {
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 40px;
            background: #f8f9fa; /* Màu xám trắng cho phần bottom */
        }

        nav {
            display: flex;
            align-items: center;
            justify-content: center;
            flex: 1;
        }

        nav ul {
            display: flex;
            gap: 30px;
            margin: 0;
            padding: 0;
            list-style: none;
        }

        /* Cập nhật màu chữ cho menu */
        nav ul li a {
            color: #333;
            text-decoration: none;
            font-size: 0.9rem;
            padding: 8px 0;
            transition: all 0.3s ease;
        }

        nav ul li a:hover {
            color: #1EE1E1;
        }

        .header-utilities {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        /* Cập nhật màu chữ cho utilities */
        .header-utilities a {
            color: #333;
            text-decoration: none;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        .header-utilities a:hover {
            color: #1EE1E1;
        }

        /* Dropdown menu */
        .dropdown-menu {
            display: none; /* Ẩn menu mặc định */
            position: absolute;
            top: 100%;
            left: 0;
            background-color: #fff;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            width: 600px; /* Làm menu rộng hơn */
            gap: 20px;
        }

        .dropdown-menu .dropdown-column {
            width: 200px;
        }

        .dropdown-menu .dropdown-column h3 {
            font-size: 1.2rem;
            color: #001a66;
            margin-bottom: 10px;
        }

        .dropdown-menu ul {
            display: flex;
            flex-wrap: wrap; /* Cho phép xuống dòng */
            gap: 10px; /* Khoảng cách giữa các mục */
            justify-content: center; /* Căn giữa các mục */
        }

        .dropdown-menu ul li {
            width: 45%; /* Đặt chiều rộng để chia thành 2 dòng */
            text-align: left; /* Căn trái nội dung */
        }

        .dropdown-menu .dropdown-column ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .dropdown-menu .dropdown-column ul li {
            margin-bottom: 10px;
        }

        .dropdown-menu .dropdown-column ul li a {
            color: #333;
            text-decoration: none;
            font-size: 1rem;
        }

        .dropdown-menu .dropdown-column ul li a:hover {
            color: #00ff99;
        }

        /* Cập nhật CSS cho Hero Section */
        .hero {
            padding: 50px 20px;
            background: #f4f4f4;
        }

        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 40px;
        }

        .hero-text {
            flex: 1;
            text-align: left;
        }

        .hero-text h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: #001a66;
        }

        .hero-text p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            color: #333;
        }

        .hero-text .cta-button {
            background: linear-gradient(135deg, #00ff99 0%, #96c93d 100%);
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: 500;
        }

        .hero-image {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .hero-image img {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero-content {
                flex-direction: column;
            }

            .hero-text {
                text-align: center;
            }

            .hero-image {
                order: -1;
            }
        }

        .stats {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            text-align: center;
            padding: 50px 20px;
            background: #f9f9f9;
        }

        .stats .stat {
            margin: 20px;
        }

        .stats .stat h3 {
            font-size: 2rem;
            color: #00ff99;
        }

        .testimonials {
            padding: 60px 20px;
            background: #f8f9fa;
            text-align: center;
        }

        .testimonials h2 {
            font-size: 2rem;
            color: #333;
            margin-bottom: 40px;
        }

        .testimonials-slider {
            max-width: 1000px;
            margin: 0 auto;
            position: relative;
        }

        .testimonial-slide {
            display: none;
            padding: 20px;
        }

        .testimonial-slide.active {
            display: block;
        }

        .testimonial-content {
            padding: 40px;
            margin-bottom: 20px;
            position: relative;
            display: flex;
            flex-direction: column;
        }

        .quote-icon {
            font-size: 4rem;
            color: #1EE1E1;
            position: absolute;
            top: -20px;
            left: 20px;
            opacity: 0.5;
        }

        .testimonial-content p {
            font-size: 1.1rem;
            line-height: 1.6;
            color: #333;
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 30px;
            margin-top: 30px;
            padding: 0 20px;
        }

        .testimonial-author img {
            width: auto;
            height: 80px; /* Tăng kích thước logo */
            object-fit: contain;
            margin-right: 20px;
            border-radius: 0;
        }

        .author-info {
            text-align: left;
            min-width: 150px;
        }

        .testimonial-navigation {
            position: absolute;
            width: 100%;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            justify-content: space-between;
            padding: 0 -20px;
        }

        .testimonial-navigation button {
            background: rgba(30, 225, 225, 0.1);
            border: none;
            color: #1EE1E1;
            font-size: 1.5rem;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .testimonial-navigation button:hover {
            background: rgba(30, 225, 225, 0.2);
        }

        .prev-testimonial {
            margin-left: -20px;
        }

        .next-testimonial {
            margin-right: -20px;
        }

        .featured-clients {
            padding: 50px 20px;
            text-align: center;
            background: #fff;
            overflow: hidden;
        }

        .featured-clients h2 {
            font-size: 2rem;
            margin-bottom: 40px;
            color: #333;
        }

        .client-slider {
            width: 100%;
            height: 85px; /* Giảm 15% từ 100px xuống 85px */
            position: relative;
            overflow: hidden;
            padding: 20px 0;
        }

        .slide-track {
            display: flex;
            width: calc(250px * 18);
            animation: scroll 46s linear infinite; /* Tăng 15% từ 40s lên 46s để chậm lại */
        }

        .slide {
            width: 212px; /* Giảm 15% từ 250px xuống 212px */
            height: 85px; /* Giảm 15% từ 100px xuống 85px */
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 20px;
        }

        .slide img {
            width: 100%;
            height: auto;
            object-fit: contain;
            transition: transform 0.3s ease;
        }

        .slide img:hover {
            transform: scale(1.1);
        }

        @keyframes scroll {
            0% {
                transform: translateX(0);
            }
            100% {
                transform: translateX(calc(-212px * 13)); /* Cập nhật theo width mới của slide */
            }
        }

        /* Thêm hiệu ứng fade ở hai bên */
        .client-slider::before,
        .client-slider::after {
            content: "";
            height: 100%;
            width: 100px;
            position: absolute;
            z-index: 2;
        }

        .client-slider::before {
            left: 0;
            background: linear-gradient(to right, #fff 0%, transparent 100%);
        }

        .client-slider::after {
            right: 0;
            background: linear-gradient(to left, #fff 0%, transparent 100%);
        }

        footer {
            background: #f4f8ff;
            padding: 40px 20px;
            font-size: 0.9rem;
            color: #333;
        }

        .footer-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 20px;
        }

        .footer-column {
            flex: 1;
            min-width: 200px;
        }

        .footer-column h3 {
            font-size: 1.2rem;
            color: #001a66;
            margin-bottom: 15px;
        }

        .footer-column ul {
            list-style: none;
            padding: 0;
        }

        .footer-column ul li {
            margin-bottom: 10px;
        }

        .footer-column ul li a {
            color: #333;
            text-decoration: none;
            font-size: 0.9rem;
        }

        .footer-column ul li a:hover {
            color: #00cc7a;
        }

        .social-icons {
            display: flex;
            gap: 10px;
            list-style: none;
            padding: 0;
        }

        .social-icons li img {
            width: 30px;
            height: 30px;
        }

        .footer-bottom {
            text-align: center;
            margin-top: 20px;
            font-size: 0.8rem;
            color: #666;
        }

        .footer-bottom a {
            color: #001a66;
            text-decoration: none;
            font-weight: bold;
        }

        .footer-bottom a:hover {
            color: #00cc7a;
        }

        .interactive-tour {
            text-align: center;
            padding: 50px 20px;
            background: #e6f7ff; /* Màu nền nhẹ */
        }

        .interactive-tour h2 {
            font-size: 2rem;
            color: #001a66;
            margin-bottom: 20px;
        }

        .interactive-tour p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            color: #333;
        }

        .interactive-tour .cta-button {
            background: linear-gradient(135deg, #00ff99 0%, #96c93d 100%);
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: 500;
        }

        .interactive-tour .cta-button:hover {
            background-color: #00cc7a;
        }

        .case-studies {
            padding: 50px 20px;
            background: #f9f9f9;
            text-align: center;
        }

        .case-studies-container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
        }

        .case-study {
            max-width: 300px;
            background: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            text-align: left;
        }

        .case-study img {
            width: 100%;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        .case-study h3 {
            font-size: 1.2rem;
            color: #001a66;
            margin-bottom: 10px;
        }

        .case-study p {
            font-size: 1rem;
            color: #333;
            margin-bottom: 15px;
        }

        .case-study a {
            color: #00ff99;
            text-decoration: none;
            font-weight: bold;
        }

        .case-study a:hover {
            text-decoration: underline;
        }

        .blog {
            padding: 50px 20px;
            background: #f9f9f9;
            text-align: center;
        }

        .blog-container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
        }

        .blog-post {
            max-width: 300px;
            background: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            text-align: left;
        }

        .blog-post img {
            width: 100%;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        .blog-post h3 {
            font-size: 1.2rem;
            color: #001a66;
            margin-bottom: 10px;
        }

        .blog-post p {
            font-size: 1rem;
            color: #333;
            margin-bottom: 15px;
        }

        .blog-post a {
            color: #00ff99;
            text-decoration: none;
            font-weight: bold;
        }

        .blog-post a:hover {
            text-decoration: underline;
        }

        /* Cập nhật style cho tất cả các nút CTA */
        .cta-button {
            background: linear-gradient(135deg, #1EE1E1 0%, #4EEC8C 100%);
            color: #fff;
            padding: 8px 16px;
            border-radius: 4px;
            text-decoration: none;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            border: none;
        }

        .cta-button:hover {
            background: linear-gradient(135deg, #4EEC8C 0%, #1EE1E1 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(30, 225, 225, 0.3);
        }

        .awards-section {
            padding: 60px 0;
            background: #fff;
        }

        .awards-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .awards-section h2 {
            font-size: 2rem;
            color: #333;
            text-align: center;
            margin-bottom: 20px;
        }

        .awards-description {
            text-align: center;
            max-width: 900px;
            margin: 0 auto 40px;
            line-height: 1.6;
            color: #666;
            font-size: 1rem;
        }

        .awards-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 30px;
            margin: 0 auto;
        }

        .award-item {
            background: #fff;
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 0.3s ease;
        }

        .award-item:hover {
            transform: translateY(-5px);
        }

        .award-item img {
            max-width: 100%;
            height: auto;
            object-fit: contain;
        }

        @media (max-width: 1200px) {
            .awards-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        @media (max-width: 992px) {
            .awards-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        @media (max-width: 768px) {
            .awards-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 480px) {
            .awards-grid {
                grid-template-columns: repeat(1, 1fr);
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-top">
            <div class="logo">
                <img src="file:///C:/Users/dangt/Downloads/Thiết kế chưa có tên (3).svg" alt="VCLOUD Logo">
            </div>
            <div class="header-top-right">
                <div class="header-contact">
                    <span>Sales: +84 (028) 7306 8789</span>
                </div>
                <div class="support-dropdown">
                    <a href="#support">Support ▾</a>
                </div>
                <div class="language-selector">
                    <span>🌐</span>
                    <span>VN</span>
                </div>
            </div>
        </div>
        <div class="header-bottom">
            <nav>
                <ul>
                    <li class="dropdown">
                        <a href="#about" id="dropdown-toggle-about">Về VCLOUD</a>
                        <div class="dropdown-menu">
                            <div class="dropdown-column">
                                <ul>
                                    <li><a href="#introduction">Giới thiệu chung</a></li>
                                    <li><a href="#development">Định hướng phát triển</a></li>
                                    <li><a href="#privacy-policy">Chính sách bảo mật</a></li>
                                    <li><a href="#data-policy">Chính sách bảo mật dữ liệu cá nhân</a></li>
                                    <li><a href="#sla-policy">Chính sách SLA</a></li>
                                </ul>
                            </div>
                        </div>
                    </li>
                    <li class="dropdown">
                        <a href="#features" id="dropdown-toggle-features">Tính năng</a>
                        <div class="dropdown-menu">
                            <div class="dropdown-column">
                                <ul>
                                    <li><a href="#k8s">K8S</a></li>
                                    <li><a href="#compute">Compute</a></li>
                                    <li><a href="#networking">Networking</a></li>
                                    <li><a href="#storage">Storage</a></li>
                                    <li><a href="#security">Security & Management</a></li>
                                    <li><a href="#database">Database Services</a></li>
                                    <li><a href="#monitoring">Monitoring</a></li>
                                    <li><a href="#self-service">Self-service portal</a></li>
                                    <li><a href="#billing">Billing</a></li>
                                    <li><a href="#reports">Reports</a></li>
                                    <li><a href="#reservation">Long term resource reservation</a></li>
                                </ul>
                            </div>
                        </div>
                    </li>
                    <li class="dropdown">
                        <a href="#blog" id="dropdown-toggle-blog">Blog</a>
                        <div class="dropdown-menu">
                            <div class="dropdown-column">
                                <ul>
                                    <li><a href="#tech-news">Tin tức công nghệ</a></li>
                                    <li><a href="#tech-blog">Tech Blog</a></li>
                                    <li><a href="#events">Sự kiện & Hoạt động</a></li>
                                </ul>
                            </div>
                        </div>
                    </li>
                    <li><a href="#pricing">Bảng giá</a></li>
                </ul>
            </nav>
            <div class="header-utilities">
                <a href="#login">Đăng nhập</a>
                <a href="#contact" class="cta-button">Liên Hệ Ngay</a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <div class="hero-text">
                <h1>Giải pháp Cloud Toàn Diện, Hiệu Suất Vượt Trội</h1>
                <p>Triển khai nhanh chóng, quản lý dễ dàng và mở rộng quy mô linh hoạt. Đảm bảo hiệu suất và bảo mật tối ưu cho mọi nền tảng số.</p>
                <a href="#start" class="cta-button">Trải nghiệm VCLOUD ngay</a>
            </div>
            <div class="hero-image">
                <img src="file:///C:/Users/dangt/Downloads/Thi%E1%BA%BFt%20k%E1%BA%BF%20ch%C6%B0a%20c%C3%B3%20t%C3%AAn%20(1).svg" alt="VCLOUD Platform">
            </div>
        </div>
    </section>

    <!-- Awards Section -->
    <section class="awards-section">
        <div class="awards-container">
            <h2>Giải thưởng và chứng nhận</h2>
            <p class="awards-description">
                VCLOUD vinh dự đạt được các giải thưởng và chứng nhận uy tín trong lĩnh vực công nghệ, 
                khẳng định vị thế tiên phong trong cung cấp giải pháp hạ tầng Công nghệ thông tin, truyền tải 
                dữ liệu và bảo mật An toàn thông tin chất lượng cao cho doanh nghiệp.
            </p>
            <div class="awards-grid">
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%20194.png" alt="Award 1">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/heloooshbsbjsf.png" alt="Award 2">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%201509%20(1).png" alt="Award 3">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%201510%20(1).png" alt="Award 4">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%201511%20(1).png" alt="Award 5">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%20195.png" alt="Award 6">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%20196.png" alt="Award 7">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%201514%20(1).png" alt="Award 8">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/anhChungDev.png" alt="Award 9">
                </div>
                <div class="award-item">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/26/Frame%20208.png" alt="Award 10">
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials">
        <h2>Chia sẻ của khách hàng</h2>
        <div class="testimonials-slider">
            <div class="testimonial-slide active">
                <div class="testimonial-content">
                    <div class="quote-icon">❝</div>
                    <p>VCLOUD mang đến hiệu suất vượt trội với tốc độ đọc/ghi ấn tượng, đảm bảo hệ thống luôn hoạt động mượt mà, ổn định. Nhờ hạ tầng mạnh mẽ và uptime 99,9%, chúng tôi có thể vận hành không gián đoạn, đáp ứng mọi yêu cầu kinh doanh!</p>
                    <div class="testimonial-author">
                        <img src="https://images.vnetwork.vn/resize?width=72&compression=5&quality=75&url=https%3A%2F%2Fstatic.vncdn.vn%2Fvnetwork.vn%2Fpub%2Fwebsites%2Fuploads%2F1%2FGroup%202116.png" alt="COO - FLY">
                        <div class="author-info">
                            <h4>COO - FLY</h4>
                            <p>WALLET PTY</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="testimonial-slide">
                <div class="testimonial-content">
                    <div class="quote-icon">❝</div>
                    <p>Nhờ có VCLOUD, chúng tôi đã tối ưu được chi phí vận hành và tăng hiệu quả kinh doanh. Đội ngũ kỹ thuật hỗ trợ 24/7 luôn sẵn sàng giải quyết mọi vấn đề một cách nhanh chóng.</p>
                    <div class="testimonial-author">
                        <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202189.svg" alt="CTO">
                        <div class="author-info">
                            <h4>CTO</h4>
                            <p>Công ty ABC</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="testimonial-slide">
                <div class="testimonial-content">
                    <div class="quote-icon">❝</div>
                    <p>VCLOUD cung cấp giải pháp toàn diện giúp chúng tôi yên tâm về bảo mật và hiệu năng. Khả năng mở rộng linh hoạt cùng các tính năng quản lý trực quan giúp việc vận hành trở nên dễ dàng hơn bao giờ hết.</p>
                    <div class="testimonial-author">
                        <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202195%20(1).svg" alt="CEO">
                        <div class="author-info">
                            <h4>CEO</h4>
                            <p>Công ty XYZ</p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="testimonial-navigation">
                <button class="prev-testimonial">❮</button>
                <button class="next-testimonial">❯</button>
            </div>
        </div>
    </section>

    <!-- Interactive Tour Section -->
    <section class="interactive-tour">
        <h2>Xem ngay Interactive Tour: Trải Nghiệm Miễn Phí</h2>
        <p>Khám phá giao diện VCloud portal trực quan chỉ trong 5 phút và bắt đầu trải nghiệm dịch vụ đám mây hiện đại ngay hôm nay.</p>
        <a href="#interactive-tour" class="cta-button">Trải nghiệm ngay →</a>
    </section>

    <!-- Blog -->
    <section class="section case-studies">
        <h2>Blog</h2>
        <div class="case-studies-container">
            <div class="case-study">
                <img src="case1-thumbnail.jpg" alt="Ánh bìa Case 1">
                <h3>“Link độc hại tấn công website trường học”</h3>
                <p>Vấn đề về link độc hại không chỉ làm mất uy tín mà còn ảnh hưởng trực tiếp đến hiệu quả hoạt động của tổ chức. Với giải pháp VNIS kết hợp VCLOUD, hệ thống không chỉ loại bỏ hoàn toàn các mối nguy mà còn nâng cấp bảo mật, tối ưu hạ tầng IT, đảm bảo website hoạt động liên tục và ổn định trong các mùa cao điểm.</p>
                <a href="#case1-details">-> Xem thêm chi tiết</a>
            </div>
            <div class="case-study">
                <img src="case2-thumbnail.jpg" alt="Ánh bìa Case 2">
                <h3>“Hệ thống phân tán làm tăng chi phí và khó quản lý?”</h3>
                <p>VNETWORK cung cấp giải pháp tập trung toàn diện, kết hợp VCLOUD, VNIS, VNCDN, và Colocation trên một nền tảng duy nhất, giúp giảm thiểu sự phức tạp trong quản lý, tăng tốc xử lý sự cố và đảm bảo hệ thống hoạt động ổn định, hiệu quả.</p>
                <a href="#case2-details">-> Xem thêm chi tiết</a>
            </div>
            <div class="case-study">
                <img src="case3-thumbnail.jpg" alt="Ánh bìa Case 3">
                <h3>“Gián đoạn dịch vụ ảnh hưởng trải nghiệm người dùng?”</h3>
                <p>VNETWORK đã giải quyết bài toán băng thông không ổn định và khó khăn trong mở rộng hạ tầng với Data Center và Colocation. Giải pháp này không chỉ đảm bảo hệ thống vận hành mượt mà mà còn hỗ trợ mở rộng linh hoạt theo nhu cầu thực tế, giúp doanh nghiệp duy trì hiệu suất ổn định và tối ưu chi phí.</p>
                <a href="#case3-details">-> Xem thêm chi tiết</a>
            </div>
        </div>
    </section>

    <!-- Featured Clients Section -->
    <section class="featured-clients">
        <h2>Khách hàng tiêu biểu</h2>
        <div class="client-slider">
            <div class="slide-track">
                <!-- First set of logos -->
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201523.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201522.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201521.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202189.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202215.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202214.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202198%20(3).svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202195%20(1).svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202217.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202190.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202193%20(1).svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202218.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202216.svg" alt="Client Logo">
                </div>
                
                <!-- Duplicate set for seamless loop -->
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201523.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201522.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/39/Frame%201521.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202189.svg" alt="Client Logo">
                </div>
                <div class="slide">
                    <img src="https://static.vncdn.vn/vnetwork.vn/pub/websites/uploads/1/Group%202215.svg" alt="Client Logo">
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-container">
            <!-- Tính năng -->
            <div class="footer-column">
                <h3>Tính năng</h3>
                <ul>
                    <li><a href="#k8s">K8S</a></li>
                    <li><a href="#compute">Compute</a></li>
                    <li><a href="#networking">Networking</a></li>
                    <li><a href="#storage">Storage</a></li>
                    <li><a href="#security">Security & Management</a></li>
                    <li><a href="#database">Database Services</a></li>
                    <li><a href="#monitoring">Monitoring</a></li>
                    <li><a href="#self-service">Self-service portal</a></li>
                    <li><a href="#billing">Billing</a></li>
                    <li><a href="#reports">Reports</a></li>
                    <li><a href="#reservation">Long term resource reservation</a></li>
                </ul>
            </div>

            <!-- Tech Hub -->
            <div class="footer-column">
                <h3>Tech Hub</h3>
                <ul>
                    <li><a href="#system-status">Trạng thái hệ thống</a></li>
                    <li><a href="#case-studies">Case studies</a></li>
                    <li><a href="#cloud-docs">Cloud Documentation</a></li>
                    <li><a href="#interactive-tour">Interactive tour</a></li>
                    <li><a href="#white-paper">White paper</a></li>
                    <li><a href="#faqs">FAQs</a></li>
                </ul>
            </div>

            <!-- Blog -->
            <div class="footer-column">
                <h3>Blog</h3>
                <ul>
                    <li><a href="#tech-news">Tin tức công nghệ</a></li>
                    <li><a href="#tech-blog">Tech Blog</a></li>
                    <li><a href="#events">Sự kiện & Hoạt động</a></li>
                </ul>
            </div>
        </div>

        <div class="footer-bottom">
            <p>CÔNG TY CỔ PHẦN VNETWORK</p>
            <p>© 2025 VNETWORK JSC. All Rights Reserved</p>
            <p>Lầu 23, tòa nhà UOA Tower, 06 Tân Trào, Phường Tân Phú, Quận 7, HCMC</p>
            <p>111 North Bridge Road #17-06 Peninsula Plaza Singapore</p>
            <p><a href="#">Terms Of Service</a> | <a href="#">Privacy Policy</a></p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Testimonials slider
            const slides = document.querySelectorAll('.testimonial-slide');
            const prevButton = document.querySelector('.prev-testimonial');
            const nextButton = document.querySelector('.next-testimonial');
            let currentSlide = 0;

            function showSlide(index) {
                slides.forEach(slide => {
                    slide.style.display = 'none';
                    slide.classList.remove('active');
                });
                slides[index].style.display = 'block';
                slides[index].classList.add('active');
            }

            function nextSlide() {
                currentSlide = (currentSlide + 1) % slides.length;
                showSlide(currentSlide);
            }

            function prevSlide() {
                currentSlide = (currentSlide - 1 + slides.length) % slides.length;
                showSlide(currentSlide);
            }

            // Thêm event listeners cho nút điều hướng
            if (prevButton && nextButton) {
                prevButton.addEventListener('click', prevSlide);
                nextButton.addEventListener('click', nextSlide);
            }

            // Hiển thị slide đầu tiên
            showSlide(0);

            // Auto play (optional)
            setInterval(nextSlide, 5000);
        });
    </script>
</body>
</html>
