FORMAT: 1A


# Entity tag type [/api//entity/{entity_id}/tagtype]


## Retrieve Entity tag types [GET]


+ Headers

        Authorization: <api_key>



Response 200 (application/json)

        {
            "tag_types" : [
                {
                    "name" : "IPTC",
                    "id" : "d3fecd7a-df05-469a-8010-4f6d8a0fed8f"
                },
                {
                    "name" : "People",
                    "id" : "607ff00f-63a2-4bb0-91c5-814d28f2baef"
                },
                {
                    "name" : "Place",
                    "id" : "38a8cc91-65f0-4a61-a35d-898d173f2e16"
                },
                {
                    "name" : "Organization",
                    "id" : "440315da-d9b2-4748-906a-68686b0abdff"
                },
                {
                    "name" : "Event",
                    "id" : "2f53b8a0-1fc2-486f-bfb5-7e43b703c93a"
                },
                {
                    "name" : "Topic",
                    "id" : "9e04775d-266c-45f7-8d1c-19326d861615"
                },
                {
                    "name" : "Job",
                    "id" : "7e5d93a9-fed8-43a8-8e74-1e2ab2b69601"
                },
                {
                    "name" : "Subject",
                    "id" : "46db2309-c07b-4ccb-aae3-f29153340cfb"
                },
                {
                    "name" : "Other",
                    "id" : "92be0db4-396e-4f08-aa67-e6ba576b739a"
                }
            ]
        }

