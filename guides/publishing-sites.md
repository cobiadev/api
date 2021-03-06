## Publishing Sites

Two primary approaches for publishing new Sites via API integration

1. Cloning at Scale - The `clone_id` method
2. Custom provisioning - Specific module placements

----

### 1) `clone_id` method

Pass basic site details (url, business details, partner IDs, etc) and a `clone_id` of an already built Site ID within the platform.

Your new Site will be created as an exact duplicate of the `clone_id` (pages, modules, styles, etc) Site, but will be assigned to the newly provided Business details. Dynamic modules like Google Maps, Contact Info and Hours of Operation will automatically reflect the new Business info.

```json
{
    "business": {
        "business_name": "Some Business",
        ...
    },
    "formatted_domain": "somesite.example.com",
    "clone_id": 12345
}
```

### 2) Specific module placements

The more advanced method for publishing Sites/Pages gives you granular detail on theme, colors, images, and what modules make up the page and where they will be displayed.

**Site**

```json
{
    "business": {
        "business_name": "Some Business",
        ...
    },
    "formatted_domain": "somesite.example.com",
    "theme_id": 123,
    "theme_settings": {
        "headerBackgroundColor": "#000000",
        "headerTextColor": "#ffffff"
    }
}
```

**Page**

```json
{
    "name": "Home",
    "title": "Title Tag Here",
    "column_widths": [[60, 40]],
    "modules": [
        {
            "module": "contactinfo",
            "row": 1,
            "column": 1
        },
        {
            "module": "googlemaps",
            "row": 1,
            "column": 1
        },
        {
            "module": "content",
            "row": 1,
            "column": 2,
            "content": "<p>Here is some content</p>"
        }
    ]
}
```
