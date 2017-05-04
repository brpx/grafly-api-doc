FORMAT: 1A


# Entity Authors [/api/entity/{entity_id}/author]


## Retrieve Entity Authors [GET]


+ Headers

        Authorization: <api_key>


+ Parameters

        + search: `search term` (string, optional)


Response 200 (application/json)


        {
            "authors" : [
                {
                    "name" : "Victor Ferreira",
                    "id" : "f0d3adbc-c81f-492b-a232-9e8bcaaa0b22",
                    "role" : "Editor"
                }
            ]
        }

