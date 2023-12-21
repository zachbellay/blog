+++
title="Always Be Refactoring"
date=2023-12-20
extra.tldr=""
+++

{{ img(path="/assets/images/daily/always-be-refactoring/abr.png", center="True")}}


>"A. Always. B. Be. R. Refactoring. Always Be Refactoring." 
>
> -Alec Baldwin in Glengarry Glen Ross

My first job out of college was at an indoor vertical farming startup. I did computer vision and machine learning and it was the hottest, sexiest stuff I had dreamed of working on. But, as a junior dev, I had no idea wtf I was doing, and was piecing together "good" software development practices. 10 months into my job at Rinse, I feel much more confident about how to write good code than I did before.

This is largely a testament to the great mentorship and engineering culture at Rinse. So, having been shaped by a scrappy seed stage startup and a 10 year old established startup here are **4 coding philosophies I live by now**:


- **Overzealously applying DRY (don't repeat yourself) is a bad idea**: Once you repeat yourself 3 times, then it is time to consider a new abstraction. But I've found that oftentimes I write code, copy paste it and tweak it, and have 2 pieces of code that are similar, and then I never need to touch it again. This is really an extension of YAGNI (you aren't going to need it). Sometimes creating "perfect" code is actually an express lane to creating shit code.
- **Done is better than perfect:** Maybe it's a bad sign, but I think users should have to complain that something is bad before I go in and fix it. Because in my experience, I can spend months perfecting code only to deploy it and no one even uses the feature. So I'd rather just ship the darn thing, and if anyone even bothers to use it and complains, then I'll go back and fix it. 
    - this really is a topic of infinite debate since this reduces down to the chicken-egg debate. In other words, is it that people don't use my software since it sucks, or my my software sucks because people don't use it?

<!-- - **Write code that is good enough:** and if it even survives the first few minutes of being around, maybe someone else will read it and tell you hey this ought to be refactored. Or maybe you will actually be coming in to write a new feature and say to yourself, hey this is ripe for a refactor.
- write code with refactorability in mind. That doesn't mean all code I write will be refactorable since I'll write plenty of one off scripts, prototypes, or whatever (these days this is ChatGPT's job). But when I'm at work I pretty much know that this will get extended or changed at some point, probably soon, my me. So I've been much better about  -->

- **Write code that is good enough,** and refactor it if/when you encounter a problem with your first approach. This means writing "stupid", "simple" code that is just if statements, for loops, constants, etc. Nothing fancy, no inheritance or mixins or function composition. At least at first. You can start doing programming gymnastics  once you have a good reason to.

- **Simple is better than complex:** When I first really grasped pythonic functional programming, such as list comprehensions and using the `map` and `filter` functions, I used them everywhere. But then I would come back to my code later and think, "God this sucks, why didn't I just use a for loop". And now I try to deliberately embarass myself by writing code so simple an APCS student could understand it. And to all your try hard FP-fans out there, sorry I'm not a 0.1% mega-genius OCaml, Lisp, Haskell FP hacker, but the rest of us think imperatively, and also have shit to do. Btw, if you haven't read [grugbrain.dev](https://grugbrain.dev), it's this sentiment but with much more depth.

Lastly, I'll leave you with 1 analogy:

- **Refactoring code is like putting food in your fridge:** When there's nothing in there, you can just throw your food in there and it's no big deal, no need to worry about what goes where. But keep haphazardly throwing stuff in there and eventually your door won't close, and your food will rot. So instead, once you have a few items, you should reorganize your fridge so that things can be stacked on top of each other but also take into account what you access frequently.
- Now coming from the other side, if you're too prescriptive and say "hey the middle shelf is only allowed to have one carton of 12 brown eggs in this 14"x5" area". But then National Quiche Appreciation Day rolls around and your roommate decides to throw a 50 person Quiche Party, well now you're fucked because your made up rule isn't letting your roommate stockpile 12 dozen eggs to serve her 50 hangry guests. 
- So moral of the story is? A smell mess is ok, clean up your mess before it gets too big, and don't be clean freak.
