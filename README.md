# PokemonService-JTW-SaveDataCacheService
The project has JWT and call to PokemonService and you can save the response into the SaveDataCacheService

The project consisted at get the JWT to get access to can call the PokemonService and get info of Pokemon to wanna know, and that response take it and send to
SaveDataCacheService to save it.

This project was adapted to save Pokemon data, but you can save Person data too.

I leave the Requests to continue:

1° STEP:  Getting Token (JWT)

Headers:  *Content-Type = application/json

Endpoint: http://localhost:8080/token  (POST)

Body: {"user": "yourName"}

Response: {
    "token": "JWT eyJhbGciOiJIUzUxMiJ9.eyJqdGkiOiJhbGVnbGFKV1QiLCJzdWIiOiJhbGVqYW5kcm8iLCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwiaWF0IjoxNjYxNTQ4MjA0LCJleHAiOjE2NjE1NDgyNjR9.Ptx0_le_o_Gltj6A4RGgjHQLQhsN4Q0KK6sfD54nReuzNqCtNXzUQdBi24-zRk5l4yRwmXowey6hspc9loWH3w"
}


2° STEP: Consuming PokemonService and getting PokemonData what you requested, later send it to SaveDataCacheService to save it and you won't lose the data.

Headers: *Authentication = Token(JWT) //Here you put the Token-JWT, You get it before with the response.
         *Content-Type = application/json
         
Endpoint: http://localhost:8080/pokemon/search  (POST)

Body: {"name": "charmander"}  //Here go to Pokemon name what you wanna get the info.

response: {"id": "8cdebde2-fbf5-4a44-9970-a90028b6e13d", "message": "To get the Data through from ID"}  //The ID do reference to identificater with the your data was saved in the service


3° STEP: Getting the data what was saved into the SaveDataCacheService.

Headers:  *Content-Type = application/json

Endpoint:  http://localhost:8081/data/get/8cdebde2-fbf5-4a44-9970-a90028b6e13d  (GET)

response: {"data": {"name": "charmander", "weight": "85", "types": ["fire"], "height": "6"}}


