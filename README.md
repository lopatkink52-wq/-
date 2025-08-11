<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Донат на танк</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #222;
    color: #fff;
    margin: 0;
    padding: 20px;
  }
  h1 {
    text-align: center;
  }
  .container {
    max-width: 600px;
    margin: auto;
    background-color: #333;
    padding: 20px;
    border-radius: 10px;
  }
  label {
    display: block;
    margin-top: 15px;
    font-weight: bold;
  }
  select, input[type="number"] {
    width: 100%;
    padding: 8px;
    margin-top: 8px;
    border-radius: 5px;
    border: none;
  }
  .pay-button {
    margin-top: 20px;
    text-align: center;
  }
</style>
</head>
<body>

<h1>Донат на конкретный танк</h1>

<div class="container">
<form id="donateForm" action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_blank">
  
  <!-- Введите свой PayPal ID или email -->
  <input type="hidden" name="business" value="ВАШ_EMAIL_PAYPAL@example.com" />

  <!-- Тип платежа -->
  <input type="hidden" name="cmd" value="_donations" />

  <!-- Название проекта -->
  <input type="hidden" name="item_name" id="item_name" value="" />

  <!-- Валюта -->
  <input type="hidden" name="currency_code" value="USD" />

  <!-- Сумма -->
  <label for="amount">Сумма доната (USD):</label>
  <input type="number" id="amount" name="amount" min="1" step="0.01" required />

  <!-- Выбор танка -->
  <label for="tank">Выберите танк:</label>
  <select id="tank" name="custom">
    <option value="">--Выберите танк--</option>
    <option value="Т-34">Т-34</option>
    <option value="ИС-7">ИС-7</option>
    <option value="МХ30">МХ30</option>
    <option value="Объект907">Объект907</option>
    <!-- Добавьте свои танки сюда -->
  </select>

  
  <!-- Кнопка оплаты -->
  <div class="pay-button">
    <button type="submit">Оплатить через PayPal</button>
  </div>
</form>
</div>

<script>
// Обновляем item_name перед отправкой формы
document.getElementById('donateForm').addEventListener('submit', function(e) {
  
  const tankSelect = document.getElementById('tank');
  const itemNameInput = document.getElementById('item_name');
  
  if (tankSelect.value === "") {
    alert("Пожалуйста, выберите танк");
    e.preventDefault();
    return false;
  }
  
  itemNameInput.value = "Донат на танк: " + tankSelect.value;

});
</script>

</body>
</html>
