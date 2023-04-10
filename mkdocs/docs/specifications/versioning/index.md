---
title: Versioning
---


ACES Versioning System
================


Scope
----------------
This document specifies the versioning of the overall ACES system and of individual ACES system components.


References
----------------
The following standards, specifications, articles, presentations, and texts are referenced in this text:

* [TB-2014-002: ACES Version 1.0 User Experience Guidelines](https://www.dropbox.com/s/v5tghz6wl2629nf/TB-2014-002.pdf?dl=0)
* [TB-2014-012: ACES Version 1.0 Component Names](http://j.mp/TB-2014-012)


Introduction
----------------
The key components of the ACES system are ACES encodings, ACES image files, ACES transforms and associated files, and an ACES Metadata File (AMF) that describes how the ACES image files were viewed when created or modified. ACES 1.0 was the first official release of these components. However, it was always expected that new transforms would need to be created based on new cameras, displays, or industry standards. Existing ACES components would also require updates in subsequent releases based on industry requirements. Therefore, a specification for consistent naming and versioning of ACES system components is needed.

This document describes the versioning of the engineering components that comprise the ACES System Release to ACES Product Partners. These version numbers are intended to be used within ACES files such as transforms and referenced in the ACES Metadata File. 

A separate document, Academy TB-2014-002, addresses naming and versioning issues as they relate to end-users.


Specification
----------------

### Versioning of the ACES System

The ACES system release consists of a variety of Academy-specified core color transforms, libraries, and utilities as well as vendor and/or user-supplied components. 

The ACES system shall use the following versioning string to identify the overall  the package of components supplied with a particular release:

*ReleaseMajorVersionNumber.ReleaseMinorVersionNumber.ReleasePatchVersionNumber*

ACES implementations shall report the version of the ACES system to  at least the minor version number. Reporting of the patch version is optional.

The 'patch' version number shall be incremented with bug fixes. New patch versions shall not require an update to all transforms. 

The 'minor' version number shall be incremented with non-substantive changes to the
existing ACES core components. Minor version releases may include additional ACES transforms (e.g. a new Output Transform to a new display encoding) and/or roll-ups of minor ODT enhancements/additions or bug fixes. Minor versions shall not require an update to all ACES core and vendor/user-supplied components.

The 'major' version number shall be incremented if substantive changes are made to the ACES core components. An increment of the major version number will require all core and vendor/user-supplied components to be updated to confirm compatibility with the new ACES major version.

The ACES system version reflects transforms included in the `aces-dev` Github repository (or derivative transforms) and shall not require incrementation when custom or ACES vendor/user-supplied components are updated.

### Versioning of individual ACES transforms

ACES transforms (expressed as CTL files in the reference implementation) shall be  assigned both a [Transform Identifier (TransformID)](#transform-ids) and a [user-facing name](#user-facing-names). 


#### Transform Identifiers (TransformIDs) {#transform-ids}

Academy-supplied ACES transforms shall include a Transform Identifier (written as "TransformID") contained in an XML tag of `<ACEStransformID>` in the file header.

A TransformID shall be included as metadata or as a comment in any implementations or AMFs that are intended to match reference ACES transforms. 

In implementations of transforms that may be intended to match the results of a combined sequence of ACES CTL transforms (e.g. a Color Space Conversion (CSC) + Look Transform (LMT) + Output Transform) each of the relevant ACES TransformIDs shall be included in the implementation transform. 


#### String format for Transform Identifiers

ACES system components are assigned a string that serves as a unique identifier for a particular release version of the ACES system. This identifier shall be constructed using a set of tokens as described in this specification so that it will be more human-readable than a typical Universally Unique Identifier (UUID).

In the following definitions, *italics* represent a changeable placeholder and **boldface** represents a required character or string.

All ACES system components, whether Academy-supplied or vendor/user-supplied, shall use the following generic versioning string format:

*URN : Type . Namespace . Name . ***a***ACESMajorVersionNumber. ***v***TransformVersionNumber*

Expected sub-strings for each of the changeable placeholders are described in the following subclauses.

To enable easier reading and parsing of Transform IDs, the sub-strings used for
*Namespace* and *Name* should not contain spaces or periods and should be limited to the ASCII character set.

##### URN
*URN* is a unique reference number and shall be `urn:ampas:aces:transformId:v1.5:`

##### Type
*Type* is one of the following:

- `IDT` - ACES Input Transform (a.k.a. Input Device Transform or IDT)
- `LMT` - ACES Look Transform (a.k.a. Look Modification Transform or LMT) 
- `RRTODT` - ACES Output Transform (concatenated RRT and ODT) 
- `InvRRTODT` - ACES Inverse Output Transform (concatenated RRT and ODT)
- `ACESlib` - ACES library functions for core transforms, e.g., Tonescales
- `ACEScsc` - Color Space Conversion transforms provided with the ACES system
- `ACESutil` - utility functions provided with the ACES system, e.g., Adjust Exposure

!!! note
	ACES 1.1 introduced "Output Transforms" as the preferred terminology to describe a rendering of ACES2065-1 data to a display. Thus a *Type* of `RRTODT` or `InvRRTODT` is preferred. However, for backwards compatibility, the following *Type* tokens:
	
	- `RRT` - Reference Rendering Transform
	- `InvRRT` - Inverse Reference Rendering Transform
	- `ODT` - Output Device Transform
	- `InvODT` - Inverse Output Device Transform

	remain valid options and should be supported, though in practice the RRT or ODT are rarely referred to or used individually.

##### Namespace
*Namespace* identifies the creator of the transform. This is usually the name of a company or, in one-off cases, could be the name of an individual. The namespace `Academy` is reserved for Academy-supplied transforms. 

In the case that a transform is provided by a vendor but is hosted on the Academy Github, it shall maintain the namespace of the vendor that created it.

##### Name
*Name* is a placeholder depending on the type of transform. 

For Output Transforms, the *Name* shall describe the device and/or output data encoding in as much detail as possible. This usually includes the encoding color primaries and white point, peak luminance of the display, any limiting color primaries and white point, and signal on-the-wire encoding. It may also indicate a "simulation" of another display encoding contained within a standard encoding, e.g. to show Rec.709 100-nit content on a 1000-nit Rec.2020 PQ display.

Example Output Transform Names:

- `urn:ampas:aces:transformId:v1.5:RRTODT:Rec2020_1000nits_P3D65limited_PQ`

For Input Transforms, the *Name* shall describe the device. If the creator of the transforms is the same as the camera manufacturer, then the *Name* need not repeat the manufacturer name because it should already be in the *Namespace*. If the Input Transform creator is not the camera manufacturer, than the manufacturer name shall be prepended to the device name in the *Name* field.

Example Input Transform names:
- `urn:ampas:aces:transformId:v1.5:IDT.Sony.F65.a1.v1`



##### ACES Major Version Number
To indicate the ACES system version with which a particular transform is compatible, the Transform Identifier shall include a string with the letter 'a' followed by the ACES major version number.

Example: `a1.`

##### Transform Version Number
The version of the individual transform is indicated with the letter 'v' followed by the *TransformVersionNumber*.

Transforms such as the RRT and ODTs rely on sub-functions and constants included in separate CTL files, i.e. ACESlib. ACESlib files often contain more than one sub-function or constant. If a change is made to the code of a sub-function that affects the output of a calling transform, the version of the calling transform’s TransformID shall be incremented (even if the code in the RRT, ODT, etc. itself may not have changed). For simple additions or modifications to an ACESlib file that do *not* affect the numerical output of a calling function, the calling function TransformID version need not be incremented.

Any transform updates to a transform file (e.g. whitespace changes, modifications to code comments, etc.) that do not change the output of that transform shall not require the transform version number to be incremented.

Examples:


#### User-Facing Names {#user-facing-names}

Academy-supplied ACES transforms shall include a user-friendly name contained in an XML tag of <ACESuserName> in the file header. 

Though human-readable, ACES TransformIDs can be complex and thus are not always appropriate for presentation to end users for selection purposes. Therefore, all transforms shall include a user-friendly name contained in an XML tag of as metadata within the transform file. Software applications can access this short, user-friendly name for presentation in their user interfaces. 

!!! note
	Recommended friendly names are described in [ACES 1.0 User Experience Guidelines](http://j.mp/TB-2014-002).


Examples:
	
	
### Versioning of ACES file formats

File formats specified for use with the ACES system include:

- SMPTE ST 268:2014 (DPX)
- SMPTE ST 2065-4
- ACES Metadata File (AMF)
- Academy-ASC Common LUT Format (CLF)

File formats standardized through SMPTE are versioned according to SMPTE conventions.

