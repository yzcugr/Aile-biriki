# Aile-biriki
Didem-Uğur Aile Birim Takip 
index.html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Birikim Takip</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<h1>Birikim Takip</h1>

<div class="card">
    <h2>Bakiye: <span id="balance">0</span> ₺</h2>
</div>

<div class="card">
    <h3>Yeni Kayıt</h3>

    <form id="form">
        <select id="type">
            <option value="income">Gelir</option>
            <option value="expense">Gider</option>
        </select>

        <input type="number" id="amount" placeholder="Tutar" required>
        <input type="text" id="category" placeholder="Kategori">
        <input type="date" id="date" required>
        <input type="text" id="note" placeholder="Not">

        <button>Ekle</button>
    </form>
</div>

<div class="card">
    <h3>Kayıtlar</h3>
    <table>
        <thead>
            <tr>
                <th>Tür</th>
                <th>Tutar</th>
                <th>Kategori</th>
                <th>Tarih</th>
                <th>Not</th>
            </tr>
        </thead>
        <tbody id="list"></tbody>
    </table>
</div>

<script src="app.js"></script>
</body>
</html>
