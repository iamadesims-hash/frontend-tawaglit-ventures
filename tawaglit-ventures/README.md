# Tawaglit Ventures - Frontend

A modern, premium Real Estate Platform built with pure HTML, CSS, and JavaScript. Includes property listings, safe guided tours, secure chat, wallet system, and more.

## 🚀 Features

- **Landing Page** with beautiful hero and authentication
- **Dashboard** with portfolio overview and activity
- **Property Marketplace** with real-time price updates
- **Property Details** with map, boost, and agent messaging
- **Safe Guided Tour** with WebRTC video + live chat
- **Secure Messaging** with E2E encryption simulation
- **Multi-currency Wallet** with Paystack, Stripe & Crypto
- **Premium Community** with group creation
- **KYC Verification** with Stripe Identity + manual upload
- **Fully Responsive** + Dark/Light mode
- **Floating Message Button** for instant agent chat

## 📁 Project Structure

tawaglit-ventures-frontend/
├── index.html
├── dashboard.html
├── properties.html
├── property-detail.html
├── upload-property.html
├── tour.html
├── messages.html
├── wallet.html
├── community.html
├── kyc.html
├── admin/
│   └── index.html
├── assets/
│   └── images/
└── README.md

## 🛠️ How to Run Locally

1. Clone or download the repository
2. Open any `.html` file in your browser (e.g. `index.html`)
3. No build step required — pure static frontend

## 🌐 Live Demo

(Deployed on Vercel — link will be added after deployment)

## 🎯 Key Pages

- `index.html` — Landing + Login/Signup
- `properties.html` — Marketplace with live updates
- `tour.html` — WebRTC Safe Guided Tour
- `messages.html` — Secure Chat
- `wallet.html` — Multi-currency Crypto & Fiat Wallet
- `admin/index.html` — Admin Panel (for demonstration)

## 🔧 Technologies Used

- HTML5
- Tailwind CSS
- Vanilla JavaScript
- Font Awesome Icons
- WebRTC (for tours)
- Socket.IO simulation
- Paystack & Stripe integration (ready)

## 📋 Next Steps (Roadmap)

- Convert to Next.js 15 + TypeScript
- Integrate real Supabase backend
- Add full authentication flow
- Deploy production backend with Socket.IO

---

**Made with ❤️ for Tawaglit Ventures**

**Author**: Dolapo Olayinka  
**Status**: Advanced Prototype (Ready for MVP Conversion)

---

You can now copy this `README.md` directly into your project root.

Would you like me to provide any more files, or shall we start converting this to a **real Next.js** project?

Explore Next.js migration steps

Review Supabase database schema

assets.html

 Here is the complete assets.htmlhtml

<!DOCTYPE html>
<html lang="en" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assets Library - Tawaglit Ventures</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gray-950 text-white pt-20">
  <!-- Shared Navbar -->
  <nav class="fixed top-0 w-full bg-black/90 backdrop-blur-md z-50 border-b border-gray-800">
    <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
      <h1 onclick="window.location='index.html'" class="text-2xl font-bold text-emerald-400 cursor-pointer">Tawaglit<span class="text-white">Ventures</span></h1>
      
      <div class="flex gap-8 text-sm font-medium">
        <a href="properties.html" class="hover:text-emerald-400">Properties</a>
        <a href="messages.html" class="hover:text-emerald-400">Messages</a>
        <a href="community.html" class="hover:text-emerald-400">Community</a>
        <a href="tour.html" class="hover:text-emerald-400">Safe Tours</a>
        <a href="wallet.html" class="hover:text-emerald-400">Wallet</a>
      </div>

      <div class="flex items-center gap-4">
        <button onclick="toggleTheme()" id="themeBtn" class="p-3 hover:bg-gray-800 rounded-2xl"><i class="fas fa-moon"></i></button>
        <button onclick="logout()" class="bg-red-600/20 text-red-400 px-6 py-2.5 rounded-2xl text-sm">Logout</button>
      </div>
    </div>
  </nav>

  <div class="max-w-7xl mx-auto px-6 py-10">
    <h1 class="text-4xl font-bold mb-2">Assets & Media Library</h1>
    <p class="text-gray-400 mb-10">Manage photos, videos, and 360° tours for your listings</p>

    <!-- Upload Section -->
    <div class="bg-gray-900 rounded-3xl p-10 mb-12">
      <h3 class="text-2xl font-semibold mb-6">Upload New Assets</h3>
      <input type="file" id="assetUpload" multiple accept="image/*,video/*" 
             class="block w-full text-sm text-gray-400 file:mr-4 file:py-6 file:px-10 file:rounded-2xl file:border-0 file:bg-emerald-600 file:text-white">
      <p class="text-xs text-gray-500 mt-4">Supported: JPG, PNG, MP4, 360° photos (Max 100MB each)</p>
    </div>

    <!-- Assets Grid -->
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6" id="assetsGrid"></div>
  </div>

  <!-- Floating Message Button -->
  <button onclick="window.location='messages.html'" 
          class="fixed bottom-8 right-8 bg-emerald-600 w-16 h-16 rounded-full shadow-2xl flex items-center justify-center text-3xl hover:scale-110 transition z-50">
    💬
  </button>

  <script>
    const sampleAssets = [
      { type: "image", url: "https://picsum.photos/id/1015/600/400", name: "Front View.jpg" },
      { type: "image", url: "https://picsum.photos/id/237/600/400", name: "Living Room.jpg" },
      { type: "video", url: "https://picsum.photos/id/201/600/400", name: "Tour Video.mp4" },
      { type: "image", url: "https://picsum.photos/id/180/600/400", name: "Kitchen.jpg" }
    ];

    function renderAssets() {
      const grid = document.getElementById('assetsGrid');
      grid.innerHTML = sampleAssets.map(asset => `
        <div class="bg-gray-900 rounded-3xl overflow-hidden">
          ${asset.type === 'video' ? 
            `<video src="${asset.url}" class="w-full h-52 object-cover" muted></video>` : 
            `<img src="${asset.url}" class="w-full h-52 object-cover">`}
          <div class="p-5">
            <p class="text-sm font-medium">${asset.name}</p>
            <p class="text-xs text-gray-500">${asset.type.toUpperCase()}</p>
          </div>
        </div>
      `).join('');
    }

    // Handle new uploads
    document.getElementById('assetUpload').addEventListener('change', function(e) {
      Array.from(e.target.files).forEach(file => {
        const reader = new FileReader();
        reader.onload = function(ev) {
          const isVideo = file.type.startsWith('video');
          const div = document.createElement('div');
          div.className = "bg-gray-900 rounded-3xl overflow-hidden";
          div.innerHTML = isVideo ? 
            `<video src="${ev.target.result}" class="w-full h-52 object-cover" muted controls></video>` : 
            `<img src="${ev.target.result}" class="w-full h-52 object-cover">`;
          document.getElementById('assetsGrid').prepend(div);
        };
        reader.readAsDataURL(file);
      });
    });

    function toggleTheme() {
      document.documentElement.classList.toggle('dark');
      localStorage.setItem('theme', document.documentElement.classList.contains('dark') ? 'dark' : 'light');
    }

    function logout() {
      if (confirm("Logout from Tawaglit Ventures?")) {
        localStorage.removeItem('tawaglit_user');
        window.location.href = 'index.html';
      }
    }

    // Initialize
    window.onload = renderAssets;
  </script>
</body>
</html>

Features Included:Media upload with preview
Image & Video support
Clean asset grid
Consistent design with other pages


