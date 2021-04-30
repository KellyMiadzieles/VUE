<template>
  <div class="home">
    <h1>Bank</h1>

    <h2>Create Account</h2>
    <input v-model="firstName" placeholder="Enter your first name"/>
    <input v-model="lastName" placeholder="Enter your last name"/>
    <input v-model="accountNum" placeholder="Enter your account number"/>
    <input v-model="balance1" placeholder="Enter the amount"/>
    <br>
    <br>
    <button v-on:click="createAccountButton()">Create Account</button>
    {{ account }}

    <h2>Balance</h2>
    <input v-model="accountNr" placeholder="Enter account number"/>
    <br>
    <br>
    <button v-on:click="getBalanceButton()">Get Balance</button>
    {{ balance }}

    <h2>Deposit</h2>
    <input v-model="accountNr1" placeholder="Enter account number"/>
    <input v-model="depositAmount" placeholder="Enter the amount"/>
    <br>
    <br>
    <button v-on:click="getDepostiButton()">Get Deposit</button>
    {{ deposit }}

    <h2>Withdraw Money</h2>
    <input v-model="withdrawAccountNr" placeholder="Enter account number"/>
    <input v-model="withdrawAmount" placeholder="Enter the amount"/>
    <br>
    <br>
    <button v-on:click="withdrawMoneyButton()">Withdraw money</button>
    {{ withdraw }}

    <h2>Transfer Money</h2>
    <input v-model="fromAccountNr" placeholder="Enter account number"/>
    <input v-model="toAccountNr" placeholder="Enter account number"/>
    <input v-model="transferAmount" placeholder="Enter the amount"/>
    <br>
    <br>
    <button v-on:click="transferMoneyButton()">Transfer money</button>
    {{ transfer }}
    <br>
    <br>
    <h1>List</h1>
    <table>
      <tr>
        <th>Account Number</th>
        <th>Balance</th>
      </tr>
      <tr v-for="account in accounts">
        <td>{{ account.accountNumber }}</td>
        <td>{{ account.balance }}</td>
        <td>{{ account }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      'firstName': '',
      'lastName': '',
      'accountNum': '',
      'balance1': '',
      'account': '',
      'balance': '',
      'accountNr': '',
      'deposit': '',
      'accountNr1': '',
      'depositAmount': '',
      'withdraw': '',
      'withdrawAmount': '',
      'withdrawAccountNr': '',
      'fromAccountNr': '',
      'toAccountNr': '',
      'transferAmount': '',
      'transfer': '',
      'accounts': []
    }
  },
  methods: {
    'createAccountButton': function () {
      this.$http.post('/api/createAccount/' + this.firstName + '/' + this.lastName + '/' + this.accountNum + '/' + this.balance1)
          .then(function (response) {
            console.log(response);
            this.account = response.data
          });
    },
    'getBalanceButton': function () {
      this.$http.get('/api/balance/' + this.accountNr)
          .then(response => {
            console.log(response);
            this.balance = response.data
          });
    },
    'getDepostiButton': function () {
      this.$http.put('/api/deposit/' + this.accountNr1 + '/' + this.depositAmount)
          .then(response => {
            console.log(response);
            this.deposit = response.data
          });
    },
    'withdrawMoneyButton': function () {
      this.$http.put('/api/withdrawMoney/' + this.withdrawAccountNr + '/' + this.withdrawAmount)
          .then(response => {
            console.log(response);
            this.withdraw = response.data
          });
    },
    'transferMoneyButton': function () {
      this.$http.put('/api/transferMoney/' + this.fromAccountNr + '/' + this.transferAmount + '/' + this.toAccountNr)
          .then(response => {
            console.log(response);
            this.transfer = response.data
          });
    },
  },
  mounted() { //et teha list
    this.$http.get("/api/account")
        .then(response => this.accounts = response.data);
  }
}
</script>
