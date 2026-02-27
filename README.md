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
body {
    font-family: Arial;
    max-width: 700px;
    margin: 40px auto;
    background: #f4f6f8;
}

.card {
    background: white;
    padding: 20px;
    margin-top: 20px;
    border-radius: 10px;
}

input, select, button {
    width: 100%;
    padding: 10px;
    margin-top: 8px;
}

table {
    width: 100%;
    margin-top: 10px;
    border-collapse: collapse;
}

th, td {
    border-bottom: 1px solid #ddd;
    padding: 8px;
}

.income { color: green; }
.expense { color: red; }
const form = document.getElementById("form");
const list = document.getElementById("list");
const balanceEl = document.getElementById("balance");

let transactions = [];

form.addEventListener("submit", e => {
    e.preventDefault();

    const t = {
        type: type.value,
        amount: Number(amount.value),
        category: category.value,
        date: date.value,
        note: note.value
    };

    transactions.push(t);
    render();
    form.reset();
});

function render() {
    list.innerHTML = "";
    let balance = 0;

    transactions.forEach(t => {
        const row = document.createElement("tr");

        row.innerHTML = `
            <td class="${t.type}">
                ${t.type === "income" ? "Gelir" : "Gider"}
            </td>
            <td>${t.amount} ₺</td>
            <td>${t.category}</td>
            <td>${t.date}</td>
            <td>${t.note}</td>
        `;

        list.appendChild(row);

        if (t.type === "income") balance += t.amount;
        else balance -= t.amount;
    });

    balanceEl.textContent = balance;
}
