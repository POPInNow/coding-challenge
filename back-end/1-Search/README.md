# Search Coding Challenge

### Story

As a user I would like to be able to search for events, ideas, or comments containing a keyword or a set of keywords.

### Defintion of Done

A search API endpoint is created. The endpoint should return a list of events, ideas, and comments where the supplied keyword(s) are mentioned.

### API Requirements / Design

```
GET /search?s={keyword(s)}
```

* Keyword(s) should be highlighted in the results enclosed in ```<em></em>```
* Order by search_score (highest score on top)
* Should return Status Code 200 if search returns 1 or more result
* Should return Status Code 204 if no result
* Should return Status Code 400 if the required "s" query string parameter is not supplied
* Should use basic auth to protect the endpoint. Just hardcode to use username: "popin" password: "is_cool".
* Should follow [The Twelve-Factor App](https://12factor.net) principles
* Should return JSON object that looks as follows:
```javascript
{
    "error": "Error message here", // if applicable
    "data": [
    	{
    		"event_id": "7d9befba-db78-4e89-8127-06b036787be2",
    		"event_question": "What are the candidate's <em>strength</em>s and weaknesses?",
    		"search_score": 48.5
    	}
    	, {
    		"event_id": "7d9befba-db78-4e89-8127-06b036787be2",
    		"idea_id": "7d9befba-db78-4e89-8127-06b036787be3",
    		"idea_content": "John's <em>strength</em> is in his ability to describe complex problem in simple terms ...",
    		"search_score": 36.5
    	}

		// Only for bonus pts:
		, {
			"idea_id": "7d9befba-db78-4e89-8127-06b036787be3",
			"comment_id": "7d9befba-db78-4e89-8127-06b036787be4",
			"comment_content": "I agree those are his <em>strength<em>s. Furthermore ...",
			"search_score": 10.0
		}
	]
}
```

### Constraints
- You only have 4 hours to do this
- Preferred programming languages: Java, Go, JavaScript (Node.js)
- If Java is chosen, app server is limited to Tomcat

### More bonus points
- Integration and unit testing
- Deployed in the cloud (AWS, Heroku, etc.)