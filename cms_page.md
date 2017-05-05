FORMAT: 1A


# Entity Pages [/api/v1.1/entity/{entity_id}/cms/pages]


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



## Retrieve Entity page by name [GET]

+ Headers

        Authorization: <api_key>

+ Parameters

    + name: `Homepage` (String, required)


Response 200 (application/json)


        {
            "status" : "published",
            "name" : "Homepage",
            "blocks" : [
                {
                    "title_visible" : "false",
                    "name" : "Manchete",
                    "items" : [
                        {
                            "scheduled_publishing" : 0,
                            "type" : "post",
                            "review_status" : "",
                            "highlights" : [],
                            "created_at" : "2017-04-26T21:56:00Z",
                            "published_at" : "2017-04-27T10:27:51Z",
                            "genre" : {
                                "id" : "e1fe8d00-7580-4dda-b3ef-019162fa5bd6",
                                "name" : "Notícia"
                            },
                            ...
                        }
                    ],
                    ...
                }
            ]
        }
