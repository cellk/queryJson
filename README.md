# queryJson

##Example 1##
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

##Example 2##
readJson.query("select * from http://api/json" ,function(res){
  console.log(res)
})

##Example 3##
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
