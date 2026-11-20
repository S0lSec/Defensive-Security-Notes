# Based on TTPs
Effective threat detection often revolves around identifying patterns that either match known malicious behaviors or diverge significantly from expected norms.

When crafting detection-related Search Processing Language searches with Splunk, we utilize two main approaches:
1. If an entity behaves in a way that we recognize as characteristic of a particular threat, it draws our attention. **Spot the known**
2. Make extensive use of mathematical and statistical techniques to highlight anomalies, working on the premise that malicious activity will often manifest as an aberration from the norm. **Spot the unusual**
**The key is to understand our data and environment then carefully tune our queries and thresholds to balance the need for accurate detection with the desire to avoid false positives.**
# Based on Analytics
Profile *normal* behavior and identifying deviations from this baseline, we can uncover suspicious activities that may signify an intrusion.

The use of the `streamstats` command allows us to perform real-time analytics on the data. Which can be useful for identifying unusual patterns or trends.