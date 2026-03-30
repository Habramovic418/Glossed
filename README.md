<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gloseed by Riri | Luxury Lip Gloss</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0a0a0a;
            color: #ffffff;
            overflow-x: hidden;
        }
        
        .font-playfair {
            font-family: 'Playfair Display', serif;
        }
        
        .gloss-gradient {
            background: linear-gradient(135deg, #ff006e 0%, #8338ec 50%, #3a86ff 100%);
        }
        
        .text-gradient {
            background: linear-gradient(135deg, #ff006e 0%, #ffbe0b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .shine-effect {
            position: relative;
            overflow: hidden;
        }
        
        .shine-effect::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                45deg,
                transparent 30%,
                rgba(255, 255, 255, 0.3) 50%,
                transparent 70%
            );
            transform: rotate(45deg);
            transition: all 0.6s;
            opacity: 0;
        }
        
        .shine-effect:hover::before {
            animation: shine 0.6s ease-in-out;
        }
        
        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); opacity: 0; }
        }
        
        .floating {
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }
        
        .marquee-container {
            overflow: hidden;
            white-space: nowrap;
        }
        
        .marquee-content {
            display: inline-block;
            animation: marquee 20s linear infinite;
        }
        
        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
        
        .product-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(255, 0, 110, 0.3);
        }
        
        .sticky-nav {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 50;
            transition: all 0.3s ease;
        }
        
        .sticky-nav.scrolled {
            background: rgba(10, 10, 10, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .liquid-bg {
            background: radial-gradient(circle at 50% 50%, rgba(255, 0, 110, 0.15) 0%, transparent 70%);
        }
        
        .cursor-glow {
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(255, 0, 110, 0.4) 0%, transparent 70%);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 0;
            filter: blur(40px);
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .reveal-text {
            clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
        }
        
        .char {
            display: inline-block;
            transform: translateY(100%);
            opacity: 0;
        }
        
        .glitter {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: glitter 3s linear infinite;
        }
        
        @keyframes glitter {
            0%, 100% { opacity: 0; transform: scale(0); }
            50% { opacity: 1; transform: scale(1); }
        }
    </style>
</head>
<body class="antialiased">

    <!-- Cursor Glow Effect -->
    <div class="cursor-glow" id="cursorGlow"></div>

    <!-- Navigation -->
    <nav class="sticky-nav py-4 px-6 lg:px-12 flex justify-between items-center" id="navbar">
        <div class="text-2xl font-playfair font-bold tracking-wider">
            GLOSEED<span class="text-pink-500">.</span>
        </div>
        <div class="hidden md:flex space-x-8 text-sm tracking-widest uppercase">
            <a href="#collection" class="hover:text-pink-500 transition-colors">Collection</a>
            <a href="#about" class="hover:text-pink-500 transition-colors">Story</a>
            <a href="#reviews" class="hover:text-pink-500 transition-colors">Reviews</a>
        </div>
        <button class="bg-white text-black px-6 py-2 rounded-full text-sm font-semibold hover:bg-pink-500 hover:text-white transition-all transform hover:scale-105 shine-effect">
            Shop Now
        </button>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center overflow-hidden pt-20">
        <div class="absolute inset-0 liquid-bg"></div>
        
        <!-- Animated Background Elements -->
        <div class="absolute top-20 left-10 w-72 h-72 bg-pink-600 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-pulse"></div>
        <div class="absolute bottom-20 right-10 w-96 h-96 bg-purple-600 rounded-full mix-blend-multiply filter blur-3xl opacity-20 animate-pulse" style="animation-delay: 2s;"></div>
        
        <div class="container mx-auto px-6 relative z-10 grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-8">
                <div class="inline-block px-4 py-1 border border-pink-500/30 rounded-full text-pink-400 text-xs tracking-widest uppercase mb-4">
                    New Collection 2026
                </div>
                <h1 class="font-playfair text-6xl md:text-8xl font-bold leading-tight reveal-text" id="heroTitle">
                    SEED YOUR<br>
                    <span class="text-gradient italic">GLOW</span>
                </h1>
                <p class="text-gray-400 text-lg md:text-xl max-w-md leading-relaxed opacity-0" id="heroSubtext">
                    Luxurious lip glosses infused with nourishing oils and light-catching pigments. 
                    Where hydration meets high shine.
                </p>
                <div class="flex gap-4 opacity-0" id="heroCTA">
                    <button class="bg-gradient-to-r from-pink-600 to-purple-600 px-8 py-4 rounded-full font-semibold text-lg hover:shadow-2xl hover:shadow-pink-500/50 transition-all transform hover:scale-105 shine-effect">
                        Explore Collection
                    </button>
                    <button class="border border-white/20 px-8 py-4 rounded-full font-semibold hover:bg-white/10 transition-all">
                        Watch Film
                    </button>
                </div>
                <div class="flex items-center gap-4 pt-8 opacity-0" id="heroStats">
                    <div>
                        <div class="text-2xl font-bold text-gradient">50K+</div>
                        <div class="text-xs text-gray-500 uppercase tracking-wider">Glow Getters</div>
                    </div>
                    <div class="w-px h-12 bg-white/10"></div>
                    <div>
                        <div class="text-2xl font-bold text-gradient">12</div>
                        <div class="text-xs text-gray-500 uppercase tracking-wider">Shades</div>
                    </div>
                    <div class="w-px h-12 bg-white/10"></div>
                    <div>
                        <div class="text-2xl font-bold text-gradient">4.9</div>
                        <div class="text-xs text-gray-500 uppercase tracking-wider">Rating</div>
                    </div>
                </div>
            </div>
            
            <div class="relative floating" id="heroImage">
                <div class="relative w-full aspect-square max-w-lg mx-auto">
                    <div class="absolute inset-0 bg-gradient-to-br from-pink-500/20 to-purple-600/20 rounded-full blur-3xl"></div>
                    <img src="https://images.unsplash.com/photo-1625093742435-6fa192b6fb10?w=800&auto=format&fit=crop&q=80" 
                         alt="Luxury Lip Gloss" 
                         class="relative z-10 w-full h-full object-cover rounded-3xl shadow-2xl border border-white/10">
                    
                    <!-- Floating Badge -->
                    <div class="absolute -bottom-6 -left-6 glass-effect p-4 rounded-2xl z-20 animate-bounce" style="animation-duration: 3s;">
                        <div class="flex items-center gap-3">
                            <div class="w-12 h-12 bg-gradient-to-br from-pink-500 to-purple-600 rounded-full flex items-center justify-center text-2xl">
                                ✨
                            </div>
                            <div>
                                <div class="text-sm font-semibold">Vegan Formula</div>
                                <div class="text-xs text-gray-400">Cruelty Free</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Scroll Indicator -->
        <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
            <svg class="w-6 h-6 text-white/50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
            </svg>
        </div>
    </section>

    <!-- Marquee Section -->
    <div class="py-8 border-y border-white/10 bg-black/50">
        <div class="marquee-container">
            <div class="marquee-content text-4xl md:text-6xl font-playfair italic text-white/10">
                HIGH SHINE • HYDRATING • NON-STICKY • VEGAN • CRUELTY FREE • HIGH SHINE • HYDRATING • NON-STICKY • VEGAN • CRUELTY FREE •
            </div>
        </div>
    </div>

    <!-- Product Collection -->
    <section id="collection" class="py-24 px-6 lg:px-12 relative">
        <div class="container mx-auto">
            <div class="text-center mb-16">
                <h2 class="font-playfair text-4xl md:text-6xl font-bold mb-4">The Collection</h2>
                <p class="text-gray-400 max-w-2xl mx-auto">Discover our signature shades, each crafted to deliver maximum shine with nourishing ingredients.</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <!-- Product 1 -->
                <div class="product-card glass-effect rounded-3xl p-6 group cursor-pointer">
                    <div class="relative overflow-hidden rounded-2xl mb-6 aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1586495777744-4413f21062fa?w=600&auto=format&fit=crop&q=80" 
                             alt="Dew Drop Gloss" 
                             class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                        <button class="absolute bottom-4 left-4 right-4 bg-white text-black py-3 rounded-full font-semibold transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                            Quick Add - $24
                        </button>
                    </div>
                    <div class="space-y-2">
                        <div class="flex justify-between items-start">
                            <div>
                                <h3 class="text-xl font-playfair font-semibold">Dew Drop</h3>
                                <p class="text-gray-400 text-sm">Crystal clear with gold reflects</p>
                            </div>
                            <div class="w-8 h-8 rounded-full bg-gradient-to-br from-yellow-200 to-yellow-400 border-2 border-white/20"></div>
                        </div>
                        <div class="flex items-center gap-1 text-xs text-gray-500">
                            <span>★★★★★</span>
                            <span>(128 reviews)</span>
                        </div>
                    </div>
                </div>

                <!-- Product 2 -->
                <div class="product-card glass-effect rounded-3xl p-6 group cursor-pointer">
                    <div class="relative overflow-hidden rounded-2xl mb-6 aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1608248543803-ba4f8c70ae0b?w=600&auto=format&fit=crop&q=80" 
                             alt="Rose Glaze Gloss" 
                             class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                        <button class="absolute bottom-4 left-4 right-4 bg-white text-black py-3 rounded-full font-semibold transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                            Quick Add - $24
                        </button>
                    </div>
                    <div class="space-y-2">
                        <div class="flex justify-between items-start">
                            <div>
                                <h3 class="text-xl font-playfair font-semibold">Rose Glaze</h3>
                                <p class="text-gray-400 text-sm">Soft pink with pearl finish</p>
                            </div>
                            <div class="w-8 h-8 rounded-full bg-gradient-to-br from-pink-300 to-rose-400 border-2 border-white/20"></div>
                        </div>
                        <div class="flex items-center gap-1 text-xs text-gray-500">
                            <span>★★★★★</span>
                            <span>(96 reviews)</span>
                        </div>
                    </div>
                </div>

                <!-- Product 3 -->
                <div class="product-card glass-effect rounded-3xl p-6 group cursor-pointer">
                    <div class="relative overflow-hidden rounded-2xl mb-6 aspect-[4/5]">
                        <img src="https://images.unsplash.com/photo-1619451334792-150fd785ee74?w=600&auto=format&fit=crop&q=80" 
                             alt="Berry Bite Gloss" 
                             class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-500">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                        <button class="absolute bottom-4 left-4 right-4 bg-white text-black py-3 rounded-full font-semibold transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                            Quick Add - $24
                        </button>
                    </div>
                    <div class="space-y-2">
                        <div class="flex justify-between items-start">
                            <div>
                                <h3 class="text-xl font-playfair font-semibold">Berry Bite</h3>
                                <p class="text-gray-400 text-sm">Deep plum with shimmer</p>
                            </div>
                            <div class="w-8 h-8 rounded-full bg-gradient-to-br from-purple-600 to-pink-700 border-2 border-white/20"></div>
                        </div>
                        <div class="flex items-center gap-1 text-xs text-gray-500">
                            <span>★★★★★</span>
                            <span>(84 reviews)</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-12">
                <button class="border border-white/20 px-8 py-3 rounded-full hover:bg-white hover:text-black transition-all">
                    View All 12 Shades
                </button>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="py-24 px-6 lg:px-12 bg-gradient-to-b from-black to-gray-900">
        <div class="container mx-auto">
            <div class="grid md:grid-cols-2 gap-16 items-center">
                <div class="space-y-8">
                    <h2 class="font-playfair text-4xl md:text-5xl font-bold leading-tight">
                        Why Gloseed<br>
                        <span class="text-gradient">is Different</span>
                    </h2>
                    
                    <div class="space-y-6">
                        <div class="flex gap-4 items-start group">
                            <div class="w-12 h-12 rounded-full bg-pink-500/20 flex items-center justify-center flex-shrink-0 group-hover:bg-pink-500/40 transition-colors">
                                <svg class="w-6 h-6 text-pink-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"></path>
                                </svg>
                            </div>
                            <div>
                                <h3 class="text-xl font-semibold mb-2">Lightweight Formula</h3>
                                <p class="text-gray-400">Non-sticky, comfortable wear that feels like nothing but looks like everything.</p>
                            </div>
                        </div>
                        
                        <div class="flex gap-4 items-start group">
                            <div class="w-12 h-12 rounded-full bg-purple-500/20 flex items-center justify-center flex-shrink-0 group-hover:bg-purple-500/40 transition-colors">
                                <svg class="w-6 h-6 text-purple-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4"></path>
                                </svg>
                            </div>
                            <div>
                                <h3 class="text-xl font-semibold mb-2">Nourishing Oils</h3>
                                <p cl
