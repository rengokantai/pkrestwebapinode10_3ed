#### pkrestwebapinode2ed
#####1 REST
######The rest goals
| Method       | safe          | Idempotent |
| ------------- |:-------------:|:-----:|
| get      | yes |yes|
| post      | no     |   no |
| put | no      |    yes |
| delete | no      |    yes |

#####3 Building a typical
######Querying the API
```
app.get('/contacts', 
		function(request, response){
			var get_params = url.parse(request.url, true).query;	//get query part, like ?arg=value
			
			if (Object.keys(get_params).length === 0)
```
######Content negotiation
Accept HTTP header specifies the media type of the resource that the consumer is willing to process.,for example
```
app.get('/groups', function(request, response) { 
response.format( { 
      'text/xml' : function() { 
         response.send(contacts.list_groups_in_xml); 
      }, 
      'application/json' : function() { 
         JSON.stringify(contacts.list_groups()); 
      }, 
      'default' : function() {. 
         response.status(406).send('Not Acceptable'); 
      }    
}); 
}); 
```