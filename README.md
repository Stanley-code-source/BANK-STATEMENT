# BANK-STATEMENT
A simple &lt;html> file for a Bank Statement
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Bank Statement | Sample Account</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(145deg, #e9eef3 0%, #dce3ec 100%);
      font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, 'Roboto', sans-serif;
      padding: 2rem 1rem;
      min-height: 100vh;
    }

    /* main statement card */
    .statement-container {
      max-width: 1300px;
      margin: 0 auto;
      background-color: #ffffff;
      border-radius: 32px;
      box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.2), 0 1px 3px rgba(0, 0, 0, 0.05);
      overflow: hidden;
      transition: all 0.2s ease;
    }

    /* header area */
    .bank-header {
      background: #0a2b3e;
      padding: 1.8rem 2rem;
      color: white;
    }

    .bank-name {
      font-size: 1.8rem;
      font-weight: 700;
      letter-spacing: -0.3px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .bank-name span {
      background: #f5b042;
      font-size: 0.9rem;
      font-weight: 600;
      padding: 2px 12px;
      border-radius: 40px;
      color: #0a2b3e;
      margin-left: 12px;
    }

    .statement-meta {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: flex-end;
      margin-top: 1.5rem;
      gap: 1rem;
    }

    .account-info p {
      margin: 4px 0;
      font-size: 0.9rem;
      opacity: 0.85;
    }

    .account-info strong {
      font-weight: 600;
      opacity: 1;
      letter-spacing: 0.3px;
    }

    .period {
      background: rgba(255, 255, 255, 0.15);
      padding: 8px 16px;
      border-radius: 60px;
      font-size: 0.85rem;
      font-weight: 500;
      backdrop-filter: blur(2px);
    }

    /* summary cards */
    .summary-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.2rem;
      padding: 1.8rem 2rem;
      background: #fbfdfe;
      border-bottom: 1px solid #e6edf4;
    }

    .summary-card {
      flex: 1;
      min-width: 160px;
      background: white;
      border-radius: 28px;
      padding: 1.2rem 1.5rem;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.02), 0 1px 2px rgba(0, 0, 0, 0.05);
      border: 1px solid #eef3fc;
      transition: transform 0.2s;
    }

    .summary-card:hover {
      transform: translateY(-2px);
      border-color: #cddfed;
    }

    .summary-label {
      font-size: 0.8rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: 600;
      color: #5b6f82;
      margin-bottom: 8px;
    }

    .summary-amount {
      font-size: 1.9rem;
      font-weight: 700;
      color: #1a2c3e;
    }

    .credit-amount {
      color: #1f8a4c;
    }

    .debit-amount {
      color: #c2412c;
    }

    .balance-amount {
      color: #0f3b5c;
    }

    /* transaction table */
    .transactions-section {
      padding: 0 2rem 2rem 2rem;
    }

    .section-title {
      font-size: 1.2rem;
      font-weight: 600;
      margin: 1.5rem 0 1rem 0;
      color: #1f3b4c;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .section-title:before {
      content: '';
      width: 5px;
      height: 20px;
      background: #f5b042;
      border-radius: 6px;
    }

    .table-wrapper {
      overflow-x: auto;
      border-radius: 24px;
      border: 1px solid #eef2f8;
      background: white;
    }

    .statement-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.9rem;
      min-width: 620px;
    }

    .statement-table th {
      text-align: left;
      padding: 1rem 1rem;
      background-color: #f8fafd;
      font-weight: 600;
      color: #2c4c6c;
      border-bottom: 1px solid #e2e9f2;
      font-size: 0.85rem;
    }

    .statement-table td {
      padding: 1rem 1rem;
      border-bottom: 1px solid #f0f4fa;
      color: #1f2f3c;
    }

    .statement-table tr:last-child td {
      border-bottom: none;
    }

    .statement-table tr:hover td {
      background-color: #fafcff;
    }

    .debit-text {
      color: #c2412c;
      font-weight: 600;
    }

    .credit-text {
      color: #1f8a4c;
      font-weight: 600;
    }

    .balance-cell {
      font-weight: 500;
      font-family: monospace;
      font-size: 0.9rem;
    }

    .transaction-desc {
      font-weight: 500;
    }

    .badge-status {
      background: #eef2fa;
      padding: 4px 8px;
      border-radius: 30px;
      font-size: 0.7rem;
      font-weight: 500;
      color: #2c5a7a;
      display: inline-block;
    }

    .footer-note {
      margin-top: 1.8rem;
      text-align: center;
      font-size: 0.75rem;
      color: #7c8b9c;
      border-top: 1px solid #eef3fc;
      padding-top: 1.5rem;
    }

    @media (max-width: 700px) {
      .bank-header {
        padding: 1.2rem 1.2rem;
      }
      .summary-grid {
        padding: 1.2rem;
        gap: 0.8rem;
      }
      .summary-card {
        padding: 0.8rem 1rem;
      }
      .summary-amount {
        font-size: 1.4rem;
      }
      .transactions-section {
        padding: 0 1.2rem 1.5rem 1.2rem;
      }
      .statement-table th, .statement-table td {
        padding: 0.75rem 0.8rem;
      }
    }
  </style>
</head>
<body>
<div class="statement-container">
  <div class="bank-header">
    <div class="bank-name">
      🌿 NEXUS BANK <span>Premium</span>
    </div>
    <div class="statement-meta">
      <div class="account-info">
        <p><strong>Account holder:</strong> Evelyn M. Carter</p>
        <p><strong>Account number:</strong> •••• •••• 3402 8719</p>
        <p><strong>Statement type:</strong> Monthly checking account</p>
      </div>
      <div class="period">
        📅 Statement period: March 1, 2025 – March 31, 2025
      </div>
    </div>
  </div>

  <div class="summary-grid">
    <div class="summary-card">
      <div class="summary-label">Current Balance</div>
      <div class="summary-amount balance-amount">$5,843.72</div>
    </div>
    <div class="summary-card">
      <div class="summary-label">Total Credits (In)</div>
      <div class="summary-amount credit-amount">+$8,250.00</div>
    </div>
    <div class="summary-card">
      <div class="summary-label">Total Debits (Out)</div>
      <div class="summary-amount debit-amount">-$7,606.28</div>
    </div>
  </div>

  <div class="transactions-section">
    <div class="section-title">Transaction history</div>
    <div class="table-wrapper">
      <table class="statement-table">
        <thead>
          <tr>
            <th>Date</th>
            <th>Description</th>
            <th>Withdrawal (Debit)</th>
            <th>Deposit (Credit)</th>
            <th>Running Balance</th>
          </tr>
        </thead>
        <tbody>
          <!-- Opening balance row (starting point) -->
          <tr>
            <td>Mar 01, 2025</td>
            <td><span class="transaction-desc">Beginning balance</span></td>
            <td>—</td>
            <td>—</td>
            <td class="balance-cell">$5,200.00</td>
          </tr>
          <tr>
            <td>Mar 03, 2025</td>
            <td><span class="transaction-desc">💼 Salary deposit - Nexus Corp</span> <span class="badge-status">Direct deposit</span></td>
            <td>—</td>
            <td class="credit-text">+$4,250.00</td>
            <td class="balance-cell">$9,450.00</td>
          </tr>
          <tr>
            <td>Mar 05, 2025</td>
            <td><span class="transaction-desc">🏢 Rent payment - Metro Properties</span></td>
            <td class="debit-text">-$1,850.00</td>
            <td>—</td>
            <td class="balance-cell">$7,600.00</td>
          </tr>
          <tr>
            <td>Mar 08, 2025</td>
            <td><span class="transaction-desc">🛒 Whole Foods Market</span></td>
            <td class="debit-text">-$124.38</td>
            <td>—</td>
            <td class="balance-cell">$7,475.62</td>
          </tr>
          <tr>
            <td>Mar 12, 2025</td>
            <td><span class="transaction-desc">⚡ Utilities - Power & Water</span></td>
            <td class="debit-text">-$189.22</td>
            <td>—</td>
            <td class="balance-cell">$7,286.40</td>
          </tr>
          <tr>
            <td>Mar 15, 2025</td>
            <td><span class="transaction-desc">🎧 Spotify / Netflix subscription</span></td>
            <td class="debit-text">-$28.99</td>
            <td>—</td>
            <td class="balance-cell">$7,257.41</td>
          </tr>
          <tr>
            <td>Mar 18, 2025</td>
            <td><span class="transaction-desc">📱 Phone bill - Verizon</span></td>
            <td class="debit-text">-$76.45</td>
            <td>—</td>
            <td class="balance-cell">$7,180.96</td>
          </tr>
          <tr>
            <td>Mar 21, 2025</td>
            <td><span class="transaction-desc">💰 Freelance payment (Invoice #204)</span> <span class="badge-status">external transfer</span></td>
            <td>—</td>
            <td class="credit-text">+$1,200.00</td>
            <td class="balance-cell">$8,380.96</td>
          </tr>
          <tr>
            <td>Mar 23, 2025</td>
            <td><span class="transaction-desc">🍽️ Dinner & Cafe - Amex payment</span></td>
            <td class="debit-text">-$97.50</td>
            <td>—</td>
            <td class="balance-cell">$8,283.46</td>
          </tr>
          <tr>
            <td>Mar 25, 2025</td>
            <td><span class="transaction-desc">🚗 Car insurance premium</span></td>
            <td class="debit-text">-$476.00</td>
            <td>—</td>
            <td class="balance-cell">$7,807.46</td>
          </tr>
          <tr>
            <td>Mar 27, 2025</td>
            <td><span class="transaction-desc">🏦 Transfer to savings account</span></td>
            <td class="debit-text">-$800.00</td>
            <td>—</td>
            <td class="balance-cell">$7,007.46</td>
          </tr>
          <tr>
            <td>Mar 28, 2025</td>
            <td><span class="transaction-desc">📦 Amazon purchase - home goods</span></td>
            <td class="debit-text">-$63.74</td>
            <td>—</td>
            <td class="balance-cell">$6,943.72</td>
          </tr>
          <tr>
            <td>Mar 30, 2025</td>
            <td><span class="transaction-desc">✨ Interest earned (monthly)</span> <span class="badge-status">credit</span></td>
            <td>—</td>
            <td class="credit-text">+$2,800.00</td>
            <td class="balance-cell">$9,743.72</td>
          </tr>
          <tr style="background: #fefaf5;">
            <td><strong>Mar 31, 2025</strong></td>
            <td><strong>🏦 Monthly fee & service charge</strong></td>
            <td class="debit-text"><strong>-$12.00</strong></td>
            <td>—</td>
            <td class="balance-cell"><strong>$5,843.72</strong></td>
          </tr>
          <!-- Note: the last debit reduces balance to final amount -->
        </tbody>
      </table>
    </div>

    <div class="footer-note">
      * This is a sample statement generated for demonstration. All transactions are simulated.<br>
      For any discrepancies, please contact customer support within 60 days.
    </div>
  </div>
</div>
</body>
</html>
