 <template>
 <!--START TEMPLATE-->
 <div class="card" style="width: 18rem;">
  <!-- START SALARY-->

    <p>Enter your salary </p>

    <p> 
    <input class="inpu" type="number" :value="vlaue0"  @input="salary = $event.target.value" >
    </p>
  <!-- END SALARY -->


  <!--START BODY CARD-->
  <div class="card-body">
     <p>Salary: {{Salary1}}</p>
        <p>Health Discounts: {{Health}}</p>
        <p>Social Security Discounts: {{Social}}</p>
    
        <p>Taxes Discounts monthly: {{Taxes}}</p>
  

      
      <div class="control">
        <p>Discounts: {{Discounts}}</p>
        <p>Net Salary: {{NetSalary}}</p>
  <!--END BODY CARD-->

        <!--START CONTROL-->
        <p>
        <button v-on:click="operacion()" class="btn btn-primary">Calculate</button>
        
        <button @click="reset" class="btn btn-danger">Reset</button> 
        </p>
        </div>
        <!--END CONTROL-->

  </div>
</div>
<!--END TEMPLATE BODY CARD-->

  
</template>

<script>  

//START JAVASCRIPT
export default {
  name: 'IngresarDatos',
  data: function () {
        return {
            salary: null,
            Health: null,
            Social: null,
            Taxes: null,
            Discounts: null,
            NetSalary: null,
            AnnualSalary: null
        }
    },
    methods: {
        reset() {
       this.Salary1 = '',
       this.Health = '',
       this.Social = '',
       this.Taxes = '',
       this.Discounts = '',
       this.NetSalary = '',
       this.AnnualSalary = ''
    },
        
        operacion: function() {
            


              //SHOW SALARY OF INPUT
            this.Salary1 = (this.salary)
            
            //CALCULATE 3.04% OF HEALT DISCOUNTS
            this.Health = parseInt(this.salary) *
                (3.04 / 100).toFixed(2)
                
            //CALCULATE 2.87% OF SOCIAL SECURITY
            this.Social = parseInt(this.salary) *
                (2.87 / 100).toFixed(2)


            //SHOW TOTAL DISCOUNT OF SALARY LESS THE BEFORE CALCULATE
            this.Discounts = parseInt(this.Health) +
                parseInt(this.Social);


            //SHOW TOTAL SALARY AFTER DISCOUNTS OF THE BEFORE CALCULATE
            this.NetSalary = parseInt(this.salary) -
                (this.Discounts);


             //CALCULATE NET SALARY X 12
            this.AnnualSalary = parseInt(this.NetSalary) * (12).toFixed(1)


            //HERE IF YOU GOT MORE 416220.01 YOU NEED PAY TAXES OF  15%
            if ( this.AnnualSalary >= 416220.01){
            this.Taxes = parseInt(this.AnnualSalary) -  (416220)

            
              this.Taxes = (this.Taxes) *  (0.15)
              this.Taxes = ((this.Taxes) /  (12)).toFixed(2)

                 console.log(this.Taxes)


              //HERE IF YOU GOT MORE 624329.01 YOU NEED PAY TAXES OF  20% MORE 2601.33

                if( this.AnnualSalary >= 624329.01){
                this.Taxes = (this.AnnualSalary) - (624329)

            
                this.Taxes = (this.Taxes) *  (0.20) + (2601.33)
                this.Taxes = ((this.Taxes) /  (12)).toFixed(2)

                console.log(this.Taxes)
                }



                //HERE IF YOU GOT MORE 624329.01 YOU NEED PAY TAXES OF  25% MORE 6648

                if( this.AnnualSalary >= 867123.01){
                this.Taxes = (this.AnnualSalary) -  (867123)

            
                this.Taxes = (this.Taxes) *  (0.25) + (6648)
                this.Taxes = ((this.Taxes) /  (12)).toFixed(2)

                console.log(this.Taxes)
                }


              //SHOW FINAL RESULT AFTER THIS PROCESS
             this.Discounts = parseInt(this.Discounts) + parseInt(this.Taxes)  

             this.NetSalary = parseInt(this.salary) - parseInt(this.Discounts)


            } 

            
            ///else if( this.AnnualSalary >= 624329.01){
            //this.Taxes = (this.AnnualSalary) - (416220)

            
            //this.Taxes = (this.Taxes) *  (0.20)
            //this.Taxes = (this.Taxes) /  (12)

            //console.log(this.Taxes + 'im')
            //}
            
            //else if (this.AnnualSalary > 624329.01){
              //  this.Taxes = 'hello'

             // }




            



          //this.Discounts = parseInt(this.Discounts) +
            //(this.Taxes)

           //this.NetSalary = parseInt(this.salary) -
                //(this.Discounts)
          
        
          
        }
        
    }
}

//END JAVASCRIPT

</script>



<style scoped>

.card {
 
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  margin: 300px;
  margin-top: 0;
  align: center
}

body {background-color: coral;}



.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}



p {
  text-align: center;
  font-weight: bold;

}



.btn {
    padding: 0.5em 1em;
  border: none;
  cursor: pointer;
}

.btn {
    margin: 5px;
    padding: 0.5em 1em;
  border: none;
  cursor: pointer;
}

</style>