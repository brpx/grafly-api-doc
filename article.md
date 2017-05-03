FORMAT: 1A


# Entity Articles [/entity/{entity_id}/article]


## Retrieve Entity Articles [GET] 

+ Headers

        Authorization: <api_key>

+ Parameters


    + status: `Published` (enum[String], optional) - Article status

        + Members
            + `Published`
            + `Draft`
            + `Ready`
            + `Unppublished`

    + offset: 10 (number, optional)

        + default: 0

    + count: 10 (number, option)

        + default: 10

    + author: `de5c7c74-2584-4b38-9e22-5f0cb7363524` (string, optional) - Author id

    + search : `search term` (string, optional) - Search term

    + category: `f9f34bf8-fcf0-4c2c-819d-8513ae2268af` (string, optional) - Category id

    + external_id: `1773212` (string, optional)

    + type: `post` (enum[string], optional) - Article type

        + Members
            + `post`
            + `gallery`

    + published_after: `2017-04-01` (date, optional)

    + published_before: `2017-04-03` (date, optional)

    + updated_after: `2016-04-01` (date, optional)

    + updated_before: `2016-04-01` (date, optional)

    + created_after: `2016-04-01` (date, optional)

    + created_before: `2016-04-01` (date, optional)


+ Response 200 (application/json)

        { "articles": [ {"id": ".....", "title": "....", ... }], "total": 15}



# Article [/entity/{entity_id}/article/{article_id}]


## Retrieve an article [GET]

+ Headers

        Authorization: <api_key>

+ Response 200 (application/json)

        {
            "id": ".....",
            "title": "....",
            ...
        }



