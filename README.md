# Playmore<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Stock Analysis Tool</title>
  <style>
    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #f5f7fa;
      margin: 0;
      padding: 0;
      color: #222;
    }
    .container {
      max-width: 900px;
      margin: 40px auto;
      background: #ffffff;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    }
    h1 {
      text-align: center;
      margin-bottom: 20px;
    }
    h2 {
      margin-top: 30px;
      font-size: 20px;
      border-bottom: 2px solid #eee;
      padding-bottom: 5px;
    }
    label {
      display: block;
      margin-top: 12px;
      font-weight: bold;
    }
    input {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border-radius: 6px;
      border: 1px solid #ccc;
    }
    button {
      margin-top: 20px;
      padding: 12px 20px;
      background: #2563eb;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background: #1e40af;
    }
    ul {
      margin-top: 15px;
      line-height: 1.8;
    }
    .result {
      background: #f1f5f9;
      padding: 20px;
      border-radius: 8px;
      margin-top: 20px;
    }
    .footer {
      text-align: center;
      margin-top: 30px;
      font-size: 14px;
      color: #666;
    }
  </style>
</head>
<body>  <div class="container">
    <h1>📈 Stock Analysis Dashboard</h1><h2>Stock Input</h2>
<label>Current Share Price (₹)</label>
<input type="number" id="price" />

<label>Earnings Per Share (EPS)</label>
<input type="number" id="eps" />

<label>Expected Target Price (₹)</label>
<input type="number" id="target" />

<label>Number of Shares</label>
<input type="number" id="shares" />

<button onclick="analyzeStock()">Analyze Stock</button>

<div class="result" id="result" style="display:none;">
  <h2>Analysis Result</h2>
  <ul id="output"></ul>
</div>

<div class="footer">
  Professional Stock Analysis Tool • Clean • Simple • Fast
</div>

  </div>  <script>
    function analyzeStock() {
      const price = parseFloat(document.getElementById('price').value);
      const eps = parseFloat(document.getElementById('eps').value);
      const target = parseFloat(document.getElementById('target').value);
      const shares = parseInt(document.getElementById('shares').value);

      if (!price || !eps || !target || !shares) {
        alert('Please fill all fields');
        return;
      }

      const peRatio = (price / eps).toFixed(2);
      const profitPerShare = (target - price).toFixed(2);
      const totalProfit = (profitPerShare * shares).toFixed(2);
      const expectedReturn = (((target - price) / price) * 100).toFixed(2);

      document.getElementById('result').style.display = 'block';
      document.getElementById('output').innerHTML = `
        <li><strong>P/E Ratio:</strong> ${peRatio}</li>
        <li><strong>Current Price:</strong> ₹${price}</li>
        <li><strong>Target Price:</strong> ₹${target}</li>
        <li><strong>Profit per Share:</strong> ₹${profitPerShare}</li>
        <li><strong>Total Profit:</strong> ₹${totalProfit}</li>
        <li><strong>Expected Return:</strong> ${expectedReturn}%</li>
        <li><strong>Risk Level:</strong> ${peRatio > 25 ? 'High' : 'Moderate / Low'}</li>
      `;
    }
  </script></body>
</html>
