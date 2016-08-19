# aapo-audit
Aapo as a case study for audit ponderings

# Background

[University of Oulu](http://www.oulu.fi/yliopisto/) and
[Futurice](http://futurice.com/) are jointly developing Aapo 2.0 mobile
application for students. Aapo 2.0 is continuation for
[Aapo](https://aapo.oulu.fi/).

[OUSPG Open](https://github.com/ouspg/ouspg-open), in the spirit of
the [Google Summer of Code](https://developers.google.com/open-source/gsoc/),
provides summer activities for people interested in Information Security.

Aapo is used as an subject for open & educative security audit.

# 2016-06-14 - Kick-off

Jani Kenttälä (@evilon) and Marko Laakso (@ikisusi) had a initial kick off
meeting with the current [Aapo](http://www.oulu.fi/yliopisto/node/37547)
project team about an educational security audit. We plan to take two
hackathon type sessions during the summer on auditing Aapo in open and
educational fashion with help from invited external experts.

In the kick-off meeting Jani and Marko got
a background briefing on the orignal and new Aapo and good past and future
work around it by the [Caleidon Team](http://www.caleidon.fi/en/) and their Tuudo.

Aapo is the second critical service right after Oodi for prodiving student services.
Neither students records nor personal device should be exposesdto any extra risk
due to Aapo.

Ari Vaulo drew as the overall architecture of the past, present and future (Aapo).

![Aapo Architecture at the Kick-off](aapo-architecture-kickoff.jpg)

Ari goes through of some good design principles already applied and
some concerns identified by the makers themseles:

 * Identity is locked on the auth, no way to post-auth masquerade :)
 * A2 fetches bus timetables and restaurant menus from external world
 and they get presented in the Aapo itself. :(
 * Authentication tokens (user & password) considered most critical.
 * Concerned about the Web Aapo and directories in that service.

We agree to continue with more technical analysis with help of Katakri next
time.

# 2016-06-21 - Katakri

We did a dive into security of the Aapo with help of [Katakri](http://formin.fi/public/default.aspx?contentid=328713&contentlan=2&culture=en-US).

Battle hardened auditors Mikko Kenttälä (@Turmi0) and Mika Seppänen (@mseppanen) of [Synopsys](http://www.codenomicon.com/) visited us to workshop with us and walk us through Katakri in practice.

Aapo project team was represented by Laura Saukko, Kaarlo Määttä, Matti Suuronen and Ari Vaulo of University of Oulu and Hannu-Pekka Heinäjärvi of [Futurice](http://futurice.com).

Diagrams were (re)drawn and [detailed notes](notes-katakri.md) were kept.

[![Aapo - technical discovery session](http://img.youtube.com/vi/RwTHZqhxExU/0.jpg)](http://www.youtube.com/watch?v=RwTHZqhxExU)

*Click the image above to watch a timelapse from the technical discovery session.*

# 2016-08-16 - Hands-on

The hands-on session started out with another walkthrough of the Aapo architecture. A clarification to earlier drafts:

 * A2 does not fetch bus timetables. The Android client fetches bus schedules directly from oulunliikenne.fi(?), as well as included a list of links to university services. These should be checked for cookies or other authentication credentials.

Some new items were discovered:

 * A2 is used for push notifications with Google and Apple services (exam registrations, lecture room changes, ...).
 * A2 sends email notifications via Oodi web services (contact us, weekly course feedback in the Aapo Android app).

Quick hands-on testing of the certificate validation in the iPhone app was tried with [Mitmproxy](https://github.com/mitmproxy/mitmproxy) - to no effect. The Android phone did not find our adhoc wlan, so it could not be tested.

Testing the certificate checks in the new [Caleidon](http://www.caleidon.fi/en/) Tuudo, as well as between T1/A1/A2 is recommended. The new Tuudo app adds another middle layer to the model, which might remove the need for A1. Fuzzing the REST API is another recommendation.

The web app seems a bit redundant, as it only adds another UI to Oodi. It should be checked for web app faults, eg. according to [OWASP](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project) guidance. The upcoming three-actor model with [Futurice](http://futurice.com/) and [Caleidon](http://www.caleidon.fi/en/) highlights the importance of clarifiying responsibilities for development, administration and responding to security defects and incidents.

Some random remarks:

 * Firewalling external accesses from A1/A2 would diminish post-exploitation possibilities (reverse shells etc).
 * In modern system building actions such as fetching external inputs and doing notifications are often compartmentalized to containers etc.
 * After the introduction of Tuudo, the old applications as well as their API:s should be deprecated and eventually removed.

# Summary

We carried out a collaborative and open mini audit of the Aapo system.
Audit took place in three phases. First phase concentrated on the
scoping of the audit. Second phase was about the design and backend services.
Third phase added in some hands on verification of the achieved common
understanding. During the whole process Katakri was used as a frame of
reference.

Together with the audit experts and the builders of the Aapo we walked
through Aapo's security goals, design principles and some implementation details.
This added to the depth of the understanding and managing the security of the Aapo
system. This will help in further development and operations of the Aapo
services.


