# queryJson

##Example 1##
```javascript
var json = {
"users" : [{
            "firstname" : "john",
            "lastname" : "doe",
            "id" : 1,
            "username" : "john.doe",
            "email" : "john.doe@email.com",
            "city" : "montreal"
            },
            {
            "firstname" : "marc",
            "lastname" : "dupont",
            "id" : 2,
            "username" : "marc.dupont",
            "email" : "marc.dupont@email.com",
            "city" : "paris"
            },
            {
            "firstname" : "July",
	    "lastname" : "Dooley",
            "id" : 3,
            "username" : "July.Dooley",
            "email" : "july@example.com",
            "city" : "montreal"
            },
            {
            "firstname" : "Mary",
            "lastname" : "moe",
            "id" : 4,
            "username" : "Mary.moe",
            "email" : "Mary.moe@email.com",
            "city" : "montreal"
            }]
}

readJson.query("select firstname, lastname from json",function(res){
  console.log(res)
})
```

##Example 2##
```javascript
readJson.query("select * from http://api/json" ,function(res){
  console.log(res)
})
```

##Example 3##
```javascript
var json = {
    "fullname" : "July Dooley",
    "location" : {
        "adresse" : "4810 Rue Jean-Talon Ouest",
        "cp" : "H4P 2N5",
        "country" : "Canada",
        "region" : "QC"
    },
    "phone" : {
    	"office" : "(514) 875-1500"
    },
    "profession" : {
        "position" : "developer",
        "start" : "2017-03-10"
    }
}

readJson.query("select office, position from json",function(res){
  console.log(res)
})
```

## example4##
```javascript
var json = {
	"fullname": "john doe",
	"location": {
		"latitude": 433453435,
		"longitude": 0,
		"adresse": "98 Avenue",
		"cp": "H1H 1 H1",
		"city": "Montreal",
		"country_id": 2,
		"region": "Qc"
	},
	"phone": {
		"home": "514 555 6666",
		"office": "999 999 0000"
	},
	"country": [{
		"id": 2,
		"name": "Canada",
		"area": 545,
		"population": 5455454,
		"nationalities": {
			"Chinese": "25 %",
			"indian": "34 %"
		}
	}, {
		"id": 4,
		"name": "USA",
		"area": 654565,
		"population": 56,
		"nationalities": {
			"Chinese": "15 %",
			"Latino": "25 %"
		}
	}],
	"relationship": {
		"parents": {
			"mother": {
				"firstname": "Alice",
				"lastname": "dupont",
				"age": 54
			}
		},
		"children": [{
			"name": "Amy"
		}, {
			"name": "Tom"
		}]
	}
}

readJson.query("select country_id, country from json", function (res) {
 readJson.params.localObj = res.country;
 idCountry = res["country_id"][0][0];
 readJson.query("select * from localObj where id = "+idCountry, function (res) {
     	console.log(res);
    })
})
```
