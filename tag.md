FORMAT: 1A


# Entity tag [/api//entity/{entity_id}/tag]


## Retrieve Entity Tags [GET]


+ Headers

        Authorization: <api_key>



Response 200 (application/json)


        {
            "tags" : [
                {
                    "name" : "accident and emergency incident",
                    "slug" : "",
                    "type" : {
                        "name" : "IPTC",
                        "id" : "d3fecd7a-df05-469a-8010-4f6d8a0fed8f"
                    },
                    "id" : "c70e86cc-a9f2-47a6-9c76-58c1500df258",
                    "description" : "A sudden, unexpected event that causes unwanted consequences or requires immediate action to prevent serious consequences."
                },
                {
                    "name" : "accomplishment",
                    "slug" : "",
                    "type" : {
                        "name" : "IPTC",
                        "id" : "d3fecd7a-df05-469a-8010-4f6d8a0fed8f"
                    },
                    "id" : "c4c53aa8-791f-49ba-9fef-4af415992ef1",
                    "description" : "Achievements by individuals or groups, animals, plants or other objects, such as  winning a competitive contest etc"
                },
                {
                    "name" : "act of terror",
                    "slug" : "",
                    "type" : {
                        "name" : "IPTC",
                        "id" : "d3fecd7a-df05-469a-8010-4f6d8a0fed8f"
                    },
                    "id" : "cabd0264-644f-41c0-b862-2fc5f8774813",
                    "description" : "Act of violence, often deadly, designed to raise fear and anxiety in a population"
                },
                {
                    "name" : "animal",
                    "slug" : "",
                    "type" : {
                        "name" : "IPTC",
                        "id" : "d3fecd7a-df05-469a-8010-4f6d8a0fed8f"
                    },
                    "id" : "1259014a-f871-4cd7-a210-5ff7908471ec",
                    "description" : "Items about animals with a focus on emotional facets"
                }
            ]
        }

