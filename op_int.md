---
title: Operational Intelligence
---

## Operational Intelligence

### Malware

#### Recommendations

* Automated Alerting and Monitoring
	* Create Dashboard tracking positive Malware identifications
	* Impacted system, Impacted files
	* Alert System and Application owners

* Automated System Integrity
	*  Automatically quarantine positively identified malware files
	*  Automatically initiate deeper malware analysis on all systems
	*  If on immutable infrastructure, then initiate redeploy
	*  Run systems check to verify critical functionality
	*  Run smoke tests and other integration tests to verify application functionality
	*  Run data integrity tests

* Increased Knowledge Sharing
	*  New malware files should be run through software like Cuckoo Sandbox.
	*  Resulting signatures should be shared with the community (Github)

### Twitter

#### Recommendations
* The tweets made by cryptocurrency influencers contain statistically significant information about the future value of Bitcoin.
* This information can then be used to create profitable trading strategies.
* Lastly the results of sentiment analysis performed on BTC datasets thesis contribute to existing literature on predicting Bitcoin prices and fills the gap of using sentiment analysis on tweets made by opinion leaders as well as strengthening the use case for using sentiment analysis in forecasting.

### CVE

#### Recommendations
* Based on our findings, the common approach of simply prioritizing the vulnerabilities based of their criticality CVSS rating is not effective.
* More than 55% of CVE records are rated critical or High. This could be overwhelming for the security team to keep up with and patch them all.
* We suggest that the remediation strategy should instead consider both the severity of the vulnerabilities and the exploitability factor.
* The vulnerabilities that are most likely to be exploited need to be patched as soon as possible.
* Organizations that are part of the integrated payment system and partner financial institutions need to be informed about the high-risk vulnerabilities identified by our AI4Cyber platform.
* This will help them apply the same remedy to defend the critical assets shared between the entire payment systems.

## Future of the Platform

AI4Cyber is one of the few tools we must use to get ahead of hackers.

Through building an AI4Cyber platform in this project, we have learnt that it is possible to achieve better cybersecurity results with the use of AI. But there is still room for improvement.

These are the next steps in enhancing our AI4Cyber platform:

* Get live date feeds through API integration with different data sources
* Work as a community to create bigger and better malware classification libraries
* Continue improving the performance of the trained predictive models to increase the accuracy level:
    * Work with more classification algorithms.  Especially as our data set gets larger
    * Automate responses to positive classifications
    * Adjust model so that it can run on more platforms:
        * Multiple OS, Network OS, Embedded OS
* Determine if Sentiment Analysis results continue to hold in varying pricing environments.
* Additionally, more complex models, and not just linear ones like we used, could be fit using  tweet volumes and social media as inputs to see if results could be improved further.
