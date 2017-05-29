# Article Migration Format (JSON)

The following JSON specification provides an intermediate step between articles from a legacy system and their representation in Graf.ly's data model. It serves the dual purpose of answering the "how to migrate" and "what to migrate" questions which arise while implementing a bulk migration process into Graf.ly.

## Reasoning

This format answers the "how to migrate" question by representing the **output of existing rules** used by the legacy _frontend_ when interpreting the various article attributes. The primary purpose of the specification is thus to **remove ambiguities**.

The "what to migrate" question is handled by separating attributes which are relevant for Graf.ly's data model from attributes which are only relevant to the _frontend_ layer, while eliminating irrelevant attributes altogether. The secondary purpose of the specification is thus to **remove uncertainty** from the migration process, while helping identify requirements not covered by Graf.ly's data model (ensuring these issues can be dealt with appropriately).

## Structure

Each article is represented by three main blocks:

* `content` - Main article content after interpretation by legacy _frontend_ rules (if any), in display order.
* `metadata` - Additional article attributes with _frontend_-defined positioning, which may or may not be displayed.
* `objects` - Objects referenced by the article, which represent separate entities from the article itself. This block makes the article self-contained but, during a mass migration, objects may be included only when they're first referenced, thus saving space in subsequent articles. Duplicate objects across articles are only migrated once.

## Specification

```
{
  "id": integer,  # ...this article's ID (unique).

  "content": {              # ...displayed content, with a defined order.
    "title": string,        # ...in HTML.
    "description": string,  # ...in HTML.

    "hero": {          # ...main media element for the article.
      "type": string,  # ...one of "image", "gallery", "video" or "infographic".
      "id": integer,   # ...reference to a media object matching the above type.
    },

    "body": [] of {              # ...content elements in display order.
      "type": string,            # ...one of "paragraph" "quote", or "media".
      "html": string,            # ...ignored when type is "media".
      "authors": [] of strings,  # ...in display order, ignored when type is not "quote".

      "media": {            # ...ignored when type is not "media".
        "type": string,     # ...one of "image", "gallery", "video" or "infographic".
        "id": integer,      # ...reference to a media object matching the above type.
        "width": integer,   # ...horizontal size (in pixels) for the media box.
        "height": integer,  # ...vertical size (in pixels) for the media box.
      },
    },
  },

  "metadata": {              # ...optionally displayed content, with fontend-defined positioning.
    "created": timestamp,    # ...article creation time.
    "published": timestamp,  # ...article publishing time.
    "updated": timestamp,    # ...article last update time.

    "authors": [] of {     # ...article authors in display order.
      "id": integer,       # ...reference to an author object.
      "location": string,  # ...in plain text (eg. "Lisboa").
    },

    "related": [] of {
      "type": string,   # ...one of "media", "article" or "link".
      "id": integer     # ...reference to a media object or an article, ignored when type is "link".
      "title": string,  # ...in HTML, ignored when type is not "link".
      "url": string,    # ...an external link, ignored when type is not "link".
    },

    "categories": [] of integers,   # ...references to category objects.
    "tags": [] of integers,         # ...references to tag objects.
    "system_tags": [] of integers,  # ...references to system tag objects.
    "labels": [] of integers,       # ...references to label objects.
    "genres": [] of integers,       # ...references to genre objects.
  },

  "objects": {             # ...referenced objects, not migrated again if already seen before.
    "authors": [] of {
      "id": integer,       # ...this author object's ID (unique).
      "name": string,      # ...in plain text.
      "role": string,      # ...in plain text.
      "email": string,     # ...in plain text.
      "photo": integer,    # ...reference to a media object of type "image".
      "bio": string,       # ...in plain text.
      "twitter": string,   # ...Twitter username without the leading "@".
      "facebook": string,  # ...Facebook username as it appears in "facebook.com/<username>".
      "url": string,
    },

    "media": [] of {
      "type": string,            # ...one of "image", "video", "gallery", "infographic" or "document".
      "id": integer,             # ...this media object's ID (unique for each type).
      "title": string,           # ...in HTML.
      "description": string,     # ...in HTML.
      "authors": [] of strings,  # ...in plain text, in display order.
      "images": [] of integers,  # ...references to images (in order), only when type is "gallery".
      "url": string,             # ...original media item's location, ignored when type is "gallery".
      "migrate": boolean,        # ...whether to migrate the media item at "url" to the new media archive.
    },

    "categories": [] of {
      "id": integer,       # ...this category object's ID (unique).
      "name": string,      # ...in plain text.
      "slug": string,      # ...in plain text (starting with a "/").
    },

    "tags": [] of {
      "id": integer,          # ...this tag object's ID (unique).
      "name": string,         # ...in plain text.
      "description": string,  # ...in plain text.
      "slug": string,         # ...in plain text (starting with an "#").
    },

    "system_tags": [] of {
      "id": integer,        # ...this system tag object's ID (unique).
      "name": string,       # ...in plain text.
      "css_class":          # ...in plain text (starting with a ".").
    },

    "labels": [] of {
      "id": integer,        # ...this label object's ID (unique).
      "name": string,       # ...in plain text.
      "css_class": string,  # ...in plain text (starting with a ".").
    },

    "genres": [] of {
      "id": integer,        # ...this genre object's ID (unique).
      "name": string,       # ...in plain text.
      "css_class": string,  # ...in plain text (starting with a ".").
    },
  },

  "opaque_data": {},  # ...must be valid JSON but is otherwise ignored (payload for the frontend).
}
```
