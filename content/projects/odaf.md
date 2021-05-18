+++
title="ODAF (Omnidirectional Autonomous Fishbowl)"

date=2021-05-13

[extra]
toc = true
thumbnail="/assets/images/projects/odaf/omnibot-v40-cropped.gif"
status="In Progress"
description=""
tools=["Arduino/C/C++", "Python", "Vanilla Javascript", "React", "Konva.js", "Fusion 360", "EasyEDA",]
+++

{{ img(path="/assets/images/projects/odaf/omnibot-v40-cropped.gif") }}

# WTF is an ODAF?

An ODAF, is a multi-year joke project started during a conversation at the Santa Clara University Graham Hall front desk in Winter Quarter 2017. A conversation along the lines of "Bro wouldn't it be hilarious if you put a fishbowl on a roomba?" was had. From there I thought, in fact, it _would_ be hilarious if such a robot existed. And so began the multi-year journey of building **ODAF**, an omnidirectional autonomous fishbowl.

# Inspiration

Before I dive into the project, I would like to acknowledge my two sources of inspiration, from whom I stole many ideas:

- Scot Tomer ([blog](torque.github.io)) - Scot's Master's thesis from the SCU RSL (Santa Clara Univeristy Robotics Systems Lab) was called [Decabot](https://magazine.scu.edu/magazines/fall-2017/here-come-the-decabots/). This madman built 10 omnidirectional robots to provide the RSL a testbed to experiment with robotic swarm control techniques. My first iteration shared many items in its BOM (bill of materials). Fun fact, I now work with Scot at OnePointOne, Inc and get to witness his engineering prowess daily.
- Kris Temmerman - Kris posted 4 [YouTube videos](https://www.youtube.com/watch?v=Q4cmc4eKXr0) featuring 2 omnidirectional robots he built. I highly recommend watching his videos if you are interested in robotics or the Maker movement in general. I am blown away by Kris's abilities, and hope to maybe one day be half the engineer he is. My second iteration stole many ideas and components from his design.

# The Early Years

Since this project was started, 4 years have gone by. I only work on this project when I am bitten by the bug, and as a result it has drawn out over the years. In the photos below I will try to give an idea of where it all started, and how things progressed to where I am with the project today.

{{ img(path="/assets/images/projects/odaf/6.jpg") }}

Like many projects, this too started on a whiteboard. On the lefthand side is a list of features that were desired, many of which were purely out of scope. For example, suspension, or water cooling would be cool, but do I really want to spend thousands of dollars and hours to prove that out? No. So we're left with the features that at the time I thought would be dead simple to implement under the hilariously labeled "v0.1":

- omnidirectional wheels
- support the weight of a few gallons of water for the fish
- can be disassembled for maintenance (i.e. no glue allowed)
- fish bowl is low to the ground to keep center of gravity low

"Easy enough!" Thought the 19 year old. Little did I know what journey I was embarking on.

## Iteration 1 - A Rough Cut

{{ img(path="/assets/images/projects/odaf/17.jpg") }}

Here was how I planned to lay out the robot. At this point I was just trying to get a feel for how much space I would need. Seems simple enough.

{{ img(path="/assets/images/projects/odaf/14.jpg") }}

Here I had gone ahead and laser cut some acrylic and well as tried to start figuring out where spacers would go to help support the upper layer of the robot that would help stabilize the fish tank.

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/0.jpg") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/2.jpg") }}
    </div>
</div>

Here we can see 2 new acrylic sheets were laser cut to form the chassis. Additionally, some motor mounts were also cut out from acrylic and hot glued to keep everything in place. Sadly, you will notice that the wheels in the second photo barely make more contact with the ground than the acrylic it is mounted to. As a result, I had to ditch this design because it simply wouldn't get enough traction to move.

## Iteration 2 - Bigger Wheels

{{ img(path="/assets/images/projects/odaf/23.jpg") }}

Here you can see the next version which features much larger wheels and motors.

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/27.jpg") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/10.jpg") }}
    </div>
</div>

Here, the robot is wired and ready to do some basic testing. The encoders have not been wired, but I started implementing the inverse kinematics to drive the robot via command line, as well as by tilting my phone.

At this point, I had selected L298N's as my motor driver, or in other words: Amazon's Choice Motor Driver. Same thing with the LM2596 buck converters. While these components were great for prototyping, there was no chance I would be able to fit a fish tank on top of this rats nest of wires.

## Iteration 3 - Planning in 3D

The most I had planned out the robot at this point was the footprint of the components to be laser cut in the acrylic. It was clear I could no longer get away with 2D planning. Over a 3 day weekend I shut myself in my room and wrestled with Fusion 360 to produce the following 3D model.

<!-- Ok I just ordered a 500 GB 980 Pro EVO off of Newegg because my windows computer SSD is broken and I can't overwrite the files, but I also want to copy them before I wipe it... And because I need to torrent video editing software to get my gif of my robot into a 16:9 ratio. So I just spent $130.79 to buy this thing, and until that gets here and I install Adobe Premeire or whatever software you can easily torrent, I have to stop working on this blog lol. -->

{{ img(path="/assets/images/projects/odaf/omnibot-v40-cropped.gif") }}

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/bottom.jpg") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/layers_off.jpg") }}
    </div>
</div>

And after some time, I was able to laser cut the acrylic for the newly designed robot, and assemble the new version.

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/1.jpg") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/3.jpg") }}
    </div>
</div>

At this point in my life, I had just graduated with my BS in Computer Science & Engineering. I was going into my 2nd summer internship at Ford Motors, and in the fall would start my 2nd year of my 5 year BS/MS program at SCU. Here I let the project sit for another 3 months before I bothered touching it again.

## Iteration 3, Phase 2 - Wiring the Electronics

The main motivation behind 3D modeling the robot was so that I would have a solid footprint to laser cut the robot chassis, and not have any issues (although a few times I did have to make some extra holes). Sadly, I quickly realized that because I didn't think much further ahead I was bitten again by not planning ahead correctly.

I neglected to model any of the electronics and their wiring in my 3D model. I figured, "that's a problem for future me", and it sure was!

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/5.jpg", width="420px") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/21.jpg", width="420px") }}
    </div>
</div>

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/13.jpg") }}
    </div>
</div>

I probably spent a total of 30 hours soldering and desoldering and snipping and folding this garbled mess of copper wire and perf board. I thought maybe I can brute force the solution by carefully fenagling these solid core wires. Eventually, I gave up realizing it was near impossible to solder all of the connections I needed, without burning the insulation off of existing wires with my soldering iron when trying to add new connections.

This point was around September 2019. I was very involved in my master's program and had also temporarily moved in with my girlfriend. As such, I no longer had the time or access to my robot. This was the longest break I had taken from this project, roughly spanning a period of 11 months until July 2020. Toward the latter half of this period, I recall feeling sad that I couldn't work on this project when the energy sprung up.

Once I graduated with my MS, I moved into a place on the Santa Clara/Sunnyvale border and was able to recollect my robot, and resume the project. After being deprived of creative expression via robotics for 11 months, I was enthusiastic to resume the project.

I started by tackling the wiring issue again. The issue was twofold:

1. There was simply not enough real estate on the perf boards to lay out all of the electronics that I needed for the robot.
2. Hand soldering the wires was simply not dense enough for all of the connections needed.

The solution: Build a PCB (printed circuit board) to connect the components, and create a new 3D model to determine the footprint of a PCB.

{{ img(path="/assets/images/projects/odaf/pcb_model.jpg") }}

So here was the new footprint. It would be a rather strange shape, but it would take advantage of as much real estate that was available on this third of the robot chassis.

I reached for yet another Maker tool, which was EasyEDA, to lay out and route my PCB. It was in fact very straight forward to use, and integrated easily with JLCPCB, which is a PCB manufacturer in China that produces PCBs for ridiculously cheap prices. The wiring schematics for the PCB can be seen below:

{{ img(path="/assets/images/projects/odaf/Sheet_1.svg") }}
{{ img(path="/assets/images/projects/odaf/Sheet_2.svg") }}

Unfortunately, I lost the PCB routing (which led to some interesting reverse engineering later on). However, here was how the PCB turned out!

{{ img(path="/assets/images/projects/odaf/9.jpg") }}

And after adding all of the components:

{{ img(path="/assets/images/projects/odaf/25.jpg") }}

<!-- {{ img(path="/assets/images/posts/weekend-in-wine-country/hike-top-view.jpeg", width="420px") }} -->

<!-- This process lends itself to having to reverse engineer how I built or designed something because I forgot how I did it, and I didn't do a great job of keeping records (or for in the case of my PCB, lost files). This -->
