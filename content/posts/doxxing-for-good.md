+++
title="Doxxing for Good"
date=2021-03-06
extra.tldr="I found an unsecure webcam online, and called the guy to turn it off, and he did."
+++

# The Story

I was watching Zack Freedman on YouTube, an up and coming hardware hacker. He mentioned Shodan, which apparently is a directory of devices accessible via internet. They include industrial controllers, webcams, databases, and video games, purportedly. I checked it out and couldn't find any live streams, which reminded me of a site I have visited before insecam.org. So I went there and I browsed around a bit and found a stream of a man sitting as his computer in what the webcam labeled "OFFICE". 

Before I came across this stream, I saw other streams with people. For example, I saw a stream of a casino in San Diego where some people were at slot machines. In another, I saw a man setting up what the webcam labeled "Big Grow Tent" in Arizona, which he eventually panned over to marijuana growing inside one of those highly reflective plastic lined grow tents. I saw another stream where people were eating outside at what seemed to be a resort in Colorado under partial construction. These were all in public places though where the Supreme Court would say they cannot have a reasonable expectation of privacy. So it felt ok. Sort of like people watching in a park, except they're 500-1000 miles away and can't see you. But anyways, continuining on.

With the stream of the man in the "OFFICE" it didn't really seem like an office. There was a 3D printer and another desk with a blanket across the chair, which was probably most likely this man's significant other. This didn't exactly seem like an office of a business. It irked me that this guy, who was probably just browsing the internet, could be surveilled by some complete stranger hundreds of miles away from him, in what seemed to be his home office. So I ended up basically doxxing this guy. I was able to figure out his name by visiting port 80 of the IP address from the camera stream. On that page, there was a link to a domain that was the man's full name dot com. So from there I was off to the races basically just using Whitepages and the like to get a phone number to call the guy. After a couple of these websites, I called the number that it listed.

{{ img(path="/assets/images/posts/d4g.png") }}

The weirdest part was watching him pick up the phone as I called to inform him that his office webcam was completely exposed to the public. I think he was a little shocked and probably scared, so the conversation was awkward and breif, but I watched him disable the live stream, which is no longer accessible. A few minutes later he texted me asking me how I knew all this, and I gave him all of the relevant information. 

# Final Thoughts

There are a few takeaways from this experience:
1. Don't put webcams in your home. Just don't.
2. IoT and the like continue to prove to threaten the privacy of people. Even if you're technically savvy. The guy in this story had a 3D printer in his office, which I would argue is technically savvier than most people. 
3. There is tons of information about us online. I found this guy's cell # and address via all publically accessible online resources. This is scary.

I feel conflicted about this experience. Because in order to preserve this man's privacy, I had to invade it further via probing into his identity. Ultimately, the ends probably justify the means, but still, I would feel pretty scared if I got a phone call out of the blue while I was watching YouTube videos that I was being watched.

Edit (3/11/21): Photo blurred for privacy concerns.


