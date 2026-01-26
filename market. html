<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mesut Tekno Market</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-50">
    <!-- Top Bar -->
    <div class="bg-blue-600 text-white text-sm py-2">
        <div class="max-w-7xl mx-auto px-4 flex justify-between items-center">
            <div class="flex gap-6">
                <span>📞 +90 544 389 40 07</span>
                <span>✉️ info@mesuttekno.com</span>
            </div>
        </div>
    </div>

    <!-- Header -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 py-4">
            <div class="flex items-center justify-between gap-4">
                <h1 class="text-2xl font-bold text-blue-600">Mesut Tekno</h1>
                <div class="flex items-center gap-4">
                    <button id="adminBtn" class="flex items-center gap-2 hover:text-blue-600">
                        👤 <span>Admin</span>
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Categories -->
    <div class="bg-white border-b">
        <div class="max-w-7xl mx-auto px-4 py-3">
            <div class="flex gap-4 overflow-x-auto">
                <button class="category-btn px-4 py-2 rounded-full bg-blue-600 text-white font-medium" data-category="all">Tümü</button>
                <button class="category-btn px-4 py-2 rounded-full hover:bg-gray-100 font-medium" data-category="Telefon">📱 Telefon</button>
                <button class="category-btn px-4 py-2 rounded-full hover:bg-gray-100 font-medium" data-category="Laptop">💻 Laptop</button>
                <button class="category-btn px-4 py-2 rounded-full hover:bg-gray-100 font-medium" data-category="Tablet">📲 Tablet</button>
                <button class="category-btn px-4 py-2 rounded-full hover:bg-gray-100 font-medium" data-category="Aksesuar">⚡ Aksesuar</button>
            </div>
        </div>
    </div>

    <!-- Login Modal -->
    <div id="loginModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-xl p-8 max-w-md w-full mx-4 relative">
            <!-- Close (X) Button -->
            <button id="closeLoginModal" aria-label="Kapat" class="absolute top-3 right-3 text-gray-500 hover:text-gray-800 text-xl">
                ✖
            </button>

            <h2 class="text-2xl font-bold mb-4">Admin Girişi</h2>
            <input type="password" id="passwordInput" placeholder="Admin şifresini giriniz" 
                class="w-full px-4 py-3 border rounded-lg mb-4 focus:border-blue-600 focus:outline-none">
            <button id="loginBtn" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700">
                Giriş Yap
            </button>
        </div>
    </div>

    <!-- Admin Panel -->
    <div id="adminPanel" class="hidden max-w-7xl mx-auto px-4 py-6">
        <div class="bg-white rounded-xl shadow-lg p-6">
            <h2 class="text-2xl font-bold mb-6">Ürün Ekle</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <input type="text" id="productName" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none" placeholder="Ürün İsmi">
                <input type="text" id="productDesc" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none" placeholder="Açıklama">
                <select id="productCategory" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none">
                    <option>Telefon</option>
                    <option>Laptop</option>
                    <option>Tablet</option>
                    <option>Aksesuar</option>
                </select>
                <input type="url" id="productImage" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none" placeholder="Görsel URL">
                <input type="number" id="productPrice" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none" placeholder="Fiyat">
                <input type="number" id="productOriginalPrice" class="px-4 py-2 border rounded-lg focus:border-blue-600 focus:outline-none" placeholder="Eski Fiyat">
            </div>
            <button id="addProductBtn" class="mt-4 w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700">
                Ürünü Ekle
            </button>
        </div>
    </div>

    <!-- Products -->
    <div class="max-w-7xl mx-auto px-4 py-8">
        <div id="productsGrid" class="grid grid-cols-2 md:grid-cols-4 gap-4"></div>
    </div>

    <script>
        let products = [
            {
                id: 1,
                name: 'iPhone 15 Pro',
                description: '256GB',
                imageUrl: 'https://images.unsplash.com/photo-1696446702883-ba4e6d7e7d42?w=400',
                price: 45000,
                originalPrice: 55000,
                category: 'Telefon'
            },
            {
                id: 2,
                name: 'Samsung Galaxy S24',
                description: '128GB',
                imageUrl: 'https://images.unsplash.com/photo-1610945415295-d9bbf067e59c?w=400',
                price: 35000,
                originalPrice: 35000,
                category: 'Telefon'
            },
            {
                id: 3,
                name: 'MacBook Pro M3',
                description: '16GB RAM',
                imageUrl: 'https://images.unsplash.com/photo-1517336714731-489689fd1ca8?w=400',
                price: 65000,
                originalPrice: 75000,
                category: 'Laptop'
            },
            {
                id: 4,
                name: 'AirPods Pro',
                description: 'Aktif Gürültü Önleme',
                imageUrl: 'https://images.unsplash.com/photo-1606841837239-c5a1a4a07af7?w=400',
                price: 8500,
                originalPrice: 8500,
                category: 'Aksesuar'
            }
        ];

        let isAdmin = false;
        let currentCategory = 'all';

        function render() {
            const filtered = products.filter(p => currentCategory === 'all' || p.category === currentCategory);
            const grid = document.getElementById('productsGrid');
            
            grid.innerHTML = filtered.map(p => {
                const hasDiscount = p.originalPrice > p.price;
                return `
                <div class="bg-white rounded-lg shadow p-4 ${hasDiscount ? 'border-4 border-yellow-400' : ''}">
                    <img src="${p.imageUrl}" class="w-full h-40 object-cover rounded mb-2">
                    <h3 class="font-bold">${p.name}</h3>
                    <p class="text-sm text-gray-600">${p.description}</p>
                    ${hasDiscount ? `<p class="text-xs line-through text-gray-400">${p.originalPrice.toLocaleString()} ₺</p>` : ''}
                    <p class="text-lg font-bold text-blue-600">${p.price.toLocaleString()} ₺</p>
                    ${isAdmin ? `
                        <button onclick="deleteProduct(${p.id})" class="w-full mt-2 bg-red-500 text-white py-2 rounded hover:bg-red-600">Sil</button>
                    ` : `
                        <div class="mt-2 bg-green-500 text-white py-2 px-4 rounded text-center font-semibold">
                            📍 Mağazadan Alınabilir
                        </div>
                    `}
                </div>
            `}).join('');
        }

        window.deleteProduct = function(id) {
            if (confirm('Silmek istediğinize emin misiniz?')) {
                products = products.filter(p => p.id !== id);
                render();
            }
        };

        document.getElementById('adminBtn').addEventListener('click', () => {
            if (isAdmin) {
                isAdmin = false;
                document.getElementById('adminPanel').classList.add('hidden');
                render();
            } else {
                document.getElementById('loginModal').classList.remove('hidden');
                // focus password for convenience
                setTimeout(() => document.getElementById('passwordInput').focus(), 50);
            }
        });

        document.getElementById('loginBtn').addEventListener('click', () => {
            if (document.getElementById('passwordInput').value === 'yunus710') {
                isAdmin = true;
                document.getElementById('loginModal').classList.add('hidden');
                document.getElementById('adminPanel').classList.remove('hidden');
                render();
            } else {
                alert('Yanlış şifre!');
            }
        });

        // Close (X) button behavior
        document.getElementById('closeLoginModal').addEventListener('click', () => {
            document.getElementById('loginModal').classList.add('hidden');
        });

        // Close modal when clicking on backdrop (outside the inner modal)
        document.getElementById('loginModal').addEventListener('click', (e) => {
            if (e.target === document.getElementById('loginModal')) {
                document.getElementById('loginModal').classList.add('hidden');
            }
        });

        // Close modal with Escape key
        window.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                const modal = document.getElementById('loginModal');
                if (!modal.classList.contains('hidden')) {
                    modal.classList.add('hidden');
                }
            }
        });

        document.getElementById('addProductBtn').addEventListener('click', () => {
            const name = document.getElementById('productName').value;
            const desc = document.getElementById('productDesc').value;
            const category = document.getElementById('productCategory').value;
            const image = document.getElementById('productImage').value;
            const price = Number(document.getElementById('productPrice').value);
            const oldPrice = Number(document.getElementById('productOriginalPrice').value) || price;

            if (name && image && price) {
                products.push({
                    id: Date.now(),
                    name,
                    description: desc,
                    category,
                    imageUrl: image,
                    price,
                    originalPrice: oldPrice
                });
                
                document.getElementById('productName').value = '';
                document.getElementById('productDesc').value = '';
                document.getElementById('productImage').value = '';
                document.getElementById('productPrice').value = '';
                document.getElementById('productOriginalPrice').value = '';
                render();
            } else {
                alert('Lütfen gerekli alanları doldurun!');
            }
        });

        document.querySelectorAll('.category-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                document.querySelectorAll('.category-btn').forEach(b => {
                    b.className = 'category-btn px-4 py-2 rounded-full hover:bg-gray-100 font-medium';
                });
                e.target.className = 'category-btn px-4 py-2 rounded-full bg-blue-600 text-white font-medium';
                currentCategory = e.target.dataset.category;
                render();
            });
        });

        // İlk render
        render();
    </script>
</body>
</html>
