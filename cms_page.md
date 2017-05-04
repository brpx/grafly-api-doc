FORMAT: 1A


# Entity Pages [/api/entity/{entity_id}/cms/pages]


## Retrieve Entity pages [GET]


+ Headers

        Authorization: <api_key>


Response 200 (application/json)

        {
            "items" : [
                {
                    "url" : "/home",
                    "description" : "Teste",
                    "status" : "published",
                    "blocks" : [
                        {
                            "items" : [
                                {
                                    "external_id" : null,
                                    "system_tags" : [
                                        {
                                            "id" : "503066bf-3feb-407b-92f3-6c76ae344389",
                                            "name" : "Tag 1",
                                            "css" : ".Tag-1"
                                        },
                                        {
                                            "id" : "e39d9e4a-a105-453e-95f0-a2a0db96bfc9",
                                            "name" : "tag 2",
                                            "css" : ".tag-2"
                                        }
                                    ], 
                                    ...
                                }
                            ]
                        ...
                        }
                        ...
                    ]
                }
            ]
        }

            
