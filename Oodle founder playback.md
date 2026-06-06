**OODLE : BUSINESS BRIEF**

**CONTEXT** 

* “Observability” is the ability to understand a system’s internal state by analyzing its external outputs, helping tech/dev teams to troubleshoot by identifying the why behind issues, debugging, analyzing root causes all in order to improve system reliability  
* Observability is a mission-critical need for software applications, infrastructure products, B2B and consumer products which have websites and mobile apps and need them to be running with minimal downtime \- so their customers are happy  
* These companies have Service Level Objectives \- guidelines for minimal downtime \- e.g  
  *  “3 nines” (99.9% uptime \- maximum 8.7 hrs downtime allowed per year)  
  * “4 nines” (99.99% uptime \- maximum 52.56 minutes downtime allowed per year)  
  * “5 nines” (99.999% uptime \- maximum 5.26 minutes downtime allowed per year)  
* Every company needs Observability. However, the spectrum of importance given to it differs from company to company \- some companies just care about their core business metrics i.e they don't spend too much time analyzing observability of their systems as long as their business is growing and customers are happy. At the other end of the spectrum is companies which take observability seriously and have strong data-oriented practices  
* The three fundamental “pillars” of observability that companies track are:  
  * Logs \- detailed records of events  
  * Metrics  \- CPU usage, error rates etc   
  * Traces \- data representing the journey of a request 

**CATEGORY**

* Companies use “observability platforms” to help them store, query and analyse logs, traces and metrics   
* Think of an observability platform like a health monitor for websites and apps. They are mission critical when a system breaks down as companies need to be able to look at the most accurate data, query it for what went wrong, debug issues quickly so the system can be back up quickly and also analyse issues so they can fix them better  
* Observability is the 3 largest line item in a company’s cloud budget \- after people costs and cloud infrastructure costs.   
* The budget spend on observability platforms is often a big line item. Companies spend roughly 20% of their cloud spend on observability. Roughly 60% of this amount goes towards logs, 30% towards metrics and the balance towards traces and other needs  
* Budgets are not determined based on company size but more by number of customers/customer usage/how fast the company is growing  
* Key factors/painpoint influencing vendor choice:   
  * Amount of logs you want to store and check from \- some companies want logs for the previous 30 days, average customers look for 60-180 days while the more compliance heavy companies can even go up to 1-2 years of storage  
  * Reliability \- fundamentally, the availability of all the logs, especially when usage spikes and an issue occurs  
  * Price \- obvious, given the budget spend on observability  
  * User experience \- especially relevant when you are running in multiple  cloud platforms and need to bring all data together   
* The key category tension is the choice and compromise between the amount of data a company wants to store and the price they are willing to pay for it

**COMPETITIVE PLAYERS**

1. Native observability solutions from cloud providers  
   * AWS Cloudwatch (starter pack) , GCP Observability suite, AWS OpenSearch (for high end analytics/log volume)  
   * Preferred by startups as an add on, not too many features   
2. Open source observability tools \- usually a “bait” strategy to get developers to use them before the volume of logs becomes high enough to sell more  
3. Managed service Observability platforms  
   * Datadog: category gold standard, storage is on SSD Disks. Expensive. Have added features like real user monitoring and security (ingest security logs). Datadog’s biggest problem point is cost \- especially seen when customers get hit with unplanned additional bills \- for eg when one of their developers queries a high number of logs without knowledge   
   * Elastic:   
   * Grafana: known for metrics; invested in AI capabilities; also has Loki as part of their ecosystem (Loki is the backend storage system while Grafana is the front end visualization). Loki’s use case is that it is an open source tool and is an add-on for log storage with Grafana. Loki’s ux is not good \- does not include features like free text search, especially relevant for engineers  
   * Clickhouse: popular and trusted. But serves analytics use cases. Observability is just one of their many use cases; have a Clickhouse Cloud offering which uses object storage (as an alternative to Datadog’s method) \- only partly solving the data fidelity:cost problem 

* Most competitors prefer a PLG to SLG motion as a sales tactic \- they offer open source tools for devs to try and get comfortable with. Once they notice that the data/logs reach a certain threshold \- around $5k a month, they enter with sales and try to sell a managed services platform to the customer  
* Given Datadog’s primacy \- most competitors focus on switching from Datadog  
* The category is crowded with competitors promising “Datadog alternative” and “‘lower price than Datadog”. Most do not deliver, leaving customers with PTSD and low trust in category except for the established players  
* Another trend is promising “native AI capability”

**CUSTOMER**

* Any company using some form of observability  
* $10-20 mn cloud infra spend on AWS or GCP  
* Series A ($40 mn+ funding) to companies that recently turned public; around 200-2000 employee size  
* Priorities:  
  * Want to improve the overall reliability of their product \- want to hit a 3 nines or 4 nines availability  
  * Want to improve the ability at which they can ship faster  
  * Want to be cost efficient (data usually grows 1x-2x faster than their business is growing)  
* Avg $250k- $ 1 mn on observability spend   
* Personas:   
  * Buyer audiences: Head of Engineering, CTO, Head of Infrastructure, Head of SRE  
  * Tech champions: SRE team, Sr. Staff engineer for dev ops team/platform engg, (they may come from one department and play the role of technically qualifying the product as well as evangelising it to other teams. They are usually the first ones to notice data fidelity pain points  
  * Influencers: Platform teams have a huge role to play to ok a migration. 3-5 senior engineers act as a counsel  
* Customer insights  
  * Tend to have a “hodgepodge” of tools \- e.g. Grafana for metrics, Splunk for logs and Datadog for application performance, management or advanced tracking  
  * Multicloud environments may be using multiple observability platforms, usually from the cloud providers \- an environment complexity challenge as the features do not match and customers find it hard to get a “single pane of glass” observability view across their stack  
  * The more serious companies may even “double-write” \- use more than 1 provider for the same stack as a failsafe  
  * Category is priority for them but brand switch is not \- hence even when they have pain, they wait for the pain to really hit the threshold ceiling before they think of switching; and even then experiment with one cluster/department before fully switching. But once they reach the threshold, they act swiftly to change    
* Potential segments:  
  * Observability seriousness \- highly data driven vs only business metrics driven  
  * Tech stack: Kubernetes, AWS, GCP, Cloudwatch  
  * Industry verticals \- non regulated vs regulated (regulated care about data fidelity more)   
  * Competitive segmentation \- Datadog users vs Grafana users vs Elastic users   
* Tipping points that may lead to brand switch thinking:  
  * Reliability : “I don't have logs when I need them”  
  * Pain and operational heads, especially for self-hosted customers to keep systems up and running   
  * Cost / contract shock: CFO complaint that the observability cost has become too high  
  * Contract renewal time  
  * Fragmentation fatigue: using different observability stacks for different clusters and unable to get a single pane view   
  * Series A/seed stage company growing very fast and still only on a cloud provider’s observability platform  
  * Using multi cloud and hence the debugging pain resulting from having to know which platform to go to, learn the tool and then debug  
  * UX performance is too slow \- queries take 30 secs/1 min to get answers

**INTRODUCTION TO OODLE** 

* Oodle was set up in 2023  
* Founder came with previous observability experience  
  * Started a previous observability platform named Neptune in 2013 but shut it down as it did not find PMF  
  * Worked as Head of Observability and Platform Engineering at Rubric and gained first hand knowledge of the observability ecosystem in a large company  
* Learning from the Rubric stint:  
  * Rubric scaled quickly to $.5 bn \- and the observability spend grew 20x in 4 years  
  * Overall data complexity and speed of debugging became major issues to deal with \- due to the complexity of business (many microservices and how they track with each other  and tech architecture (on prem/cloud/multi cloud)   
  * In these 4 years, the teams had to internally invest significant bandwidth and make constant trade offs in order to control budgets \- trade off between cost and having the full data fidelity to debug issues a lot faster  
* Founders spoke to about 30-50 other companies and found the problem to be near universal  
* This learning led to the founding of Oodle with **a clear mission: remove the trade off between full data fidelity and cost**  
* There were also “founding” learnings from the Rubric experience \- go where there is a massive market, a differentiated tech product and a clear urgency/why now rationale  
* The name “Oodle”   
  * derived from an internal acronym \- Optimized Observability Data Lake  
  * Sounded cool/rhymed with poodle  
  * Oodle also means “lots of” 

**PRODUCT:**  

* Based on the experience with their past observability startup Oodle designed the product with the first principle of not just providing incremental advantages over existing products but designing a fundamentally new architecture to solve the trade off between full data fidelity and cost   
* The basic problem was apparent \- data was being stored in disks which drove up the cost of storage. However, analytics which has 10x-100x more data could be stored in an object storage layer (a flexible, highly scalable storage architecture which uses flat structures rather than hierarchical folders). Hence the first observation was to use object storage layer   
* The next level question was to see how accessing and querying data could be made faster. The co-founder had expertise in file systems in the object storage layer and innovated a file format structure purpose-built for observability. Key product insight used here on how observability data is used  \- (a) customers care about recent data more than older data and (b) time is a natural dimension in observability data \- e.g. “I need to know what happened in the last 2 hrs” © observability data is highly compressible \- text heavy (4) it needed to have fast aggregations  
* The innovations of serverless systems was another wave that added to the ability to solve the problem \- Oodle built serverless on S3 (modelling on other innovations like Leon on S3)   
* AI (“AI is the new UI”) was the next wave that helped Oodle add better UI and additional analytical capabilities on top  
* One strategic decision the company took was \- rather than lose focus innovating on everything, they innovated on the storage and the underlying database engine but forked Grafana (metrics visualization layer) and AWS OpenSearch (the gold standard for logs). And combined the experience into a unified product   
* The end architecture is a genuine differentiator in the industry \- really delivering unlike fake competitor claims on both data fidelity and cost. It will take a high caliber team at least 2 years to replicate. (Note: Even clickhouse could solve only the storage part of the problem but not the fast querying)    
* The architecture simply separates storage from compute. Because people mostly query only their most recent data, the architecture exploits it by not running the compute all the time \- customers get to pay lower and only pay slightly more for each query   
* Key product features:   
  1. Plug and play which can integrate directly into customers’ existing observability stack (no need for new visualizations, training etc. Migrating into Oodle is easy)   
  2. Cost effective \- 5X lower cost than any competitor  
  3. Ability to store 10x more data   
  4. 100% open standard  
  5. AI native \- truly AI native way to debug their incidents  
     * AI conversational interface where customers can ask any question on their data vs staring at multiple dashboards trying to make sense of what they see  
     * Automatically generates an automatic incident report that helps investigate issues much faster  
  6. Drop-in replacement for Elastic and Grafana   
  7. Helps unify multiple stacks into one system (particularly relevant for multi cloud environments)  
  8. Customers can go live within 10-15 minutes (usually takes 5 hours of effort over 2-3 weeks to switch an installation)  
  9. Also includes added features like user and usage monitoring which helps customers who in the team is using the most   
* Product demo: specially for Elastic users for logs  
  * Use Fluent or Vector, drop a few lines of configuration and this “double-writes” everything to Oodle; logs are lightweight (vs metrics) and there are not many assets to import except in a few case   
  * Especially for Elastic customers \- they will find it feature rich on Day 1 itself compared to Elastic   
  * Migrate out is as easy as migrate in (for customers worried about what to do if they have to switch from Oodle) \- all the logs can be stored in their own S3 bucket   
  * Additional optimization can be done over time (additional configurations they may have done to improve Elastic performance)   
* For Grafana users using Kubernetes clusters  
  * Enter the Kubernetes cluster name, get a config file and run commands on the Kubernetes cluster and all logs will be shipped to Oodle   
* Cloudwatch users need a little more infra before they can switch  
* Once customers see success they can then integrate more clusters \- usually takes a 1-2 week timeframe (e.g. Olive, a customer sent 20 tb per day and Oodle cut over within 2 weeks)

**PRODUCT: OODLE VS COMPETITION**

| COMPETITOR  | OODLE COMPARISON |
| :---- | :---- |
| Datadog | 10x lower cost \-  Cost compromises: with Datadog, customers have to turn off features in order to control budgets \- impacting full data fidelity (e.g. monitor only 10 out of 100 websites). Or shut off granular needs \- tenant level monitoring or customer level slicing and dicing. Datadog also leads to unpredictable pricing experiences (e.g. one spike from a dev and the customer gets a $5k bill). Custom metrics (customer id/tenant id/user id/service id) are expensive 10x more data: higher data fidelity at the same budget \- hence insights become richer Object storage vs disk based architecture \- serves the “bursty” nature of queries  Datadog locks you into their proprietary platform while Oodle is open standard Datadog has similar AI capabilities Datadog has consolidated security and observability into one play which Oodle does not have  Datadog offers real user monitoring which Oodle plans to add in a couple of quarters  |
| Grafana | Better UX Cost AI native Straight drop in replacement/onboarding is faster |
| Elastic | Much better reliability at scale  Oodle can run 10X faster queries AI native Straight drop in replacement/onboarding is faster |
| Others  | Clickhouse \- Oodle is end to end observability while clickhouse is more focussed on database. Oodle solves both the database and the compute problem while Clickhouse is restricted to the former  Self hosted \- much better reliability (they see logs dropping if they drop 7 days worth of logs) Managed service \- cost is the advantage here. Plus architectural limitations  |

**INPUTS INTO POSITIONING/VISION/PURPOSE**

* “We wanted to remove the trade off between full data fidelity and cost”  
* “Think of the Observability space as a health monitor \- it is mission critical \- the vitals have to be accurate and become relevant when your system breaks down”  
* “Companies which we admire are Datadog (for its transparency), Snowflake (which did the same thing with data warehousing) and Databricks”  
* “We want to be transparent in every customer interaction \- promise X and deliver X. This is a critical need in a category where most players have made similar claims but not delivered to customers”  
* “Our reliability and availability is an order of magnitude higher than customers’ own applications so they can trust us to be relevant when they are down”  
* “When we built the product, we realized that an incremental approach was not going to cut it. We had to fundamentally alter the architecture.”  
* “Our customers have found us to be true partners in solving their observability issues rather than vendors \- they love how we put customer problems front and centre. Our team has proven to be good at handholding customers and being available to them. Customers love the pace and speed at which we operate in terms of launching features and custom features for them”

**SALES/MARKETING**

* So far, all sales has been through network \- investor intros and direct network contacts  
* Learning sales principle from Rubric: “If the prospect has not agreed with your pain point description within 30 seconds, he will not become a customer”   
* Limitations:  
  * Trust is critical in this category \- the larger the company, the more the trust. Hence Oodle has prioritized smaller companies rather than enterprise level selling  
  * A related “artificial” constraint \- focus on prospects where the sales cycle at max is between 90-120 days  
* The sweet spot as per the current customer list:   
  * 90% of customers (around 10\) pay $40k-$110k per year  
  * 80% are annual contracts; 40% are multi-year contracts  
  * Some small scale customers \- paying around $5-6k per year  
* Sales process:   
  * Approach buyer/tech champion through network to understand painpoints  
  * Customized deck targeted at buyers   
  * The first hook is Playground \- it’s public and customers can experiment with a meaningful scale and run on it without even entering an email id. They can check entire performance, scale and cost efficiency  
  * Next stage is a 2 week POC with well defined success criteria, meeting cadence and points of contact.   
    * Helps prospects understand if it can work on their environment, can they trust the company to be around, does it work at scale, are there any rough edges, is it prepared for a “migrate-out” scenario i.e if they want to pull the plug from the Oodle  
    * Always starts with logs as the first use case \- easy to switch, the customer has to just drop in a few lines of code and the entire logs show up on Oodle  
    * Starts usually for one cluster/department. Or try out a new workload or product line with Oodle  
    * No payment for POC. Flexible to ensure “no double payment with existing vendor” in case the prospect still has any doubts  
    * Includes a “bonus/surprises” experience for customers \- e.g. cost and usage attribution, ai detection of anomalies   
    * Upsell/Expansion motion \- once the POC is successful, customers expand \- deploy it for more clusters/departments, expand to traces and metrics, consolidate all data under Oodle \- this happens with very little sales motion \- a testament to how good the product is  
  * Oodle enjoys a 90%+ conversion from POC to signup  
* Customer acquisition stories:   
  * Lookout: a cybersecurity unicorn serving 2k+ enterprises. Datadog customer, came through investor contact. Cared heavily about security. Heavy focus on data and observability. Datadog costs were getting higher and they were turning off features. They were on a fast migration path and also wanted to “influence” features provided by vendor. Training was an issue (10+ years of Datadog) They also wanted a vendor they could walk away from if not happy (they had a backup migrate out plan). Had 3500 nodes/3000+alerts/300+ dashboards which Oodle took 6 weeks end to end to run in production \- a complex installation involving 80 AWS accounts and 100+ GCP projects. Lookout was blown away by Oodle’s timeline and cost savings (5x). VP Engineering took the call, senior engg manager was the tech champion  
  * Olive: microfinance for middle class families \- sensitive about PII data. Self hosted. Concerned about reliability \- they were missing out on logs. Oodle provided the reliability at a small premium over self hosted  
  * Fuel Labs: Young startup with $80 mn+ funding. Using both Cloudwatch and OpenSearch and double-writing for logs. The UI was good but not reliable. Concerned about scale \- 500 gb of logs Cost was an issue as well. Oodle started with dev cluster and has now replaced the entire stack. Their next level use case was to unify multiple Grafana stacks (and the challenge of replicating every time they spin up a new environment). Oodle unified everything under a single pane of glass plus also gave them cost and usage attribution. Log volume has expanded 5x. CTO was the buyer

* Core ICP for targeting:   
  * Replacement for Elastic or any Elastic like offering (e.g. AWS OpenSearch)  
    * We are also an OpenSearch fork  
    * Elastic users have already shown openness to shipping logs to a managed services vendor (so no security concerns)  
    * No change in buying/paying process: customers who want to switch can go to Marketplace and route the $ to Oodle  
  * The best messaging wedge is: single click elastic replacement/opensearch replacement/managed opensearch replacement for logs

* Marketing initiatives:  
  * Excellent website \- blogs, customer case studies, “x alternative” pages, pricing, technical docs  
  * Initial messaging was around cost but deprioritized later as it was more a buyer problem than a user problem  
  * Marketing efforts have included linkedin ads/google ads (Datadog alternative/debug with Cursor etc), Hacker News (which brought one engagement through reposting by a colleague), mid/small events \- SRE Con, dev ops days etc \- again engagement but no conversions, likely because in conferences we only get one persona at a time  
  * Haven't done strong follow ups even when there was some engagement  
  * Competitors are bidding heavily on “X alternative”. Everyone is going to the market and saying “lower price/better than Datadog”. There is customer PTSD on this issue \- is there any way to exploit it  
  * Have 4-5 email domains warmed up on Instantly but haven't done outbound campaigns yet

* Marketing bucket list/want to try/learning  
  * Currently prioritized sales-led motion as PLG needs focus and people/product investment. Definitely want to do PLG but closer to our A round plus when we shrink time to value for our large customers  
  * We don't mind experimenting but at some point we want to pick a lane and stay with it.   
  * Want to try out:  
    * Messaging: “Rise of AI has changed the rules of observability and existing methods don't work any longer” \- this is our fundraising narrative, unique to us (with the possible exception of Clickhouse) and difficult to copy.  We would like to test it as a long term positioning  
    * Potential to name the architecture and make it front and centre of the messaging/selling with prospects as well  
    * Should we change our motion from the current buyer first and move to user first, learn the problem before going to the buyer   
      * Reach out cold to engineering/buyers and ask for review/advice on what we are building  
      * Power moves like connecting with tech champions on issues they care about (e.g we saw you said x, we have done…” \- social listening)  
      * Content around observability without selling anything  
    * We have so far been thinking about the replacement market. Should we go after smaller companies who are using their cloud providers observability platforms (e.g. AWS/GCP) and convert them  
    * Add on use plays:   
      * Kubernetes Observability  
      * Synthesis monitoring (different urls to be monitored)  
    * Can we go after companies which are running self-hosted with price as an attack vector?  
    * Industry verticals like fintech/ecomm/saas that care about margins . if they provide software to others, their own availability becomes important. \+ if they are growing fast but have no time to instrument observability or don't have the expertise and are looking for a quick drop in  
    * Can we exploit customer PTSD with category? E.g. go after companies who switched to competitors 2 years ago and hit them with a transparency message? (based on customer PTSD with   
    * Use status pages as a signal   
    * Executive dinners  
    * Reddit de-anonymization/Discord/Slack channels

**WHAT KEEPS THE FOUNDERS AWAKE AT NIGHT**

* Short term:  
  * Our most immediate challenge is to scale the GTM motion \- how do we create demand to get a qualified pipeline that can complement our POC to production conversion rate \- we are trying to find out a “repeatable demand generation engine” so we have a constant flow of POCs at a faster rate  
  * We worry the longer we take to approach the right quality prospects, the more we are leaving money on the table. We are clearly looking for a 90-120 day sales cycle  
* Mid/long term:  
  * From Day 1, we have always wanted to build a large, enduring business  
  * Our aspiration is to become the observability layer for companies so they can accelerate their innovation and serve their customers better  
  * We want to think big \- how can we create a category reset moment , especially near our Series A

