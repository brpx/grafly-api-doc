FORMAT: 1A


# Entity Block types [/api/v1.1/entity/{entity_id}/cms/blocktypes]


## Retrieve Entity block types [GET]


+ Headers

        Authorization: <api_key>


Response 200 (application/json)


        {
            "items" : [
                {
                    "name" : "Manchete",
                    "system_tags" : [],
                    "description" : null,
                    "max" : "2",
                    "visual_constraints" : {
                        "kicker" : true,
                        "related" : true,
                        "description" : true,
                        "label" : true,
                        "thumbnail" : true
                    },
                    "id" : "bluw47xdgq9",
                    "min" : "1"
                },
                {
                    "max" : "6",
                    "description" : null,
                    "visual_constraints" : {
                        "thumbnail" : true,
                        "label" : true,
                        "description" : true,
                        "related" : true,
                        "kicker" : true
                    },
                    "id" : "n43kb74d7mm",
                    "min" : "1",
                    "system_tags" : [],
                    "name" : "Últimas"
                }
            ]
        }


## Retrieve Entity block type by name [GET]

+ Headers

        Authorization: <api_key>

+ Parameters

    + name: `Manchete` (String, required)


Response 200 (application/json)


        {
            "max" : "2",
            "id" : "bluw47xdgq9",
            "description" : null,
            "system_tags" : [],
            "visual_constraints" : {
                "description" : true,
                "label" : true,
                "related" : true,
                "kicker" : true,
                "thumbnail" : true
            },
            "name" : "Manchete",
            "min" : "1"
        }
