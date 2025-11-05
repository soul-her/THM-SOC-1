OpenCTI Data Model

OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the Structured Threat Information Expression (STIX2) standards. STIX is a serialised and standardised language format used in threat intelligence exchange. It allows for the data to be implemented as entities and relationships, effectively tracing the origin of the provided information.


What is MISP?

MISP (Malware Information Sharing Platform) is an open-source threat information platform that facilitates the collection, storage and distribution of threat intelligence and Indicators of Compromise (IOCs) related to malware, cyber attacks, financial fraud or any intelligence within a community of trusted members. 

this is how u create an event in MISP
/../../Pictures/misp.png

Feeds are resources that contain indicators that can be imported into MISP and provide attributed information about security events. These feeds provide analysts and organisations with continuously updated information on threats and adversaries and aid in their proactive defence against attacks.

Taxonomies

A taxonomy is a means of classifying information based on standard features or attributes. On MISP, taxonomies are used to categorise events, indicators and threat actors based on tags that identify them.

Task 5 scenario event
CIRCL (Computer Incident Respons Center Luxembourg) published an event associated with PupyRAT infection. Your organisation is on alert for remote access trojans and malware in the wild, and you have been tasked to investigate this event and correlate the details with your SIEM. Use what you have learned from the room to identify the event and complete this task.
What event ID has been assigned to the PupyRAT event?
-1145

The event is associated with the adversary gaining ______ into organisations.
-remote access (got the answer by looking at the tags )

What IP address has been mapped as the PupyRAT C2 Server
-89.107.62.39

From the Intrusion Set Galaxy, what attack group is known to use this form of attack?
-Magic hound

There is a taxonomy tag set with a Certainty level of 50. Which one is it
-osint

