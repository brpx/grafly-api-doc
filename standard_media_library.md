FORMAT: 1A


# Search media [/]


## Search media [GET]

+ Parameters

    + q: `search term` ( String, required)

    + offset: 10 (number, optional)

        + default: 0

    + count: 10 (number, option)

        + default: 10


+ Response 200 (application/json)

        {
            "total" : 50,
            "results" : [
                {
                    "copyrightstatus" : "None",
                    "usage" : {
                        "last_used" : null,
                        "times" : 0
                    },
                    "description" : "epa06171348 Miklos Ungvari of Hungary (in white) and Tomas Bringas of Chile fight in the men's 73kg category during the World Judo Championships in Papp Laszlo Budapest Sports Arena in Budapest, Hungary, 30 August 2017.  EPA/Tibor Illyes HUNGARY OUT\nHUNGARY OUT    ",
                    "type" : "photo",
                    "thumb" : "http://stream.publico.pt/Fotos/1280x1024/00164/23673J.JPG",
                    "url" : "http://stream.publico.pt/Fotos/1280x1024/00164/23673J.JPG",
                    "added_date" : "2017-08-30 11:03:00+01:00",
                    "title" : "Judo World Championships in Budapest\t",
                    "author" : "Tibor Illyes - LUSA",
                    "id" : "16423673",
                    "tags" : []
                },
                {
                    "title" : "Judo World Championships in Budapest\t",
                    "added_date" : "2017-08-30 10:59:00+01:00",
                    "author" : "Tamas Kovacs - LUSA",
                    "url" : "http://stream.publico.pt/Fotos/1280x1024/00164/23661B.JPG",
                    "tags" : [],
                    "id" : "16423661",
                    "copyrightstatus" : "None",
                    "thumb" : "http://stream.publico.pt/Fotos/1280x1024/00164/23661B.JPG",
                    "type" : "photo",
                    "usage" : {
                        "times" : 0,
                        "last_used" : null
                    },
                    "description" : "epa06171343 Igor Wandtke of Germany (in white) and Martin Hojak of Slovenian fight in the men's 73kg category during the World Judo Championships in Papp Laszlo Budapest Sports Arena in Budapest, Hungary, 30 August 2017.  EPA/Tamas Kovacs HUNGARY OUT\nHUNGARY OUT  "
                }
            ]
        }
 
