---
title: Video Codec Requirements
docname: draft-moffitt-netvc-requirements-latest
date: 2015-13-09
category: info

ipr: trust200902
area: RAI
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: J. Moffitt
    name: Jack Moffitt
    organization: Mozilla
    email: jack@metajack.im

 -
    ins: M. Zanaty
    name: Mo Zanaty
    organization: Cisco
    email: mzanaty@cisco.com


normative:


informative:


--- abstract

This document provides specific requirements for an Internet video codec.
These requirements address quality, bit-rate, and packet-loss
robustness, as well as other desirable properties.

--- middle

# Introduction

This document provides requirements for a video codec designed specifically
for use over the Internet. The requirements attempt to address the needs of
the most common streaming and interactive video transmission applications and
ensure good quality when operating in typical Internet conditions. These
requirements also address issues of quality, frame rate, bit-rate, and
packet-loss robustness. Other desirable but not required video codec
properties are also considered.
   
# Applications

The following applications should be considered for Internet video codecs,
along with their requirements:

- Point-to-point calls
- Broadcast
- Conferencing
- Telepresence
- Teleoperation
- Screencasting
- In-game video chat
- Video storage
- Other applications

## Point-to-Point Calls

One-to-one video chat applications are proliferating. These interactive uses
of a video codec involve two connected participants sending and receiving
encoded video to each other. Frame sizes will typically be 360p to 720p and
bandwidth used around 1 Mbit/s.

The endpoints will need to negotiate and change session details during the
call. For example, one endpoint may request higher resolution video when the
size of the display window is increased.

## Broadcast

Broadcasting is live or pre-recorded video being sent to many participants at
the same time. This will typically involve frame sizes up to 1080p and
bandwidth requirements as high as 6 Mbit/s.

Example applications in this area include on-demand video service like Netflix
and YouTube as well as digital transmission of live sporting events.

## Conferencing

Video conferencing requires many of the same things as point-to-point calls,
but involves more than 2 participants. It is more complicated due to the
shifting focus of attention among the participants. For example, when one
participant is speaking, the user may prefer to have their video appear larger
and the other participants smaller, which may have consequences for codec
parameters.

Frame sizes and bitrates are similar to point-to-point applications.

## Telepresence

Telepresence tries to use high fidelity reproduction to make remote video
conference participants feel like they are real people in the same room. This
requires high resolutions and large amounts of bandwidth. It is otherwise very
similar to video conferencing applications.

## Teleoperation

Teleoperation requires the high fidelity of telepresence, but includes
increased requirements for low latency. Remote control of surgical tools is
one example application.

## Screencasting

Screencasting is the sharing of the contents of some or all of a computer or
mobile display. It is commonly used to send the visual output of applications
to other endpoints. For example, a speaker at a conference might share the
window for their presentation program and a mobile app developer might want to
record a demo of their application.

Two main features distinguish this application. First, since the inputs are
often RGB, it is important to preserve the color information at a higher
fidelity than normal video. Second, the input for the encoder is potentially
higher level than raw pixels or contains both pixels and higher level objects
such as text along with font and positioning information.

## Video Storage

Archival video brings several unique requirements. Many applications will want
lossless compression or very high rates, and others will want low
complexity. Examples of the former include archival storage of film masters;
examples of the latter would be surveillance gear or video camera capture
systems.

## Other Applications

The preceding list of application is by no means complete. The requirements
needed to enable these applications should be sufficient to meet the needs of
many other applications that were not listed.

# Constraints Imposed by the Internet on the Codec

- must be able to interpret packets when previous packets are lost
- prediction across frames is reasonable but must allow for resync
- keyframes and other features for dynamic resync
- ability to vary bandwidth because of internet best-effort
- ECN
- use with other multimedia standards

# Detailed Basic Requirements

- variable frame rate
- variable resolution
- any resolution from 1x1 to 4k?
- 8bit to 12bit
- loss robustness
- loss concealment?
- error recovery
- 420, 444, 422
- color spaces: req 709 and 2020
- alpha plane
- parallelism considerations (entropy coder in separate thread, wavefront
  parallel, etc.)
- hardware feasibility
- software feasibility

explicit non-requirements:

- multiview
- scalable video coding
- bit-error robustness


# Additional Considerations

The features described in this section are potentially desirable but are not
part of the strict requirements. Their benefits should be weighed against
their costs before including them in the codec.

- lossless
- RGB mode
- aux planes (depth, etc.)

# Security Considerations

Although this document itself does not have security considerations, this
section describes the security requirements for the codec.

As for any protocol to be used over the Internet, security is a very important
aspect to consider.  This goes beyond the obvious considerations of preventing
buffer overflows and similar attacks that can lead to denial-of-service (DoS)
or remote code execution.  One very important security aspect is to make sure
that the decoders have a bounded and reasonable worst-case complexity.  This
prevents an attacker from causing a DoS by sending packets that are specially
crafted to take a very long (or infinite) time to decode.
