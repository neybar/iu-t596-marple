---
title: Date Sources
---

## Data Sources: Justification and Collection Summary

In order to have world class AI we need world class data.  Fortunately we have access to some really high quality data.  There is also data in abundance.  Normally this would be a big problem for human analysts, but for computers and especially AI huge amounts of data becomes an asset.  The main focus then becomes the task of finding quality data, and then formatting it in a usable way.

For data we have decided to turn to some well-known sources:
* [Github](#github)
* [Mitre CVE](#mitre)
* [Shodan](#shodan)
* [Twitter](#twitter)
* [Phishtank](#phishtank)

### Github {#github}

<img src="{{'/assets/images/github_logo.png' | relative_url}}" />

#### Justification

GitHub is a gold mine of Malware data.  In order to start really discovering what is available it is valuable to do a topic search. Each of the repos that are returned have a variable degree of value.  Some are going to be easy to use, while others are specialized and require work to format it for AI use.  The amount of work being done in the field (and stored in GitHub) is going to be critical to stay ahead of attackers

Value & Volume:
* 163 Malware topics
* Over 3600 repos
* Topics range from white hat to black hat activities
* Examples are malware signatures, malware removal utilities, malware classification, targeted malware by software, etc.
* The primary challenge will be to utilize automation to find valuable data here, and then feed that into AI that can help identify and prevent malware

#### Collection Strategy

For Github our primary collection strategy is going to be via the Github API.  Using the solid PyGithub library we are able to search by topic and repo to collect nearly any kind of data, and projects.  For an example we are looking specifically at how Github can provide data regarding Malware.  The use, prevention, tracking, and classification of all sorts of Malware.

#### View Github Data

For more details about Github data view our [Sample Data]({{ '/malware' | relative_url }})

### Mitre CVE {#mitre}

<img src="{{'/assets/images/cvelogobanner.png' | relative_url}}" />

#### Justification

CVE(Common Vulnerabilities and Exposures) data related to the critical assets we identified for the Fintech industry can be retrieved from the National Vulnerability Database(NVD).  Data retrieved from these sources gives details such as CVSS score and Risk Factor. Intelligence gained from CVE data helps with prioritizing patches and software updates based on the seriousness of the threats associated with each vulnerability.

The CVE Database is a valuable critical asset in the FinTech industry as it stores sensitive personal and financial customer data. Database vulnerabilities could lead to cyber threats such as SQL Injection, DDoS and data theft.

Implementing a good AI4Cyber solution based on vulnerability dataset will protect it from potential data breach.

#### Collection Strategy

CVE data can be collected by searching using the web interface or programmatically via the API provided by Mitre.

Web-Based Search:
* [www.cvedetails.com](www.cvedetails.com) provides an easy-to-use web interface to CVE vulnerability data.
* CVE vulnerability data are taken from National Vulnerability Database (NVD) XML feeds provided by the National Institute of Standards and Technology.
* Additional data from several sources like exploits from [www.exploit-db.com](www.exploit-db.com), vendor statements and additional vendor supplied data, Metasploit modules are also published in addition to NVD CVE data.
* This data can be searched by using key words for the critical assets such as "SQL Database", "Oracle Database" or using the vendor and products names.
* The data search result can be sorted based by CVSS score, published date or complexity and can be downloaded for use by the AI4Cyber platform.

#### View CVE Data

For more details about CVE data view our [Sample Data]({{ '/cve' | relative_url }})

### Shodan {#shodan}
<img src="{{'/assets/images/shodan.jpg' | relative_url}}" />

#### Justification

Shodan searches for internet-connected devices — from routers and servers, to Internet of Things (IoT) devices, such as thermostats and baby monitors, to complex systems that govern a wide range of industries.

Shodan is often used by Academics and cybersecurity professionals to analyze what kind of devices are connecting to the internet, what kind of software they’re using, and identify trends in security, device usage, and the overall makeup of the internet.

Shodan is also extremely useful when it comes to networks monitor and  patching vulnerabilities —- when Microsoft’s Exchange servers were hacked by zero-day threats in March of 2021, experts were able to quickly put out a patch and close the server vulnerabilities.

#### Collection Strategy

As with any search engine, Shodan works well with basic, single-term searches, but the real power comes with customized queries. Basic filters you can use:City,Country,Geo,Hostname,Proudct,OS, Port, Before/After

Using search filters is the best way to search on Shodan quickly and efficiently, but you have to register for an account with Shodan in order to use advanced search filters and download data files

* Data Export: You can export your results in various formats using the top menu after you’ve performed a search.
* Free member. Two pages of search results, limited filters.
* Basic membership. One-time fee for lifetime use, gives access to map and photo search options, limited filters.
* Premium Accounts: A premium account is a one-time payment it gives you increased access to the API. Full details and docs are available at [https://developer.shodan.io](https://developer.shodan.io).
** With a premium account you also have access to REST and Streaming APIs.  This is the best way for automated collection stragegies.

### Twitter {#twitter}

<img src="{{'/assets/images/twitter_logo.png' | relative_url}}" width="325px" />

#### Justification

Twitter and other social media platforms have been used to influence financial markets, with devastating effects. Financial criminals use social media in “pump-and-dump” schemes to temporarily inflate the price of stocks through false or misleading tweets; when they sell their shares and stop promoting the stock, the resulting plunge in shares’ value harms unsuspecting investors

* Over 330 million monthly active users. 
* Twitter data hack is used for stealing credentials. They hacked the account of an internal twitter employee under the pretext of helping to fix the VPN problems. They used this initial compromise to navigate through twitter’s internal websites and their systems.
* Given the number of followers for each high-profile user account, the fraudulent tweets reached millions of potential victims across the globe. The hackers seized the account of Binance, a cryptocurrency exchange and sent a tweet which included a link to a bitcoin scam address. The Hackers stole approximately $118,000 worth of bitcoin through the Twitter Hack.
* The consequences of the Twitter Hack show why it is critical for Twitter and other social media companies to implement robust controls before they experience a cyber incident, not after.

#### Collection Strategy

Twitter provides a fantastic amount of data.  Really the only reasonable way to collect data from Twitter is via their API.  Using a language such as Python and a twitter library we can start to collect all sorts of interesting data.  Here is an overview of some of the data that we will be collecting:

<img src="{{'/assets/images/twitter_api.png' | relative_url}}" />

### Phishtank and AZSecure Data {#phishtank}

<img src="{{'/assets/images/phishtank.gif' | relative_url}}" />

#### Justification

Legitimate financial websites can be used as a baseline for investigating the spoof financial website dataset. 

Phishing websites are one of the largest mediums used by adversaries to gain access to financial credentials. \*The URL can be used in company with phishing emails to send potential victims to the spoof website.

Value & Volume:
* 50 Legitimate Financial Websites
* Data includes all files on the server that were collected (text, images, code, etc.).
* The source code for legitimate websites can be used by adversaries to set up phishing websites using similar components, text, images, and URL's.
* 389 Spoof Financial Websites
* Data includes all files on the server that were collected (text, images, code, etc.). Some folders may contain malware.
* AZSecure-Data is provided via zip file download for easy access, and it provides instructions for working with malware.

#### Collection Strategy
Phishing Data is widely available and can be downloaded directly to a computer, imported into a database via API, or accessed directly from the website UI.

Collection:

* [https://www.azsecure-data.org/phishing-websites.html](https://www.azsecure-data.org/phishing-websites.html) provides an easy to access, downloaded file structure of phishing websites.
* AZSecure-Data for phishing websites comes directly from [http://www.phishtank.com/](http://www.phishtank.com/); a collaborative clearing house for phishing site data. 
* Phishtank and AZSecure-Data have comprehensible developer-driven API documentation.
* AZSecure-Data has already been categorized into financial data, whereas Phishtank requires search for specific categories.

