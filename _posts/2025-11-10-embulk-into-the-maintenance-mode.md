---
layout: posts
title: Embulk into the "maintenance mode"
date: 2025-11-10
description: "The Embulk project is going into the maintenance mode. Please do not expect that Embulk will be maintained actively. Even if you submit a pull request to the Embulk project, it may not be reviewed nor merged."
author: "dmikurube"
---

On October 15, 2025, I sent the following email to those who were in the GitHub organization: [https://github.com/embulk](https://github.com/embulk)

```
(... snip: greetings in Japanese ...)


To all who have been or are involved in Embulk, and who belong to Embulk's GitHub
organization,

I'm sending this email to addresses confirmed publicly in Embulk-related git log,
or addresses confirmed individually.

The English message follows the Japanese part.


(... snip: the message in Japanese ...)


Long time no see. This is Dai.


You might have seen some recent topics about RubyGems closely.

https://rubycentral.org/news/rubygems-org-aws-root-access-event-september-2025/
https://andre.arko.net/2025/10/09/the-rubygems-security-incident/

I do not know what is correct or who is at fault, and I am not in a position to
comment on it.


However, I feel that the biggest lesson we should learn from this case is:
"In an open-source project involving multiple stakeholders, we should establish
and formalize clear project governance that reflects the reality, while the community
can still discuss it peacefully and democratically — **before** such issues arise."

"Especially when security is a significant concern there, or when money and/or
for-profit company(s) are involved."


As for the open-source project Embulk, I too have stepped down, and already been
inactive as a maintainer. The situation has been like "we have no active maintainers"
for about six months already.

https://www.embulk.org/articles/2025/04/11/dmikurube-is-stepping-down.html


In Embulk, now, the (even though inactive) "maintainers" are practically:
* Only I and Sato-san are looking at the areas close to the Embulk core.
* We sometimes ask @hito4_t -san to take a look at JDBC-related things.
* Along with them, embulk-output-bigquery has a couple of its own independent
  maintainers.


When I was still at Treasure Data, I was doing some governance and administrative
actions such as establishing the Core Team entity as a form of governance, and
removing some individuals (including some in-TD and ex-TD persons) from the GitHub
organization after some communications when they weren't actively participating in
the community.

I, however, have left TD, and became inactive as a maintainer. It is getting harder
for me to continue such governance and administrative actions with confidence —
especially with many inactive members in the GitHub organization.

If the situation continues for a couple more years, it wouldn't be surprising to see
a problem similar to the RubyGems case mentioned at the top of this email.
(Embulk is not depended on by so many users like RubyGems, though.)


The maintenance of Embulk has already been almost suspended in practice, although
it appears to be continuing on the surface. For example, even if a security-related
report comes to us, it would be hard for us to handle it timely and properly.


Therefore, in order to "establish and formalize clear project governance that
reflects the reality, while the community can still discuss it peacefully and
democratically," I think about transitioning Embulk into the "maintenance mode"
roughly with the following measures:

1. Minimize the GitHub organization and the Core Team members to only "those who are
   willing to continue participating to some extent going forward".
    * What we want for "those who are willing to continue participating to some
      extent going forward" would be just "showing your membership, name and
      affiliation publicly in the GitHub organization" and "willing to spend a
      dedicated time as one of the responsible members in the party when
      something happens and discussions are needed".
    * I guess, however, you already know that even only these are still hard.
2. Agree that "we can no longer continue managing this project actively" among the
   remaining members.
3. Reduce the scope of what we need to manage (ex. Zulip chat).
4. When someone raises their hand to take over Embulk, discuss it among the
   remaining members.
5. Declare the "maintenance mode" with these measures above, and announce it to
   the public.
    * I think about containing this email itself, almost as-is, in the announcement
      at https://embulk.org/ and else.


What do you think?

I'd appreciate it if you could share your thoughts and/or indicate your intention
whether you wish to remain involved or not, as a response to this email.
(If needed, you could respond only to me.)

I believe that it'd be best to take action after receiving some form of response
from everyone. However, if I receive no response from someone by the end of this
month, October 2025, I'll interpret it as meaning "no intention to remain involved",
and proceed accordingly.


Thank you very much for your understanding and cooperation.
```

(*) Please note that the Bundler/RubyGems case mentioned in the email was concluded on October 17, 2025. See: ["The Transition of RubyGems Repository Ownership"](https://www.ruby-lang.org/en/news/2025/10/17/rubygems-repository-transition/)

What is happening?
===================

As stated in the email, the Embulk project is going into the "maintenance mode" with the following measures.

1. The Embulk GitHub organization [https://github.com/embulk](https://github.com/embulk) is going to have only the minimum belonging members who are willing to continue participating.
2. The Embulk team is going to reduce the things that need to be managed. For example, the Zulip chat for Embulk developers will shut down.
3. The Embulk team declares the maintenance mode, which means that "we can no longer continue managing this project actively".

Long story short, please do not expect that Embulk will be maintained actively. Even if you submit a pull request to the Embulk project, it may not be reviewed nor merged. As Embulk has been licensed under [the Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0), such maintenance has never been guaranteed, though.

Who is going to stay in the organization?
==========================================

Finally, we received responses to my email from 10 members out of 18 recipients (including Bcc'ed) before the end of October 2025. Based on their responses (or lack thereof), only the following four individuals will remain in the Embulk GitHub organization.

- [@frsyuki](https://github.com/frsyuki), the original creator
- [@hito4t](https://github.com/hito4t)
- [@hiroyuki-sato](https://github.com/hiroyuki-sato)
- [@dmikurube](https://github.com/dmikurube), the author of this announcement

Will Embulk never be updated or maintained?
============================================

I won't say "never". We may update Embulk if we feel inclined to do so. That said, please do not expect it.

We may do just some minor tidy-ups and clean-ups. However, a major update does not seem realistic, such as catching up with future versions of Java, or upgrading incompatible dependencies like [Jackson 2 to 3](https://github.com/FasterXML/jackson/wiki/Jackson-Release-3.0).

Alternatively, if someone raises their hand to take over Embulk, as stated in the email, the remaining members will discuss it. However, I personally do not expect that to happen, as we have not received any good proposals in response to the following announcement from last year: [Looking for long-term maintainers around the Embulk eco-system](https://www.embulk.org/articles/2024/11/28/looking-for-long-term-maintainers.html)

Please understand that declining a takeover proposal from someone who is completely new to the community could actually be better for users. As you may know, Embulk has been used to transfer sensitive data within some organizations. What if Embulk were handed over to someone with malicious intent?  Simply declining such a proposal and discontinuing the project could actually be the better option. Taking over is not easy.

Conclusion
===========

I believe that Embulk has fulfilled its role. It was a good opportunity for me personally to take over and maintain Embulk over the years.

Thanks to Sada for creating Embulk, and thank you everyone who has been involved in the community!
