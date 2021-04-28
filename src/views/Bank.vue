<template>
  <div class="home">
    <h1>Bank</h1>

    <h2>Create Account</h2>
    <input v-model="firstName" placeholder="Enter your first name"/>
    <input v-model="lastName" placeholder="Enter your last name"/>
    <input v-model="accountNum" placeholder="Enter your account number"/>
    <input v-model="balance1" placeholder="Enter your balance"/>
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
    <input v-model="depositAmount" placeholder="Enter the amount you want to deposit"/>
    <br>
    <br>
    <button v-on:click="getDepostiButton()">Get Deposit</button>
    {{ deposit }}

    <h2>Withdraw Money</h2>
    <input v-model="withdrawAccountNr" placeholder="Enter account number"/>
    <input v-model="withdrawAmount" placeholder="Enter the amount you want to withdraw"/>
    <br>
    <br>
    <button v-on:click="withdrawMoneyButton()">Withdraw money</button>
    {{ withdraw }}

    <h2>Transfer Money</h2>
    <input v-model="fromAccountNr" placeholder="Enter account number"/>
    <input v-model="toAccountNr" placeholder="Enter account number"/>
    <input v-model="transferAmount" placeholder="Enter the amount you want to transfer"/>
    <br>
    <br>
    <button v-on:click="transferMoneyButton()">Transfer money</button>
    {{ transfer }}
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
      'transfer': ''
    }
  },
  methods: {
    'createAccountButton': function () {
      this.$http.post('http://localhost:8080/createAccount/' + this.firstName + '/' + this.lastName + '/' + this.accountNum + '/' + this.balance1)
          .then(function (response) {
            console.log(response);
            this.account = response.data
          });
    },
    'getBalanceButton': function () {
      this.$http.get('http://localhost:8080/balance/' + this.accountNr)
          .then(response => {
            console.log(response);
            this.balance = response.data
          });
    },
    'getDepostiButton': function () {
      this.$http.put('http://localhost:8080/deposit/' + this.accountNr1 + '/' + this.depositAmount)
          .then(response => {
            console.log(response);
            this.deposit = response.data
          });
    },
    'withdrawMoneyButton': function () {
      this.$http.put('http://localhost:8080/withdrawMoney/' + this.withdrawAccountNr + '/' + this.withdrawAmount)
          .then(response => {
            console.log(response);
            this.withdraw = response.data
          });
    },
    'transferMoneyButton': function () {
      this.$http.put('http://localhost:8080/transferMoney/' + this.fromAccountNr + '/' + this.transferAmount + '/' + this.toAccountNr)
          .then(response => {
            console.log(response);
            this.transfer = response.data
          });
    }
  }
}
</script>
