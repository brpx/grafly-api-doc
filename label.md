FORMAT: 1A


# Entity Label [/api/v1.1/entity/{entity_id}/label]


## Retrieve Entity Label [GET]


+ Headers

        Authorization: <api_key>



Response 200 (application/json)


        {
            "labels" : [
                {
                    "css_class" : ".updating",
                    "name" : "Em actualização",
                    "id" : "449c7578-acb2-44aa-b858-4de78900a4b1"
                },
                {
                    "css_class" : ".live",
                    "name" : "Em directo",
                    "id" : "2fd5a34f-02ee-496b-8aba-9be386eb6031"
                }
            ]
        }

