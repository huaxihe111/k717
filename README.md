# k717[inex.html](https://github.com/user-attachments/files/34124652/inex.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>k栋饮品</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background: #f5f5f5;
      color: #222;
      font-family: Arial, "Microsoft YaHei", sans-serif;
    }

    button,
    input,
    select,
    textarea {
      font-family: inherit;
    }

    button {
      cursor: pointer;
    }

    .app {
      width: 100%;
      max-width: 480px;
      min-height: 100vh;
      margin: auto;
      background: #fff;
      padding-bottom: 65px;
    }

    .top-header {
      height: 85px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-bottom: 1px solid #eee;
      background: #fff;
    }

    .shop-name {
      font-size: 27px;
      font-weight: bold;
      letter-spacing: 2px;
    }

    .category-bar {
      display: flex;
      height: 52px;
      border-bottom: 1px solid #eee;
      background: #fff;
    }

    .category-item {
      flex: 1;
      border: 0;
      background: #fff;
      color: #999;
      font-size: 16px;
    }

    .category-item.active {
      color: #111;
      font-weight: bold;
      border-bottom: 3px solid #111;
    }

    .product-list {
      padding: 0 15px;
    }

    .product-card {
      display: flex;
      align-items: center;
      gap: 13px;
      min-height: 135px;
      padding: 15px 0;
      border-bottom: 1px solid #eee;
    }

    .product-card:active {
      background: #fafafa;
    }

    .product-image {
      width: 105px;
      height: 105px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 10px;
      background: linear-gradient(135deg, #f0dfce, #b87b4d);
      font-size: 42px;
    }

    .product-info {
      flex: 1;
    }

    .product-title {
      margin-bottom: 7px;
      font-size: 18px;
      font-weight: bold;
    }

    .product-desc {
      min-height: 38px;
      margin-bottom: 8px;
      color: #999;
      font-size: 13px;
      line-height: 1.5;
    }

    .product-bottom {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .price {
      font-size: 18px;
      font-weight: bold;
    }

    .price::before {
      content: "¥";
      margin-right: 2px;
      font-size: 13px;
    }

    .add-btn,
    .black-button {
      border: 0;
      background: #111;
      color: #fff;
    }

    .add-btn {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      font-size: 22px;
      line-height: 25px;
    }

    .sold-out {
      color: #999;
      font-size: 14px;
    }

    .bottom-nav {
      position: fixed;
      left: 50%;
      bottom: 0;
      z-index: 20;
      display: flex;
      width: 100%;
      max-width: 480px;
      height: 64px;
      transform: translateX(-50%);
      border-top: 1px solid #ddd;
      background: #fff;
    }

    .nav-item {
      flex: 1;
      border: 0;
      background: #fff;
      color: #999;
      font-size: 15px;
    }

    .nav-item.active {
      color: #111;
      font-weight: bold;
    }

    .nav-icon {
      display: block;
      margin-bottom: 3px;
      font-size: 21px;
    }

    /* 购物车 */
    .cart-button {
      position: fixed;
      right: 20px;
      bottom: 80px;
      z-index: 25;
      width: 56px;
      height: 56px;
      border: 3px solid #111;
      border-radius: 50%;
      background: #fff;
      font-size: 22px;
    }

    .cart-count {
      position: absolute;
      top: -7px;
      right: -7px;
      display: none;
      min-width: 20px;
      height: 20px;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      background: #d00;
      color: #fff;
      font-size: 12px;
    }

    .cart-panel {
      position: fixed;
      left: 50%;
      bottom: 64px;
      z-index: 30;
      display: none;
      width: 100%;
      max-width: 480px;
      max-height: 75vh;
      padding: 18px;
      overflow: hidden;
      transform: translateX(-50%);
      background: #fff;
      box-shadow: 0 -3px 15px rgba(0, 0, 0, .15);
    }

    .cart-panel.show {
      display: block;
    }

    .cart-title,
    .page-title,
    .order-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .cart-title {
      margin-bottom: 12px;
      font-size: 18px;
      font-weight: bold;
    }

    .clear-button {
      border: 0;
      background: none;
      color: #999;
      font-size: 13px;
    }

    .cart-items {
      max-height: 38vh;
      overflow-y: auto;
    }

    .cart-row {
      display: flex;
      justify-content: space-between;
      padding: 11px 0;
      border-bottom: 1px solid #eee;
      font-size: 14px;
    }

    .cart-total {
      display: flex;
      justify-content: space-between;
      padding: 16px 0 10px;
      font-size: 18px;
      font-weight: bold;
    }

    .pay-button,
    .save-button {
      width: 100%;
      height: 44px;
      border: 0;
      border-radius: 5px;
      background: #111;
      color: #fff;
      font-size: 16px;
    }

    .empty {
      padding: 35px 0;
      color: #999;
      text-align: center;
    }

    /* 我的页面 */
    .mine-page {
      display: none;
      min-height: calc(100vh - 64px);
      background: #fff;
    }

    .login-area {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 22px 15px;
      border-bottom: 1px solid #eee;
    }

    .login-title {
      margin-bottom: 6px;
      font-size: 18px;
      font-weight: bold;
    }

    .login-desc {
      color: #999;
      font-size: 13px;
    }

    .login-button {
      height: 38px;
      padding: 0 18px;
      border: 0;
      border-radius: 6px;
      background: #111;
      color: #fff;
    }

    .mine-menu {
      padding: 0 15px;
    }

    .mine-menu-item {
      width: 100%;
      height: 58px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 0;
      border-bottom: 1px solid #eee;
      background: #fff;
      text-align: left;
      font-size: 16px;
    }

    .arrow {
      color: #999;
      font-size: 23px;
    }

    /* 页面 */
    .sub-page {
      display: none;
      min-height: calc(100vh - 64px);
      padding: 18px 15px;
      background: #fff;
    }

    .page-title {
      height: 45px;
      margin-bottom: 15px;
      border-bottom: 1px solid #eee;
      font-size: 21px;
      font-weight: bold;
    }

    .back-button {
      border: 0;
      background: none;
      color: #555;
      font-size: 15px;
    }

    .detail-image {
      height: 230px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 20px;
      border-radius: 12px;
      background: linear-gradient(135deg, #f0dfce, #b87b4d);
      font-size: 90px;
    }

    .detail-title {
      margin-bottom: 10px;
      font-size: 25px;
      font-weight: bold;
    }

    .detail-desc {
      margin-bottom: 20px;
      color: #888;
      line-height: 1.7;
    }

    .detail-price {
      margin-bottom: 20px;
      font-size: 25px;
      font-weight: bold;
    }

    .detail-price::before {
      content: "¥";
      margin-right: 3px;
      font-size: 16px;
    }

    .address-input,
    .admin-input,
    .admin-select {
      width: 100%;
      min-height: 42px;
      margin: 8px 0 15px;
      padding: 9px 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      outline: none;
      font-size: 14px;
    }

    textarea.address-input {
      resize: vertical;
    }

    .payment-box,
    .order-card,
    .admin-card {
      margin-bottom: 15px;
      padding: 15px;
      border: 1px solid #eee;
      border-radius: 7px;
    }

    .payment-row,
    .order-row {
      display: flex;
      justify-content: space-between;
      padding: 9px 0;
      border-bottom: 1px solid #eee;
      font-size: 14px;
    }

    .payment-total {
      display: flex;
      justify-content: space-between;
      padding: 17px 0;
      font-size: 19px;
      font-weight: bold;
    }

    .order-status {
      color: #d97706;
    }

    .order-status.paid {
      color: #16803c;
    }

    /* 后台 */
    .admin-page {
      display: none;
      min-height: calc(100vh - 64px);
      padding: 15px;
      background: #fff;
    }

    .admin-toolbar {
      display: flex;
      gap: 8px;
      margin-bottom: 15px;
    }

    .admin-toolbar button {
      flex: 1;
      height: 38px;
      border: 1px solid #111;
      background: #fff;
      font-size: 14px;
    }

    .admin-toolbar button.active {
      background: #111;
      color: #fff;
    }

    .admin-card h3 {
      margin-bottom: 10px;
      font-size: 17px;
    }

    .admin-line {
      display: flex;
      justify-content: space-between;
      gap: 10px;
      padding: 7px 0;
      color: #555;
      font-size: 14px;
    }

    .admin-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 7px;
      margin-top: 12px;
    }

    .admin-actions button {
      padding: 7px 10px;
      border: 1px solid #111;
      background: #fff;
      font-size: 13px;
    }

    .admin-actions button.dark {
      background: #111;
      color: #fff;
    }

    .admin-form {
      margin-bottom: 18px;
      padding: 15px;
      background: #fafafa;
    }

    .admin-form h2 {
      margin-bottom: 10px;
      font-size: 19px;
    }

    .form-row {
      display: flex;
      gap: 8px;
    }

    .form-row > * {
      flex: 1;
    }

    .status-on_sale {
      color: #16803c;
    }

    .status-sold_out,
    .status-off_sale {
      color: #d00;
    }
  </style>
</head>

<body>
  <div class="app">

    <!-- 客户商品页 -->
    <div id="customerView">
      <header class="top-header">
        <div class="shop-name">k栋饮品</div>
      </header>

      <div class="category-bar">
        <button class="category-item active" onclick="changeCategory(this, 'coffee')">咖啡</button>
        <button class="category-item" onclick="changeCategory(this, 'tea')">茶</button>
        <button class="category-item" onclick="changeCategory(this, 'alcohol')">酒</button>
      </div>

      <main id="productPage">
        <div class="product-list" id="productList"></div>
      </main>

      <section class="mine-page" id="minePage">
        <div class="login-area">
          <div>
            <div class="login-title">欢迎来到 k栋饮品</div>
            <div class="login-desc">查看订单和消费信息</div>
          </div>
          <button class="login-button" onclick="alert('本地演示无需登录')">登录</button>
        </div>

        <div class="mine-menu">
          <button class="mine-menu-item" onclick="showOrders()">
            查看订单 <span class="arrow">›</span>
          </button>
        </div>
      </section>
    </div>

    <!-- 商品详情 -->
    <section class="sub-page" id="detailPage">
      <div class="page-title">
        <button class="back-button" onclick="showCustomer()">‹ 返回</button>
        <span>商品详情</span>
        <span></span>
      </div>
      <div id="detailContent"></div>
    </section>

    <!-- 支付页面 -->
    <section class="sub-page" id="paymentPage">
      <div class="page-title">
        <button class="back-button" onclick="showCustomer()">‹ 返回</button>
        <span>订单支付</span>
        <span></span>
      </div>
      <div id="paymentContent"></div>
    </section>

    <!-- 订单页面 -->
    <section class="sub-page" id="ordersPage">
      <div class="page-title">
        <button class="back-button" onclick="showCustomer()">‹ 返回</button>
        <span>我的订单</span>
        <span></span>
      </div>

      <div class="admin-toolbar">
        <button id="unpaidTab" class="active" onclick="showOrders('unpaid')">未支付</button>
        <button id="paidTab" onclick="showOrders('paid')">已支付</button>
      </div>

      <div id="ordersContent"></div>
    </section>

    <!-- 后台页面 -->
    <section class="admin-page" id="adminPage">
      <div class="page-title">
        <button class="back-button" onclick="showCustomer()">‹ 客户页面</button>
        <span>后台管理</span>
        <span></span>
      </div>

      <div class="admin-toolbar">
        <button class="active" id="adminProductTab" onclick="showAdminTab('products')">
          商品管理
        </button>
        <button id="adminOrderTab" onclick="showAdminTab('orders')">
          已支付订单
        </button>
      </div>

      <div id="adminContent"></div>
    </section>

    <!-- 购物车 -->
    <button class="cart-button" id="cartButton" onclick="toggleCart()">
      🛒
      <span class="cart-count" id="cartCount">0</span>
    </button>

    <div class="cart-panel" id="cartPanel">
      <div class="cart-title">
        <span>购物车</span>
        <button class="clear-button" onclick="clearCart()">清空</button>
      </div>
      <div id="cartContent"></div>
    </div>

    <!-- 底部导航 -->
    <nav class="bottom-nav">
      <button class="nav-item active" onclick="showCustomer('product')">
        <span class="nav-icon">☕</span>
        商品
      </button>
      <button class="nav-item" onclick="showCustomer('mine')">
        <span class="nav-icon">♙</span>
        我的
      </button>
      <button class="nav-item" onclick="showAdmin()">
        <span class="nav-icon">⚙</span>
        后台
      </button>
    </nav>
  </div>

  <script>
    const defaultProducts = [
      {
        id: 1,
        category: "coffee",
        name: "美式咖啡",
        desc: "醇香浓郁，清爽回甘",
        price: 15,
        stock: 20,
        status: "on_sale",
        icon: "☕"
      },
      {
        id: 2,
        category: "coffee",
        name: "拿铁咖啡",
        desc: "咖啡与牛奶的经典搭配",
        price: 20,
        stock: 20,
        status: "on_sale",
        icon: "🥤"
      },
      {
        id: 3,
        category: "tea",
        name: "茉莉绿茶",
        desc: "清香淡雅，口感清爽",
        price: 12,
        stock: 20,
        status: "on_sale",
        icon: "🍵"
      },
      {
        id: 4,
        category: "tea",
        name: "水果茶",
        desc: "多种水果，酸甜可口",
        price: 18,
        stock: 20,
        status: "on_sale",
        icon: "🍹"
      },
      {
        id: 5,
        category: "alcohol",
        name: "精酿啤酒",
        desc: "麦芽香气浓郁，口感清爽",
        price: 18,
        stock: 20,
        status: "on_sale",
        icon: "🍺"
      },
      {
        id: 6,
        category: "alcohol",
        name: "果味鸡尾酒",
        desc: "果香浓郁，清爽微醺",
        price: 32,
        stock: 20,
        status: "on_sale",
        icon: "🍸"
      }
    ];

    let products = loadData("k_products", defaultProducts);
    let orders = loadData("k_orders", []);
    let cart = [];
    let currentCategory = "coffee";
    let currentDetailProduct = null;
    let currentPaymentOrder = null;
    let currentOrderTab = "unpaid";
    let adminTab = "products";

    function loadData(key, defaultValue) {
      const data = localStorage.getItem(key);
      return data ? JSON.parse(data) : defaultValue;
    }

    function saveData() {
      localStorage.setItem("k_products", JSON.stringify(products));
      localStorage.setItem("k_orders", JSON.stringify(orders));
      localStorage.setItem("k_update_time", Date.now().toString());
    }

    function money(value) {
      return Number(value).toFixed(2);
    }

    function getCategoryProducts() {
      return products.filter(item => {
        return item.category === currentCategory &&
          item.status !== "off_sale";
      });
    }

    function renderProducts() {
      const list = document.getElementById("productList");
      const data = getCategoryProducts();

      if (!data.length) {
        list.innerHTML = `<div class="empty">暂无商品</div>`;
        return;
      }

      list.innerHTML = data.map(product => {
        const soldOut = product.status === "sold_out" || product.stock <= 0;

        return `
          <div class="product-card" onclick="showDetail(${product.id})">
            <div class="product-image">${product.icon || "🥤"}</div>

            <div class="product-info">
              <div class="product-title">${product.name}</div>
              <div class="product-desc">${product.desc || ""}</div>

              <div class="product-bottom">
                <div class="price">${money(product.price)}</div>

                ${
                  soldOut
                    ? `<span class="sold-out">已售罄</span>`
                    : `
                      <button class="add-btn"
                        onclick="event.stopPropagation(); addToCart(${product.id})">
                        +
                      </button>
                    `
                }
              </div>
            </div>
          </div>
        `;
      }).join("");
    }

    function changeCategory(button, category) {
      currentCategory = category;

      document.querySelectorAll(".category-item").forEach(item => {
        item.classList.remove("active");
      });

      button.classList.add("active");
      renderProducts();
    }

    function addToCart(id) {
      const product = products.find(item => item.id === id);

      if (!product || product.status !== "on_sale" || product.stock <= 0) {
        alert("该商品已售罄或已下架");
        return;
      }

      const item = cart.find(item => item.id === id);

      if (item) {
        if (item.quantity >= product.stock) {
          alert("库存不足");
          return;
        }
        item.quantity++;
      } else {
        cart.push({
          id: product.id,
          name: product.name,
          price: product.price,
          quantity: 1
        });
      }

      updateCart();
    }

    function getCartTotal() {
      return cart.reduce((sum, item) => {
        return sum + item.price * item.quantity;
      }, 0);
    }

    function updateCart() {
      const count = cart.reduce((sum, item) => sum + item.quantity, 0);
      const countElement = document.getElementById("cartCount");
      const content = document.getElementById("cartContent");

      countElement.textContent = count;
      countElement.style.display = count ? "flex" : "none";

      if (!cart.length) {
        content.innerHTML = `<div class="empty">购物车还是空的</div>`;
        return;
      }

      content.innerHTML = `
        <div class="cart-items">
          ${cart.map(item => `
            <div class="cart-row">
              <span>${item.name} × ${item.quantity}</span>
              <span>¥${money(item.price * item.quantity)}</span>
            </div>
          `).join("")}
        </div>

        <div class="cart-total">
          <span>合计</span>
          <span>¥${money(getCartTotal())}</span>
        </div>

        <button class="pay-button" onclick="goPay()">去支付</button>
      `;
    }

    function toggleCart() {
      document.getElementById("cartPanel").classList.toggle("show");
    }

    function clearCart() {
      cart = [];
      updateCart();
    }

    function showDetail(id) {
      const product = products.find(item => item.id === id);
      if (!product) return;

      currentDetailProduct = product;

      hideAll();
      document.getElementById("detailPage").style.display = "block";

      document.getElementById("detailContent").innerHTML = `
        <div class="detail-image">${product.icon || "🥤"}</div>
        <div class="detail-title">${product.name}</div>
        <div class="detail-desc">${product.desc || ""}</div>
        <div class="detail-price">${money(product.price)}</div>

        ${
          product.status === "on_sale" && product.stock > 0
            ? `<button class="pay-button" onclick="addToCart(${product.id})">
                加入购物车
              </button>`
            : `<div class="sold-out">该商品已售罄</div>`
        }
      `;
    }

    function goPay() {
      if (!cart.length) {
        alert("购物车为空");
        return;
      }

      currentPaymentOrder = {
        id: "K" + Date.now(),
        items: cart.map(item => ({ ...item })),
        total: getCartTotal(),
        address: "",
        status: "unpaid",
        time: new Date().toLocaleString()
      };

      hideAll();
      document.getElementById("paymentPage").style.display = "block";
      renderPayment();
    }

    function renderPayment() {
      const order = currentPaymentOrder;

      document.getElementById("paymentContent").innerHTML = `
        <div class="payment-box">
          <div class="order-header">
            <span>订单编号：${order.id}</span>
            <span class="order-status">未支付</span>
          </div>

          <label>收货地址</label>
          <textarea id="addressInput"
            class="address-input"
            rows="3"
            placeholder="请输入收货地址"></textarea>

          ${order.items.map(item => `
            <div class="payment-row">
              <span>${item.name} × ${item.quantity}</span>
              <span>¥${money(item.price * item.quantity)}</span>
            </div>
          `).join("")}

          <div class="payment-total">
            <span>应付金额</span>
            <span>¥${money(order.total)}</span>
          </div>

          <button class="pay-button" onclick="confirmPay()">
            模拟支付 ¥${money(order.total)}
          </button>
        </div>
      `;
    }

    function confirmPay() {
      const address = document.getElementById("addressInput").value.trim();

      if (!address) {
        alert("请填写收货地址");
        return;
      }

      for (const item of currentPaymentOrder.items) {
        const product = products.find(product => product.id === item.id);

        if (!product || product.status !== "on_sale" ||
            product.stock < item.quantity) {
          alert(`${item.name}库存不足，请重新下单`);
          return;
        }
      }

      currentPaymentOrder.address = address;
      currentPaymentOrder.status = "paid";
      currentPaymentOrder.paidAt = new Date().toLocaleString();

      currentPaymentOrder.items.forEach(item => {
        const product = products.find(product => product.id === item.id);
        product.stock -= item.quantity;

        if (product.stock <= 0) {
          product.stock = 0;
          product.status = "sold_out";
        }
      });

      orders.unshift(currentPaymentOrder);
      cart = [];
      currentPaymentOrder = null;
      saveData();
      updateCart();
      alert("支付成功，订单已保存");
      showCustomer("mine");
    }

    function showOrders(tab = "unpaid") {
      hideAll();
      document.getElementById("ordersPage").style.display = "block";
      currentOrderTab = tab;

      document.getElementById("unpaidTab").classList.toggle(
        "active", tab === "unpaid"
      );
      document.getElementById("paidTab").classList.toggle(
        "active", tab === "paid"
      );

      const data = orders.filter(order => order.status === tab);
      const content = document.getElementById("ordersContent");

      if (!data.length) {
        content.innerHTML = `<div class="empty">暂无订单</div>`;
        return;
      }

      content.innerHTML = data.map(order => `
        <div class="order-card">
          <div class="order-header">
            <span>订单号：${order.id}</span>
            <span class="order-status ${tab === "paid" ? "paid" : ""}">
              ${tab === "paid" ? "已支付" : "未支付"}
            </span>
          </div>

          ${order.items.map(item => `
            <div class="order-row">
              <span>${item.name} × ${item.quantity}</span>
              <span>¥${money(item.price * item.quantity)}</span>
            </div>
          `).join("")}

          <div class="order-row">
            <span>收货地址</span>
            <span>${order.address}</span>
          </div>

          <div class="order-row">
            <strong>合计</strong>
            <strong>¥${money(order.total)}</strong>
          </div>
        </div>
      `).join("");
    }

    function showCustomer(page = "product") {
      hideAll();

      document.getElementById("customerView").style.display = "block";
      document.getElementById("cartButton").style.display = "block";

      document.querySelectorAll(".nav-item").forEach(item => {
        item.classList.remove("active");
      });

      if (page === "mine") {
        document.getElementById("productPage").style.display = "none";
        document.getElementById("minePage").style.display = "block";
        document.querySelector(".nav-item:nth-child(2)").classList.add("active");
        document.getElementById("cartButton").style.display = "none";
      } else {
        document.getElementById("productPage").style.display = "block";
        document.querySelector(".nav-item:first-child").classList.add("active");
      }
    }

    function showAdmin() {
      hideAll();
      document.getElementById("adminPage").style.display = "block";
      document.getElementById("cartButton").style.display = "none";
      renderAdmin();
    }

    function hideAll() {
      document.getElementById("customerView").style.display = "none";
      document.getElementById("detailPage").style.display = "none";
      document.getElementById("paymentPage").style.display = "none";
      document.getElementById("ordersPage").style.display = "none";
      document.getElementById("adminPage").style.display = "none";
      document.getElementById("cartPanel").classList.remove("show");
    }

    function showAdminTab(tab) {
      adminTab = tab;

      document.getElementById("adminProductTab").classList.toggle(
        "active", tab === "products"
      );
      document.getElementById("adminOrderTab").classList.toggle(
        "active", tab === "orders"
      );

      renderAdmin();
    }

    function renderAdmin() {
      const content = document.getElementById("adminContent");

      if (adminTab === "orders") {
        const paidOrders = orders.filter(order => order.status === "paid");

        content.innerHTML = `
          ${
            paidOrders.length
              ? paidOrders.map(order => `
                <div class="admin-card">
                  <h3>订单：${order.id}</h3>
                  <div class="admin-line">
                    <span>支付时间</span>
                    <span>${order.paidAt}</span>
                  </div>
                  <div class="admin-line">
                    <span>收货地址</span>
                    <span>${order.address}</span>
                  </div>
                  ${order.items.map(item => `
                    <div class="admin-line">
                      <span>${item.name} × ${item.quantity}</span>
                      <span>¥${money(item.price * item.quantity)}</span>
                    </div>
                  `).join("")}
                  <div class="admin-line">
                    <strong>订单金额</strong>
                    <strong>¥${money(order.total)}</strong>
                  </div>
                </div>
              `).join("")
              : `<div class="empty">暂无已支付订单</div>`
          }
        `;
        return;
      }

      content.innerHTML = `
        <form class="admin-form" onsubmit="addProduct(event)">
          <h2>新增商品</h2>

          <input class="admin-input" id="newName"
            placeholder="商品名称" required>

          <div class="form-row">
            <select class="admin-select" id="newCategory">
              <option value="coffee">咖啡</option>
              <option value="tea">茶</option>
              <option value="alcohol">酒</option>
            </select>

            <input class="admin-input" id="newPrice"
              type="number" step="0.01" placeholder="价格" required>
          </div>

          <div class="form-row">
            <input class="admin-input" id="newStock"
              type="number" placeholder="库存" required>

            <input class="admin-input" id="newIcon"
              placeholder="图标，如 ☕">
          </div>

          <input class="admin-input" id="newDesc"
            placeholder="商品描述">

          <button class="save-button">新增商品</button>
        </form>

        ${products.map(product => `
          <div class="admin-card">
            <h3>${product.icon || "🥤"} ${product.name}</h3>

            <div class="admin-line">
              <span>分类</span>
              <span>${product.category}</span>
            </div>

            <div class="admin-line">
              <span>价格</span>
              <span>¥${money(product.price)}</span>
            </div>

            <div class="admin-line">
              <span>库存</span>
              <span>${product.stock}</span>
            </div>

            <div class="admin-line">
              <span>状态</span>
              <span class="status-${product.status}">
                ${getStatusText(product.status)}
              </span>
            </div>

            <div class="admin-actions">
              <button onclick="editPrice(${product.id})">
                修改价格
              </button>

              <button onclick="editStock(${product.id})">
                修改库存
              </button>

              ${
                product.status === "off_sale"
                  ? `<button class="dark" onclick="setStatus(${product.id}, 'on_sale')">
                      上架
                    </button>`
                  : `<button onclick="setStatus(${product.id}, 'off_sale')">
                      下架
                    </button>`
              }

              ${
                product.status === "sold_out"
                  ? `<button class="dark" onclick="setStatus(${product.id}, 'on_sale')">
                      恢复销售
                    </button>`
                  : `<button onclick="setStatus(${product.id}, 'sold_out')">
                      标记售罄
                    </button>`
              }
            </div>
          </div>
        `).join("")}
      `;
    }

    function getStatusText(status) {
      return {
        on_sale: "在售",
        sold_out: "已售罄",
        off_sale: "已下架"
      }[status] || status;
    }

    function addProduct(event) {
      event.preventDefault();

      const product = {
        id: Date.now(),
        name: document.getElementById("newName").value.trim(),
        category: document.getElementById("newCategory").value,
        price: Number(document.getElementById("newPrice").value),
        stock: Number(document.getElementById("newStock").value),
        icon: document.getElementById("newIcon").value || "🥤",
        desc: document.getElementById("newDesc").value.trim(),
        status: "on_sale"
      };

      if (product.stock <= 0) {
        product.status = "sold_out";
      }

      products.unshift(product);
      saveData();
      renderProducts();
      renderAdmin();
      alert("商品添加成功");
    }

    function editPrice(id) {
      const product = products.find(item => item.id === id);
      const value = prompt("请输入新价格", product.price);

      if (value === null) return;

      const price = Number(value);

      if (price < 0 || Number.isNaN(price)) {
        alert("请输入正确的价格");
        return;
      }

      product.price = price;
      saveData();
      renderProducts();
      renderAdmin();
    }

    function editStock(id) {
      const product = products.find(item => item.id === id);
      const value = prompt("请输入库存数量", product.stock);

      if (value === null) return;

      const stock = Number(value);

      if (stock < 0 || Number.isNaN(stock)) {
        alert("请输入正确的库存");
        return;
      }

      product.stock = stock;

      if (stock <= 0) {
        product.status = "sold_out";
      } else if (product.status === "sold_out") {
        product.status = "on_sale";
      }

      saveData();
      renderProducts();
      renderAdmin();
    }

    function setStatus(id, status) {
      const product = products.find(item => item.id === id);

      if (status === "on_sale" && product.stock <= 0) {
        alert("库存为0，不能上架，请先修改库存");
        return;
      }

      product.status = status;
      saveData();
      renderProducts();
      renderAdmin();
    }

    // 监听其他标签页的实时更新
    window.addEventListener("storage", event => {
      if (event.key === "k_update_time") {
        products = loadData("k_products", defaultProducts);
        orders = loadData("k_orders", []);

        renderProducts();
        updateCart();

        if (document.getElementById("adminPage").style.display === "block") {
          renderAdmin();
        }
      }
    });

    renderProducts();
    updateCart();
  </script>
</body>
</html>
