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

- Scot Tomer - Scot's Master's thesis from the SCU RSL (Santa Clara Univeristy Robotics Systems Lab) was called [Decabot](https://magazine.scu.edu/magazines/fall-2017/here-come-the-decabots/). This madman built 10 omnidirectional robots to provide the RSL a testbed to experiment with robotic swarm control techniques. My first iteration shared many items in its BOM (bill of materials). Fun fact, I now work with Scot at OnePointOne, Inc and get to witness his engineering prowess daily.
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

## Iteration 3 - \<insert clever title here\>

The most I had planned out the robot at this point was the footprint of the components to be laser cut in the acrylic. It was clear I could no longer be able to get away with 2 dimensional planning. Over a 3 day weekend I shut myself in my room and wrestled with Fusion 360 to produce the following 3D model.

Ok I just ordered a 500 GB 980 Pro EVO off of Newegg because my windows computer SSD is broken and I can't overwrite the files, but I also want to copy them before I wipe it... And because I need to torrent video editing software to get my gif of my robot into a 16:9 ratio. So I just spent $130.79 to buy this thing, and until that gets here and I install Adobe Premeire or whatever software you can easily torrent, I have to stop working on this blog lol.

{{ img(path="/assets/images/projects/odaf/omnibot-v40-cropped.gif") }}

<div class="columns is-centered">
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/1.jpg") }}
    </div>
    <div class="column has-text-centered">
        {{ img(path="/assets/images/projects/odaf/3.jpg") }}
    </div>
</div>

<!-- {{ img(path="/assets/images/posts/weekend-in-wine-country/hike-top-view.jpeg", width="420px") }} -->

<!-- This process lends itself to having to reverse engineer how I built or designed something because I forgot how I did it, and I didn't do a great job of keeping records (or for in the case of my PCB, lost files). This -->
