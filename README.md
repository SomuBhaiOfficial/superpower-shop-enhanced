# superpower-shop-enhanced

// The Superpower Shop - Interactive Marketplace for Cosmic Abilities
// Developed with 90% human-like code patterns and natural conventions

class SuperpowerShop {
  constructor() {
    // Core application state
    this.products = [];
    this.bundles = [];
    this.cart = [];
    this.currentFilter = 'all';
    this.isAdminMode = false;
    this.powerMeterInterval = null;
    this.konamiCode = [];
    this.targetKonami = [38, 38, 40, 40, 37, 39, 37, 39, 66, 65]; // ↑↑↓↓←→←→BA
    this.secretDiscountCode = '';

    // Initialize the application
    this.initializeApp();
  }

  async initializeApp() {
    console.log('🚀 Initializing Superpower Shop...');

    // Show loading screen
    this.showLoadingScreen();

    // Load product data
    await this.loadProductData();

    // Setup event listeners
    this.setupEventListeners();

    // Initialize UI components
    this.initializeUI();

    // Start background animations
    this.startBackgroundEffects();

    // Setup easter eggs
    this.initializeEasterEggs();

    // Hide loading screen after setup
    setTimeout(() => {
      this.hideLoadingScreen();
    }, 3000);
  }

  showLoadingScreen() {
    const loadingScreen = document.getElementById('loadingScreen');
    const loadingMessage = document.getElementById('loadingMessage');
    const mysteriousMessages = [
      "Scanning quantum signatures...",
      "Calibrating power matrices...",
      "Consulting ancient scrolls...",
      "Analyzing side effect probability...",
      "Negotiating with interdimensional suppliers...",
      "Checking cosmic alignment...",
      "Validating superhero license...",
      "Performing ritual power dance...",
      "Bribing physics to cooperate...",
      "Installing reality patches..."
    ];
    let messageIndex = 0;
    const messageInterval = setInterval(() => {
      loadingMessage.textContent = mysteriousMessages[messageIndex];
      messageIndex = (messageIndex + 1) % mysteriousMessages.length;
    }, 400);

    // Stop message rotation after 2.5 seconds
    setTimeout(() => {
      clearInterval(messageInterval);
      loadingMessage.textContent = "Welcome to the Superpower Shop!";
    }, 2500);
  }

  hideLoadingScreen() {
    const loadingScreen = document.getElementById('loadingScreen');
    const mainContent = document.getElementById('mainContent');
    loadingScreen.style.opacity = '0';
    setTimeout(() => {
      loadingScreen.classList.add('hidden');
      mainContent.classList.remove('hidden');
      mainContent.classList.add('fade-in');
    }, 500);
  }

  async loadProductData() {
    // Simulate loading from an API with realistic data structure
    const productData = {
      "products": [
        {
          "id": 1,
          "name": "Flight Master",
          "price": 999,
          "originalPrice": 1299,
          "description": "Soar through the skies with complete aerial mastery! Experience the freedom of flight with advanced propulsion technology.",
          "sideEffect": "Only works 2 feet above ground - perfect for avoiding puddles and impressing very short people",
          "icon": "✈️",
          "category": "movement",
          "powerLevel": 7,
          "rarity": "uncommon",
          "lastPurchased": "2 hours ago in Metropolis",
          "testimonial": "Great for avoiding puddles! My ankles have never been drier. - SkyWalker99 ⭐⭐⭐⭐",
          "availability": 5,
          "similarProducts": [2, 7, 9]
        },
        {
          "id": 2,
          "name": "Invisibility Cloak",
          "price": 1299,
          "originalPrice": 1599,
          "description": "Become completely invisible at will! Vanish from sight and move unseen through any environment.",
          "sideEffect": "Only works when nobody is looking at you - creates interesting philosophical paradoxes",
          "icon": "👻",
          "category": "stealth",
          "powerLevel": 8,
          "rarity": "rare",
          "lastPurchased": "45 minutes ago in Gotham City",
          "testimonial": "Finally got some alone time! Wait, can anyone see this review? - NotThere ⭐⭐⭐⭐⭐",
          "availability": 3,
          "similarProducts": [9, 1, 8]
        },
        {
          "id": 3,
          "name": "Mind Reader Pro",
          "price": 1599,
          "originalPrice": 1999,
          "description": "Read anyone's deepest thoughts and secrets! Unlock the mysteries of the human mind.",
          "sideEffect": "Only receive thoughts in Morse code - hope you studied your dots and dashes",
          "icon": "🧠",
          "category": "psychic",
          "powerLevel": 9,
          "rarity": "legendary",
          "lastPurchased": "1 hour ago in Xavier Institute",
          "testimonial": "Learned Morse code just for this. Worth it. Dot dot dash! - ThoughtThief ⭐⭐⭐",
          "availability": 2,
          "similarProducts": [5, 8, 11]
        },
        {
          "id": 4,
          "name": "Super Strength",
          "price": 899,
          "originalPrice": 1199,
          "description": "Lift cars, punch through walls, be unstoppable! Incredible physical power at your fingertips.",
          "sideEffect": "Can't control gentle touch - everything breaks. RIP door handles and handshakes",
          "icon": "💪",
          "category": "physical",
          "powerLevel": 6,
          "rarity": "common",
          "lastPurchased": "30 minutes ago in Central City",
          "testimonial": "Broke 47 door handles this week. Send help. - GentleGiant ⭐⭐",
          "availability": 8,
          "similarProducts": [15, 1, 12]
        },
        {
          "id": 5,
          "name": "Telekinesis Master",
          "price": 1399,
          "originalPrice": 1799,
          "description": "Move objects with the power of your mind! The ultimate expression of mental prowess.",
          "sideEffect": "Can only move hamburgers and burger-related items - at least you'll never go hungry",
          "icon": "🔮",
          "category": "psychic",
          "powerLevel": 8,
          "rarity": "rare",
          "lastPurchased": "3 hours ago in Star City",
          "testimonial": "Best power for fast food workers everywhere! - BurgerMover ⭐⭐⭐⭐",
          "availability": 4,
          "similarProducts": [3, 8, 13]
        },
        {
          "id": 6,
          "name": "Time Travel Device",
          "price": 2499,
          "originalPrice": 2999,
          "description": "Journey through time and change history! The ultimate power over the temporal dimension.",
          "sideEffect": "Only travels to embarrassing moments in your past - prepare for maximum cringe",
          "icon": "⏰",
          "category": "temporal",
          "powerLevel": 10,
          "rarity": "mythic",
          "lastPurchased": "6 hours ago in Coast City",
          "testimonial": "Went back to my high school graduation speech. Mistakes were made. - TimeTraveler2000 ⭐⭐",
          "availability": 1,
          "similarProducts": [11, 3, 14]
        },
        {
          "id": 7,
          "name": "Super Speed",
          "price": 1199,
          "originalPrice": 1499,
          "description": "Run faster than lightning across any terrain! Leave everyone in your dust.",
          "sideEffect": "Go completely blind while running - GPS highly recommended",
          "icon": "💨",
          "category": "movement",
          "powerLevel": 7,
          "rarity": "uncommon",
          "lastPurchased": "90 minutes ago in Keystone City",
          "testimonial": "Really fast but walked into so many walls. - SpeedDemon ⭐⭐⭐",
          "availability": 6,
          "similarProducts": [1, 2, 15]
        },
        {
          "id": 8,
          "name": "Telepathy Headset",
          "price": 1099,
          "originalPrice": 1399,
          "description": "Communicate directly through thoughts! Connect minds across any distance.",
          "sideEffect": "Can only hear what people think about lunch - surprisingly informative",
          "icon": "📡",
          "category": "psychic",
          "powerLevel": 6,
          "rarity": "common",
          "lastPurchased": "20 minutes ago in Jump City",
          "testimonial": "Everyone thinks about sandwiches more than expected. - LunchListener ⭐⭐⭐⭐",
          "availability": 7,
          "similarProducts": [3, 5, 14]
        },
        {
          "id": 9,
          "name": "Shape Shifter",
          "price": 1799,
          "originalPrice": 2199,
          "description": "Transform into any form you desire! The ultimate disguise and infiltration tool.",
          "sideEffect": "Can only turn into different types of furniture - IKEA jokes not included",
          "icon": "🦎",
          "category": "transformation",
          "powerLevel": 8,
          "rarity": "rare",
          "lastPurchased": "4 hours ago in Titans Tower",
          "testimonial": "Great for home decoration but terrible for stealth missions. - ChairPerson ⭐⭐⭐",
          "availability": 3,
          "similarProducts": [2, 15, 1]
        },
        {
          "id": 10,
          "name": "Energy Blast",
          "price": 1399,
          "originalPrice": 1699,
          "description": "Shoot powerful energy beams from your hands! Devastating ranged attacks at your command.",
          "sideEffect": "Only works when you're hiccupping - carbonated drinks are your best friend",
          "icon": "⚡",
          "category": "energy",
          "powerLevel": 7,
          "rarity": "uncommon",
          "lastPurchased": "1 hour ago in Central City",
          "testimonial": "Learned to hiccup on command. Very useful party trick. - HiccupHero ⭐⭐⭐⭐",
          "availability": 5,
          "similarProducts": [13, 4, 12]
        },
        {
          "id": 11,
          "name": "Weather Control",
          "price": 2199,
          "originalPrice": 2599,
          "description": "Command the elements themselves! Summon storms, sunshine, and everything between.",
          "sideEffect": "Only works based on your current mood - anger management classes recommended",
          "icon": "🌩️",
          "category": "elemental",
          "powerLevel": 9,
          "rarity": "legendary",
          "lastPurchased": "5 hours ago in Star City",
          "testimonial": "My therapist says I need to work on my anger issues. - StormyMcStormface ⭐⭐",
          "availability": 2,
          "similarProducts": [6, 12, 10]
        },
        {
          "id": 12,
          "name": "X-Ray Vision",
          "price": 1699,
          "originalPrice": 1999,
          "description": "See through solid objects and uncover hidden secrets! Nothing can hide from you.",
          "sideEffect": "Can only see people's underwear, nothing else - awkward family dinners guaranteed",
          "icon": "👁️",
          "category": "vision",
          "powerLevel": 6,
          "rarity": "uncommon",
          "lastPurchased": "2 hours ago in Metropolis",
          "testimonial": "TMI about everyone. Ignorance was bliss. - SeeAllKnowAll ⭐",
          "availability": 4,
          "similarProducts": [14, 11, 4]
        },
        {
          "id": 13,
          "name": "Laser Eyes",
          "price": 1899,
          "originalPrice": 2299,
          "description": "Shoot precision laser beams from your eyes! The ultimate offensive capability.",
          "sideEffect": "Only shoots at things you find mildly annoying - goodbye, slow walkers",
          "icon": "🔴",
          "category": "energy",
          "powerLevel": 8,
          "rarity": "rare",
          "lastPurchased": "3 hours ago in Gotham City",
          "testimonial": "Accidentally destroyed a lot of printers and traffic lights. - LaserGuy2023 ⭐⭐⭐",
          "availability": 3,
          "similarProducts": [10, 5, 12]
        },
        {
          "id": 14,
          "name": "Super Hearing",
          "price": 799,
          "originalPrice": 1099,
          "description": "Hear everything within miles! Perfect for surveillance and eavesdropping.",
          "sideEffect": "Can only hear people complaining - world's most depressing superpower",
          "icon": "👂",
          "category": "sensory",
          "powerLevel": 5,
          "rarity": "common",
          "lastPurchased": "15 minutes ago in Coast City",
          "testimonial": "People complain about everything. EVERYTHING. - SuperEars ⭐⭐",
          "availability": 9,
          "similarProducts": [12, 8, 3]
        },
        {
          "id": 15,
          "name": "Elastic Body",
          "price": 1299,
          "originalPrice": 1599,
          "description": "Stretch your body like rubber! Ultimate flexibility and reach.",
          "sideEffect": "Randomly snaps back at inconvenient times - job interviews are interesting",
          "icon": "🌡️",
          "category": "physical",
          "powerLevel": 6,
          "rarity": "uncommon",
          "lastPurchased": "40 minutes ago in Jump City",
          "testimonial": "Snapped back during my wedding vows. Awkward silence ensued. - StretchGuy ⭐⭐⭐",
          "availability": 5,
          "similarProducts": [4, 9, 7]
        }
      ],
      "bundles": [
        {
          "id": 1,
          "name": "Classic Hero Bundle",
          "items": [1, 4],
          "freeItem": "Talks to Pigeons",
          "discount": 15,
          "description": "The essential superhero starter pack! Flight + Strength = Classic heroism",
          "originalPrice": 2298,
          "bundlePrice": 1953
        },
        {
          "id": 2,
          "name": "Mind Powers Bundle",
          "items": [3, 8],
          "freeItem": "Always Knows What Day It Is",
          "discount": 20,
          "description": "Master the mysteries of the mind! Read thoughts + telepathy",
          "originalPrice": 2698,
          "bundlePrice": 2158
        },
        {
          "id": 3,
          "name": "Stealth Bundle",
          "items": [2, 9],
          "freeItem": "Makes Weird Noises When Walking",
          "discount": 18,
          "description": "Perfect for those who prefer the shadows! Invisibility + shape-shifting",
          "originalPrice": 3098,
          "bundlePrice": 2540
        },
        {
          "id": 4,
          "name": "Energy Master Bundle",
          "items": [10, 13],
          "freeItem": "Glows Slightly in the Dark",
          "discount": 22,
          "description": "Unleash devastating energy attacks! Energy blast + laser eyes",
          "originalPrice": 3298,
          "bundlePrice": 2572
        }
      ]
    };

    this.products = productData.products;
    this.bundles = productData.bundles;
    console.log(`📦 Loaded ${this.products.length} products and ${this.bundles.length} bundles`);
  }

  setupEventListeners() {
    // Header controls
    document.getElementById('cartToggle').addEventListener('click', () => this.toggleCart());
    document.getElementById('adminToggle').addEventListener('click', () => this.toggleAdmin());
    document.getElementById('mainLogo').addEventListener('click', this.handleLogoClick.bind(this));

    // Category filters event delegation (better for dynamic content)
    document.getElementById('filterContainer').addEventListener('click', (e) => {
      if (e.target.classList.contains('category-filter')) {
        this.filterProducts(e.target.dataset.category);
        this.updateActiveFilter(e.target);
      }
    });

    // Modal controls
    document.getElementById('closeCart').addEventListener('click', () => this.hideModal('cartModal'));
    document.getElementById('closeAdmin').addEventListener('click', () => this.toggleAdmin());
    document.getElementById('closeProductModal').addEventListener('click', () => this.hideModal('productModal'));

    // Cart actions
    document.getElementById('clearCart').addEventListener('click', () => this.clearCart());
    document.getElementById('checkoutButton').addEventListener('click', () => this.processCheckout());

    // Admin form submission
    document.getElementById('addProductForm').addEventListener('submit', this.handleAddProduct.bind(this));

    // Mystery box click
    document.getElementById('mysteryBox').addEventListener('click', () => this.revealMysteryDiscount());

    // Keyboard events (easter eggs)
    document.addEventListener('keydown', this.handleKeyDown.bind(this));
    document.addEventListener('keypress', this.handleKeyPress.bind(this));

    // Close modals by clicking backdrop
    document.querySelectorAll('.modal-backdrop').forEach(backdrop => {
      backdrop.addEventListener('click', (e) => {
        const modal = e.target.closest('.modal');
        if (modal) {
          this.hideModal(modal.id);
        }
      });
    });

    console.log('🎮 Event listeners initialized');
  }

  initializeUI() {
    // Render filter buttons first
    this.renderCategoryFilters();

    // Render initial products and bundles
    this.renderProducts();
    this.renderBundles();

    // Update cart UI and disclaimer scroll
    this.updateCartDisplay();
    this.initializeDisclaimerScroll();

    // Initialize security level animation
    this.animateSecurityLevel();

    console.log('🎨 UI components initialized');
  }

  startBackgroundEffects() {
    // Animate power meter bar
    this.animatePowerMeter();

    // Periodically randomize orb positions in background
    setInterval(() => {
      this.randomizeOrbPositions();
    }, 10000);

    console.log('✨ Background effects started');
  }

  renderCategoryFilters() {
    // Prepare category list (including 'all')
    const categories = ['all', ...new Set(this.products.map(p => p.category))];
    const filterContainer = document.getElementById('filterContainer');
    filterContainer.innerHTML = categories.map(category =>
      `<button class="category-filter${category === 'all' ? ' active' : ''}" data-category="${category}">${category.toUpperCase()}</button>`
    ).join('');
  }

  filterProducts(category) {
    this.currentFilter = category;
    this.renderProducts();
  }

  updateActiveFilter(activeBtn) {
    document.querySelectorAll('.category-filter').forEach(btn => btn.classList.remove('active'));
    activeBtn.classList.add('active');
  }

  renderProducts() {
    const productGrid = document.getElementById('productGrid');
    const filteredProducts = this.currentFilter === 'all' 
      ? this.products 
      : this.products.filter(product => product.category === this.currentFilter);

    productGrid.innerHTML = filteredProducts.map(product => this.createProductCard(product)).join('');

    // Attach listeners on new product cards (e.g., add to cart)
    this.attachProductEventListeners();
  }

  createProductCard(product) {
    const rarityClass = product.rarity || 'common';

    return `
      <div class="product-card ${rarityClass}" data-id="${product.id}">
        <div class="product-icon">${product.icon}</div>
        <h3 class="product-name">${product.name}</h3>
        <p class="product-description">${product.description}</p>
        <p class="product-side-effect"><strong>Side Effect:</strong> ${product.sideEffect}</p>
        <p class="product-price">Price: $${product.price} <span class="original-price">$${product.originalPrice}</span></p>
        <p class="product-availability">Availability: ${product.availability} units</p>
        <p class="product-testimonial">"${product.testimonial.split(' - ')[0]}" — <em>${product.testimonial.split(' - ')[1]?.replace(/⭐/g, '') || 'Anonymous'}</em></p>
        <button class="add-to-cart-btn">Add to Cart</button>
      </div>
    `;
  }

  attachProductEventListeners() {
    document.querySelectorAll('.add-to-cart-btn').forEach(button => {
      button.addEventListener('click', (e) => {
        const productId = parseInt(e.target.closest('.product-card').dataset.id);
        this.addToCart(productId);
      });
    });
  }

  addToCart(productId) {
    const product = this.products.find(p => p.id === productId);
    if (!product) return;

    // Check availability before adding
    const ca
