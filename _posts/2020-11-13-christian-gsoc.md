---
layout: article
title: Looking Back on a Summer of Code 
subnav: blog
comments: true
tagline: "I have been active on Github since 2013 and although I have participated in various projects, such as serving on the security team for Arch Linux, I have never really contributed a large amount of code..."
author: 'Christian Rebischke'
categories:
  - '<a href="/projects#in-toto">in-toto</a>'

---

*Note: For 15 years, the Google Summer of Code program has given student developers an opportunity to spend their summer break working with an open source organization on a three month programming project. This year, Christian Rebischke, a 27 years old Master’s student from Germany (Technical University of Clausthal), spent his Google Summer working on in-toto. Christian came to the in-toto project through his affiliation with the Cloud Native Computing Foundation (CNCF). In this post Christian shares a little of his experience with the Summer of Code program.*

I have been active on Github since 2013 and although I have participated in various projects, such as serving on the security team for Arch Linux, I have never really contributed a large amount of code to these initiatives. Most of my contributions were smaller fixes or documentation enhancements. As a result, when I first saw the announcements for [Google Summer of Code](https://summerofcode.withgoogle.com/), I hesitated for a long time. However, a few people I met in the [Internet Relay Chat (IRC)](https://en.wikipedia.org/wiki/Internet_Relay_Chat) encouraged me to try it. I was completing my master’s program and so, realizing this might be my last chance, I decided to go all-in and applied to three projects: Prometheus, Flux and [in-toto](https://in-toto.io). I focused on projects inside of the CNCF because my dream job would be in the realm of Site Reliability Engineering. I knew little about in-toto except that it is related to the [Reproducible Builds](https://wiki.archlinux.org/index.php/Reproducible_Builds) efforts of Linux Distributions, because Arch Linux is  going through the same process. But I never really had a close look at the project, so it was something of a surprise when in-toto was the project that chose me.

As it turns out, the choice was an appropriate one for me.  I have served as a package maintainer for several years now, and in that capacity, supply chain security has long been a major concern. As a package maintainer I try to ensure that all users can be certain they are using the package the project owners originally conceived. This only works with a secure supply chain, and providing that seems to be a big problem for many developers. Otherwise, why do so many projects lack standards, like signed tarballs? Or, even if a signed tarball exists, there are so many other key factors that ensure a supply chain is secure that one secure step doesn’t mean that the final product is what the owner originally envisioned. A secure supply chain begins with the first letter of code and ends with the deployment of the product on a target system. Managing all of these steps is indeed difficult and I can fully understand why developers have so many problems with it, especially if you have to deal with various artifacts on each step of your supply chain, like input and output of compilation or code verification.

I started my Summer of Code journey in the CNCF in-toto Slack channel in May 2020. The first task I worked on was getting to know the specification and the main objective of my upcoming internship. I learned that in-toto was born as a research project in the [Secure Systems Lab](https:/ssl.engineering.nyu.edu/) of New York University, under the guidance of  [Professor Justin Cappos](https://engineering.nyu.edu/faculty/justin-cappos) and that it focuses on securing the supply chain. The motivating idea is that every step in a software supply chain should be verifiable, starting with signed commits, through build servers and continuous integration or continuous deployment to the end user.  in-toto solves this objective via defining links, each responsible for generating in-toto link data. These links are files in JSON format that represent a step in a software supply chain, and they testify which person or machine completed  a particular step in a software supply chain. Each of these steps can be signed and later verified. My task has been to port this functionality from its Python implementation to the Go implementation.

My contributions began with a few small pull requests to the Go implementation that cleaned up issues found by go-lint. I also took a look at existing pull requests that had stalled somewhere along the line. In June 2020, having already gotten more confident with the code base, I started with bigger adjustments.  My primary tasks included signing generated link data via signature algorithms, as specified in the in-toto specification, and providing full support for RSA-PSS, ED25519 and ECDSA.

Throughout this work I was mentored by four in-toto project members: [Lukas Pühringer](https:/ssl.engineering.nyu.edu/people#lukas_puhringer), [Trishank Karthik Kuppusamy](https://engineering.nyu.edu/alumni/trishank-kuppusamy), [Santiago Torres-Arias](https://www.cerias.purdue.edu/site/people/faculty/view/3153), and Professor Cappos. For communication we used the CNCF in-toto slack channel and Github's comment functionality in issues and pull requests. This worked pretty well for us, even under the circumstances that some of my mentors lived in another time zone. The time zone differences, though, actually became a benefit. Lukas was also in Europe, so I could talk with him early on, and later on I could ask my mentors in the US for direct feedback. This distributed the work equally and no mentor got too distracted by my questions.  We had some great times hacking together on the pull requests. The feedback I received was always on point and I really enjoyed working with the community.  I think that, in all my time contributing to open source projects, I have never experienced such a professional and friendly community. 

There were other positive takeaways from this experience. It has long been a dream of mine to contribute more than just a few lines of code to a project. The Google Summer of Code was my first successful try to deep-dive into a foreign code base and I feel I have definitely increased my skills in reading foreign code, getting familiar quickly with a code base, and communicating with project developers. I also found and submitted a fix for a bug in the  Go crypto library that led to a nil pointer dereference and invalid memory access, and I attended my first [Kubecon](https://www.cncf.io/events/kubecon-cloudnativecon-europe-2020/). Though sadly the conference was online-only due to the Covid-19 outbreak,  I still enjoyed every minute of it.  I even found some other interesting projects to work on in the future, like [TUF (The Update Framework)](https://theupdateframework.io/). I have already submitted my first pull request to the TUF Go implementation and I plan to keep working on the in-toto Go implementation. 

In summary, I think Google Summer of Code brought me to a project that I think is important, interesting and challenging all at the same time. Moreover, I really think that this project brings me one step closer to my future career goal. The Go implementation and the proximity to the CNCF will definitely help me in increasing my Site Reliability Skills. The in-toto Go implementation has been the project I was always looking for, one that unites my personal highlights of open source: an awesome, friendly and helpful community, a do-able challenge that helps me to grow, and a project with a higher purpose. 

I do not want to finish without honouring my four mentors: Lukas Pühringer, Justin Cappos, Santiago Torres-Arias and Trishank Karthik Kuppusamy. They always reacted quickly when needed and they always gave me the right hints, when I had difficulties understanding the specification or the code base. 
I could not be happier.

*Editor’s note: When asked to comment on Christian’s work, Torres-Arias observed, “I can’t think of a more successful Google Summer of Code experience than Christian’s in the in-toto project. I believe this not only because of the raw contributions to the in-toto golang codebase, but also because it is a perfect example of the values that GSOC is working to foster: allowing a young open source enthusiast to integrate themselves with an open source project. As always, it is very rewarding to see a contributor take on small tasks, meet people, grow initiative and eventually become a esteemed member of the community for an indefinite amount of time.”*

