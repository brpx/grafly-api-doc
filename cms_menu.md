FORMAT: 1A


# Entity Menus [/api/v1.1/entity/{entity_id}/cms/menus]


## Retrieve Entity menus [GET]


+ Headers

        Authorization: <api_key>


Response 200 (application/json)


        {      
            "items" : [
                {
                    "id" : "4wx9z5c2r3u",
                    "status" : "published",
                    "name" : "Homepage",
                    "description" : "menu homepage",
                    "children" : [
                        {
                            "id" : "aak1cmbezke",
                            "destination" : "1259014a-f871-4cd7-a210-5ff7908471ec",
                            "name" : "Animal Tag",
                            "type" : "tag"
                        },
                        {
                            "destination" : "5cc511b1-091f-40e9-abde-9543899ea2cf",
                            "id" : "j0t445wp73e",
                            "name" : "Economia",
                            "type" : "category"
                        }
                    ]
                }
            ]
        } 

## Retrieve Entity menu by name [GET]

+ Headers

        Authorization: <api_key>

+ Parameters

    + name: `Homepage` (String, required)


Response 200 (application/json)


        {
            "name" : "Homepage",
            "children" : [
                {
                    "destination" : "1259014a-f871-4cd7-a210-5ff7908471ec",
                    "name" : "Animal Tag",
                    "type" : "tag",
                    "id" : "aak1cmbezke"
                },
                {
                    "name" : "Economia",
                    "type" : "category",
                    "id" : "j0t445wp73e",
                    "destination" : "5cc511b1-091f-40e9-abde-9543899ea2cf"
                }
            ],
            "id" : "4wx9z5c2r3u",
            "status" : "published",
            "description" : "menu homepage"
        }
