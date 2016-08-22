# 2016-08-16 - Hands-on session

The hands-on session started out with another walkthrough of the Aapo
architecture. A clarification to earlier drafts:

* A2 does not fetch bus timetables. The Android client fetches bus schedules
  directly from oulunliikenne.fi(?), as well as included a list of links to
  university services. These should be checked for cookies or other
  authentication credentials.

Some new items were discovered:

* A2 is used for push notifications with Google and Apple services
  (exam registrations, lecture room changes, ...).
* A2 sends email notifications via Oodi web services (contact us, weekly
  course feedback in the Aapo Android app).

Quick hands-on testing of the certificate validation in the iPhone app was
tried with [Mitmproxy](https://github.com/mitmproxy/mitmproxy) - to no effect.
The Android phone did not find our adhoc wlan, so it could not be tested.

Testing the certificate checks in the new
[Caleidon](http://www.caleidon.fi/en/) Tuudo, as well as between T1/A1/A2 is
recommended. The new Tuudo app adds another middle layer to the model, which
might remove the need for A1. Fuzzing the REST API is another recommendation.

The web app seems a bit redundant, as it only adds another UI to Oodi.
It should be checked for web app faults, eg. according to
[OWASP](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)
guidance. The upcoming three-actor model with [Futurice](http://futurice.com/)
and [Caleidon](http://www.caleidon.fi/en/) highlights the importance of
clarifiying responsibilities for development, administration and responding to
security defects and incidents.

Some random remarks:

* Firewalling external accesses from A1/A2 would diminish post-exploitation
  possibilities (reverse shells etc).
* In modern system building actions such as fetching external inputs and doing
  notifications are often compartmentalized to containers etc.
* After the introduction of Tuudo, the old applications as well as their API:s
  should be deprecated and eventually removed.
