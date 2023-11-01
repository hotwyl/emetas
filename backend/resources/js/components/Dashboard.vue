<template>
    <div class="dashboard">
      <div class="header">
        <h1>Dashboard de Finanças</h1>
      </div>
      <div class="overview">
        <div class="balance">
          <h2>Saldo Total</h2>
          <p>{{ currencyFormat(totalBalance) }}</p>
        </div>
        <div class="income">
          <h2>Renda Total</h2>
          <p>{{ currencyFormat(totalIncome) }}</p>
        </div>
        <div class="expenses">
          <h2>Despesas Totais</h2>
          <p>{{ currencyFormat(totalExpenses) }}</p>
        </div>
      </div>
      <div class="transactions">
        <h2>Transações Recentes</h2>
        <table>
          <thead>
            <tr>
              <th>Data</th>
              <th>Descrição</th>
              <th>Tipo</th>
              <th>Valor</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(transaction, index) in recentTransactions" :key="index">
              <td>{{ transaction.date }}</td>
              <td>{{ transaction.description }}</td>
              <td>{{ transaction.type }}</td>
              <td>{{ currencyFormat(transaction.amount) }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        transactions: [
          { date: '2023-10-28', description: 'Compra Online', type: 'Despesa', amount: -50.0 },
          { date: '2023-10-25', description: 'Salário', type: 'Renda', amount: 2500.0 },
          // Adicione mais transações aqui
        ],
      };
    },
    computed: {
      totalBalance() {
        return this.transactions.reduce((acc, transaction) => acc + transaction.amount, 0);
      },
      totalIncome() {
        return this.transactions
          .filter((transaction) => transaction.amount > 0)
          .reduce((acc, transaction) => acc + transaction.amount, 0);
      },
      totalExpenses() {
        return this.transactions
          .filter((transaction) => transaction.amount < 0)
          .reduce((acc, transaction) => acc + transaction.amount, 0);
      },
      recentTransactions() {
        return this.transactions.slice(0, 5);
      },
    },
    methods: {
      currencyFormat(value) {
        // Implemente a lógica de formatação de moeda de acordo com a sua preferência
        return new Intl.NumberFormat('pt-BR', {
          style: 'currency',
          currency: 'BRL',
        }).format(value);
      },
    },
  };
  </script>
  
  <style>
  .dashboard {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .header {
    text-align: center;
  }
  
  .overview {
    display: flex;
    justify-content: space-around;
    margin: 40px 0;
  }
  
  .balance,
  .income,
  .expenses {
    text-align: center;
  }
  
  .transactions {
    margin-top: 40px;
  }
  
  table {
    width: 100%;
    border-collapse: collapse;
  }
  
  th,
  td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
  }
  
  th {
    background-color: #f2f2f2;
  }
  </style>
  