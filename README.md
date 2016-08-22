# Aapo-audit

Aapo as a case study for audit ponderings

## Background

[University of Oulu](http://www.oulu.fi/yliopisto/) and
[Futurice](http://futurice.com/) are jointly developing Aapo 2.0 mobile
application for students. Aapo 2.0 is continuation for
[Aapo](https://aapo.oulu.fi/).

[OUSPG Open](https://github.com/ouspg/ouspg-open), in the spirit of
the [Google Summer of Code](https://developers.google.com/open-source/gsoc/),
provides summer activities for people interested in Information Security.

Aapo was used as an subject for open & educative security audit.

## Summary

This was a collaborative, open and time limited audit of the Aapo system.
Audit took place in three phases (3 days). First phase concentrated on the
scoping of the audit. Second phase was about the design and backend services.
Third phase added in some hands on verification of the achieved common
understanding. During the whole process Katakri was used as a frame of
reference.

Together with the audit experts and the builders of the Aapo we walked
through Aapo's security goals, design principles and some implementation details.
This added to the depth of the understanding and managing the security of the
Aapo system. This will help in further development and operations of the Aapo
services.

## Assets

During the discussions, three assets were discovered for protecting:

* Privacy of the users
* Due process of students (e.g. their records should be protected)
* End-points of the users.

Ari Vaulo also brought up the wider aspect of protecting the Oulu University's
Information systems. Indeed Aapo should not create new opportunities
for attacking University Systems. However, we will refrain from promoting
the Oulu University information systems in general to the list of protected
assets, as it would muddy the responsibilities.

## Aapo's Security-Related Design Principles

* Usernames and passwords are not stored in Aapo.
* University production systems should not be exposed to the internet directly,
  and without input sanitation.
* Aapo's own backend database uses different privileges based on the need.
* Aapo's backend has limited privileges towards Oodi.
* Aapo implements mechanism to prevent changing of identity. Implementation
   uses one-time session key, which is required in transactions.
* All requests are logged.
* Aapo's backend implements input sanitation by parsing and reconstructing
  queries before forwarding deeper in to the system.
* Aapo system has no direct filesystem write-access in the Aapo's backend
  servers.
* University firewall allows only connections to the frontline server's (A1)
  https-port (TCP:443).
* Backline-server (A2) HTTPS-service listens only connections from frontline
  server (A1).

For the A1 and A2 explanations, please see
[Aapo Architecture Picture](aapo-architecture-kataktri.jpg)

## Notes from the sessions

* [First Session](session-1.md)
* [Second Session](session-2.md)
* [Third Session](session-3.md)
