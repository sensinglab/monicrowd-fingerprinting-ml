# Information Elements Automatic Analyser (IEAA)

**Bit-Level Information Element Analysis for Wi-Fi Device Fingerprinting**

## Overview

The Information Elements Automatic Analyser (IEAA) is a research tool developed and refined within the MoniCrowd project to support the construction of rule-based Wi-Fi device fingerprints under MAC address randomization.

The analyser examines the structural and content characteristics of Information Elements (IEs) extracted from Wi-Fi probe requests, evaluating their stability across repeated transmissions and across physical devices.

Its analysis supports the selection of IE identifiers, lengths, vendor-specific structures, and content bits for fingerprint construction.

The IEAA is used in conjunction with a threshold optimization procedure that evaluates candidate fingerprinting configurations against device-counting ground truth, accounting for fragmentation and collision errors.
