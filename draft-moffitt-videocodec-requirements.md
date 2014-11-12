---
title: Video Codec Requirements
docname: draft-moffitt-videocodec-requirements-latest
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

# Definitions

# Applications

The following applications should be considered for Internet video codecs,
along with their requirements:

- Point-to-point calls
- Conferencing
- Telepresence
- Teleoperation
- Screencasting
- In-game video chat
- Video storage
- Other applications

# Constraints Imposed by the Internet on the Codec

# Detailed Basic Requirements

- variable frame rate
- variable resolution
- any resolution from 1x1 to 4k?
- 8bit to 12bit
- loss robustness
- loss concealment?
- 420, 444, 422, 411
- color spaces: req 709 and 2020
- alpha plane
- parallelism considerations (entropy coder in spearate thread, wavefront
  parallel, etc)
- hardware feasibility
- software feasibility

explicit non-requirements:

- multiview
- svc
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
