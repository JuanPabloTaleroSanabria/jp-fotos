<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Portafolio Fotográfico</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', 'Segoe UI', sans-serif;
        }

        body {
            background-color: #f8f8f8;
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background-color: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            letter-spacing: 1px;
            color: #222;
        }

        .logo span {
            color: #e74c3c;
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 30px;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            text-transform: uppercase;
            font-size: 14px;
            letter-spacing: 1px;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #e74c3c;
        }

        .menu-btn {
            display: none;
            cursor: pointer;
            font-size: 24px;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background-color: #000;
            background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('/api/placeholder/1920/1080');
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
        }

        .hero-content {
            max-width: 800px;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            letter-spacing: 2px;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .btn {
            display: inline-block;
            background-color: #e74c3c;
            color: white;
            padding: 12px 30px;
            border-radius: 3px;
            text-decoration: none;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            background-color: #c0392b;
            transform: translateY(-3px);
        }

        /* Galleries Section */
        .galleries {
            padding: 100px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #333;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .section-title p {
            color: #666;
            max-width: 700px;
            margin: 0 auto;
        }

        .categories {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin-bottom: 50px;
        }

        .category-btn {
            padding: 10px 25px;
            margin: 5px;
            background-color: #f1f1f1;
            color: #333;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s;
        }

        .category-btn.active, .category-btn:hover {
            background-color: #e74c3c;
            color: white;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 5px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
            height: 300px;
        }

        .gallery-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .gallery-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .gallery-item:hover .gallery-img {
            transform: scale(1.1);
        }

        .gallery-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s;
            padding: 20px;
            text-align: center;
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        .gallery-overlay h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
        }

        .gallery-overlay p {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Upload Section */
        .upload-section {
            background-color: #f1f1f1;
            padding: 100px 0;
        }

        .upload-container {
            background-color: white;
            max-width: 800px;
            margin: 0 auto;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 500;
            color: #333;
        }

        .form-control {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: #e74c3c;
        }

        .upload-area {
            border: 2px dashed #ddd;
            border-radius: 5px;
            padding: 40px 20px;
            text-align: center;
            transition: all 0.3s;
            cursor: pointer;
        }

        .upload-area:hover {
            border-color: #e74c3c;
        }

        .upload-area i {
            font-size: 40px;
            color: #999;
            margin-bottom: 15px;
            display: block;
        }

        .upload-area p {
            margin-bottom: 10px;
            color: #666;
        }

        .upload-area .btn {
            margin-top: 15px;
        }

        .image-preview {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
            gap: 10px;
            margin-top: 20px;
        }

        .preview-item {
            position: relative;
            height: 100px;
            overflow: hidden;
            border-radius: 5px;
        }

        .preview-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .preview-item .remove-btn {
            position: absolute;
            top: 5px;
            right: 5px;
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            border: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 12px;
        }

        /* Contact */
        .contact {
            padding: 100px 0;
        }

        .contact-form {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .input-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        .input-group {
            flex-basis: 48%;
        }

        textarea.form-control {
            height: 150px;
            resize: none;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            overflow: auto;
        }

        .modal-content {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            padding: 20px;
        }

        .modal-image {
            max-width: 90%;
            max-height: 90vh;
            object-fit: contain;
        }

        .close-modal {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
            z-index: 2001;
        }

        .modal-nav {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            padding: 0 40px;
            transform: translateY(-50%);
        }

        .modal-nav button {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 24px;
            transition: background 0.3s;
        }

        .modal-nav button:hover {
            background: rgba(255, 255, 255, 0.4);
        }

        .modal-caption {
            position: absolute;
            bottom: 20px;
            left: 0;
            width: 100%;
            text-align: center;
            color: white;
            padding: 20px;
        }

        .modal-caption h3 {
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        .modal-caption p {
            font-size: 1rem;
            opacity: 0.8;
        }

        /* Footer */
        footer {
            background-color: #222;
            color: white;
            padding: 50px 0 20px;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            margin-bottom: 40px;
        }

        .footer-section {
            flex-basis: 30%;
        }

        .footer-section h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
            color: white;
        }

        .footer-section h3::after {
            content: '';
            position: absolute;
            width: 50px;
            height: 2px;
            background-color: #e74c3c;
            bottom: 0;
            left: 0;
        }

        .footer-section p {
            margin-bottom: 10px;
            color: #ddd;
        }

        .social-links {
            margin-top: 20px;
        }

        .social-links a {
            display: inline-block;
            height: 40px;
            width: 40px;
            background-color: #333;
            color: white;
            border-radius: 50%;
            margin-right: 10px;
            text-align: center;
            line-height: 40px;
            transition: all 0.3s;
        }

        .social-links a:hover {
            background-color: #e74c3c;
            transform: translateY(-5px);
        }

        .contact-info {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .contact-info i {
            margin-right: 15px;
            color: #e74c3c;
            font-size: 1.2rem;
        }

        .quick-links li {
            margin-bottom: 15px;
            list-style: none;
        }

        .quick-links a {
            color: #ddd;
            text-decoration: none;
            transition: color 0.3s;
        }

        .quick-links a:hover {
            color: #e74c3c;
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #333;
            color: #ddd;
        }

        /* Responsive */
        @media (max-width: 992px) {
            .footer-content {
                flex-direction: column;
            }

            .footer-section {
                margin-bottom: 30px;
            }

            .menu-btn {
                display: block;
            }

            .nav-links {
                position: fixed;
                background-color: white;
                height: 100vh;
                width: 250px;
                top: 0;
                right: -250px;
                flex-direction: column;
                padding-top: 80px;
                transition: right 0.3s;
                z-index: 999;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }

            .nav-active {
                right: 0;
            }

            .nav-links li {
                margin: 15px 30px;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1rem;
            }
        }

        @media (max-width: 768px) {
            .gallery-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }

            .input-row {
                flex-direction: column;
            }

            .input-group {
                margin-bottom: 20px;
            }

            .modal-nav {
                padding: 0 20px;
            }
        }

        @media (max-width: 480px) {
            .gallery-grid {
                grid-template-columns: 1fr;
            }

            .section-title h2 {
                font-size: 2rem;
            }

            .hero h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <nav>
                <div class="logo">Foto<span>Portfolio</span></div>
                <ul class="nav-links">
                    <li><a href="#inicio">Inicio</a></li>
                    <li><a href="#galerias">Galerías</a></li>
                    <li><a href="#subir">Subir Fotos</a></li>
                    <li><a href="#contacto">Contacto</a></li>
                </ul>
                <div class="menu-btn">☰</div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="inicio">
        <div class="hero-content">
            <h1>Mi Portafolio Fotográfico</h1>
            <p>Capturando momentos únicos y transformándolos en recuerdos eternos</p>
            <a href="#galerias" class="btn">Ver Galerías</a>
        </div>
    </section>

    <!-- Galleries Section -->
    <section class="galleries" id="galerias">
        <div class="container">
            <div class="section-title">
                <h2>Mis Galerías</h2>
                <p>Explora mi trabajo organizado por categorías</p>
            </div>

            <div class="categories">
                <button class="category-btn active" data-category="all">Todas</button>
                <button class="category-btn" data-category="naturaleza">Naturaleza</button>
                <button class="category-btn" data-category="retratos">Retratos</button>
                <button class="category-btn" data-category="eventos">Eventos</button>
                <button class="category-btn" data-category="viajes">Viajes</button>
                <button class="category-btn" data-category="bodas">Bodas</button>
            </div>

            <div class="gallery-grid">
                <!-- Gallery Item 1 -->
                <div class="gallery-item" data-category="naturaleza">
                    <img src="/api/placeholder/600/600" alt="Naturaleza" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Amanecer en la Montaña</h3>
                        <p>Capturando la belleza natural al amanecer</p>
                    </div>
                </div>
                <!-- Gallery Item 2 -->
                <div class="gallery-item" data-category="retratos">
                    <img src="/api/placeholder/600/600" alt="Retrato" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Retrato Urbano</h3>
                        <p>Sesión fotográfica en entorno urbano</p>
                    </div>
                </div>
                <!-- Gallery Item 3 -->
                <div class="gallery-item" data-category="eventos">
                    <img src="/api/placeholder/600/600" alt="Evento" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Concierto en Vivo</h3>
                        <p>Capturando la energía de eventos en vivo</p>
                    </div>
                </div>
                <!-- Gallery Item 4 -->
                <div class="gallery-item" data-category="viajes">
                    <img src="/api/placeholder/600/600" alt="Viaje" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Calles de París</h3>
                        <p>Explorando la ciudad de la luz</p>
                    </div>
                </div>
                <!-- Gallery Item 5 -->
                <div class="gallery-item" data-category="bodas">
                    <img src="/api/placeholder/600/600" alt="Boda" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Momentos Especiales</h3>
                        <p>Capturando el día más importante</p>
                    </div>
                </div>
                <!-- Gallery Item 6 -->
                <div class="gallery-item" data-category="naturaleza">
                    <img src="/api/placeholder/600/600" alt="Naturaleza" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Atardecer en la Playa</h3>
                        <p>La magia de los colores al atardecer</p>
                    </div>
                </div>
                <!-- Gallery Item 7 -->
                <div class="gallery-item" data-category="retratos">
                    <img src="/api/placeholder/600/600" alt="Retrato" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Retrato en Estudio</h3>
                        <p>Iluminación profesional en estudio</p>
                    </div>
                </div>
                <!-- Gallery Item 8 -->
                <div class="gallery-item" data-category="eventos">
                    <img src="/api/placeholder/600/600" alt="Evento" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Festival de Verano</h3>
                        <p>Momentos únicos en festivales</p>
                    </div>
                </div>
                <!-- Gallery Item 9 -->
                <div class="gallery-item" data-category="viajes">
                    <img src="/api/placeholder/600/600" alt="Viaje" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Montañas de Suiza</h3>
                        <p>Paisajes impresionantes en los Alpes</p>
                    </div>
                </div>
                <!-- Gallery Item 10 -->
                <div class="gallery-item" data-category="bodas">
                    <img src="/api/placeholder/600/600" alt="Boda" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Ceremonia al Aire Libre</h3>
                        <p>Celebraciones en entornos naturales</p>
                    </div>
                </div>
                <!-- Gallery Item 11 -->
                <div class="gallery-item" data-category="naturaleza">
                    <img src="/api/placeholder/600/600" alt="Naturaleza" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Vida Silvestre</h3>
                        <p>Fotografía de fauna en su hábitat natural</p>
                    </div>
                </div>
                <!-- Gallery Item 12 -->
                <div class="gallery-item" data-category="viajes">
                    <img src="/api/placeholder/600/600" alt="Viaje" class="gallery-img">
                    <div class="gallery-overlay">
                        <h3>Arquitectura Antigua</h3>
                        <p>Explorando monumentos históricos</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Upload Section -->
    <section class="upload-section" id="subir">
        <div class="container">
            <div class="section-title">
                <h2>Subir Fotos</h2>
                <p>Sube tus fotos fácilmente y organízalas por categorías</p>
            </div>

            <div class="upload-container">
                <form id="upload-form">
                    <div class="form-group">
                        <label for="photo-title">Título de la Foto</label>
                        <input type="text" id="photo-title" class="form-control" placeholder="Ej. Amanecer en la Montaña">
                    </div>

                    <div class="form-group">
                        <label for="photo-category">Categoría</label>
                        <select id="photo-category" class="form-control">
                            <option value="">Selecciona una categoría</option>
                            <option value="naturaleza">Naturaleza</option>
                            <option value="retratos">Retratos</option>
                            <option value="eventos">Eventos</option>
                            <option value="viajes">Viajes</option>
                            <option value="bodas">Bodas</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="photo-description">Descripción</label>
                        <textarea id="photo-description" class="form-control" placeholder="Describe tu fotografía..."></textarea>
                    </div>

                    <div class="form-group">
                        <label>Sube tus Fotos</label>
                        <div class="upload-area" id="drop-area">
                            <i>📸</i>
                            <p>Arrastra y suelta tus fotos aquí o</p>
                            <button type="button" class="btn" id="browse-btn">Seleccionar Archivos</button>
                            <input type="file" id="file-input" multiple style="display: none;" accept="image/*">
                        </div>
                        <div class="image-preview" id="image-preview"></div>
                    </div>

                    <div class="form-group">
                        <label for="new-category">¿Nueva Categoría?</label>
                        <input type="text" id="new-category" class="form-control" placeholder="Crear nueva categoría (opcional)">
                    </div>

                    <button type="submit" class="btn" style="width: 100%;">Subir Fotos</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contacto">
        <div class="container">
            <div class="section-title">
                <h2>Contacto</h2>
                <p>¿Interesado en mis servicios? ¡Hablemos!</p>
            </div>

            <div class="contact-form">
                <form>
                    <div class="input-row">
                        <div class="input-group">
                            <label for="name">Nombre</label>
                            <input type="text" id="name" class="form-control" placeholder="Tu nombre">
                        </div>
                        <div class="input-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" class="form-control" placeholder="Tu correo electrónico">
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="subject">Asunto</label>
                        <input type="text" id="subject" class="form-control" placeholder="Asunto de tu mensaje">
                    </div>

                    <div class="form-group">
                        <label for="message">Mensaje</label>
                        <textarea id="message" class="form-control" placeholder="Escribe tu mensaje aquí..."></textarea>
                    </div>

                    <button type="submit" class="btn" style="width: 100%;">Enviar Mensaje</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Image Modal -->
    <div class="modal" id="image-modal">
        <span class="close-modal">&times;</span>
        <div class="modal-content">
            <img src="" alt="" class="modal-image" id="modal-image">
            <div class="modal-nav">
                <button id="prev-btn">&lt;</button>
                <button id="next-btn">&gt;</button>
            </div>
            <div class="modal-caption">
                <h3 id="modal-title"></h3>
                <p id="modal-description"></p>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>FotoPortfolio</h3>
                    <p>Un espacio dedicado a compartir mi pasión por la fotografía, capturando momentos especiales y transformándolos en recuerdos eternos.</p>
                    <div class="social-links">
                        <a href="#">FB</a>
                        <a href="#">IG</a>
                        <a href="#">PT</a>
                        <a href="#">FL</a>
                    </div>
                </div>
                <div class="footer-section">
                    <h3>Contacto</h3>
                    <div class="contact-info">
                        <i>📧</i>
                        <span>contacto@fotoportfolio.com</span>
                    </div>
                    <div class="contact-info">
                        <i>📱</i>
                        <span>+123 456 7890</span>
                    </div>
                    <div class="contact-info">
                        <i>📍</i>
                        <span>Tu Ciudad, País</span>
                    </div>
                </div>
                <div class="footer-section">
                    <h3>Enlaces Rápidos</h3>
                    <ul class="quick-links">
                        <li><a href="#inicio">Inicio</a></li>
                        <li><a href="#galerias">Galerías</a></li>
                        <li><a href="#subir">Subir Fotos</a></li>
                        <li><a href="#contacto">Contacto</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2025 FotoPortfolio. Todos los derechos reservados.</p>
            </div>
        </div>
    </footer>

    <script>
        // Menú responsive
        const menuBtn = document.querySelector('.menu-btn');
        const navLinks = document.querySelector('.nav-links');

        menuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('nav-active');
        });
