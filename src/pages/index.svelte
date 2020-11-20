<script>
	import DataTable from '@fouita/data-table'
		
	const data = [
		  {
		    "first_name": "Wynn",
		    "last_name": "Donovan",
		    "company": "EMTRAK",
		    "email": "wynn.donovan@emtrak.io",
		    "phone": "+1 (809) 577-3968",
		    "address": "555 Freeman Street, Winesburg, New Jersey, 8986"
		  },
		  {
		    "first_name": "Arlene",
		    "last_name": "Cooley",
		    "company": "XUMONK",
		    "email": "arlene.cooley@xumonk.us",
		    "phone": "+1 (926) 459-2880",
		    "address": "659 Dupont Street, Lynn, West Virginia, 7173"
		  },
		  {
		    "first_name": "Jewell",
		    "last_name": "Sellers",
		    "company": "TECHADE",
		    "email": "jewell.sellers@techade.info",
		    "phone": "+1 (957) 456-2432",
		    "address": "955 Beekman Place, Waikele, Northern Mariana Islands, 341"
		  }
	]

	const head= {
		first_name: 'First Name',
		last_name: 'Last Name',
		email: 'Email',
		phone: 'Phone',
		company: 'Company',
	}


</script>


<DataTable {head} rows={data} hover />