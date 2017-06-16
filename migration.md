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

### Notes
* URL attributes must be ASCII-only (URL-encoded).
* Time attributes are in UNIX format (seconds since `1970-01-01 00:00:00 UTC`).
* The article's `content` may be omitted (along with its `metadata` and `taxonomies`), turning it into a stub. When this is the case, its `objects` are migrated as normal but no actual article is created in Graf.ly. The `id` is the only mandatory attribute, which must always be unique for the whole article set.

### Format
```
{
  "document": "migration.article",  #  ...always "migration.article".
  "revision": "0.10",               #  ...document format revision.

  "id": string,         # ...this article's ID (unique).
  "legacy_id": string,  # ...this article's legacy ID (opaque, for future reference).
  "hidden": boolean,    # ...when "true", this article won't appear in search results.

  "content": {                  # ...displayed content, with a defined order.
    "title": string,            # ...in HTML.
    "alternate_title": string,  # ...in HTML.
    "description": string,      # ...in HTML.

    "hero": {          # ...main media element for the article.
      "type": string,  # ...one of "image", "gallery", "video" or "infographic".
      "id": string,    # ...reference to a media object matching the above type.
    },

    "body": [] of {              # ...content elements in display order.
      "type": string,            # ...one of "paragraph" "quote", "media" or "article".
      "html": string,            # ...ignored when type is not "paragraph" or "quote".
      "authors": [] of strings,  # ...in display order, ignored when type is not "quote".

      "article": {       # ...ignored when type is not "article".
        "type": string,  # ...currently only "live" (sub-articles of different types aren't allowed).
        "id": string,    # ...reference to another article (previously migrated).
      },

      "media": {            # ...ignored when type is not "media".
        "type": string,     # ...one of "image", "gallery", "video" or "infographic".
        "id": string,       # ...reference to a media object matching the above type.
        "width": integer,   # ...horizontal size (in pixels) for the media box.
        "height": integer,  # ...vertical size (in pixels) for the media box.
      },
    },
  },

  "metadata": {              # ...optionally displayed content, with fontend-defined positioning.
    "created": timestamp,    # ...article creation time.
    "published": timestamp,  # ...article publishing time.
    "updated": timestamp,    # ...article last update time.

    "authors": [] of {         # ...article authors in display order.
      "id": string,            # ...reference to an author object.
      "location": string,      # ...in plain text (eg. "Lisboa").
      "role": string,          # ...role at the time of publishing.
      "contribution": string,  # ...in plain text.
    },

    "related": [] of {
      "type": string,   # ...one of "media", "article" or "link".
      "id": string,     # ...reference to a media object or an article, ignored when type is "link".
      "title": string,  # ...in HTML, ignored when type is not "link".
      "url": string,    # ...an external link, ignored when type is not "link".
    },

    "taxonomies": [] of {
      "type": string,  # ...one of "category", "tag", "system_tag", "label" or "genre".
      "id": string,    # ...reference to the taxonomy object's ID.
    },
  },

  "objects": {                      # ...referenced objects, not migrated again if already seen before.
    "authors": [] of {
      "id": string,                 # ...this author object's ID (unique).
      "legacy_id": string,          # ...this author's legacy ID (opaque, for future reference).
      "name": string,               # ...in plain text.
      "role": string,               # ...in plain text.
      "email": string,              # ...in plain text.
      "photo": string,              # ...reference to a media object of type "image".
      "bio": string,                # ...in plain text.
      "slug": string,               # ...in plain text.
      "system_tags": [] of string,  # ...references to system tag objects (their IDs).

      "social": [] of {
        "type": string,  # ...one of "facebook", "twitter", "google_plus" or "other".
        "url": string,   # ...full URL to the authors' website or social network profile.
      },
    },

    "media": [] of {
      "type": string,               # ...one of "image", "video", "gallery", "infographic" or "document".
      "id": string,                 # ...this media object's ID (unique for each type).
      "legacy_id": string,          # ...this media's legacy ID (opaque, for future reference).
      "created": timestamp,         # ...media creation time.
      "published": timestamp,       # ...media publishing time.
      "updated": timestamp,         # ...media last update time.
      "title": string,              # ...in HTML.
      "lead": string,               # ...in HTML.
      "description": string,        # ...in HTML, only when type is "video", "gallery" or "infographic".
      "width": integer,             # ...horizontal size (in pixels) for vector media (eg. SWF, SVG).
      "height": integer,            # ...vertical size (in pixels) for vector media (eg. SWF, SVG).
      "thumbnail": string,          # ...reference to an image object ID, only when type is "video" or "infographic".
      "authors": [] of strings,     # ...in plain text, in display order.
      "author_ids": [] of strings,  # ...references to author object IDs.
      "images": [] of strings,      # ...references to images (in order), only when type is "gallery".
      "url": string,                # ...original media item's location, ignored when type is "gallery".
      "migrate": boolean,           # ...migrate the "url" when "true" (otherwise migrated outside this process).
      "external": boolean,          # ...migration consists of just a stub article, only when type is "video".

      "taxonomies": [] of {
        "type": string,  # ...one of "category", "tag", "system_tag", "label" or "genre".
        "id": string,    # ...reference to the taxonomy object's ID.
      },
    },

    "taxonomies": [] of {
      "id": string,           # ...this item's ID (unique for each type).
      "type": string,         # ...one of "category", "tag", "system_tag", "label" or "genre".
      "name": string,         # ...in plain text.
      "slug": string,         # ...in plain text, only when type is "category" or "tag".
      "css_class": string,    # ...in plain_text, only when type is "system_tag", "label" or "genre".
      "subtype": string,      # ...in plain text, case-sensitive, only when type is "tag".
      "description": string,  # ...in plain text, only when type is "tag".
    },
  },

  "opaque_data": {},  # ...must be valid JSON but is otherwise ignored (payload for the frontend).
}
```
