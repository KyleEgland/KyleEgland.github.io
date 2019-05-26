---
layout: post
title: Back to Frameworks
---

# Web App Development (Learning) Status

I've been working on web app development in my free-time (ref previous posts) and found that doing things "from scratch" is just too much "re-inventing the wheel".  Therefore, I've turned on my heals and walked back into frameworks.  I've been working with Flask for quite some time now and have rather enjoyed it.  The modular nature of it and breadth of available ad-ons is quite profound.  Additionally, since I've also been working with APIs lately, I've found it necessary to create some test rigging - the subject of this post.

## Flask API Call Test
#### The Intent

I'm building an interface to aggregate some information but, wanted to be able to play with the interface to ensure that my processing and handling of information is sound within flask.  This project utilizes flask and some jQuery (look in the credits for original code explanation done by Pretty Printed on YouTube).  The gist is, the app presents a form (well two) to send an authorization request to an API endpoint.  The response from the endpoint (in this case) should contain a bearer token which the application stashes in the session object.  The second form part of the page presented by flask allows for the input of an endpoint on the API from which the token was received.  Once a form request is made (and a token has been obtained) a get request is sent to the API endpoint specified with the bearer token.  The response from the api is then passed to jQuery which parses it onto the page.

That's basically all there is to it.  Unfortunately, there's not enough time give a better write-up (I know...excuses...).  It was quite a lot of fun to create.  Give it a try, maybe you'll find it useful.

Thanks for reading my words and checking out my work :)

Kyle
