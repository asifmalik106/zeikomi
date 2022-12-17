<script>
export default {
  data() {
    return {
      amount: "",
      with10: 0,
      with8: 0,
      taxIncluded: false,
      showFraction: false,
      statusText8: "With 8% Tax",
      statusText10: "With 10% Tax"
    }
  },
  watch: {
    amount: function(newAmount) {
      this.calculateNow(newAmount)
    },
    taxIncluded: function(){
      this.calculateNow(this.amount)

    },
    showFraction: function(){
      this.calculateNow(this.amount)

    }
  },
  methods:{
    calculateWithTax: function(newAmount){
      this.with10 = (newAmount/1.10).toFixed(this.getFractionDigits())
      this.with8 = (newAmount/1.08).toFixed(this.getFractionDigits())
    },
    calculateWithoutTax: function(newAmount){
      this.with10 = (newAmount*1.10).toFixed(this.getFractionDigits())
      this.with8 = (newAmount*1.08).toFixed(this.getFractionDigits())
    },
    getFractionDigits: function(){
      let fractionDigits = 0;
      if(this.showFraction){
        fractionDigits = 2
      }
      return fractionDigits;
    },
    calculateNow: function(newAmount){
      if(this.taxIncluded){
        this.statusText8 = "Without 8% Tax";
        this.statusText10 = "Without 10% Tax";
        this.calculateWithTax(newAmount)
      }else{
        this.statusText8 = "With 8% Tax";
        this.statusText10 = "With 10% Tax";
        this.calculateWithoutTax(newAmount)
      }
    }

  }
}
</script>

<template>
  <div class="card">
    <div class="card-header">
      <h2 class="my-2 display-6">Zeikomi Calculator (税込)</h2>
    </div>
    <div class="card-body">
      <form>
        <div class="my-2">
          <input type="number" class="form-control amount" v-model="amount">
        </div>
        <div class="form-check form-switch">
          <label class="form-check-label" for="flexSwitchCheckDefault">Tax Already Included</label>
          <input class="form-check-input" v-model="taxIncluded"  type="checkbox" role="switch" id="flexSwitchCheckDefault">
        </div>
        <div class="form-check form-switch">
        <label class="form-check-label" for="flexSwitchCheckDefault">Show Fraction</label>
        <input class="form-check-input" v-model="showFraction"  type="checkbox" role="switch" id="flexSwitchCheckDefault">
      </div>
      </form>
      <hr/>
      <table class="table">
        <tbody>
        <tr>
          <td class="align-middle">{{ statusText8 }}</td>
          <td class="display-6">{{ with8 }}</td>
        </tr><tr>
          <td class="align-middle">{{ statusText10 }}</td>
          <td class="display-6">{{ with10 }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.amount{
  font-size: 72px;
}
</style>
