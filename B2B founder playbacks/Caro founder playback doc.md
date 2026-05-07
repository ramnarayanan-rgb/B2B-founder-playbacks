**CARO : BUSINESS BRIEF**

**CONTEXT \- RECRUITMENT** 

* The lifecycle of a candidate who is being recruited into a company \- either as a new hire or as a backfill (replacement for a candidate who has left)   
  * Finance creates a budget for each department at the beginning of the financial year \- e.g. this year, we have x money to hire y number of candidates  
  * Each business owner (engineering/sales/..) knows how many candidates they need at what seniority level and briefs the recruitment team for what they need when  
  * (or) HR triggers replacement of backfills \- for people who have left  
  * Finance approves the budgets and gives recruitment teams the salary bands within which they can hire  
  * The recruitment team then hunts for the new hires/backfills and manages the entire process (recruitment/interviews/salary negotiations/relocations (e.g. work visa needs etc.) in co-ordination with the respective departments  
  * Once the candidate is identified and joining date is agreed, HR takes over the onboarding and finance creates the payroll for the candidate  
* While this is a normal process for all companies, this becomes a significant dynamic collaboration problem especially for tech companies, once they hit around 700/1000 employees size and start hiring around 300 candidates a year. The factors that lead to this are:   
  * Hiring mix changes: The hiring mix is an ever-changing mix: Recruitment teams will have identified candidates by which time a department leader decides to change the need (e.g. from senior titles to more junior titles or vice versa)   
  * Executive decisions:Large changes to product/engineering plans, hiring freezes, new revenue sources etc would mean immediate large scale changes to the hiring they need   
  * Confidentiality:a senior executive has left or is being replaced; backfill needs to be triggered without recruiting teams knowing who  
  * Budget management: salary/seniority mix/numbers/joining date changes lead to anomalies vs the budget which finance finds hard to manage   
  * Uneven monthly hiring numbers: the recruiting team has a capacity to hire say 120 people a year but that does not mean an even 10 hires a month. One month may see a lump in the form of  50 hires which the recruitment team simply does not have the capacity to manage  
* The fundamental problem which literally every single company faces is seamless collaboration through the recruitment hiring lifecycle     
* It is an extremely hard problem to solve because it is a multi-party problem : different teams (finance/recruiting/HR) with different priorities/“horses in the race” \- finance needs to manage budget, recruitment needs to hit quotas, HR needs backfills filled quickly and business teams need the right mix for growth at any given point of time

**THE CATEGORY**

* The fundamental need is one of “observability” \- the ability to have all the data in one place that can lead to efficient recruiting  
* Each department in the company uses a different source of truth that feeds into recruitment \- e.g. Workday for HR, Anaplan for Finance and Greenhouse for ATS, they don't talk to each other \- the challenge is the collaboration \- companies don't have a way of putting all the data together in one place dynamically based on which decisions can be made  
* The category does not have a defined name is named either “Headcount management” by smaller companies, mid level teams or “Workforce Management” in larger companies/senior executives  
* While there are many small players that exist in this category, it remains deeply underpenetrated category \- every single company tries to solve the issue through google sheets or through some internal workaround  
* Key category dynamic \- 100% of the companies face the problem but the category is still deeply under penetrated

**THE CUSTOMER AND SEGMENTS**

* Primarily tech companies \>700 in employee size, hiring 300+ (new hires+backfills) a year. It has been noticed that they fall into two broad segments:  
  * Fast growing tech companies (700/1000 employees) with significant expansion plans and high hiring velocity, usually around raising Series B \- Open AI is a good example. Sometimes, there would even be a 300 employee company (e.g. Cursor) that wants to expand to a 600 employee company At this time, they worry less about the budget management and more about how quickly recruitment is in place. In such companies, mid level Recruitment team lead is the target  
  * Large companies (5000/10000 employees) where the hiring is high but stable. The priority here is budget management and finance teams take the call  
    

**CUSTOMER PERSONAS** 

* Key signals: tech company, Min size 700, hiring 300+ a year(LinkedIn insights), has a defined Recruitment team.   
* Tech signals: Workday for HR, Anaplan for Finance, Greenhouse for ATS; an added signal is that companies also have a dedicated “Workday team” to manage workday Ops  
* Verification signals: company news. (e.g. linkedin insight shows hires growth in the last six months but the company has decided on a hiring freeze)  
* In tech companies, it is usually engineering teams that need the most hires, but other teams like sales could also be making large scale hires  
* Entry personas \- mid level: Director of Recruiting Ops (or) Director of FP\&A  
* Budget owner personas: Head/VP of Recruiting, VP Finance/FP\&A  
* Executive personas: CFO, Chief People Officer   
* Persona insights:   
  * The big priority for these companies is “how do we move fast and make the changes we need to get there?”. This is ironically also the reason why the recruitment process is so hard to manage  
  * Collaboration is the biggest challenge:   
    * Each persona cares about its KPI more than the collaboration: (1) finance cares about budget (they call it “envelope”)/cost control (2)  recruitment cares about hitting its hiring quotas (3) HR cares about backfills and org structure   
    * Finance is good at numbers while recruitment can never get their numbers right  
  * No team wants to be seen as the “bad guy” \- so they do help (e.g. engineering wants to hire x people while they have approvals only for Y. Finance tries to help by pointing out that there are backfills approvals available which they can use)  
  * Most usually, Recruitment and/or Finance teams take the lead in deciding they need a solution. HR acts more like an “advisor” \- especially org structure level  
  * The problem is most deeply felt by mid level recruitment and finance personas as they are the ones who have to act.   
  * Executive  personas need “summary data” for decision-making and don't want to look at rows and rows of google sheets to get there (e.g. we needed to hire x people, what is the status/we want to make a change \- what is the current status of what we have already hired etc)  
  * The imperative at the executive level is to show up with “value” \- do the storytelling around their performance rather than excuses. For eg. if the recruitment team has not hit the quota needed, they need to show that they only had approvals from a particular month and present how they performed against the approvals they have been given \- 99% of the time, the data needed here is not available  
* Tipping points:   
  * Once the hiring size reaches around the 300 mark is the first tipping point that they cannot manage with google sheets any more  
  * Timeliness of information becomes crucial \- executives want some information and it takes days to find, verify, organise and present.   
  * At the executive level,accuracy of data is also a tipping point \- either finance or recruitment executive leaders lose their credibility if they share wrong information based on data created by their own mid level teams 

**COMPETITIVE PLAYERS**

1) Read-only solutions \- they are bespoke, they solve the observability problem but they are not dynamic.   
1. Spreadsheet: Base level competitor/existing state is the spreadsheet. The fields are mostly similar across companies \- list of hires, cost approval status, updates (interviewed/hired/repurposed). It is manually updated periodically. It allows for comments (on changes needed). As the hiring grows, one spreadsheet for the company becomes a multi-tab spreadsheet \- one for each department. Every single company uses a spreadsheet  
2. Airtable: Once a spreadsheet becomes hard to maintain, the next level of sophistication is Airtable \- to add simple workflows \- e.g trigger a slackbot to notify people  
3. Homegrown workflow: Use Workato on Workday data and finance data, put it into Databricks and into Tableau  
2) Custom apps \- built on top of Workday to show the data they need \- these are much loved but again don’t solve the whole problem fundamentally due to cross team empathy \- the builders build for their department and don’t account for the needs of the other departments  (i.e if HR builds it, it integrates only with HR software and is not useful for other teams). However, this might be one of the biggest competitors as teams tend to think build first and not buy.   
3) New but likely to increase in conversation volume within companies \- vibe coding solutions internally  
4) Workday/Anaplan to see if they have any additional workflows that can help. These solutions exist but just like custom apps, they solve for one department and the others find it hard to use/accept it  
5) Multiple small startups in the space:   
   1) Team Ohana: Around $1.5-2 mn in size. Started with small accounts ($20k value) but has recently shifted to going after bigger businesses. Their solution leans a bit towards finance. The founder is a salesperson. Marketing uses words like “workforce intelligence” to describe the category. Polished website but SaaS era sensibility. Have started adding functionalities like chatbots where VPs can just ask questions on top of the data and get answers  
   2) Headcount 365: led by ex head of Talent at Uber. Extremely good content on the website. Like Team Ohana, moving towards bigger contracts  
   3) Players like Truplan and Trace which have either shut down or acquired 

Overall \- there are constraints on both sides of the solutions. Sheets/airtable etc are bespoke and collaborative but not dynamic. Custom apps as well as other competitors on the other hand, lean towards one department more than the other

**INTRODUCTION TO CARO** 

* Caro was set up in 2023  
* The idea was to find ways to help companies save money \- as the market was in a bad place with layoffs etc.   
* In Year 1, Caro did not write a word of code \- they just cold called prospects on LinkedIn with a few hypotheses in mind. Initial finding was that saving money was a crowded space \- software licenses/travel spends etc  
* A key breakthrough was when one prospect said, “75% of our spend is on people. And the way we manage them \- spreadsheets \- has not changed in 20 years”. This led to the idea   
* Even here, there were already HR & Payroll systems. The entry point came from another customer conversation \- “if we budgeted for a hire in March but recruitment happened in Feb, we lose $10k. If this happened multiple times in a 1000 person company, we would end up being wildly over budget or wildly under budget. And that’s what finance teams would like to track to a T”  
* Caro is today a $1 mn company with a roster of around 10 paying customers including Open AI Figma, Discord, Affirm, Native, Intercom, Motive  
* Avg customer pricing: $100k ARR. Pricing today is per seat

**PRODUCT:**  

* Product built around Initial product lens hypothesis: the spreadsheet is breaking due to 3 reasons  
  1. Integrations: manual work pulling the data together did not work because things are changing all the time (hence integrated Workday/Anaplan/ATS)  
  2. permissions/RBAC: the problem was that spreadsheet data was visible to all \- senior staff compensation, forced replacement, new senior hires, other department salaries etc. Companies were trying to overcome this with things like secret spreadsheets/multiple spreadsheets etc we built a complex role based permissions model  
  3. Approval and auditability: spreadsheets were not good here, especially on what people can and cannot change (e.g. can change the offer amount but not seniority level). We built approval workflows  
* The key product innovation: a common schema that helps a company build “the lifecycle of a hire BEFORE he joins the company  
* We realised that we were building only a “better spreadsheet” which did not show enough incremental value for customers to buy/did not win us the “build vs buy” argument  
* Current version of the product has 4 components:   
  1. Headcount: the baseline transactions of all movements which has maximum PMF. In itself, complicated \- hires \- who’s leaving/joining, summary information, attrition, internal mobility  
  2. Recruitment: for the recruiting team to look st capacity, matching supply to demand, recruiting quotas and performance   
  3. Envelope: for finance to see how each org (eg legal/engineering) is tracking against their budget. Finance has Anaplan but cant ask orgs to yse that to find the information   
  4. Scenario planning: our version of Charhop \- a scenario builder where departments can pull their existing teams, make org chart changes and look at cost implications of such decisions. This is a valid feature but very less used as companies don't do scenario planning every day  
  5. Also built a “lifecycle view” \- which helps companies track the status of any candidate through their lifecycle. Early feedback- customers like this view  
* Product roadmap Caro is working on::  
  1. By solving observability, we are also solving lifecycle as we already have the data  
  2. hence, workflows. E.g. The plan was for an engineer but we see that the recruitment plan was for staff. Can Caro fix it? Or the role exists but needs the specs/JD to input into the recruiting systems. Or a candidate is approaching the offer stage and needs a visa \- so kickstart the process with the legal team. Or candidate verification for compliance reasons. Or analytics that HR is heavily into but Workday is bad at. Trying to surface and solve these issues through creating mini agents that customers can spin out and use  
* Constraints for sales/company size targeting:   
  1. We integrate only with Workday \- companies especially in tech get into Workday when they get into a 700/1000 employee size  
  2. Workday has an elegant methodology they call “Position management” \- basically every position is called a “chair” \- people can come and go but the chair is the true unit and remains. We integrate with Workday because we hire for the chair this quarter  
  3. Because of this approach, we can't integrate with other systems and are not able to serve customers who don't have Workday (e.g. Cursor \- a 300 person company, wanted to hire 400 but we could not solve for them because they are on Rippling)

**INPUTS TO PERSONALITY/TONE** 

* “We initially did not write a line of code \- we first cold called companies to understand the problems they have that needed to be solved”  
* “We had a few problem hypotheses and needed to prove/disprove them   
* “ We tried to solve the observability problem logically \- step by step. We found 3 issues and set about solving each issue one by one”

**INPUTS INTO POSITIONING/VISION/PURPOSE**

* Caro is the only product that is “bidirectional” \- most other systems integrate only with a HR system or a payroll system  
* Caro is the only system that is dynamic/real time   
* Every department has its own source of truth (Worday/Anaplan etc). Caro is the only collaborative source-of-truth for recruitment

**SALES TECHNIQUES**

* Use LinkedIn to find prospects and message them  
* Approached only companies in the 700/1000 person mark due to the constraint that we only integrate Workday (and hence their broad customer range)  
* No sales deck, walk in with a demo  
* Caro has touched around 80 prospects so far out of which the conversion has been 10  
* Seasonality \- Q4 is a bad time to sell. Other quarters are ok  
* 60-65% of our customer base came through recruitment while 30% through finance and 5% through HR  
* Specific prospect/customer learnings:   
  * Roblox \- 2500 person company: spoke to Head of Corp FP\&A as it seemed finance was leading and Recruitment was following. Fell off as they were building something on their own as they built a lot by themselves.   
  * Okta: 7000 person company met the Head of Recruiting Ops and Workforce planning \- a formalised role at this size. He was able to sell us to his boss but not finance. Learning \- we need a savvy champion in the company who is able to “work the system”   
  * AirBnB: 8000 person company \- needed exactly what we had. Our learning was that we tried to sell the kitchen sink to them (Headcount/Envelope/) but in that size of company, even one of these needs is a big problem to solve by itself. They needed only scenario planning and went with ChartHop which was a visual org chart builder   
  * Figma \- the buyer was head of Recruiting Ops. VP signed the contract. Hiring budgets was not an issue for Figma. The tipping point however was the mistakes in the data which made them look for a solution  
  * OpenAI: not representative but interesting case. Hiring around 3000 people with hiring budgets not being an issue. However, Finance was involved because they were thinking about long term control needs 

**MARKETING** 

* Basic website that looks like a landing page with 3 blogs  
* Focus on the 150 prospects but open to experimentation  
* Marketing approach \- since the company has a limited customer list, there is no point in driving a bunch of people to the website. We would rather be super targeted about this


  
**WHAT KEEPS THE FOUNDER AWAKE AT NIGHT**

* We feel we have room to grow to $5 mn \- $10mn in revenue  
* Why are we not growing at 5x year on year, when the problem definitely exists? We know for sure that that the problem exists, but worry whether the category has a future, given how hard it is to convert customers as well as the underpenetration of the category itself  
* We have a real fear that very few companies are actually going to need our solution  
* Why are we unable to unlock growth in spite of 100% of the companies facing this problem  \- is it the product, the marketing or the go-to-market?  
* What is the description that describes the category’s best value \- Headcount management is the real PMF but is undervalued by senior titles. Bigger companies call it “Workforce planning” but it may be a misleading term   
* Who is the rightful owner of the problem in the company? How do we manage messaging for different personas which is really a 4-way Venn diagram? What is the headline we should put on our website?  
* How can we quantify value/ROI to executive level personas? Hours saved is not a good measure. Is there a way to quantify the impact of delivery on the recruitment plan?  
* Product:   
  * Should we continue to think about new features that solve the next level problem? especially if they are not gaining as much PMF as the base headcount feature? Or should we double down on what’s working?  
  * What is the AI play here? Does the observability problem stay forever or will it evolve over time?  
* Short term go-to-market goal: we have curated a list of 150 companies that fit our criteria and need personalised ways of keeping in touch with this list. (e.g. ABM personalisation for Stitchflow) 

