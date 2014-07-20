---
layout: post
title: SMIMP: The Design Goals
---

As we work to get everything tightened up for the first public draft, I wanted to share some more details about just what it is we are working on. I'd love to go ahead and release a public draft today - but the specification needs to be solid. To avoid having too many distractions about half-baked parts of the specification, we are waiting till it's a bit more solid (or the end of the month, which ever comes first).

Today, I want to talk about the design goals of SMIMP - what are we trying to solve for - so here is the goals sections, pulled directly from the working copy of the specification:

**Transparent Crypto** - The user must not be required to take any action for a message to be encrypted. All messages must be encrypted, with no option to disable. It must be impossible for a message to "fail open" and expose contents to a third party.

**Strong Crypto** - Strong cryptography should be used throughout the system. To simplify implementation and assure security, libsodium should be used for all possible operations. Implementors should be discouraged from rolling their own implementations.

**Simple Public Key Lookup** - An address should be tied to a single public key, and a public key tied to a single address. 

**Verifiable User History** - Every change to a user’s identity information (change of key, change of server(s), etc.) must be signed by the user’s private key, and contain the hash of the last change. This provides a hash chain from the initial user creation record to current, allowing clients to easily detect manipulation.

**Forward Secrecy** - The user should be able to upload single use public keys, signed by their master key, so that past message contents can’t be revealed if their master private key is compromised.

**Ease of Implementation** - The design should be simple enough that core components can be easily implemented, allowing for a healthy market for clients and servers.

**Minimal New Protocols** - Whenever possible, existing protocols, such as HTTPS, should be used instead of creating a new protocol.

**Simple Self Hosting** - Due to attacks against large providers (hacks and rubber stamp courts), it should be simple to run your own SMIMP mail server, on a commodity VPS. A user should not need to be an experienced server administrator to successfully run their own server.

**Firewall Friendly** - All message transport should be over HTTPS to remove the need for administrators to open ports on the firewall. This also minimizes the opportunities for filtering, as all message transport will be legitimate HTTPS traffic, and thus harder to distinguish from other traffic.

**Proof of Work** - Messages will each have a proof of work associated with it as an anti-spam measure; the receiving mail server is responsible for determining the difficulty based on factors of its choosing.

**User Authentication** - This infrastructure should be usable by other systems to validate that a user is who they claim to be.

These are lofty goals, but I believe that the specification lives up to them. 

There's another goal that's not stated here, but is very important to everyone that's involved with this effort - this is owned by the community, and it will evolve at the direction of the community. While input from corporate interests, law enforcement, and the like will be taken under consideration as this evolves, no single entity (person or company) will control the standard.
