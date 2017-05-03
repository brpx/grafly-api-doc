FORMAT: 1A


# Entity Genre [/api/entity/{entity_id}/genre]


## Retrieve Entity Genre [GET]


+ Headers

        Authorization: <api_key>



Response 200 (application/json)


        {
            "genres" : [
                {
                    "css_class" : ".entrevista",
                    "name" : "Entrevista",
                    "id" : "73a28181-049e-4c23-bccf-249a2d11aa04"
                },
                {
                    "css_class" : ".noticia",
                    "name" : "Notícia",
                    "id" : "e1fe8d00-7580-4dda-b3ef-019162fa5bd6"
                },
                {
                    "css_class" : ".opiniao",
                    "name" : "Opinião",
                    "id" : "f80446d4-eeee-4549-8abb-d65ac62dcd5a"
                },
                {
                    "css_class" : ".reportagem",
                    "name" : "Reportagem",
                    "id" : "b274feca-93b6-47f7-8c75-6b3756d336c0"
                }
            ]
        }

