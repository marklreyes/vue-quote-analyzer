<template>
	<div class="container">
		<div class="row">
			<div class="col-md-3 offset-md-2">
				<div class="card">
					<div class="card-body text-center">
						<p>Total Pounds</p>
						<p>{{ totalPounds }}</p>
					</div>
				</div>
			</div>
			<div class="col-md-3">
				<div class="card">
					<div class="card-body text-center">
						<p>Invoice</p>
						<p>{{ totalInvoice }}</p>
					</div>
				</div>
			</div>
			<div class="col-md-3">
				<div class="card">
					<div class="card-body text-center">
						<p>Avg $/CWT</p>
						<p>{{ avgCWT }}</p>
					</div>
				</div>
			</div>
		</div>
		<div class="row">
			<div class="col-md-3 offset-md-9">
				<div class="card border-0">
					<div class="card-body">
						<select class="form-control form-control-sm" v-model="selected" @change="onChange($event)">
            <option v-for="option in options" v-bind:value="option.value">
              {{ option.text }}
            </option>
          </select>
					</div>
				</div>
			</div>
		</div>
		<div class="row">
			<div class="col-12">
				<div class="table-responsive">
					<table class="table table-bordered table-striped">
						<thead>
							<tr>
								<th>Location</th>
								<th>Part #</th>
								<th>Steel Product</th>
								<th>Weight</th>
								<!-- Loop -->
								<th>Big Creek Steel</th>
								<th>Steel Core</th>
								<th>AC Steel</th>
								<th>RBI</th>
								<!-- /Loop -->
							</tr>
						</thead>
						<tbody>
							<tr v-bind:key="result.PartNo" v-for="result in results">
								<td>{{ result.Location }}</td>
								<td>{{ result.PartNo }}</td>
								<td>{{ result.Product }}</td>
								<td>{{ result.Weight }}</td>
								<!-- Loop -->
                <td v-bind:key="index" v-for="quote in result.Quotes">
                  <span v-bind:class="classObjects.finalPrice" v-on:click="isSelected(quote.FinalPrice)">${{ quote.FinalPrice }}</span>
                  <span v-bind:class="classObjects.packagingFee" v-on:click="isSelected(quote.PackagingFee)">${{ quote.PackagingFee }}</span>
                  <span v-bind:class="classObjects.freightFee" v-on:click="isSelected(quote.FreightFee)">${{ quote.FreightFee }}</span>
                </td>
								<!-- /Loop -->
							</tr>
						</tbody>
					</table>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
  name: 'TableView',
  props: {
    totalPounds: {
      type: Number
    },
    totalInvoice: {
      type: Number
    },
    avgCWT: {
      type: Number
    },
    finalPrice: {
      type: Array
    },
    packagingFee: {
      type: Array
    },
    freightFee: {
      type: Array
    }
  },
  data() {
    return {
      classObjects: {
        finalPrice: 'd-block',
        packagingFee: 'd-none',
        freightFee: 'd-none'
      },
      selected: 'FinalPrice',
      options: [
        { text: 'Final Price', value: 'FinalPrice' },
        { text: 'Packaging Fee', value: 'PackagingFee' },
        { text: 'Freight Fee', value: 'FreightFee' }
      ],
      results:
      [
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "12345",
              "Product": "HR CSB PKL O 0.093x48x96",
              "Weight": 400000,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 32.49,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.54
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 31.99,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.58
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 25.90,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.25
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          },
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "A23456",
              "Product": "CR CSB NCT LO 0.042x47x120",
              "Weight": 215000,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 33.45,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.54
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 31.99,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.58
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 40.90,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.25
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          },
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "A3456",
              "Product": "GA CSB CTR D G90 0.056x48x72",
              "Weight": 330250,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 29.45,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.34
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 31.99,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.56
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 30.90,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.75
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          },
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "A4567",
              "Product": "GN CSB CTR D A90 0.0118x48x72",
              "Weight": 245000,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 37.45,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.54
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 36.99,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.58
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 42.90,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.25
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          },
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "A56789",
              "Product": "GA CSB CTR D G90 0.067x48x72",
              "Weight": 510500,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 32.45,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.54
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 31.99,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.58
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 38.90,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.25
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          },
          {
              "Location": "Cleveland, Ohio",
              "PartNo": "A67890",
              "Product": "HR CSB PKL O 0.123x48x72",
              "Weight": 25500,
              "Quotes": [
                  {
                      "Company": "Big Creek Steel",
                      "FinalPrice": 31.99,
                      "PackagingFee": 0.59,
                      "FreightFee": 1.54
                  },
                  {
                      "Company": "Steel Core",
                      "FinalPrice": 40.80,
                      "PackagingFee": 0.69,
                      "FreightFee": 1.58
                  },
                  {
                      "Company": "AC Steel",
                      "FinalPrice": 35.60,
                      "PackagingFee": 0.89,
                      "FreightFee": 1.25
                  },
                  {
                      "Company": "RBI",
                      "FinalPrice": 40.90,
                      "PackagingFee": 0.79,
                      "FreightFee": 1.44
                  }
              ]
          }
      ]
    }
  },
  methods: {
    isSelected(quote) {
      console.log('quote selected', quote);
    },
    onChange(event) {
        switch(event.target.value) {
          case 'FinalPrice':
            this.classObjects.finalPrice = 'd-block';
            this.classObjects.packagingFee = 'd-none';
            this.classObjects.freightFee = 'd-none';            
            break;
          case 'PackagingFee':
            console.log('show PackagingFee');
            this.classObjects.finalPrice = 'd-none';
            this.classObjects.packagingFee = 'd-block';
            this.classObjects.freightFee = 'd-none'; 
            break;
          case 'FreightFee':
            console.log('show FreightFee');
            this.classObjects.finalPrice = 'd-none';
            this.classObjects.packagingFee = 'd-none';
            this.classObjects.freightFee = 'd-block'; 
            break;
        }
    }
  },
  computed: {
    toUSD(price) {
      return '$' + price;
    },
    invoiceUSD() {
      return '$' + this.totalInvoice;
    },
    cwtUSD() {
      return '$' + this.avgCWT;
    },  
    computedClass() {
      let className = 'default';

      // More complicated logic to determine what class should be applied

      return className;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h3 {
		margin: 40px 0 0;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		display: inline-block;
		margin: 0 10px;
	}

	a {
		color: #42b983;
	}
</style>