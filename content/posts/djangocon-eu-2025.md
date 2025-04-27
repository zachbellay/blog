+++
title="Takeaways from DjangoCon EU 2025"
date=2025-04-26
extra.tldr="Dublin and the Django community are awesome."
taxonomies.tags = ["post"]
taxonomies.categories = ["django", "djangocon"]
extra.toc = true
+++

Here are some of the most interesting things I learned at DjangoCon EU 2025 in Dublin, Ireland, partially written with the help of AI:
[link to talks](https://pretalx.evolutio.pt/djangocon-europe-2025/schedule/)

My list of the best talks are at the bottom.

<img src="/imgs/djangocon-eu-2025/group-photo.png" alt="Group photo of DjangoCon EU 2025 conference goers, with me circled">
Me at DjangoCon EU 2025!


---

## Database
- **How to lock DB rows from Django**: `select_for_update` locks a row prior to making changes, ensuring data consistency in concurrent environments.
- **Move to BigInt Primary Keys ASAP**: Always use a BigInt (64 bits) or UUID for primary keys. If your table is nearing 2.1 billion entries (the 32-bit integer limit), you can use negative values to double the range, but this comes with caveats. [Talk](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/DLUM9M/)
- **Partition DB Tables by Tenant**: The `PostgresPartitionedModel` mixin helps partition data into separate PostgreSQL partitions based on a value, improving performance for large tables.
    - see `django-postgres-extra` package for more details [Github](https://github.com/SectorLabs/django-postgres-extra)
- **Save 99.8% on space in Postgres Indexes**: Always explicitly set `db_index` on foreign keys. By default, foreign keys are indexed, but you can optimize further:
    - PostgreSQL builds indexes for null values, but you can add a condition to an `Index` to dramatically reduce index size (up to ~99% smaller).
    ```py
    # Partial index example
    class Restaurant(models.Model):
        restaurant_chain = models.ForeignKey(..., db_index=False)
        class Meta:
            indexes = [
                models.Index(
                    fields=["restaurant_chain"],
                    condition=~models.Q(restaurant_chain=None),
                ),
            ]
    ```
- **Write Performance Tests in Pytest**: Write tests that load data into the DB and time how long views take to ensure good performance (or see regressions).
- **Check Laptop vs Cloud Server IO Speed**: If your DB/app is slower in the cloud, compare cloud disk speed with your laptop's disk speed to see if the bottleneck is hardware or I/O.
    - TODO: Insert command that can do this (will need to find this one talks are posted on YouTube)
- **TCP_NODELAY and Nagle's Algorithm**: If you're experiencing a bottleneck of around 25 requests/sec or 40ms per call, it might be due to TCP_NODELAY or Nagle's algorithm. These can be disabled using environment variables to improve performance.

---

## Tools & Libraries

- **`strace`**: A Linux utility for inspecting system calls made by a process (doesn't require root).
- **`django-neopolitan`**: Use the `CRUDView` for easy CRUD views (from the first htmx talk).
- **`django-auto-prefetch`**: Automatically prefetches related objects to reduce DB queries. [GitHub](https://github.com/tolomea/django-auto-prefetch)
- **`django-csp`**: Content Security Policy for django -- is going to be merged into Django core.
- **`django-otp-webauthn`**: Enables Face ID or fingerprint login (passkey support). [Talk repo](https://github.com/knyghty/talk-passkeys/tree/main)
- **`django-two-factor-auth`**: For 2FA/MFA in Django.
- **`silence-lint-error`**: Add inline linter silencing to gradually introduce linting rules. [PyPI](https://pypi.org/project/silence-lint-error/)
    - Use inline linter silencing to gradually enforce linting rules ("plug the leak, then bail out the boat").
- **`MaxMind`**: Recommended for blocking "bad people" (not just bots) using their database.
    - a bad bot being some script that is hitting `/xmlrpc.php` versus a bad person being someone who is maliciously solving captcha's, using legit looking emails/phone numbers, and doing bad things to your site (like trying to host crypto miners, etc)
- **`dj-angles`**: Use HTML-like elements in Django templates, e.g. <dj-partial /> instead of {% include 'partial.html' %} [Docs](https://dj-angles.adamghill.com/en/stable/)

---

## Best Practices

- **Dump sqlmigrate in PRs**: Set up a GitHub Action so that any PR with a migration outputs the contents of `sqlmigrate`, forcing devs to review the generated SQL.
    - stated example was so that 
- **Count DB Queries in Tests**: In pytest, count the number of queries per test and fail if above a threshold. Add a decorator to bypass for WIP or exceptions. The purpose is to find code that make excessive DB queries that you wouldn't expect.
    - In the talk, speaker showed some innocent code like `create_customer_profile()` which had 36K DB queries
- **Clean Up Old Flags**: Avoid reusing old feature flags -- see the Knightmare ($460M mistake) for why. [Read more](https://dougseven.com/2014/04/17/knightmare-a-devops-cautionary-tale/)

---

## Django & Community

- **Django Admin Customization**: The head of Canonical engineering linked a django spreadsheet like application for managing Canonical software quality Django dashboard [Github](https://github.com/canonical/dashboard)
    - I thought it was cool for 2 reasons
        - 1 : very dense information layout w/ table
        <img src="/imgs/djangocon-eu-2025/dashboard1.png">
        - 2 : highly customized django admin, though talked w/ the author, and he said he thinks it's super hacky and not maintainable, and that he wants to move it to move it outside of django admin and use htmx
        <img src="/imgs/djangocon-eu-2025/dashboard2.png">
- **Django Feature Proposals**: Now discussed on GitHub issues! [See here](https://github.com/django/new-features/issues/) -- this is great since Github is where developers live.
- **Django Template Backend written in Rust**: A Django template rendering backend written in Rust is in development. [GitHub](https://github.com/LilyFoote/django-rusty-templates)
- **Roasting App**: Roasting app made with htmx, makes use of hyperscript, which at the very least is an interesting case study [GitHub](https://github.com/scriptogre/roast-roulette)

---

## Modeling & Architecture

- **Schema-aware EAV Modeling**: For apps where users define their own models/forms, a generic EAV (Entity-Attribute-Value) system can help. Example:
    ```py
    boat = Entity.objects.with_attributes(object="MaritimeBoat").first()
    print(boat.size) # 32 meters
    ```
    [Talk link](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/DGQ9JD/)

---

## Templates & Misc

- **`{% spaceless %}`**: Template tag to remove spaces in Django templates.
- **B+ Tree**: High-level overview of B+ tree data structures.

## Some Companies using Django
- Octopus Energy : UK/Australia energy company
- Divio : django hosting for agencies
- codered.cloud : easy django hosting
- Monit : parking management system
- Gem Logic: Jewelry ERP 
- Zelthy: Custom healthcare app development platform in India


---

## Platforms & Things to Check Out

- **Divio**: Platform for agencies to easily host multiple Django projects.
- **Django Static Site Generators**:
    - [django-distill](https://django-distill.com/)
    - [calico-ssg](https://calico-ssg.com/techstack.html)
- **100 Words/Day Blog**: [softwarecrafts.uk/100-words](https://softwarecrafts.uk/100-words)

---

## Vibes
- seems like people prefer `django-cotton` over `django-components` because of the HTML like syntax
- there was much talk about how django's governance as a project, and basically only a tiny minority participates or contributes (superstars)

### (What I noticed as an American in Europe)
- everyone was friendly, life essentials in Europe seem much, much better than in the US -- Germans don't pay for college, have state sponsored healthcare, no such thing as "at-will" employment, excellent public transit, much cheaper childcare compared to the US, etc
- Lots of conference goers worked for the government 
- Dublin is also experiencing a cost of living crisis, facing NIMBYism to upzone.
- All Ubers in Dublin were actually licensed taxi drivers, which were hailed via the app. This seemed much less exploitative of the drivers than the typical gigified Uber driver. 
- Comparing SF to Dublin, there was virtually no homelessness or crazy people on the streets, and no poop on the streets (I hate to play into the narrative, but it was true, I also did go to the touristy areas though)

--- 
## The Best Talks

I went in with low expectations, since the the talk titles did not seem great, but I was blown away by the quality of many of the talks. Some of the best talks (which I will be re-watching once they are released on YouTube):
- [Turn back time: Converting integer fields to bigint using Django migrations at scale](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/DLUM9M/)
- [Data-Oriented Design](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/KKABLJ/)
    - by Adam Johnson (adamchainz) who maintains many popular django packages
- [Django + HTMX: Patterns to Success](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/W7NRA7/)
- [How to get Foreign Keys horribly wrong in Django](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/HAFUBH/)
- [100 Million Parking Transactions Per Year with Django](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/YHVBFJ/)
- [Dynamic models without dynamic models](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/DGQ9JD/)
- [Just-in-Time Development with Django and HTMX: Faster, Leaner, and Smarter](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/9TRSPC/)
    - I talked to this speaker afterward, and asked him how they did nested modals + updating widgets in a form after creating a new object in a nested modal. He showed me how he did it, I've been trying to figure this out for 8 months!
- [Anatomy of a Database Operation](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/BQHSMN/)
- [Django Admin at Scale: From Milliseconds to Microseconds](https://pretalx.evolutio.pt/djangocon-europe-2025/talk/WKMHAU/)
- many lightning talks were great since speakers had to just get to the meat of the subject

---

<div style="display: none">

Source material:

Things I learned:
- `select_for_update` — locks a row prior to changes
- use the `strace` linux utility for looking at what sys calls a linux process is calling (doesn't require root)
- `PostgresPartitionedModel` - mixin to partition data into separate pg partitions based on some value
- **make sure your primary key is a BigInt!** (64 bits, instead of 32 bits) or UUID
    - if your table is close to 2.1 billion entries, you can use negative values, to double the number of entries in your table (4.2 billion), with some caveats 
- If you have a problem where you're being bottlenecked as 25 requests/sec or 40ms per call, is likely TCP_NODELAY or nagle's algorithm, can be disable with some env variables
- always explicitly set db_index on foreign keys
    - Foreign keys by default have an index associated with them
    - postgres still builds indexes for null values, so by adding a condition to an `Index`, you can dramatically reduce the index size ~99%
```py
# source https://ckrybus.com/snippets/django-foreign-key-partial-index/
class RestaurantChain(models.Model):
    name = models.CharField(max_length=512)


class Restaurant(models.Model):
    name = models.CharField(max_length=512)
    restaurant_chain = models.ForeignKey(
        RestaurantChain, on_delete=models.CASCADE, null=True, blank=True, db_index=False
    )

    class Meta:
        indexes = [
            models.Index(
                fields=["restaurant_chain"],
                condition=~models.Q(restaurant_chain=None),
            ),
        ]
```
- use the `django-neopolitan` `CRUDView` for CRUD views -- from the first htmx talk
- If you find your DB/application is much slower in the cloud, compare cloud disk speed with laptop disk speed to see if bottleneck is actually hardware in DB or other IO 
    - TODO: Insert command that can do this (will need to find this one talks are posted on YouTube)
- Spreadsheet for managing Canonical software quality Django dashboard
    - https://github.com/canonical/dashboard
    - I thought it was cool for 2 reasons
        - 1 : very dense information layout w/ table
        <img src="/imgs/djangocon-eu-2025/dashboard1.png">
        - 2 : highly customized django admin, though talked w/ the author, and he said he thinks it's super hacky and not maintainable, and that he wants to move it to move it outside of django admin and use htmx
        <img src="/imgs/djangocon-eu-2025/dashboard2.png">
- create a github action that for any PR with migration outputs the contents of sqlmigrate so devs have to see the SQL
    - this way developers have to look at the generated SQL
- `django-csp` is going into django core
- ability to to login w/ Face ID or fingerprint w/ django (passkey): `django-otp-webauthn`
    - Talk GitHub repo: https://github.com/knyghty/talk-passkeys/tree/main
- django-auto-prefetch 
    - https://github.com/tolomea/django-auto-prefetch
- Great talk on schema aware generic EAV modeling 
    - speaker has a product that allows users to arbitrarily define models + forms, and so he had to build a generic EAV based modeling system to handle that arbitrary data
    - basically users would define a schema, and then he built a generic way of getting those objects, something like
    ```py
    boat = Entity.objects.with_attributes(object="MaritimeBoat").first()
    print(boat.size) # 32 meters
    ```
    - https://pretalx.evolutio.pt/djangocon-europe-2025/talk/DGQ9JD/
- Clean up old flags: Knightmare ($460M mistake)
    - High frequency trading firm re-used old flag and that led to unexpected behavior
    - https://dougseven.com/2014/04/17/knightmare-a-devops-cautionary-tale/
- `{% spaceless %}` template tag removes spaces in template
- 2FA/MFA : `django-two-factor-auth`
- write performance tests! 
    - write a test that loads a bunch of data into the DB and time how long the view takes 
- add inline linter silencing so that you can gradually add in linting rules on an existing codebase
    - "plug the leak, then bail out the boat"
    - https://pypi.org/project/silence-lint-error/
- in pytest, count number of queries per test, and if above a threshold, fail the test.     
    - add a decorator to a test to be able to bypass/ignore in case it's ok or a WIP
- MaxMind recommended for blocking "bad people" (distinct from bad bots, since bots can typically be mitigated with reCaptcha, but humans aren't, so MaxMind keeps a DB of these things and you can block based on that)
- high level overview of B+ tree
- Roasting app made with htmx, makes use of hyperscript, which at the very least is an interesting case study
    - https://github.com/scriptogre/roast-roulette
- a new django template rendering backend written in rust is being written:
    - https://github.com/LilyFoote/django-rusty-templates
- django feature proposals can now be discussed on github issues!
    - https://github.com/django/new-features/issues/

Libraries:




Platforms:
- Divio, for agencies to easily host multiple django projects 


Things to check out:
- Django static site generator
    - https://django-distill.com/
- calico-ssg Django based static site generator
    - https://calico-ssg.com/techstack.html
    - Has some interesting dependencies 
- 100 words/day blog post
    - https://softwarecrafts.uk/100-words
</div>
