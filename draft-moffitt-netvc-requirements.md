---
title: Video Codec Requirements
docname: draft-moffitt-netvc-requirements-latest
date: 2014-11-10
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
of a video codec 

# Constraints Imposed by the Internet on the Codec

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
  parallel, etc)
- hardware feasibility
- software feasibility

explicit non-requirements:

- multiview
- scalable video coding
- bit-error robustness


# Additional Considerations

The features described in this section are potentially desirable but are not
part of the strict requirements. The benefits of them should be weighed
against their costs before including them in the codec.

- lossless
- RGB mode
- aux planes (depth, etc)

# Security Considerations

Although this document itself does not have security considerations, this
section describes the security requirements for the codec.

*todo*
