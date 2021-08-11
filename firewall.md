## Firewall Rules
Firewall Rules is a flexible and intuitive framework for filtering HTTP requests. It gives you fine-grained control over which requests reach your applications. When incoming requests match your firewall rules, their requests will be blocked. 

## Configure Firewall Rules
One may configure firewall rules in the `firewall` section in `index.js` in `rocket-booster-template`. There can be multiple rules at the same time. Use an array to have multiple rules at the same time.

To create a new firewall rules, one must add a object with the following attributes to the array. The object must contains the following fields: `field`, `operator`, and `value`.

For each request, the value of the property you choose for Field is compared to the value you specify for Value.

Use the `Operator` correctly. To see an detailed docs for configuration, check below. For an expression to match, the value of the request Field and the value specified in the Value input must satisfy the comparison operator.

To delete a rule, you may simply remove it from array.

e.g., 
```
firewall: [
    {
      field: 'country',
      operator: 'in',
      value: ['CN', 'KP', 'SY', 'PK', 'CU'],
    },
  ]
```

## Docs for Firewall Rules

Field: 'asn' | 'continent' | 'country' | 'hostname' | 'ip' | 'user-agent'
Operator: 'match' | 'equal' | 'not equal' | 'greater' | 'less' | 'in' | 'not in' | 'contain' | 'not contain'
Value: Depends on the choices above

Note that 'match' operator can only work for Regex Expression object in the value. You may fill the value like this: 

`value: new RegExp('Fill your regex here')`

'greater' or 'less' only works for 'asn'. 'contain' | 'not contain' | 'equal' | 'not equal' works for everything else besides 'asn'

