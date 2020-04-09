---
layout: post
title: Risk Management Framework
date: 2017-08-06 19:00:20 -0800
description: Risk Management Framework
img: risk-mgmt.jpg
tags: [RMF, Risk Management Framework, NIST]
---
<!-- <img src='{{site.baseurl}}/assets/img/emailer.jpg' alt='file desc'> -->


# Risk Management Framework and FISMA compliance

These publications include FIPS 199, FIPS 200, and the NIST 800 series.

Maintained by the National Institute of Standards and Technology (NIST) the Risk Management Framework (RMF) is a set of criteria that dictate how United States government IT systems must be architected, secured, and monitored.

NIST SP 800-37 Rev.2 defines the RMF as a 6-step process to architect and engineer a data security process for new IT systems, and suggest best practices and procedures each federal agency must follow when enabling a new system. Several supplemental documents are referenced as well (SP 800-30, SP 800-53, SP 800-53A, and SP 800-37) but I'll get more into that later.



What is FISMA?

It's the U.S. law signed in 2002 that made it a requirement for federal agegencies to develop, document, and implement an information security and protetction program.


---

All information is reference from https://csrc.nist.gov
The Risk Managment Framework (RMF) is commonly associated with the Federal Information Security Modernization Act of 2014 (FISMA).


### Overview
The selection and specification of security controls for a system is accomplished as part of an organization-wide information security program that involves the management of organizational risk---that is, the risk to the organization or to individuals associated with the operation of a system. The management of organizational risk is a key element in the organization's information security program and provides an effective framework for selecting the appropriate security controls for a system---the security controls necessary to protect individuals and the operations and assets of the organization.

### Risk-based Approach
The Risk Management Framework provides a process that integrates security and risk management activities into the system developlement life cycle. The risk-based approach to security control selection and specification considers effectiveness, efficiency, and constraints due to applicable laws, directives, Executive Orders, policies, standards, or regulations. The following activities related to managing organizational risk are paramount to an effective information security program and can be applied to both new and legacy systems within the context of the system development life cycle and the Federal Enterprise Architecture:

![system development life cycle](https://csrc.nist.gov/CSRC/media/Projects/Risk-Management/images-media/OrgRMF_v3.png)

### Prepare Step
*Prepare* carries out essential activities at the organization, mission and business process, and information system levels of the enterprise to help prepare the organization to manage its security and privacy risks using the Risk Management Framework.

### Categorize Step
*Categorize* the system and the information processed, stored, and transmitted by that system based on an impact analysis.

This step is all administrative and involves gaining an understanding of the organization. Prior to categorizing a system, the system boundary should be defined. Based on that system boundary, all information about the organization and its mission, its roles and responsibilities as well as the system's operating environment, intended use and connections with other systems may affect the final security impact level determined for the information system.

### Select Step
*Select* an intial set of baseline security controls for the system based on the security categorization; tailoring and supplementing the security control baseline as needed based on organization assessment of risk and local conditions.

Security controls are the management, operational, and technical safeguards or contermeasures employed within an organizational information system that protect the confidentiality, integrity, and availability of the system and its information. Assurance boosts confidence in the fact that the security controls implemented within an information system are effective in their application.

### Implement Step
*Implement* the security controls and document how the controls are deployed within the system and environment of operation.

Policies should be tailored to each device to align with the required security documentation.

See appropriate NIST publication in the publication section.

### Assess Step
*Assess* the security controls using appropriate procedures to determine the extent to which the controls are implemented correctly, operating as intended, and producing the desired outcome with respect to meeting the security requirements for the system.

### Authorize Step
*Authorize* system operation based upon a determination of risk to organizational operations and assets, individuals, other organizations and the Nation resulting from the operation of the system and the decision that this risk is acceptable. User reporting is designed to work with POA&M (Plan of Action & Milestones). This provides the tracking and status for any failed controls.

### Monitor Step
*Monitor* and assess selected security controls in the system on an ongoing basis including assessing security control effectiveness, documenting changes to the system or environment or operation, conducting security impact analyses of the associated changes, and reporting the security state of the system to appropriate organizational officials.

Continuous monitoring programs allow an organization to maintain the security authorization of an information system over time in a highly dynamic operatin environment where systems adapt to changing threats, vulnerabilities, technologies, and mission/business processes. While the use of automated support tools is not required, risk management can become near real-time through the use of automated tools. This will help with configuration drift and other potential security incidents associated with unexpected change on different core components and their configuraitons as well as provide ATO (Authorization to Operate) standara reporting.

---

[FedRAMP Security Assessment Framework](https://www.fedramp.gov/assets/resources/documents/FedRAMP_Security_Assessment_Framework.pdf) - Detailed security assessment process to achieve compliance with FedRAMP.

### Applicable Laws and Regulations
- Computer Fraud and Abuse Act (PL 99-474, 18 USC 1030)
- E-Authenication Guidance for Federal Agencies (OMB M-04-04)
- Federal Information Security Management Act (FISMA) of 2002 (Title III, PL 107-347)
- Freedom of Information Act as Amended in 2002 (PL 104-232, 5 USC 552)
- Guidance on Inter-Agency Sharing of Personal Data - Protecting Personal Privacy (OMB M-01-05)
- Homeland Security Presidential Directive-7, Critical Infrastructure Identification
- Internal Control Systems (OMB Circular A-123)
- Management of Federal Information Resources (OMB Circular A-130)
- Management's Responsibility for Internal Control (OMB Circular A-123)
- Privacy Act of 1974 as amended (5 USC 552a)
- Protection of Sensitive Agency Information (OMB M-06-16)
- Records Management by Federal Agencies (44 USC 31)
- Responsibilities for the Maintenance of Records about individuals by Federal Agencies (OMB Circular A-108)
- Security of Federal Automated Information Systems (OMB Circular A-130, Appendix III)

### Application Standards and Guidance



#### FIPS
[FIPS 140-2](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.140-2.pdf) - Security Requirements for Cryptographic Modules

[FIPS 199](https://csrc.nist.gov/publications/detail/fips/199/final) - Standards for Security Categorization of Federal Information and Information Systems.<br>

[FIPS 200](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.200.pdf) - Minimum Security Requirements for Federal Information and Information Systems

[FIPS 201-2](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.201-2.pdf) - Personal Identity Verfication (PIV) of Federal Employees and Contractors

---

#### NIST Special Pubs
**[NIST SP 800-37 Rev.2](https://csrc.nist.gov/publications/detail/sp/800-37/rev-2/final) - Risk Management Framework for Information Systems and Orgranizations: A system Life Cycle Approach for Security and Privacy**


[NIST SP 800-18 Rev.1](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-18r1.pdf) - Guide for Developing Security Plans for Federal Information Systems

[NIST SP 800-27 Rev.A](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-27ra.pdf) - Engineering Principles for Information Technology Security

[NIST SP 800-30 Rev.1](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-30r1.pdf) - Guide for Conducting Risk Assessments

[NIST SP 800-34 Rev.1](https://csrc.nist.gov/publications/detail/sp/800-34/rev-1/final) - Contingency Planning Guide for Federal Information Systems


[NIST SP 800-39](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-39.pdf) - Managing Information Security Risk -- Organization, Mission, and Information System View

[NIST SP 800-53 Rev.4](https://csrc.nist.gov/publications/detail/sp/800-53/rev-4/final) - Security and Privacy Controls for Federal Information Systems and Organizations<br>

[NIST SP 800-60 Rev.1](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final) - Computer Security Incident Handling Guide<br>

[NIST SP 800-61 Vol.1 Rev.2](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-60v1r1.pdf) - Guide for Mapping Types of Information and Information Systems to Security Categories<br>

[NIST SP 800-64 Rev.2](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-64r2.pdf) - Security Considerations in the System Development Life Cycle

[NIST SP 800-83 Rev.1](https://csrc.nist.gov/publications/detail/sp/800-83/rev-1/final) - Guide to Malware Incident Prevention and Handling for Desktops and Laptops<br>

[NSIT SP 800-84](https://csrc.nist.gov/publications/detail/sp/800-84/final) - Guide to Test, Training, and Exercise Programs for IT Plans and Capabilities<br>

[NIST SP 800-86](https://csrc.nist.gov/publications/detail/sp/800-86/final) - Guide to Integrating Forensic Techniques into Incident Response<br>

[NIST SP 800-92](https://csrc.nist.gov/publications/detail/sp/800-92/final) - Guide to Computer Security Log Management<br>

[NIST SP 800-94](https://csrc.nist.gov/publications/detail/sp/800-94/rev-1/draft) - Guide to Intrusion Detection and Prevention Systems (IDPS)<br>

[NIST SP 800-115](https://csrc.nist.gov/publications/detail/sp/800-115/final) - Technical Guide to Information Security Testing and Assesment<br>

[NIST SP 800-128](https://csrc.nist.gov/publications/detail/sp/800-128/final) - Guide for Security-Focused Configuration Management of Information Systems<br>

[NIST SP 800-171](https://csrc.nist.gov/publications/detail/sp/800-171/rev-1/final) - Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations<br>

[NIST SP 800-137](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-137.pdf) - Information Security Continuous Monitoring (ISCM) for Federal Information Systems and Organizations

[NIST SP 800-145](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf) - NIST Definition of Cloud Computing

[NIST SP 800-160](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-160v1.pdf) - Systems Security Engineering -- Considerations for a Multidisciplinary Approach in the Engineering of Trustworthy Secure Systems
