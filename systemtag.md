FORMAT: 1A


# Entity System tag [/api/entity/{entity_id}/systemtag]


## Retrieve Entity sytem tag [GET]


+ Headers

        Authorization: <api_key>



Response 200 (application/json)


        {
            "systemtags" : [
                {
                    "css" : ".Tag-1",
                    "name" : "Tag 1",
                    "context" : [
                        {
                            "name" : "Posts Body",
                            "id" : "posts_body"
                        }
                    ],
                    "id" : "503066bf-3feb-407b-92f3-6c76ae344389"
                },
                {
                    "css" : ".tag-2",
                    "name" : "tag 2",
                    "context" : [
                        {
                            "name" : "Posts Body",
                            "id" : "posts_body"
                        }
                    ],
                    "id" : "e39d9e4a-a105-453e-95f0-a2a0db96bfc9"
                },
                {
                    "css" : ".Tag-3",
                    "name" : "Tag 3",
                    "context" : [
                        {
                            "name" : "Posts Media",
                            "id" : "posts_media"
                        }
                    ],
                    "id" : "71cae06b-866b-4fa2-bfa4-2496a500b72a"
                },
                {
                    "css" : ".Tag-4",
                    "name" : "Tag 4",
                    "context" : [
                        {
                            "name" : "Posts Media",
                            "id" : "posts_media"
                        },
                        {
                            "name" : "Posts Widgets",
                            "id" : "posts_widgets"
                        },
                        {
                            "name" : "Posts Body",
                            "id" : "posts_body"
                        }
                    ],
                    "id" : "bbca19e4-7454-4310-ba1d-0686625aaa33"
                },
                {
                    "css" : ".Tag-5",
                    "name" : "Tag 5",
                    "context" : [
                        {
                            "name" : "Content Blocks",
                            "id" : "content_blocks"
                        }
                    ],
                    "id" : "67fec774-3f89-4ed2-b654-d7d55d69ac90"
                },
                {
                    "css" : ".Tag-6",
                    "name" : "Tag 6",
                    "context" : [
                        {
                            "name" : "Users & Authors",
                            "id" : "users_and_authors"
                        }
                    ],
                    "id" : "ff85a6c8-6b50-4f50-bd12-b7485f2ad544"
                }
            ]
        }

