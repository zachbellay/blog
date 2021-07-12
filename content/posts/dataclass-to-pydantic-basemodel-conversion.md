+++
title="Dataclass to Pydantic BaseModel Conversion"
date=2021-05-27
extra.tldr="If you're trying to convert a Python dataclass to a Pydantic Basemodel object, don't. Just convert the dataclass object to subclass BaseModel."
+++

_Note:_ This post is a dramaticized development experience I had at work that stemmed largely from miscommunication and bad assumptions. Nonetheless, if you're in a situation like this, here's what I did.

## The Problem

Let's say an existing codebase uses Python dataclasses as follows:

```py

@dataclass
class Potato:
    x: str
    y: int

```

But what if I want to use the _sexy_ new Python library FastAPI to build a REST app? Oooh, so ✨shiny✨. So many 💯emojis❤️ in the 💻git👾 📀commits💾. It feels like Flask. I love Flask. I mean it has to be good right? Linus Torvalds did say "Mo' emojis, mo' performance." Ok, I'm in, let's use it.

Aside from cargo culting FastAPI, why would you want to use it? I would say there are 2 main draws.

1. **Asynchronous IO** - people hate async/await stuff, but it's faster and uses the CPU more efficiently in many cases.
2. **Swagger/Open Docs** - it's awesome to have "self-documenting" rest APIs generated for you out of the box. It's great for testing and debugging, and in startup land, putting out fires in production (whoops!).

## Keeping the Dataclass, but Still Using FastAPI

Well, step 1: we need to convert the dataclass object to an object that subclasses the Pydantic BaseModel class. Why? Because that's what FastAPI expects. Well that's not so hard, but what if I'm already using the `Potato` class in other places? I would like to preserve that interface so I don't have to go rewriting a bunch of code.

With this constraint the closest thing I have found thus far is to use a Python library called `dacite` to avoid having to change the `Potato` class from a dataclass to subclassing the Pydantic BaseModel.

```py
from dacite import from_dict, Config
from fastapi import Request
from dataclasses import asdict
from starlette.responses import JSONResponse

router = APIRouter(prefix="")

@router.post("/potato", tags=["Potato"])
async def create_image_metadata(
    request: Request,
):

    data = await request.json()
    if type(data) != dict:
        return JSONResponse(status_code=400, content={"message": "Invalid JSON"})

    try:
        potato = from_dict(
            data_class=Potato, data=data, config=Config(cast=[Enum])
        )

        new_potato = await potato_dao.create_potato(potato)
        return asdict(new_potato)
```

Unfortunately, the down side is you lose out on the auto generated documentation by Swagger/Open Docs. You also don't get any validation that would generally occur with Pydantic type hints. At which point, you basically are now bending over backwards to use FastAPI and get none of the benefits. You may as well just revert back to Starlette, which is what FastAPI is building on.

## Ditching the dataclass, and Subclassing Pydantic BaseModel

So, here's where I landed. I wanted to use FastAPI, but I had existing code that defined types using the dataclass decorator. Maybe someone with a bigger brain than I could write a function as follows:

```py
from pydantic.dataclasses import pyd_dataclass

@dataclass
class Potato:
    x: str
    y: int

tater = Potato(x='bob', y=69420)

# Doesn't work :(
pydantic_tater=pyd_dataclass(tater)

# TODO: magic function
pydantic_tater = dataclass_to_basemodel(tater)

```

So, I gave up. Instead, I just did the following:

```py

import pydantic import BaseModel

class Potato(BaseModel):
    x: str
    int: y

```

And from there I bit the bullet and converted all of the objects that were using dataclass to BaseModel, and changed the interface.
