---
title: Data Analysis
---

## Data Analysis: Approaches and Justifications for Data Analysis 

Based on the data that we collected in our [Data Sources]({{'/data_sources' | relative_url}}) we have taken several Analytical approaches to see what is going on in the world of Malware and what we can do with that information as it relates to CyberSecurity for AI.

Here are some of the analysis that we did:

* [Github Topic Analysis](#github_wordcloud)
* [Github Readme Analysis](#github_lda)
* [Twitter Sentiment Analysis](#twitter-sentiment-analysis)
* [Phishing Predictive Analysis](#phishing-predictive-analysis)
* [Shodan Data Mining](#shodan-data-mining)
* [CVE and EPSS Analysis](#cve-and-epss-analysis)

### Github Topic Analysis (Pre-AI Vis) {#github_wordcloud}

Our goal with Github data is to discover patterns relating to Malware.

The first task is to collect data.  This was done by interacting with the Github API.  We searched for any repo that has a topic of 'Malware'.  Github and Github authors can assign these tags.  So the data is somewhat self-collating.  However, repos can have more than one topic tag. 

Once we had a large number of repos and their associated meta data (>2K repos), it seemed like a good idea to run a quick visualization to see what we were working with.

This lead to the creation of a wordcloud.  We took all the topics that came with the repo metadata, sorted, counted, and weighted the topics.  You can view the [resulting word cloud here]({{'/wordcloud' | relative_url}}).

The result was better than hoped for.  The repos seem to span some really interesting topics.  Since the primary topic was 'Malware', then it was no surprise to see it at the top of the list.  Some of the other topics are:
* virus
* hacking
* security
* ransomware
* windows
* linux
* trojan
* keylogger
* infosec
* etc

### Github Readme Analysis (LDA) {#github_lda}

After producing the wordcloud, it seemed like we were on the right path to use Github as a data source.

The next effort was to dig deeper into Github.  One attribute of nearly all repos is a "ReadMe" file, which is a sort of front page for a repo.  It commonly tells why the repo exists, projects goals, howto, and installation instructions.

The analysis that we wanted to perform was a reduction technique using the LDA (Linear Dsicriminant Analysis) algorithm.  We needed to do some pre-processing to get the data into good shape.  After downloading all the readme files into a directory we had to:

* Remove any unusable characters like ([{\*&^,.}])
** Many Readme files are written in Markdown so we needed to strip those meta characters out
* Remove stop words
* Remove words relating to common install/compile processes
* lowercase

Once the data was in good shape we ran it through the LDA model.  

You can [see the LDA visualization here]({{'/github_readme' | relative_url}}).

This analysis was less useful than we had hoped.  It really reinforced the initial findings in the wordcloud.  It showed that the repos indeed were interested in malware and other cybersecurity topics.

Our next step with github is to look individually at specific repos, rather than looking holistic dally at the entire repo set.  One thing that would be nice is to see if we can refine our analysis to help us identify *which* repos to look at.

### Twitter Sentiment Analysis

The next dataset that we are interested in for AI4Cyber is Twitter.  Twitter can be an excellent source for finding out about in progress cyber attacks, as well as hearing about what promenent hackers and professionals think is on the horizon.

Our analysis for Twitter is to do a Sentiment Analysis.  Similar to the Github data we needed to do some pre-processing.  This effort was nearly identical, so it won't be repeated here.

With the clean, pre-processed data we wanted to look at two axis for our Sentiment Analysis.  One axis is subjectivity.  We gave a score of 0 for tweets that are fact, a score of +1 indicates a tweet that is an opinion.  Our next axis is polarity.  A score of -1 inticates a tweet with negative sentiment, and a +1 indicates a tweet with a positive sentiment.

We hope to see results that favor factual events and that have a high polarity.  We'd like to see polarity at either end (-1, +1) meaning that there is engagement.  Tweents that receive polarity scores of near 0 probably aren't going to be very meaning ful to us.

This reasearch is on going and there are no visualizations available at this time.

We did however get a twitter dataset relating to bitcoin.  We created a [wordcloud]({{'/wordcloud' | relative_url}}) based on a topic analysis which you can see.

### Phishing Predictive Analysis

Phishing is the targeted approach of gathering sensitive data from victims.  For this effort we focused in on phishing websites, esspecially ones that targeted gathering financial information.

When looking at the phishing website source code, our preliminary goal was to build a predictive classifier that could categorize the source code folders into authentic websites or phishing websites.

In our Pre-processing setup we ran into some issues with finding a common file structure or other easy-to-read formant such as a relational database.  Creating a common format for the website data proved difficult since websites are organized so differently.

For the modeling, we were able to convert some html sites to txt and ran some Python code to gather keywords.  Ultimately this search was unfruitful.  We discovered that source code for phishing websites isn't ideal for a predictive classifier.

In future efforts we would like to use Random Tree Classifier on a better and cleaner data set, and believe that we would gain good results.  Email may prove to be a better data set to work with.

### Shodan Data Mining

Shodan data is interesting in that it targets appliances and other IoT (Internet of Things) devices.  Since Fintech is just as reliant on these types of devices if not more (think ATM), we need to be aware of this attack vector and protect against it.

Our approach here was use Shodan.io to:

* Search data to include financial organizations in both US and London (reputed as the Fintech Capital).
* Shodan data set contains 2500 records with basic network environment attributes, such as IP’s, port, hostname, location (country, city), product, service.
* Apache httpd, nginx, and Microsoft IIS httpd identified as the most common products/protocols in use.
* Link CPE (Common Platform Enumeration)data associated with CVE’s from NVD to Shodan dataset.
* Consolidate datasets and generate a dataset to perform classification analytics by using either Naïve Bayes or Random Forest in Weka to perform predicative analysis.
* Unfortunately, being unable to complete the above two steps the attempt to use Shodan data for predicative analysis was unsuccessful...

Although the attempt to conduct classification analysis did not succeed and the outcomes seemed to be fruitless. However, the exercise itself has provided an invaluable lesson to me for future study. Analytical tools are made available to assist with modeling and perform analysis, while data collection and data pre-processing are critical preparation in order to leverage the strength of the various analytics approaches and tools.

### CVE and EPSS Analysis

* It is very hard to patch all open and critical vulnerabilities in the system. Therefore, an intelligent way of prioritizing them is necessary.
* The latest research at Blackhat unveiled Exploit Prediction Scoring System (EPSS)” model
* EPSS provides a new capability for efficient, data-driven vulnerability management. It uses current threat information from CVE and real-world exploit data.
* Data-driven prioritization of vulnerabilities can be made based on a combination of EPSS and CVSS scores.
* CVE data related to our critical assets database and source code was downloaded from [www.cvedetails.com](www.cvedetails.com) and was filtered out per type and score.
* Exploit Prediction Scoring System (EPSS) data for all CVEs since January 1, 2017 -- over 60,000, was downloaded in a .csv format from [https://www.first.org/epss/data_stats](https://www.first.org/epss/data_stats)
* Data collected from these 2 sources were imported into SQL database tables.
* A correlation between CVE and EPSS data was made by querying from the 2 tables based on CVEID
* To classify the vulnerabilities, the data was converted into a feature matrix.
* The data was then exported in .csv format and was imported into the WEKA machine learning tool for classification.​ The file contains 1694 instances and 5 attributes.
* Risk attribute was selected in WEKA to classify the vulnerabilities as High, Medium and Low risk based on the CVSS and EPSS scores
* The model was tested using hold-out and cross-validation methods by switching different algorithms such as Naive Bayes and Random Forest. 
* Naive Bayes gave a 92% accuracy rate and the overall performance metrics for Recall, F-Measure and TP-Rate was 0.92
* The following images show the visualization of the different attributes after the data is loaded in WEKA.

<img src="{{'/assets/images/cvs_analysis_type.png' | relative_url}}"
<img src="{{'/assets/images/cvs_analysis_class.png' | relative_url}}"




