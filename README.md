<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ร้านค้าสินค้า</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      background-color: #304674;
      font-family: sans-serif;
      color: white;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(32%, 1fr));
      gap: 10px;
      padding: 15px;
    }
    .product {
      background: #3b537f;
      border-radius: 8px;
      padding: 10px;
      text-align: center;
    }
    .product img {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 6px;
    }
    .product h3 {
      font-size: 16px;
      margin: 10px 0 5px;
    }
    .product p {
      margin: 5px 0;
      font-size: 14px;
    }
    .btn {
      background: #00bb66;
      color: white;
      padding: 6px 12px;
      border: none;
      border-radius: 5px;
      text-decoration: none;
      display: inline-block;
      margin-top: 8px;
    }
  </style>
</head>
<body>

  <div class="container" id="product-list">Loading...</div>

  <script>
    const API_URL = "( https://script.google.com/macros/s/AKfycbybewxJ6t17rGGFlHb50uEBIR1CGpNdgOeULZ0-__7EalxcPURvewqKaJeWGrLfnGVT/exec )"; // ใส่ลิงก์ Web App ของคุณที่นี่

    fetch(API_URL)
      .then(res => res.json())
      .then(data => {
        const container = document.getElementById("product-list");
        container.innerHTML = "";
        data.forEach(item => {
          container.innerHTML += `
            <div class="product">
              <img src="${item.Picture}" alt="${item.Name}">
              <h3>${item.Name}</h3>
              <p>ราคา: ${item.Price} ກີບ</p>
              <a class="btn" href="https://wa.me/+8562099872754?text=ສັ່ງຊື້: ${encodeURIComponent(item.Name)} - ${encodeURIComponent(item.Price)} ກີບ" target="_blank">สั่งซื้อ</a>
            </div>
          `;
        });
      })
      .catch(err => {
        document.getElementById("product-list").innerHTML = "เกิดข้อผิดพลาดในการโหลดข้อมูล";
        console.error(err);
      });
  </script>

</body>
</html>
